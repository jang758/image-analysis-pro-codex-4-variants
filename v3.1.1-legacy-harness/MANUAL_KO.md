# Image Analysis Pro v3.1.1 기존 하네스 사용설명서

## 주요 기능

- 하나의 이미지를 세 단계로 처리합니다.
  1. 원본 이미지의 18개 섹션 기술 분석
  2. 분석을 15개 범주의 중간 리포트로 압축
  3. 중간 리포트를 이미지 생성용 프롬프트로 변환
- 분석, 중간 리포트, 생성 프롬프트를 영어·한국어·전체 보기로 제공합니다.
- 선택한 Gemini 모델 하나가 모든 단계를 처리하며 자동으로 다른 모델로 바꾸지 않습니다.
- Agentic Vision을 켜면 첫 번째 이미지 분석 단계에서 확대·회전·계산을 위한 코드 실행을 허용합니다.
- 실행 모델, Agentic Vision 사용 내역, 처리 시간, 토큰, 예상 비용과 오류 이유를 실행 리포트에 기록합니다.
- 큰 이미지는 분석용으로 자동 축소하며 결과와 실행 기록을 ZIP으로 저장할 수 있습니다.

## 메뉴 설명

### Settings

| 메뉴 | 기능 |
|---|---|
| Gemini API Key | Gemini API 키 입력. 키는 저장되지 않습니다. `붙여넣기`와 `보기/숨기기`를 사용할 수 있습니다. |
| Model | 사용할 Gemini 모델 선택. 기본값은 `gemini-pro-latest`입니다. |
| Custom Model | 목록에 없는 모델 ID를 직접 입력합니다. 값이 있으면 Model 선택보다 우선합니다. 사용하지 않을 때는 비워 둡니다. |
| Max Tokens (Analysis) | 첫 단계 기술 분석의 최대 출력 토큰 수입니다. |
| Max Tokens (Report) | 중간 리포트의 최대 출력 토큰 수입니다. |
| Max Tokens (Prompt) | 생성 프롬프트의 최대 출력 토큰 수입니다. |
| Thinking Level | 모델의 사고 수준을 선택합니다. |
| Camera Meta Style | 생성 프롬프트의 카메라 표현을 숫자, 영문 철자 또는 생략으로 설정합니다. 실제 EXIF를 읽는 기능은 아닙니다. |
| Agentic Vision | 첫 단계에서 선택 모델의 코드 기반 이미지 조사를 허용합니다. |
| Save Settings (Key 제외) | API 키를 제외한 설정을 브라우저에 저장합니다. |
| Clear | 저장된 설정과 현재 API 키 입력을 초기화합니다. |
| Refresh Models | API 키로 현재 계정에서 사용할 수 있는 분석 모델 목록을 갱신합니다. |
| Clear History | 저장된 실행 히스토리를 지웁니다. |
| 통합된 분석 필드 22개 보기 | 분석에서 사용하는 세부 필드 목록을 펼쳐 봅니다. |

### Image Input

- 입력 영역 클릭, 드래그 앤 드롭, 페이지에서 `Ctrl+V`, 또는 `Choose File`로 이미지를 추가합니다.
- 각 이미지는 독립된 작업 카드로 생성됩니다.

### 작업 카드

| 메뉴 | 기능 |
|---|---|
| 3-Step Analysis | 세 단계 분석을 시작합니다. |
| Cancel | 현재 실행을 취소합니다. |
| Retry Failed Step | 자동 재시도까지 실패한 단계만 최초 실행 모델과 설정으로 다시 실행합니다. 완료된 앞 단계는 유지합니다. |
| Finalize Current State | 더 이상 재시도하지 않고 현재 결과와 실패 이유를 히스토리·리포트·ZIP 대상으로 확정합니다. |
| ZIP | 분석, 리포트, 프롬프트, 실행 리포트와 메타데이터를 저장합니다. |
| Delete | 화면에서 해당 작업 카드를 제거합니다. |

### 결과 영역

- `Complete Technical Analysis`: 18개 섹션의 상세 분석
- `Intermediate Report`: 분석을 압축한 15개 범주의 중간 리포트
- `Generation Prompt`: 이미지 생성에 사용할 최종 프롬프트
- `실행 리포트`: 모델, Agentic Vision, 시간, 토큰, 예상 비용과 오류 기록
- 각 영역에서 `English`, `한국어`, `Full` 탭을 선택하고 현재 탭을 `Copy`로 복사합니다.
- `Debug / Raw Response`에서 단계별 처리 내용과 오류를 확인합니다.

## 사용 방법

1. `기존하네스.html`을 브라우저에서 엽니다.
2. Gemini API Key에 키를 입력합니다.
3. Model을 선택합니다. Custom Model을 사용하지 않으면 해당 칸을 비워 둡니다.
4. 필요에 따라 토큰 수, Thinking Level, Camera Meta Style과 Agentic Vision을 설정합니다.
5. Image Input에 이미지를 추가합니다.
6. 생성된 작업 카드에서 `3-Step Analysis`를 누릅니다.
7. 완료 후 각 결과의 언어 탭을 선택해 확인하거나 복사합니다.
8. 전체 결과가 필요하면 `ZIP`을 누릅니다.
9. 실패 시 `Retry Failed Step`으로 실패 단계만 다시 실행하거나 `Finalize Current State`로 현재 상태를 확정합니다.
10. 이전 실행 리포트는 `실행 히스토리`에서 펼쳐 확인합니다.
