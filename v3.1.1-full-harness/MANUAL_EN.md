# Image Analysis Pro v3.1.1 Full Harness Manual

## Main features

- Processes one image in an evidence-oriented three-stage workflow:
  1. Build an 18-section evidence ledger that separates observations, inferences, and unverified details
  2. Synthesize English and Korean analyses and an intermediate report from verified evidence
  3. Reinspect the source image and finalize the analysis, report, and generation prompt
- Rechecks the original image in the final stage for pose, subject, contact, background, and detail omissions.
- Provides the analysis, intermediate report, and generation prompt in English, Korean, and combined views.
- Uses the selected Gemini model for every stage without automatic model substitution.
- When Agentic Vision is enabled, the first and third stages may use code-based inspection because both receive the source image.
- Records models, Agentic Vision inspections, time, tokens, estimated cost, and failure reasons in the execution report.
- Automatically saves completed results as one TXT file plus the unchanged source image in the shared `results` folder.

## Menu guide

### Settings

| Menu | Function |
|---|---|
| Gemini API Key | Enter the Gemini API key. It is not saved. Paste and show/hide controls are available. |
| Model | Select the Gemini model. The default is `gemini-pro-latest`. |
| Custom Model | Enter an exact model ID not shown in the list. A value here overrides Model; leave it empty for normal use. |
| Max Tokens (Analysis) | Maximum output tokens for the evidence-ledger and final-analysis work. |
| Max Tokens (Report) | Maximum output tokens for the intermediate report. |
| Max Tokens (Prompt) | Maximum output tokens for the final generation prompt. |
| Thinking Level | Select the model thinking level. |
| Camera Meta Style | Format camera wording in the generation prompt as numeric, spelled out, or omitted. It does not read EXIF data. |
| Agentic Vision | Allow code-based image inspection by the selected model in the first and third stages. |
| Save Settings (Key excluded) | Save browser settings without the API key. |
| Clear | Reset saved settings and clear the current API-key field. |
| Refresh Models | Use the API key to refresh analysis models available to the account. |
| Connect shared results folder | Connect the repository's `results` folder as the automatic save destination. |
| Clear History | Delete stored run history. |
| Integrated 22 analysis fields | Expand the detailed field list used by the analysis. |

### Image Input

- Add an image by clicking the input area, dragging and dropping, pasting with `Ctrl+V` on the page, or selecting `Choose File`.
- Each image creates an independent job card.

### Job card

| Menu | Function |
|---|---|
| 3-Step Analysis | Start the evidence ledger, bilingual synthesis, and source-image reaudit stages. |
| Cancel | Cancel the current run. |
| Retry Failed Step | Rerun only the failed stage with the original run model and settings after automatic retries are exhausted. Completed earlier stages are preserved. |
| Finalize Current State | Save completed outputs and the failure reason to history and the `results` folder. |
| Save Again | Save the current TXT and unchanged source image again under a new, non-overwriting shared base name. |
| Delete | Remove the job card from the page. |

### Output areas

- `Complete Technical Analysis`: final 18-section analysis after evidence processing and reaudit
- `Intermediate Report`: 15-category report synthesized from verified evidence
- `Generation Prompt`: generation prompt finalized after comparison with the source image
- `Execution Report`: models, Agentic Vision inspections, time, tokens, estimated cost, and errors
- Select `English`, `한국어`, or `Full` in each area and use `Copy` to copy the active tab.
- Open `Debug / Raw Response` to inspect stage processing and errors.

## How to use

1. Open `전체개선.html` in a browser.
2. When first using this HTML app, select `Connect shared results folder` and choose this repository's `results` folder.
3. Enter a Gemini API key and select a Model. Leave Custom Model empty unless you need an unlisted model ID.
4. Set the desired options, add an image, and select `3-Step Analysis`.
5. On completion, one TXT contains the EN/KR analysis, intermediate report, prompt, and execution report; the original image is saved unchanged with the same base name plus `_ref`.
6. Names follow `date_time_milliseconds_v311_full-improvement_source-name` and never overwrite an existing TXT.
7. Select `Save Again` to create another pair under a new base name.
8. After a failure, retry the failed stage or use `Finalize Current State` to save the current outputs and error.
9. Opening Run History does not create another filesystem save.
