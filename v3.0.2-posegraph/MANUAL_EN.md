# Image Analysis Pro Pose & Face v3.0.2 PoseGraph Harness Manual

## Main features

- Analyzes pose, face, hands, and contact relationships in three stages:
  1. `Pose Map`: map global composition, stable subject IDs, left/right conventions, joints, keypoints, support, and contact candidates from the source image
  2. `Face/Hand/Contact Resolver`: compare the source image with the Pose Map and verify faces, hands, contacts, overlaps, and occlusions
  3. `Pose-Locked Compiler`: use only the verified state to write English and Korean analyses and generation prompts
- Assigns stable IDs such as S1 and S2 and separates anatomical subject-left/right from image-left/right.
- Distinguishes physical contact from simple 2D overlap and locks final output to the verified state.
- Uses the selected Gemini model for every stage without automatic model substitution.
- Agentic Vision is available only in the Resolver stage for targeted face, hand, and contact zoom or crop inspection.
- Records models, Agentic Vision inspections, time, tokens, estimated cost, retries, and failure reasons in the execution report.

## Menu guide

### Settings

| Menu | Function |
|---|---|
| Gemini API Key | Enter the Gemini API key. It is not saved, and `Ctrl+V` in this field pastes the key. |
| Model | Select the Gemini model. The default is `gemini-pro-latest`. |
| Custom Model | Enter an exact model ID not shown in the list. A value here overrides Model; leave it empty for normal use. |
| Temperature | Set output variability. It is omitted for current Gemini 3 models so the model default is used. |
| Max tokens — Analysis | Maximum output tokens for the Pose Map, Resolver, and Compiler. |
| Max tokens — Prompt | Prompt token setting. The final structured Compiler output uses the analysis limit. |
| Thinking | Select the model thinking level. |
| Thinking budget — Gemini 2.5 | Set the Gemini 2.5 thinking-token budget. `-1` uses dynamic allocation. |
| Camera Description Style | Format verified camera wording as numeric, spelled out, or omitted. It does not read EXIF data or invent camera numbers. |
| Agentic Vision | Allow code-based zoom and crop inspection by the selected model in the Resolver stage. It cannot run with Thinking Off. |
| Save Settings | Save browser settings without the API key. |
| Reset Settings | Reset saved settings and clear the current API-key field. |
| Refresh Model List | Load analysis models available to the account using the API key. |
| Test Selected Model | Run a short check of the current model, API key, and structured-request format. |
| Safety OFF | Status indicator showing that the four adjustable safety filters are requested as OFF. |

### Image input and history

- Add an image by clicking the input area, dragging and dropping, pasting with `Ctrl+V` on the page, or selecting `Choose File`.
- `NET` shows the browser online state.
- `Saved History` stores result and report text. Use `View` to open an item or `Clear History` to delete the history.

### Job card

| Menu | Function |
|---|---|
| Analyze | Run Pose Map → Resolver → Pose-Locked Compiler. |
| Cancel | Cancel the current run. |
| Retry Failed Step with Current Model | Resume from the failed stage with the currently selected model after automatic retries are exhausted. Verified earlier stages are preserved. |
| Finalize Current State | Preserve the current outputs and failure reason for history, reports, and ZIP export. |
| Save ZIP | Save analysis EN/KR, prompt EN/KR, execution reports EN/KR, run JSON, internal PoseGraph trace, and the processed image. |
| Delete | Remove the job card from the page. |

### Output areas

- `Long Analysis`: scene analysis based on verified pose, face, hand, and contact state
- `Generation Prompt`: image-generation prompt locked to the verified state
- `Execution Report`: initial and final models, per-stage requested and resolved models, Agentic Vision inspections, time, tokens, estimated cost, and errors
- Select `EN`, `KR`, or `Full` in each area and use `Copy` to copy the active tab.
- Open `Processing Log / Errors` to inspect HTTP status, time, retries, and failure reasons for Pose Map, Resolver, and Compiler.

## How to use

1. Open `PoseGraph하네스.html` in a browser.
2. Enter a Gemini API key.
3. Select a Model. Leave Custom Model empty unless you need an unlisted model ID.
4. Optionally select `Test Selected Model` to verify the connection and structured output.
5. Set token limits, Thinking, Camera Description Style, and Agentic Vision. To use Agentic Vision in the Resolver, select a Gemini 3 model and do not select Thinking Off.
6. Add an image and select `Analyze` on the job card.
7. After completion, review or copy the long analysis, generation prompt, and execution report in the desired language.
8. Select `Save ZIP` for the complete result set.
9. If automatic retries fail, change the model if desired and select `Retry Failed Step with Current Model`. A Custom Model value overrides the model list.
10. Gemini 2.5 cannot be selected when retrying from the Agentic Resolver. It can be used for a retry that starts at the non-Agentic Compiler.
11. If you do not want to retry, select `Finalize Current State` to preserve the current outputs and error information.
