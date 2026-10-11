# Global Company 웹사이트 구축 — 작업수행일지

- 고객: Global Company (TikTok LIVE 크리에이터 에이전시) / 담당: 박재현 대표
- 수행: 올인웹 (김성곤)
- 플랫폼: Webflow + Lumos Framework, Webflow MCP로 구축
- 최종 업데이트: 2026-10-11

---

## 1. 프로젝트 기준 정보

| 항목 | 내용 |
|---|---|
| Figma (작업 파일) | `iB6KIWwcJvNiGhCiEjm1Tv` — 디자인 페이지 `웹디자인V3-1차검수진행중`(40515:11666), `📓 Style Guide & Components`(7:5) |
| Figma (고객 공유본) | `NFg0avYhRYSwwh0HGRPcjp` |
| Webflow 사이트 | `글로벙컴퍼니` / `global-company` (Site ID `6ac8f703fef5e75c9add8463`) |
| 프레임워크 | Lumos (올인웹 커스텀 템플릿 기반, 버전 표기 확인 불가) |
| 사용 스킬 | `lumos-skill`, `webflow-gsap-animation` (Global Company 보완판) |

### 개발 기준 — 컴포넌트 사용 (2026-10-11 대표님 지시)
1. **Lumos Starter 템플릿 컴포넌트를 최대한 사용한다.** (Slider, Card Primary, Button Main, Form Input·Select·Textarea·Checkbox·Radio, Accordion, Modal, Tab, Dropdown, Nav, Footer 등)
2. **디자인을 바꿔야 할 때는 원본을 직접 고치지 않고, 해당 컴포넌트에 변형(Variant)을 추가해서** 사용한다. (원본 스타일을 바꾸면 모든 인스턴스에 반영되므로)
3. **맞는 컴포넌트가 없을 때만 새 컴포넌트를 만든다.** 새 컴포넌트도 Lumos 규칙(클래스 이름, 테마 변수, 반응형 변수)을 따른다.
4. 참고: Slider 등의 Slot에는 컴포넌트만 넣을 수 있다. 슬라이드 내용(예: 크리에이터 카드)은 카드 컴포넌트로 만들어 넣는다. CMS 목록을 Slot에 넣는 방식은 구현 전에 먼저 시험한다.

## 2. 일정 (고객 메일 합의 기준)

| 일자 | 내용 | 상태 |
|---|---|---|
| 10/09 | 디자인 확정 회신, 개발 진행 합의 | 완료 |
| 10/10 | 고객: 대표 실적 대상 기간·정산·환산 기준 자료 전달 | 수신 여부 확인 필요 |
| 10/12(월) | 웹 개발 착수 | 예정 |
| 10/16(금) | 중도금 1,122,000원 지급 기한 | 예정 |
| 10/26(월) | 개발 완료, 임시 도메인 전달 | 예정 |
| 10/28(수) | 목표 완료일 (검수·수정 2회차 포함) | 예정 |
| 개발 중반 | 개인정보처리방침용 기술 정보·계정 개설(Global Company 명의) 안내 | 예정 |

## 3. 진행 현황 요약

| 구분 | 상태 |
|---|---|
| 메일·요구사항 검토 | ✅ 완료 |
| Figma 디자인 구조 검토 | ✅ 완료 |
| Webflow MCP 연결 | ✅ 완료 |
| Lumos 확인 | ✅ Skill(GitHub 최신본과 동일) / ⚠️ v2.2.3 Notion 문서 미확인 |
| 디자인 토큰·스타일가이드 셋업 | 🟡 대부분 완료, 수식 값 3건 미완 |
| GSAP 애니메이션 스킬 보완 | ✅ 완료 |
| CMS 설계·페이지 개발 | ⬜ 미착수 |

---

## 4. 작업 기록

### 2026-10-09 — 착수 검토

**고객 메일 검토 (2개 스레드 전체)**
- 확정 사항
  - 검정·금색 / 우주 → 금빛 → 나무·풀·꽃 → 대표 → 구성원 흐름
  - 메인 인물 구도: 중앙 대표(슈트), 좌 조담인, 우 이철희
  - 대표 소개는 검은 티셔츠 정면(B안), 주소 비노출, 사훈은 CHALLENGE 문장 먼저
- 크리에이터 9명
  - 소개 순서: 이철희 → 조담인 → 승환 → 김린아 → 최윤진 → 박정은 → 노진희 → 신솔 → 최성연
  - 분류: 전체 / 일상·소통 / 음악·보컬 / 운동·피트니스 / 요리·먹방 / 취미·라이프
- 10/9 추가 요청 (비용·일정 변경 없이 수락)
  - '숫자로 보는' 카드: 크리에이터 67 · 에이전트 23 · 총 90명 (2026년 10월 기준)
  - 크리에이터 영역 안내 문구: "홈페이지에는 소속 크리에이터 중 일부를 소개합니다."
  - 버튼 문구 'TikTok 프로필 보기'
  - 하단 모집 문구 통일
  - 실적 카드: "5.43M 다이아 · 약 3,800만 원"
- 지원서 요구사항
  - 필수·선택 동의 분리, 사전 체크 금지, 선택 미동의 시 해당 정보 미전송
  - 이메일 알림, Google Sheets 저장(Make)
  - GA4·TikTok Pixel에 개인정보 전송 금지, 테스트는 가상 정보로
- 이번 오픈 제외: 유튜브 지원, 자체 브랜드, 해외 진출, 유료 협업, 'LIVE'/시청자 수 연출

**Figma 검토**
- 디자인 페이지 최상위 프레임 15개 확인: Home(PC·모바일·하단 고정 버튼), 메뉴, LIVE Guide, 크리에이터 목록·상세, 지원(PC·모바일)·완료, 소식 목록·상세, 개인정보처리방침, 메인 팝업, 스크롤 연출 6단계 작업본
- 모바일 시안은 Home과 지원 페이지만 있음. 나머지는 반응형으로 구현하기로 합의
- 확인 필요: 작업 파일과 고객 공유본이 다름, 10/9 추가 요청 5건의 시안 반영 여부 미확인

**Webflow MCP / Lumos**
- MCP 가이드(v2.1.0) 검토, 초기 연결은 401 인증 오류
- Lumos Skill: GitHub `lumosframework/skill`(2026-03-24)과 세션 설치본이 완전히 같음을 확인
- Lumos v2.2.3 Notion 문서: 네트워크 정책 차단(403)으로 미확인

### 2026-10-09 ~ 10-10 — Webflow 연결 및 디자인 토큰 셋업

**연결 확인**
- MCP 재연결 후 사이트 접근 정상 (사이트 1개)
- Lumos 구성 확인: 변수 컬렉션(Theme·Typography·Text Style·Spacing 등), `u-*` 유틸리티 클래스
- CMS 컬렉션 없음, 커스텀 코드 비어 있음
- 확인 필요: 사이트 이름 오타('글로벙'), 시간대 America/Chicago(→ Asia/Seoul 권장, Designer에서 직접 변경 필요)

**Figma 토큰 추출**
- 색상: navy·gold·cream·gray·red·blue 원색과 의미별 색(semantic)
- 타이포그래피: 제목 Noto Serif KR Medium, 본문 Pretendard. PC 1440과 모바일 390 크기 모두 추출
- 간격, 모서리(8 / 32 / 999)

**셋업 적용 (승인 후)**

| # | 작업 | 결과 |
|---|---|---|
| 1 | Figma 원색 swatch 23개, 투명도 swatch 6개 추가 | ✅ (color-mix 생성은 실패해서 8자리 hex로 대체) |
| 2 | brand-500 → gold-400, brand-text → navy-1000 연결 | ✅ |
| 3 | 테마 기본(Base) 모드 → Figma 다크 값 (21개) | ✅ |
| 4 | 테마 Dark 모드도 같은 값으로 (22개) | ✅ |
| 5 | 테마 변수 추가: `text-secondary`, `text-tertiary`, `error`, `link` (brand 모드는 네이비 64%) | ✅ |
| 6 | `site/viewport-max` 112.5 → 90 (1440 기준) | ✅ |
| 7 | `font/secondary-family` = Noto Serif KR 추가 | ✅ (폰트 연결은 대표님이 Designer에서 진행 예정) |
| 8 | `font-size/text-xlarge`(20px), `text-2xlarge`(24px) 추가 | ✅ (현재 고정값) |
| 9 | Text Style 모드 추가: `Text XLarge`, `Text 2XLarge` + 클래스 `u-text-style-xlarge`, `u-text-style-2xlarge` | ✅ |
| 10 | H1~H6·Display: 제목 서체, 굵기 500, 줄간격 1.1~1.3, 자간 tight | ✅ |
| 11 | `radius/main` 3px → 32px(2rem) | ✅ |
| 12 | `button_main_wrap` 모서리 → round(알약형) | ✅ |
| 13 | `form_field` 테두리 색 → 테마 border 변수 | ✅ |
| 14 | 글자 크기 유동값(clamp) — Display~XSmall | ❌ MCP가 수식 값 저장 실패 |
| 15 | 섹션 간격(80·120px) | ❌ 같은 이유 |

**스타일가이드 확인**
- Styleguide 페이지에는 타이포그래피와 버튼만 있음
- 카드(Card Primary)와 입력(Form Input·Select·Textarea·Checkbox·Radio)은 사이트 컴포넌트로 존재 → 테마 변수로 자동 반영

### 2026-10-11 — 재시도, 화면 확인, GSAP 스킬

**수식 값 재시도**
- Designer를 연 상태(Home, 디자인 모드)에서 clamp와 `calc(1rem + 4px)`를 다시 시도 → 모두 `internal error`
- 판단: Webflow MCP가 수식 값 저장을 지원하지 않음 → 직접 입력 방식(B)으로 전환 제안

**Styleguide 화면 캡처 확인** (Designer 페이지 전환 후 캡처 성공)
- 정상: 알약형 금색 기본 버튼, 32px 카드, 금색 테두리, brand 카드 안의 버튼 반전
- 확인 필요
  - 타이포그래피 영역 배경이 흰색으로 보임 (캡처가 투명 배경을 흰색으로 보여준 것일 수 있음)
  - 보조(Secondary) 버튼이 회색 배경에 어두운 글자로 보임
  - 텍스트 링크 버튼이 어두운 박스로 보임

**webflow-gsap-animation 스킬 검토·보완**
- 새 스킬 확인 (SKILL.md 3.8KB)
- 보완 반영
  - 스크립트 위치를 Lumos 규칙과 통일
  - MCP 제약 추가 (인라인 스크립트 2000자, Head/Footer 코드는 통째로 덮어씀, 수식 변수 실패 이력)
  - IX3 추가
  - Lumos trigger 변수와 충돌 방지 규칙 추가
  - Global Company 메모: 스크롤 6단계, 인물 구도 고정, 하단 고정 버튼, 실시간 연출 금지, 개인정보 이벤트 금지
- 적용 위치: 이번 세션의 동기화 스킬과 저장소 `skills/webflow-gsap-animation/SKILL.md`
- 브랜치 `claude/global-company-gsap-skill`에 커밋 후 원격에 올림 (PR 미생성)
- 계정 스킬에는 대표님이 직접 업로드 필요 (동기화 시 원래대로 돌아갈 수 있음)

**작업수행일지 작성**
- `docs/global-company-worklog.md` 생성 (이 문서), 같은 브랜치에 커밋 후 원격에 올림
- 이후 작업이 있을 때마다 이 일지에 이어서 기록

**Lumos 컴포넌트 재사용 가능 여부 확인**
- Slider 컴포넌트 조회 (Swiper 기반)
  - 변형 3가지: Overflow Visible / Overflow Hidden / Crop Left
  - 화면별 슬라이드 개수(4/3/2/1), 속도, 컨트롤 등 속성(props)
  - 슬라이드는 Slot에 넣는 구조
- 결론: MCP로 기존 컴포넌트 넣기, 속성 변경, Slot 채우기가 가능함
- 대표님 지시로 **"개발 기준 — 컴포넌트 사용"** 추가 (1번 항목 아래)

**메인페이지 2번째 섹션~푸터 Figma → Webflow 제작 검토 (검토만, 사이트 변경 없음)**
- 범위(PC 기준, 히어로 제외): Statement(사훈) → LIVE Proof(대표 소개 + 숫자 카드 4개) → Creators(헤더 + 9:16 카드 마퀴) → CTA(크리에이터 모집) → Footer
- 모바일 시안 확인: LIVE Proof는 카드 대신 (01)~(04) 번호 목록, Creators는 첫 카드가 이철희
- Webflow Home 현황: Nav 인스턴스만 있고 본문(`page_main`)은 비어 있음, Footer 없음
- 시안과 고객 확정 내용이 다른 부분 3건 발견: 숫자 카드의 67·23·90명 표기 누락, CTA 문구가 예전 문구('방송 세팅부터 성장 전략까지'), 크리에이터 영역 안내 문구 누락
- Figma 이미지 다운로드는 네트워크 정책으로 차단 → 화면 확인은 인라인 캡처로 진행

**메인페이지 Statement 섹션 제작 (Home `page_main` 첫 섹션)**
- 구조 (모두 Lumos 템플릿 컴포넌트): `Section`(ID `statement`) → `Content Wrapper`(Center) → `Typography Heading` + `Typography Paragraph`
- 내용: "CHALLENGE WITHOUT LIMITS. / CREATE NEW POSSIBILITIES." (H2, 줄바꿈) + "끝없이 도전하고, 새로운 가능성을 창조하라." (Text Main), 최대 폭 제한 해제
- 변형(Variant) 추가 (원본은 그대로)
  - Typography Heading → **`H2 Accent`** (H2 복제 + 색 `heading-accent` 금색)
  - Typography Paragraph → **`Text Main Secondary`** (Text Main 복제 + 색 `text-secondary` 회색)
- 섹션 위아래 간격: Lumos Spacer **Page Top**(약 160~176px) 사용. Figma는 200px → 차이는 개발 중 조정 예정
- 과정 중 슬롯 이름 오류로 빈 Section 2개가 생겼고, 즉시 삭제함
- 화면 확인: Designer 재연결 후 캡처 → 금색 제목·회색 문구·가운데 정렬·간격 정상
- 서체: 대표님이 Noto Serif KR 연결 완료. Designer 화면에서 세리프·굵기 정상 확인 (MCP 캡처 도구는 Google Fonts를 반영하지 않아 고딕으로 보임 → 서체는 Designer 화면 기준으로 확인)

**메인페이지 LIVE Proof 섹션 제작 (Statement 다음)**
- 승인 사항: 4번째 숫자 카드에 67·23·90명 표기 추가, Figma 대표 이미지를 Webflow에 업로드
- 구조 (모두 Lumos 템플릿 컴포넌트): `Section`(ID `live-proof`) → `Layout`(Columns) [왼쪽: Eyebrow + Heading(H1) + Paragraph + Tag / 오른쪽: Visual Image] → Eyebrow("숫자로 보는 GLOBAL COMPANY") → `Grid`(2열) + `Card Primary` 4개
- 변형(Variant) 추가 (원본은 그대로)
  - Card Primary → **`Stat`** (작은 모서리, 안쪽 여백 space-4, 테두리 없음, 작은 본문)
  - Typography Tag → **`Gold Outline`** (금색 10% 배경, 금색 글자·테두리, 둥근 모양)
- 카드 4개: 5.43M 다이아·약 3,800만 원(안내 문구 2줄 포함) / MBC·SBS / WINNER / 소속 크리에이터 67명·에이전트 23명(총 90명, 기준 2026년 10월). 카드 링크는 숨김
- 대표 이미지: Figma 캡처본(1배, 599×765) 업로드 → 원본 사진으로 교체 필요
- 화면 확인: Designer 캡처로 텍스트·배치·카드 내용 정상 확인
- 시안과 남은 차이 (사용자 확인 후 처리)
  - 제목 2번째 줄 금색, 본문 첫 줄 굵게: MCP로는 일반 텍스트만 넣을 수 있어 미적용 → Designer에서 굵게(strong) 처리 필요
  - 대표 이미지가 가로로 넓게 잘려 보임 (Tall 4/5 변형이 이 폭에서 세로 비율로 보이지 않음)
  - 숫자 카드 배치·섹션 간격은 Figma 값과 비교 후 조정 예정

**LIVE Proof 보완 (대표님 승인: 2번 이미지 비율, 3번 배치·간격)**
- 이미지 비율: 원인은 Layout `Columns` 변형의 오른쪽 열이 16:9로 고정·잘림(clip)되어 있던 것
  - Layout에 **`Columns Tall Media`** 변형 추가 (Columns 복제 + 오른쪽 열 비율·높이 auto) → 이미지가 자체 비율(Tall 4/5)대로 세로형 표시
- 숫자 카드 배치: Figma도 2열 × 2줄이라 그대로 유지
- "숫자로 보는 GLOBAL COMPANY" 라벨: 가운데 → **왼쪽 정렬**로 수정 (Eyebrow Classes에 `u-alignment-start u-margin-bottom-0`)
  - 처음엔 Content Wrapper로 감싸려 했으나 MCP로 컴포넌트 순서 이동이 막혀 있어 삽입했던 것은 바로 삭제
- 섹션 위 간격: Main → **Small** (Figma 이미지 위 약 76px과 비슷)
- 남은 차이: 라벨~카드 간격 약 70px(Figma 48px), 섹션 아래 간격 약 80px(Figma 120px) → 수식 변수(섹션 간격) 정리 때 함께 조정

**메인페이지 CTA 섹션 제작 (대표님 승인: 확정 문구, 배경 이미지 업로드, 임시 링크 #)**
- 구조 (모두 Lumos 템플릿 컴포넌트): `Section`(ID `cta`, 위·아래 간격 Large) → Background: `Visual Image` / Container: `Content Wrapper`(Center) → Eyebrow + Heading(H1) + Paragraph + `Button Wrapper`(`Button Main`) + Paragraph(Text Small)
- 내용: "CREATOR RECRUITMENT" / "YOUR STAGE / STARTS HERE." / 고객 확정 문구 "처음이라도 괜찮습니다. 방송 방향 상담부터 첫 방송 준비, 진행과 시청자 소통, 방송 후 피드백까지 함께합니다." / 버튼 "크리에이터 지원하기"(링크 #, 지원 페이지 생성 후 연결) / "지원서 작성 3분 · 접수 후 순차적으로 연락드립니다"
- 배경 이미지: Figma 무대 조명 이미지를 캡처 URL로 업로드 (`cta-stage-background.png`, 1440×760, 투명도 35% 포함)
- 변형(Variant) 추가: Visual Image → **`Cover Transparent`** (Cover 복제 + 이미지 틀 배경 투명, 이미지 투명도 0.3 + screen 합성)
- `Media Overlay`를 넣었으나 캡처에서 회색 막처럼 보여(color-mix 표현 추정) 삭제. 이미지 변형만으로 시안과 비슷한 어두운 무대 분위기 확인
- 남은 차이: 제목 2번째 줄 금색 그라데이션(굵게 처리 필요), 버튼 금색 그라데이션·빛 번짐, 하단 금빛 타원 광원, 버튼~안내 문구 간격(시안 24px)

**푸터 제작 시도 (Lumos Footer 변형 방식, 대표님 승인)**
- Footer 컴포넌트에 **`Global Company`** 변형 추가 (아직 스타일 변경 없음)
- Footer 안의 Grid → Footer Group → Footer Link처럼 **컴포넌트 안 슬롯에 들어간 컴포넌트는 MCP로 문구·링크 수정이 불가**함을 확인 (ID 조회·수정 모두 실패)
- 시험 삽입한 Grid는 삭제해 Footer 원래 상태로 복구 → 진행 방식 대표님 확인 대기

**푸터 제작 (대표님 결정: 1번 — 구조·스타일은 올인웹, 문구·링크는 Designer에서 직접 입력)**
- Footer 정의에 추가: 새 `Grid`(3열) + `Footer Group` 3개(링크 5·2·1개), 워드마크 문단(`footer_wordmark`), 슬로건 문단(`footer_motto`)
- 기존 Lumos 메뉴 Grid는 삭제하지 않고 **Visibility 끔** (변형 스타일로는 컴포넌트 안 컴포넌트에 붙인 클래스를 제어할 수 없어 이 방식 사용 → 기본 변형에도 새 Grid가 보임)
- `Global Company` 변형 스타일: 배경·글자색 테마 변수 / 레이아웃 세로 역순(메뉴 → 워드마크) / 로고·SNS 아이콘 숨김 / 하단 링크는 첫 번째(개인정보처리방침)만 표시 / 워드마크·슬로건 표시
- 기본 변형에서는 워드마크·슬로건 숨김 (`display: none`)
- 워드마크 금색 그라데이션: MCP가 `-webkit-background-clip`을 허용하지 않아 금색 단색(`heading-accent`)으로 대체 → Designer에서 "Clip background to text"로 그라데이션 적용 가능
- Home 페이지 본문 아래에 Footer 배치, `Global Company` 변형 적용, 캡처로 배치 확인
- Designer에서 직접 입력할 항목: 그룹 제목 3개(MENU·FOLLOW US·EMAIL), 메뉴 링크 5개, SNS 2개, 이메일 1개, 저작권 문구, 개인정보처리방침 문구
- 남은 차이: 메뉴 글자 크기(시안 28px), 메뉴와 정보 사이 세로 구분선, 워드마크 그라데이션

**푸터 새 컴포넌트 제작 (대표님 지시: Lumos 컴포넌트가 아닌 새로 제작, 기존 만든 컴포넌트는 유지)**
- 새 컴포넌트 **`Global Footer`** (그룹 Global) 생성. Lumos Footer와 별개로 Home 본문(`page_main`) 아래에 배치
- 기존 Lumos Footer의 `Global Company` 변형과 추가 요소는 **그대로 유지** (대표님 지시). Home에 넣었던 Lumos Footer 인스턴스만 제거
- 구조: `<footer>` → (스크린리더용 h2 "Footer") → `u-container` → Top[메뉴 nav(Home·LIVE Guide·Creators·Insight·Contact) + 정보 영역(FOLLOW US: TikTok·Instagram / EMAIL: mils5959@naver.com)] → 워드마크 "Global Company" → Bottom[© 2026 Global Company. All rights reserved. + 개인정보처리방침 / 슬로건]
- 스타일: 새 클래스 `gfooter_*` 15개를 Lumos 변수로 작성 (배경·글자·강조색·테두리·간격 변수 사용, 하드코딩 색 없음). 태블릿 이하는 세로 배치, 메뉴와 정보 사이 구분선은 정보 영역 왼쪽 테두리로 구현
- 링크: Home만 실제 연결, 나머지 메뉴·SNS·개인정보처리방침은 임시 #, 이메일은 mailto
- 시도 후 변경한 부분: 별도 구분선 요소는 Designer 캔버스에서 넓은 막대로 보여 삭제 → 테두리로 대체 / `w--current` 클래스는 예약어라 만들 수 없어 현재 페이지 금색 표시는 미적용(메뉴 모두 흰색)
- 시안과 남은 차이: 워드마크 금색 그라데이션(금색 단색으로 대체, Designer에서 글자 모양 배경 설정 필요), Home 메뉴 금색 강조, 저작권 연도는 고정 2026(Lumos 자동 연도 스크립트 미사용)
- 화면 확인: Designer 캡처로 시안 배치 확인 (캡처 도구는 Google Fonts 미반영 → 워드마크 서체는 Designer 화면에서 확인 필요)

**미해결 1·2번 처리 방식 결정**
- 수식 값 3가지(글자 크기 유동값, XL/2XL, 섹션 간격)와 버튼 색 이상(보조·텍스트 링크)은 따로 처리하지 않음
- **개발하면서 해당 화면을 만들 때 그때그때 수정**하기로 결정 (대표님 지시)

---

## 5. 미해결·확인 필요 사항

| # | 항목 | 담당 | 상태 |
|---|---|---|---|
| 1 | 글자 크기 유동값·XL/2XL·섹션 간격 → Designer에서 직접 입력 | 대표님 (값 목록은 올인웹 작성) | 개발 중 수시 처리 (10/11 결정) |
| 2 | 보조·텍스트 링크 버튼 색 이상 원인 확인 | 올인웹 | 개발 중 수시 처리 (10/11 결정) |
| 3 | 타이포그래피 영역 실제 배경색 확인 | 대표님 (Designer) | 확인 요청 |
| 4 | Noto Serif KR 연결 (Google Fonts) | 대표님 | 예정 |
| 5 | 사이트 이름 오타, 시간대 Asia/Seoul | 대표님 (Designer) | 확인 요청 |
| 6 | Lumos v2.2.3 문서 확인 (Notion 접근 차단) | — | 보류 |
| 7 | Figma에 10/9 추가 요청 5건 반영 여부 | 올인웹 | 미확인 |
| 8 | 버튼 hover 색 (Figma 상태 미확인, 임의 지정) | 올인웹 | 확인 필요 |
| 9 | 고객 실적 기준 자료(10/10) 수신 여부 | 대표님 | 확인 필요 |
| 10 | GSAP 스킬 브랜치 → main PR 여부 | 대표님 | 결정 대기 |

## 6. 다음 단계 (제안)

1. CMS 컬렉션 설계: 크리에이터(9명, 순서·분류·TikTok 연결), 소식·이벤트(성과/뉴스/이벤트/정보), 메인 팝업
2. 10/12 개발 착수: 공통(내비게이션·푸터·하단 고정 버튼) → Home(스크롤 연출 6단계) → 각 페이지 (미해결 1·2번은 이 과정에서 함께 수정)
