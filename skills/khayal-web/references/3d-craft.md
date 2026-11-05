# 3D craft: realism and consistency

General rules for 3D and hybrid sites, drawn from debugging real one-shot builds. They are stated in general form: apply them to whatever object, effect, or scene the site has. They are patterns, not verified standards, so adjust them by what the screenshot shows.

Reply in the user's language.

## Real 3D or a trick

- If the user asks for 3D, or would reasonably expect it from the description, build it as geometry or materials in the scene. A 2D overlay, a flat texture, or a CSS effect passed off as 3D gets caught.
- If a cheaper trick is chosen on purpose, say so in the proposal, with the reason.
- Be exact about what is real. Real-time approximations (refraction, shadows, reflections) are not physically exact rendering. Never claim ray tracing, path tracing, or accuracy the renderer does not provide.

## Detail and consistency within an object

- Before modeling, list every part of the object, and decide the target level of detail for each. Then bring every part to that level: shape, edges and thickness, material, and finish.
- Parts that are small, hidden from the main angle, or functional are the ones most often left crude (openings, closures, handles, seams, joints, attachments). Check these first. One detailed part next to a rough one reads as wrong.
- Keep scale, materials, and lighting consistent between parts of one object and between all copies of it.
- Compare the result with a reference at the same angle, part by part, before calling it done.

## Effects belong to their object

- Anything that belongs to an object (particles, droplets, decals, glows, labels, attachments) is a child of that object in the scene graph, so it follows the object's position, rotation, tilt, and scale. A world-space effect placed "near" an object drifts when the object moves.
- Test it: rotate, tilt, move, and scale the parent, and watch every effect keep its place.

## Restraint and budgets

- Start sparse. Too many is the usual failure: large counts of particles, droplets, or glints read as noise, not realism.
- Write a budget per effect in `DESIGN.md` (count, size range, speed) and keep to it. Treat any starting number as a guess, and adjust by the screenshot.
- Vary size and spacing. Moving elements follow physical limits: they stop at edges and boundaries and never pass through geometry.
- Reduce first, add later.

## Model real objects from references

- For a real-world object, get reference photos from the user or from licensed sources. Use them only as reference for proportions and parts. Do not copy their textures or images into the site as assets.
- Keep a short note of which proportions are estimated, and tell the user.

## Many 3D objects on one page

- Plan before building. If the page shows many 3D objects (for example one per card in a grid), share geometry, materials, and textures across instances, use instancing where objects are identical, and use one renderer with several views, or render still images while idle, instead of a full WebGL context per object. Browsers cap active WebGL contexts, and too many cause lost contexts and jank.
- Every instance gets the same treatment (lighting, scale, interaction, loading). Count them in the audit: if there should be N working objects, there are N.
- Pause instances that are offscreen.

## A loader that actually gates

- A full-screen preloader stays until every scene needed for the first view has rendered its first frame, and fonts and key textures are ready. Not a fixed timer.
- Set a maximum wait (for example 10 seconds) after which the page reveals with posters or fallbacks, so the loader can never get stuck. Say on the loader if it fell back.
- While it is shown, the content underneath is inert, and the loader leaves the accessibility tree when done.
- Show honest progress, such as "3 of 9 scenes ready".

## Layout around 3D

- Decorative shapes (color blobs, glows, gradients) sit in a lower stacking layer than text and never cover it. Text has its own layer, and its contrast is checked over the 3D.
- Prefer one compact, consistent grid with fixed aspect ratios over elements that overlap or depend on absolute positions.
- Check overlap by screenshot at 360, 768, 1280, and 1920px. Overlap bugs rarely show at the width you built at.

## Reporting fixes

- A visual fix is done when you have looked at a screenshot of it, not when the code changed.
- If a fix is only partly real (an approximation, an estimated proportion), say so in the same sentence as "done".
