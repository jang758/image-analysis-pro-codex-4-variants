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
| Finalize Current State | Preserve completed outputs and the failure reason for history, reports, and ZIP export. |
| ZIP | Save analyses, reports, prompts, execution reports, and metadata. |
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
2. Enter a Gemini API key.
3. Select a Model. Leave Custom Model empty unless you need an unlisted model ID.
4. Set token limits, Thinking Level, Camera Meta Style, and Agentic Vision as needed.
5. Add an image under Image Input.
6. Select `3-Step Analysis` on the new job card.
7. After all three stages finish, review the analysis, intermediate report, generation prompt, and execution report in the desired language.
8. Use `Copy` for the active tab or `ZIP` for the complete result set.
9. After a failure, use `Retry Failed Step` to rerun only that stage or `Finalize Current State` to preserve the current state.
10. Expand an item under Run History to review a previous execution report.
