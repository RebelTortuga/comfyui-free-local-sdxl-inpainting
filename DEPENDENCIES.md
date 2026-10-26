# Dependencies

Install only the packages needed by this graph. Provider mappings below are based on upstream documentation; exact installed revisions were not supplied.

| Extension | Upstream | Required types |
|---|---|---|
| Prompt history | https://github.com/dawncreatescode/comfyui-PromptHistory | `SelectPromptPairHistory` |
| Inpaint Crop and Stitch | https://github.com/lquesada/ComfyUI-Inpaint-CropAndStitch | `InpaintCropImproved, InpaintStitchImproved` |
| SAM2 | https://github.com/neverbiasu/ComfyUI-SAM2 | `SAM2ModelLoader, GroundingDinoModelLoader, GroundingDinoSAM2Segment` |
| LayerStyle | https://github.com/chflame163/ComfyUI_LayerStyle | `LayerMask: MaskEdgeUltraDetail (legacy exact type)` |
| Essentials | https://github.com/cubiq/ComfyUI_essentials | `MaskBlur+` |

## Exact node inventory

- `CLIPTextEncode`
- `CheckpointLoaderSimple`
- `GroundingDinoModelLoader (segment anything2)`
- `GroundingDinoSAM2Segment (segment anything2)`
- `GrowMask`
- `ImageScaleBy`
- `ImageToMask`
- `ImageUpscaleWithModel`
- `InpaintCropImproved`
- `InpaintModelConditioning`
- `InpaintStitchImproved`
- `KSampler`
- `LayerMask: MaskEdgeUltraDetail`
- `LoadImage`
- `MaskBlur+`
- `MaskToImage`
- `PreviewImage`
- `SAM2ModelLoader (segment anything2)`
- `SaveImage`
- `SelectPromptPairHistory`
- `UpscaleModelLoader`
- `VAEDecode`

- [Clean Slate Controller](https://github.com/RebelTortuga/comfyui-clean-slate): `CleanSlateController`.
