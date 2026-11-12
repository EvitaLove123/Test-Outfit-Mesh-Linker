# Test Outfit-Mesh-Linker

A mobile-friendly, browser-side prototype for transferring outfit skin weights onto a VRM humanoid skeleton. Model files are processed locally in the browser; they are not uploaded.

## Implemented in the current build
- Load Body files in **VRM 0.x and VRM 1.0** using the `@pixiv/three-vrm` loader (no UniVRM).
- Load Outfit files in GLB/glTF, whether mesh-only or already skinned.
- Inspect mesh counts, vertex counts, skinned meshes, and bone counts.
- Transfer weights from a Body skinned mesh to Outfit vertices using closest-triangle surface projection and barycentric interpolation.
- Normalize and write four skin influences per Outfit vertex.
- Bind the resulting SkinnedMesh to the Body mesh's existing Three.js skeleton for in-memory preview.
- Preview, rotate, zoom, and hide/show the Body and Outfit.
- Keep source files local in the browser.

## Important limitations — not a finished VRM exporter
- The current transfer prototype uses the first valid Body SkinnedMesh as its source surface. It samples up to approximately 18,000 triangles for mobile performance; very complex or overlapping body surfaces may need a more advanced spatial index and source-region selection.
- The Outfit and Body must be aligned in the same scale, coordinate space, and rest pose. Surface transfer cannot fix incorrect garment fit or mismatched proportions.
- Existing Outfit skinning is replaced by transferred Body weights; automatic semantic bone remapping is not provided.
- The current build creates a linked mesh in memory only. It does **not** write a new VRM file.
- VRM 0.x / 1.0 re-export and validation are not yet implemented. A correct exporter must preserve the original VRM version and its metadata, humanoid mapping, expressions, material extensions, spring bones / secondary nodes, colliders, and valid glTF skin data. The project does not create fake VRM metadata and does not use UniVRM.

## Usage
1. Choose a VRM Body and a GLB/glTF Outfit.
2. Load the models and inspect their alignment.
3. Confirm that both are in the same rest pose and coordinate space.
4. Select **Transfer Weights & Link Outfit**.
5. Inspect the deformation and fit in the preview.

## Technical
- Three.js 0.160.0, GLTFLoader, OrbitControls.
- `@pixiv/three-vrm` v3 loader for VRM 0.x / 1.0 import.
- No UniVRM dependency.
