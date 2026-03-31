# AI 증명사진 스튜디오

## 프로젝트 구조

단일 파일 웹앱 (`index.html`). 빌드 도구 없음.

## 기술 스택

- HTML/CSS/JS (단일 파일)
- Tailwind CSS (CDN)
- JSZip (CDN) - ZIP 다운로드
- Google Gemini API (`gemini-2.5-flash-image`, v1beta)

## 핵심 로직

- 사용자가 API 키 직접 입력 (서버리스)
- 원본 사진 + 프롬프트를 `generateContent` API로 전송
- `responseModalities: ['IMAGE']`로 이미지 생성
- 429 에러 시 exponential backoff 재시도 (최대 3회)

## 스타일 (6종)

표준/부드러운/신뢰감 x 정면/측면

## 배포

- GitHub Pages: https://tigerjk9.github.io/ai-id-photo-studio/
- main 브랜치에서 직접 배포

## 주의사항

- 모델명 변경 시 `generateImageAPI` 함수의 apiUrl 수정 필요 (line ~303)
- 프롬프트는 `PHOTO_STYLES` 배열에 정의 (line ~212)
- 강압적 프롬프트는 AI 생성 실패를 유발할 수 있으므로 균형 유지
