# Test Outfit-Mesh-Linker

A mobile-friendly, browser-side prototype for previewing a rigged Body model together with a separate Outfit mesh.

## Current prototype
- Load Body and Outfit from local GLB/glTF files.
- Preview both models in one Three.js scene.
- Rotate and zoom the preview; hide/show either model.
- Inspect mesh counts, vertex counts, skinned meshes, and bone count.
- Model files are loaded locally in the browser and are not uploaded by this page.

## Not implemented yet
- Automatic surface-based bone-weight transfer.
- Binding the Outfit to the Body's shared skeleton.
- Skeleton remapping/removal for outfits that already have a rig.
- Animation preview.
- VRM 0.x / VRM 1.0 export and validation.

## Usage
Open the page in a modern browser, choose the Body and Outfit GLB/glTF files, then select **Load selected models**. For accurate future weight transfer, both models should use the same coordinate space, scale, and rest pose.

## Technical
- Three.js + GLTFLoader + OrbitControls via jsDelivr CDN.
- No UniVRM dependency.
