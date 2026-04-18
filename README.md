# 🪪 AI 증명사진 스튜디오 (AI ID Photo Studio)

> **사진 한 장으로 AI가 만들어주는 전문가급 증명사진**
> Google Gemini 2.5 Flash Image(나노 바나나)를 활용해 표준/부드러움/신뢰감 × 정면/측면 = 6가지 증명사진을 생성합니다.

[![Live Demo](https://img.shields.io/badge/Live%20Demo-Try%20Now-black?logo=vercel)](https://ai-id-photo-studio.vercel.app/)
[![Gemini](https://img.shields.io/badge/Gemini-2.5%20Flash%20Image-blue)](https://ai.google.dev/gemini-api/docs/image-generation)
[![BYOK](https://img.shields.io/badge/Bring%20Your%20Own-API%20Key-orange)](https://aistudio.google.com/apikey)

---

## 🤔 기획 동기

> "내 사진 한 장으로 AI가 알아서 전문가처럼 만들어주면 얼마나 좋을까?"

급하게 증명사진이 필요한데 사진관 예약·촬영·보정 대기까지 시간이 걸리는 불편함을 해결하기 위한 프로젝트입니다. **사진 한 장 + 클릭 몇 번**으로 신분증·이력서·프로필용 증명사진을 즉석에서 생성합니다.

---

## ✨ 주요 기능

| 기능 | 설명 |
|------|------|
| 🖼️ **3가지 스타일** | 표준 · 부드러운 인상 · 신뢰감 있는 인상 |
| 📐 **2가지 구도** | 정면 · 측면 (총 6개 조합 한 번에 생성) |
| 💾 **개별/전체 다운로드** | 마음에 드는 한 장 저장 또는 ZIP 일괄 다운로드 |
| 🔐 **BYOK 방식** | 사용자 본인의 Gemini API 키 사용 (브라우저 내에서만 사용, 외부 저장 없음) |
| 🚫 **얼굴 특징 보존** | 원본 얼굴은 유지하되 의상·배경·조명만 재생성 |

---

## 🚀 바로 사용하기

👉 **[https://ai-id-photo-studio.vercel.app/](https://ai-id-photo-studio.vercel.app/)**

### 사용 단계
1. **사진 업로드** - 얼굴이 잘 보이는 정면 사진 권장
2. **API 키 입력** - [Google AI Studio](https://aistudio.google.com/apikey)에서 무료 발급
3. **"증명사진 만들기"** 클릭 → 6장 동시 생성
4. **결과 저장** - 개별 다운로드 또는 ZIP 일괄 다운로드

> ⚠️ AI는 얼굴 특징을 항상 완벽히 반영하진 못합니다. 마음에 드는 결과를 위해 여러 번 시도해 보세요.

---

## 🛠️ 기술 스택

| 분류 | 기술 |
|------|------|
| **프론트엔드** | Vanilla JavaScript (단일 `index.html` 파일) |
| **스타일링** | Tailwind CSS (CDN) |
| **AI 모델** | Google **Gemini 2.5 Flash Image** (`gemini-2.5-flash-image`) |
| **압축 다운로드** | [JSZip](https://stuk.github.io/jszip/) |
| **호스팅** | Vercel (정적 웹사이트, GitHub 연동 자동 배포) |

> 💡 백엔드 서버 없이 모든 요청이 사용자 브라우저에서 Google Gemini API로 직접 전송됩니다.

---

## 📦 로컬 실행

```bash
# 저장소 복제
git clone https://github.com/tigerjk9/ai-id-photo-studio.git
cd ai-id-photo-studio

# 정적 서버 실행 (Python 3 기준)
python -m http.server 8000

# 브라우저에서 http://localhost:8000 접속
```

> 💡 별도 빌드 과정 없음. `index.html`을 브라우저에서 직접 열어도 동작합니다.

---

## 💡 핵심 노하우: 프롬프트 엔지니어링

각 스타일과 구도의 미묘한 차이를 AI가 정확히 표현하도록 영문 프롬프트를 정교하게 설계했습니다.

### 측면 구도 통합 결정
초기에는 **좌측/우측 측면**을 분리했으나, 프롬프트로 일관되게 컨트롤하기 어렵고 강압적인 표현 사용 시 이미지 생성 실패율이 올라가는 문제가 있었습니다. → **"측면" 단일 옵션으로 통합**하여 안정성 확보.

### 얼굴 특징 보존 전략
원본 사진의 얼굴 특징(이목구비, 표정, 헤어스타일)은 유지하되, 의상·배경·조명만 재생성하도록 프롬프트를 구성했습니다.

---

## 🔑 API 키 발급 가이드

1. [Google AI Studio](https://aistudio.google.com/apikey) 접속
2. Google 계정 로그인
3. **"Create API Key"** 클릭 → 키 복사
4. 본 앱 입력란에 붙여넣기

> 🔒 **보안:** API 키는 사용자 브라우저 내에서만 사용되며, 외부 서버로 전송·저장되지 않습니다.
> 단, 입력 필드에 잠시 보관되므로 **공용 PC 사용 후에는 새로고침** 권장.

---

## 📁 저장소 구성

```
ai-id-photo-studio/
├── README.md       # 본 문서
├── PRD.md          # 제품 요구사항 문서
├── CLAUDE.md       # AI 개발 컨텍스트
└── index.html      # 단일 파일 웹앱 (HTML + CSS + JS 통합)
```

---

## 📝 변경 이력

| 날짜 | 내용 |
|------|------|
| 2026-04-19 | Vercel(`ai-id-photo-studio.vercel.app`) 배포 + Netlify 호스팅 종료 + README 현행화 |
| 이전 | Gemini 모델명 GA 전환: `gemini-2.5-flash-image-preview` → `gemini-2.5-flash-image` (404 오류 해결) |

---

## 🐛 알려진 제약

- 얼굴 인식이 어려운 사진(측면, 가림, 저해상도)은 결과 품질 저하
- 모델 응답 시간: 6장 동시 생성 시 수십 초 소요
- API 무료 할당량 초과 시 429 오류 (자동 재시도 포함)

---

## 🙏 크레딧

- **Google Gemini 2.5 Flash Image (Nano Banana)** - 멀티모달 이미지 생성 모델
- **Tailwind CSS** - 유틸리티 우선 CSS 프레임워크
- **JSZip** - 클라이언트 사이드 ZIP 생성
- **나노 바나나 프롬프트 참고** - [tigerjk9.github.io/ai/nano-banana](https://tigerjk9.github.io/ai/nano-banana/)

---

## 📝 라이선스

MIT License - 자유롭게 사용·수정·재배포 가능합니다.

---

## 👤 제작자

**김진관 (닷커넥터)**
- GitHub: [@tigerjk9](https://github.com/tigerjk9)
- Project Link: [ai-id-photo-studio](https://github.com/tigerjk9/ai-id-photo-studio)

---

> 🪪 **지금 바로 [AI 증명사진 스튜디오](https://ai-id-photo-studio.vercel.app/)에서 전문가급 증명사진을 만들어보세요!**
