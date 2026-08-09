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
- Automatically downsizes oversized images for analysis and exports results and run records as a ZIP file.

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
| Finalize Current State | Stop retrying and preserve the current outputs and failure reason for history, reports, and ZIP export. |
| ZIP | Save analysis, reports, prompts, execution reports, and metadata. |
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
2. Enter a Gemini API key.
3. Select a Model. Leave Custom Model empty unless you need an unlisted model ID.
4. Set token limits, Thinking Level, Camera Meta Style, and Agentic Vision as needed.
5. Add an image under Image Input.
6. Select `3-Step Analysis` on the new job card.
7. After completion, select a language tab to read or copy each result.
8. Select `ZIP` to save the complete result set.
9. After a failure, use `Retry Failed Step` to rerun only that stage or `Finalize Current State` to preserve the current state.
10. Expand an item under Run History to review a previous execution report.
