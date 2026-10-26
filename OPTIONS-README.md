# Detailed Options Guide

This guide explains the supplied workflow. Change one setting at a time and compare outputs using the same input image and seed. Save a copy before changing connections.

## Image and prompts

- **Input image:** choose the image you want edited or animated. No example photograph is bundled.
- **Positive prompt:** describe the edit or motion you want. Be specific about what should change.
- **Negative prompt:** describe unwanted features. Its influence depends on the model and guidance settings.
- **Prompt history:** positive and negative fields start blank. The history node can save and reuse prompt pairs; local history files are not included.

## Generation controls

| Control | Meaning | Practical effect |
| --- | --- | --- |
| Seed | Starting random state | Keep it fixed for comparisons; identical seeds do not guarantee identical results across hardware or software changes. |
| Steps | Sampling iterations | More steps usually take longer; more is not automatically better. |
| CFG | Prompt guidance strength | Higher values can strengthen prompt influence but may introduce artifacts. |
| Denoise | Amount of regeneration | Lower values tend to preserve more of the encoded input; behavior depends on the model and conditioning. |
| Sampler / scheduler | Sampling method and noise schedule | Keep supplied defaults for your first result. |
| Dimensions | Image or video size | Larger dimensions usually require more memory and time. |

## Supplied sampler settings

| Node | Steps | CFG | Sampler | Scheduler | Denoise |
| --- | --- | --- | --- | --- | --- |
| 14 | 30 | 7 | dpmpp_3m_sde | karras | 0.85 |
| 31 | 20 | 8 | dpmpp_3m_sde | karras | 0.4 |

## Workflow-specific controls and behavior

1. Load your image and enter positive/negative prompts in the prompt-history node.
2. Replace `pink top` in GroundingDINO/SAM2 with the object you want selected.
3. Inspect the mask preview; tune detection and mask-edge controls before rendering.
4. Run the workflow. It performs crop-and-stitch inpainting, followed by 4× upscaling and another sampling pass.
5. Inspect the final result and save output in ComfyUI's output directory.

Despite the original “All Manual” filename, this uploaded graph takes its active mask from SAM2; the painted LoadImage mask is not the active selection source. To use a painted mask, reconnect the LoadImage MASK output into the mask-processing chain in a separate copy. This repository preserves the submitted graph.

The first sampler uses 30 steps, CFG 7, denoise 0.85; the second uses 20 steps, CFG 8, denoise 0.4. The upscaling pass can require substantially more memory.


## Mask and refinement stages

- **Detection text:** names the object SAM2/GroundingDINO should select; the supplied text is `pink top`. Change it for your image.
- **Detection threshold:** adjusts detection filtering. Inspect the preview rather than assuming a correct selection.
- **GrowMask / edge refinement / blur:** change mask coverage and blending near boundaries.
- **Crop and Stitch:** processes a region around the selection and places the result back into the image.
- **4× upscale and second sampler:** enlarges and refines the result; this can use substantially more memory than the first pass.

## Verification limits

Graph references were checked. These settings are documented from the uploaded JSON; GPU rendering, timings, and minimum VRAM were not verified during packaging.
