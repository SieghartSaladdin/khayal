# How to measure

Measure in a real browser. The desktop app's preview pane shows local files as static snapshots, so it cannot measure frame rate, console output, or transfer size. If only that pane is available, write "not measured" for the runtime metrics and say why.

## Setup

- Serve the ID folder over local HTTP (for example `python -m http.server 8080` run in the background from that folder). Pages opened from `file://` report a transfer size of 0 and block some features.
- Use Chrome with devtools access (performance trace, Lighthouse, emulation, console, network) when the tools exist.
- Keep the tab in the foreground. Background tabs throttle `requestAnimationFrame` and make frame rates meaningless.

## What to record

1. **First-try success:** yes or no, plus the number of fix rounds and what each fixed.
2. **Console:** every error and warning, verbatim.
3. **Frame rate:** run the snippet below once idle and once while scrolling. Record average fps and the 99th-percentile frame time. If the tool supports CPU throttling, run again at 4x slowdown.
4. **Transfer size:** run the second snippet, and for cross-origin files (CDN libraries, fonts) use the network tool, because the browser reports 0 for them without a timing header. List the three largest files.
5. **Mobile:** viewport 375 by 812. No horizontal scroll (`document.documentElement.scrollWidth <= innerWidth`), tap targets at least 44px, nothing covering content. Take a screenshot.
6. **Reduced motion:** emulate `prefers-reduced-motion: reduce`. Content is visible, nothing loops.
7. **No WebGL** (for any technique using WebGL): inject `HTMLCanvasElement.prototype.getContext = () => null` before the page loads, then confirm the fallback appears and the page is usable. If the tool cannot inject before load, mark it not measured.
8. **Keyboard:** reach and operate every control with Tab, Enter, Space, and Escape, with visible focus.
9. **Lighthouse:** performance and accessibility on the mobile preset. Run twice and report both, because lab scores vary.

## Frame-rate snippet

```js
const measure = ms => new Promise(res => {
  const d = []; let last = null, start = null;
  function f(n) {
    if (start === null) start = n;
    if (last !== null) d.push(n - last);
    last = n;
    if (n - start < ms) requestAnimationFrame(f);
    else {
      d.sort((a, b) => a - b);
      const avg = d.reduce((a, b) => a + b, 0) / d.length;
      res({ avgFps: +(1000 / avg).toFixed(1), p99FrameMs: +d[Math.floor(d.length * .99)].toFixed(1), frames: d.length });
    }
  }
  requestAnimationFrame(f);
});
const idle = await measure(5000);
let y = 0; const max = document.documentElement.scrollHeight - innerHeight;
const timer = setInterval(() => { y = (y + 40) % Math.max(1, max); scrollTo(0, y); }, 16);
const scrolling = await measure(5000);
clearInterval(timer);
({ idle, scrolling })
```

## Transfer-size snippet

```js
const r = performance.getEntriesByType('resource');
({
  totalKB: Math.round(r.reduce((a, e) => a + (e.transferSize || e.encodedBodySize || 0), 0) / 1024),
  top3: [...r].sort((a, b) => (b.transferSize || 0) - (a.transferSize || 0)).slice(0, 3).map(e => [e.name, Math.round((e.transferSize || 0) / 1024)])
})
```

## Reporting

Write numbers with units, the tool used, and the date. Anything skipped is "not measured: reason". These are single lab runs on one machine, so they inform the user's judgment and are not a standard. Targets such as 60 fps are guidelines, not pass or fail rules.
