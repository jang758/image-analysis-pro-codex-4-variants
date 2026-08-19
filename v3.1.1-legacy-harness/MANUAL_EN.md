# Image Analysis Pro v3.1.1 Legacy Harness Manual

## Main features

- Processes one image in three stages:
  1. An 18-section technical analysis of the source image
  2. A condensed intermediate report with 15 categories
  3. An image-generation prompt compiled from the report
- Provides the analysis, intermediate report, and generation prompt in English, Korean, and combined views.
- Uses the selected Gemini model for every stage without automatic model substitution.
- When Agentic Vision is enabled, the first image-analysis stage may use code execution for zooming, rotation, and calculations.
- Records the selected and resolved model, Agentic Vision activity, time, tokens, estimated cost, and failure reasons in the execution report.
- Automatically downsizes oversized images for analysis. Completed results are automatically saved as one TXT file plus the unchanged source image in the shared `results` folder.

## Menu guide

### Settings

| Menu | Function |
|---|---|
| Gemini API Key | Enter the Gemini API key. It is not saved. Paste and show/hide controls are available. |
| Model | Select the Gemini model. The default is `gemini-pro-latest`. |
| Custom Model | Enter an exact model ID not shown in the list. A value here overrides Model; leave it empty for normal use. |
| Max Tokens (Analysis) | Maximum output tokens for the technical-analysis stage. |
| Max Tokens (Report) | Maximum output tokens for the intermediate-report stage. |
| Max Tokens (Prompt) | Maximum output tokens for the generation-prompt stage. |
| Thinking Level | Select the model thinking level. |
| Camera Meta Style | Format camera wording in the generation prompt as numeric, spelled out, or omitted. It does not read EXIF data. |
| Agentic Vision | Allow code-based image inspection by the selected model in the first stage. |
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
| 3-Step Analysis | Start the three-stage workflow. |
| Cancel | Cancel the current run. |
| Retry Failed Step | Rerun only the failed stage with the original run model and settings after automatic retries are exhausted. Completed earlier stages are preserved. |
| Finalize Current State | Stop retrying and save the current outputs and failure reason to history and the `results` folder. |
| Save Again | Save the current TXT and unchanged source image again under a new, non-overwriting shared base name. |
| Delete | Remove the job card from the page. |

### Output areas

- `Complete Technical Analysis`: detailed 18-section analysis
- `Intermediate Report`: condensed 15-category report
- `Generation Prompt`: final prompt for image generation
- `Execution Report`: model, Agentic Vision, time, tokens, estimated cost, and errors
- Select `English`, `한국어`, or `Full` in each area and use `Copy` to copy the active tab.
- Open `Debug / Raw Response` to inspect stage processing and errors.

## How to use

1. Open `기존하네스.html` in a browser.
2. When first using this HTML app, select `Connect shared results folder` and choose this repository's `results` folder. Reconnect the same folder if the browser asks for permission again.
3. Enter a Gemini API key and select a Model. Leave Custom Model empty unless you need an unlisted model ID.
4. Set token limits, Thinking Level, Camera Meta Style, and Agentic Vision as needed.
5. Add an image and select `3-Step Analysis` on its job card.
6. On completion, one TXT contains the EN/KR analysis, intermediate report, prompt, and execution report; the original image is saved unchanged with the same base name plus `_ref`.
7. Names follow `date_time_milliseconds_v311_legacy-harness_source-name` and never overwrite an existing TXT.
8. Select `Save Again` to create another pair under a new base name.
9. After a failure, retry the failed stage or use `Finalize Current State` to save the current outputs and error.
10. Opening Run History does not create another filesystem save.
