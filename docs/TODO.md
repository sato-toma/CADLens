# CADYomi TODO

## Near-term UX improvements

- [x] Filter the loaded node list by name, entity type, or ID to make large models easier to inspect.

## Node-level workflow and decoration

- [ ] Define node-level export/import behavior for STEP entities and assembly subtrees, including whether hierarchy, properties, colors, and placement are preserved.
- [ ] Export a selected node or subtree from the loaded STEP document without exporting unrelated nodes.
- [ ] Import an exported node or subtree and add it to the current document tree.
- [ ] Define a plugin-facing decoration interface that targets a selected node or subtree without coupling decoration logic to the application core.
- [ ] Make node selection and decoration usable on mobile browsers, including touch-friendly controls and clear feedback for the selected target.
- [ ] Expose supported node and decoration operations through a stable application API that can later be wrapped as MCP tools for natural-language LLM use.
- [ ] Define API operation schemas, validation, and target scoping so automated operations can only affect explicitly selected or identified nodes.
- [ ] Add tests for node/subtree round trips, preservation of supported metadata, mobile interaction, and API operation validation.

## Progressive STEP geometry

- [ ] Add an OCCT/XDE document-backed WASM bridge to replace eager `ReadStepFile()` import.
- [ ] Keep the STEP document handle alive after metadata import and release it on file replacement or page cleanup.
- [ ] Implement `getEntityBounds(handle, entityId)` without tessellation.
- [ ] Implement `tessellateEntity(handle, entityId, options)` for one entity at a time.
- [ ] Support selected subtrees by resolving assembly descendants without tessellating unrelated nodes.
- [x] Add tessellation quality presets such as draft, normal, and precise instead of hard-coded values.
- [ ] Add progress events and cancellation for import and tessellation.
- [ ] Replace the fixed 120-second timeout with operation-specific cancellation and a device-aware limit.
- [ ] Release selected mesh buffers when selection changes.
- [ ] Add a small LRU cache for recently selected entity meshes with an explicit memory limit.
- [ ] Preserve face/entity mapping and colors in partial tessellation results.
- [ ] Add a full-model rendering command that is explicit and separate from opening a STEP file.

## Performance verification

- [ ] Measure metadata display time, OCCT document open time, first selected tessellation time, and memory usage.
- [ ] Test a simple part and a large assembly on desktop and mobile browsers.
- [ ] Compare `linearDeflection` and `angularDeflection` presets using triangle count, time, memory, and visual quality.
- [ ] Add browser smoke tests for worker timeout, cancellation, and recovery to the metadata-only view.
- [ ] Record fixture size and test environment with each performance result without committing restricted STEP files.

## Binding maintenance

- [ ] Decide whether to use the pinned `opencascade.js` binding or a maintained custom Emscripten build.
- [ ] Add the required XDE manual bindings and document the exact OCCT commit and Emscripten toolchain.
- [ ] Review LGPL-2.1-only and generated WASM distribution obligations before shipping the XDE build.
