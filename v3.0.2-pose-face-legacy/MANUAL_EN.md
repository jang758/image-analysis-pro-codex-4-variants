# Image Analysis Pro Pose & Face v3.0.2 Legacy Harness Manual

## Main features

- Prioritizes pose, followed by face and expression.
- Processes the image in two stages:
  1. Analyze the source image from whole scene to body, face, and contact details, then reassemble the whole scene
  2. Create an image-generation prompt using only the first-stage analysis
- Provides the analysis and generation prompt in English, Korean, and combined views.
- Uses the selected Gemini model for both stages without automatic model substitution.
- When Agentic Vision is enabled, the first image-analysis stage may use code-based zoom and crop inspection with the selected model.
- Records models, Agentic Vision activity, time, tokens, estimated cost, retries, and failure reasons in the execution report.
- Automatically downsizes oversized images and exports results, run data, and the processed image as a ZIP file.

## Menu guide

### Settings

| Menu | Function |
|---|---|
| Gemini API Key | Enter the Gemini API key. It is not saved, and `Ctrl+V` in this field pastes the key. |
| Model | Select the Gemini model. The default is `gemini-pro-latest`. |
| Custom Model | Enter an exact model ID not shown in the list. A value here overrides Model; leave it empty for normal use. |
| Temperature | Set output variability. It is omitted for current Gemini 3 models so the model default is used. |
| Max tokens — Analysis | Maximum output tokens for the long analysis. |
| Max tokens — Prompt | Maximum output tokens for the generation prompt. |
| Thinking | Select the model thinking level. |
| Thinking budget — Gemini 2.5 | Set the Gemini 2.5 thinking-token budget. `-1` uses dynamic allocation. |
| Camera Description Style | Format camera wording in the generation prompt as numeric, spelled out, or omitted. It does not read EXIF data. |
| Agentic Vision | Allow code-based zoom and crop inspection by the selected model in the first stage. It cannot run with Thinking Off. |
| Save Settings | Save browser settings without the API key. |
| Reset Settings | Reset saved settings and clear the current API-key field. |
| Refresh Model List | Load analysis models available to the account using the API key. |
| Test Selected Model | Run a short check of the current model, API key, and request format. |
| Safety OFF | Status indicator showing that the four adjustable safety filters are requested as OFF. |

### Image input and history

- Add an image by clicking the input area, dragging and dropping, pasting with `Ctrl+V` on the page, or selecting `Choose File`.
- `NET` shows the browser online state.
- `Saved History` stores result and report text. Use `View` to open an item or `Clear History` to delete the history.

### Job card

| Menu | Function |
|---|---|
| Analyze | Start the two-stage analysis. |
| Cancel | Cancel the current run. |
| Retry Failed Step with Current Model | Resume from the failed stage with the currently selected model after automatic retries are exhausted. Completed earlier stages are preserved. |
| Finalize Current State | Stop retrying and preserve the current outputs and failure reason for history, reports, and ZIP export. |
| Save ZIP | Save analysis EN/KR, prompt EN/KR, execution reports EN/KR, run JSON, internal trace, and the processed image. |
| Delete | Remove the job card from the page. |

### Output areas

- `Long Analysis`: scene, pose, face, contact, occlusion, camera, lighting, and whole-scene reconstruction
- `Generation Prompt`: image-generation prompt grounded in the long analysis
- `Execution Report`: initial and final models, per-stage requested and resolved models, Agentic Vision, time, tokens, estimated cost, and errors
- Select `EN`, `KR`, or `Full` in each area and use `Copy` to copy the active tab.
- Open `Processing Log / Errors` to inspect stage HTTP status, time, retries, and failure reasons.

## How to use

1. Open `기존하네스.html` in a browser.
2. Enter a Gemini API key.
3. Select a Model. Leave Custom Model empty unless you need an unlisted model ID.
4. Optionally select `Test Selected Model` to verify the connection.
5. Set token limits, Thinking, Camera Description Style, and Agentic Vision. For Agentic Vision, use a Gemini 3 model and do not select Thinking Off.
6. Add an image and select `Analyze` on the job card.
7. After completion, review or copy the long analysis, generation prompt, and execution report in the desired language.
8. Select `Save ZIP` for the complete result set.
9. If automatic retries fail, change the model if desired and select `Retry Failed Step with Current Model`. A Custom Model value overrides the model list.
10. If you do not want to retry, select `Finalize Current State` to preserve the current outputs and error information.
