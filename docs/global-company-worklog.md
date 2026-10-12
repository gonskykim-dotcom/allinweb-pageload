# Global Company 웹사이트 구축 — 작업수행일지

- 고객: Global Company (TikTok LIVE 크리에이터 에이전시) / 담당: 박재현 대표
- 수행: 올인웹 (김성곤)
- 플랫폼: Webflow + Lumos Framework, Webflow MCP로 구축
- 최종 업데이트: 2026-10-12

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
5. **(10/11 추가) 컴포넌트 안에 들어간 컴포넌트는 연결을 끊어(Unlink) 일반 요소로 만든 뒤 수정한다.** MCP로는 중첩 컴포넌트의 문구·링크를 바꿀 수 없기 때문.
6. **(10/11 추가) 컴포넌트로 해결되지 않는 부분은 연결을 끊거나 새로 만든다.** 새로 만들 때도 색·간격·글자는 Lumos 변수를 사용한다.

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

**Lumos 푸터 문구 입력 (새 기준 5·6번 적용)**
- 비교용으로 Home 맨 아래에 Lumos Footer(`Global Company` 변형)를 추가 배치 → 현재 Home에 푸터 2개(`Global Footer`, Lumos Footer)
- Footer 안 메뉴 Grid → Footer Group 3개 차례로 연결 끊기(Unlink) → 그룹 제목(MENU·FOLLOW US·EMAIL)과 링크 8개 문구 입력. Home 링크는 "/", 이메일은 mailto
- 저작권 문구 "Global Company. All rights reserved."로 수정, "Privacy Policy"는 글자 수정이 안 되는 요소라 같은 클래스의 문단으로 새로 만들어 "개인정보처리방침"으로 교체
- 연결을 끊은 Grid가 열 설정을 잃어 `u-grid` + `footer_menu_grid` 조합 클래스로 3열(모바일 1열) 지정
- 화면 확인 완료

**워드마크 SVG 전환 검토 (검토만)**
- Figma 워드마크를 SVG로 내보내기 성공(약 17KB). SVG 사용 시 금색 그라데이션·서체가 시안 그대로 유지됨 → SVG 추천

**워드마크 SVG 적용 (대표님 승인)**
- Figma 노드 40349:13090을 SVG로 추출 → Webflow 자산 `global-company-wordmark.svg` 업로드 (Figma 주소로 바로 업로드 성공)
- `Global Footer`, Lumos Footer 두 곳의 워드마크 글자(문단)를 SVG 이미지로 교체. 가로폭 100%·높이 자동, 장식용(alt 비움, aria-hidden), 지연 로딩
- 클래스 `gfooter_wordmark`, `footer_wordmark`에서 글자용 속성 제거, 이미지용(가로 100%)으로 변경. Lumos Footer는 기본 변형에서 숨김 유지
- 화면 확인: 두 푸터 모두 시안과 같은 세리프 서체·금색 그라데이션으로 표시
- 참고: 워드마크 문구나 색을 바꾸려면 Figma에서 다시 추출해야 함

**CMS 구축 설계 검토 (검토만, 사이트 변경 없음)**
- 확인 자료: Figma 크리에이터 목록(40530:5373)·상세(40530:6246), 소식 목록(40530:5918)·상세(40530:6055), 메인 팝업(40530:4983), 고객 메일 확정 사항
- 컬렉션 3개 제안: 크리에이터 / 소식·이벤트(Insight) / 메인 팝업 (+ 분류를 여러 개 고를 경우 '크리에이터 분류' 컬렉션 추가)
- 기본 기능으로 되는 것: 순서 정렬, 값 없는 통계 자동 숨김(조건부 표시), 관련 글(같은 분류·현재 글 제외), 팝업 게시 기간 필터, 페이지네이션
- 추가 스크립트 필요: 분류 필터 버튼, 이전/다음 글, 목차, D-day 표시, 링크 복사, '오늘 하루 보지 않기'
- 결정 필요 8건(분류 단일/복수, 하이라이트 영상 방식, 협업 이력 입력 방식, D-day 자동 여부, 외부 필터 스크립트 사용, TikTok 버튼 문구, 사이트 플랜, 실제 데이터 수급) → 대표님 확인 대기

**CMS 컬렉션 생성 (대표님 결정 반영, 페이지는 만들지 않음)**
- 결정: ① 분류는 1명당 1개(선택 항목) ② 하이라이트 영상은 TikTok 샘플 링크 사용 ③ 협업 이력은 서식 있는 글 ④ D-day 자동 계산 ⑤ 필터·이전/다음 글은 직접 JS 작성(외부 스크립트 미사용) ⑥ 버튼 문구 'TikTok 프로필 보기' ⑦ CMS 사용 가능 플랜 확인(컬렉션 생성 성공)
- **Creators** (`6acb90cfb313d128cec38c3e`): 이름·슬러그 + 26개 필드 — TikTok 닉네임·아이디·프로필 링크, 소개 순서, 분류(일상·소통/음악·보컬/운동·피트니스/요리·먹방/취미·라이프), 카드 사진(9:16), 원형 프로필 사진, 키워드 1~3, 소개글, 한 줄 문구, 하이라이트 썸네일·TikTok 링크·캡션·길이, 갤러리, 브랜드 협업 이력, 통계 5종 + 기준일, 강조 색, Home 노출
- **Insights** (`6acb90f7b914c960d334eb72`): 이름·슬러그 + 분류(성과/뉴스/이벤트/정보), 게시일, 요약, 대표 이미지, 대표 글, 핵심 요약, 본문(H2 → 목차), 읽는 시간, 작성자, 태그, 이벤트 시작·종료일(D-day·진행중·마감 자동), 관련 크리에이터(참조)
- **Popups** (`6acb90f8e028ee9ba1d8fe9f`): 이름·슬러그 + 팝업 이미지(4:5, 필수), 이미지 설명(alt), 연결 링크, 게시 시작·종료일, 사용
- TikTok 샘플 링크: `https://www.tiktok.com/@scout2015/video/6718335390845095173` (TikTok 공식 임베드 안내 예시 영상) → 하이라이트 링크 필드 도움말에 기재
- 필드마다 입력 예시를 도움말로 넣음. 필드 슬러그는 한글 이름이 로마자로 자동 변환됨(예: `tiktok-nigneim`) — 페이지·JS 연결 시 이 슬러그 사용
- 참고: Webflow는 컬렉션을 만들면 템플릿 페이지가 자동 생성됨(페이지 디자인은 아직 하지 않음). Popups 템플릿 페이지는 쓰지 않으므로 페이지 작업 때 비활성화 필요
- 남은 결정: ⑧ 크리에이터 실제 데이터(소개·통계·협업 이력·사진) 수급

**크리에이터 임시 항목 9개 입력 (대표님 승인, Draft 상태)**
- Figma 기준: 이름, TikTok 닉네임·아이디, 프로필 링크(`https://www.tiktok.com/@아이디`), 소개 순서 1~9, Home 노출 켬
- 하이라이트 TikTok 링크: 9명 모두 샘플 링크(TikTok 공식 예시 영상)
- 분류·사진·소개글·통계·협업 이력은 확정 자료가 없어 비워 둠 (고객 자료 수급 후 입력)
- 프로필 링크는 아이디로 만든 주소라 실제 접속 확인은 하지 않음

**미해결 1·2번 처리 방식 결정**
- 수식 값 3가지(글자 크기 유동값, XL/2XL, 섹션 간격)와 버튼 색 이상(보조·텍스트 링크)은 따로 처리하지 않음
- **개발하면서 해당 화면을 만들 때 그때그때 수정**하기로 결정 (대표님 지시)

**대표님 이메일·Dropbox 9명 자료 확인 (10/11, 검토만, 사이트 변경 없음)**
- 이메일 2개 스레드 전체 확인: 10/7 분류·한 줄 문구·소개글·키워드, 10/9 소개 순서·활동명·TikTok ID 확정
- 소개 순서(10/9 확정)는 CMS 입력 순서와 같음: 이철희 → 조담인 → 승환 → 김린아 → 최윤진 → 박정은 → 노진희 → 신솔 → 최성연
- CMS와 다른 점: 분류·문구·소개글·키워드 미입력, 닉네임 3건(최윤진·박정은·이철희) 수정 필요, 키워드 4개인 인원 2명(승환·조담인, 필드는 3개)
- Dropbox `03_구성원_크리에이터/직원분들 사진`: 9명 폴더 모두 있음, 총 27장 (조담인 7, 이철희 5, 김린아 5, 최성연 3, 최윤진 3, 노진희 1, 신솔 1, 승환 1, 박정은 1)
- 사진 내용(구도·세로 비율)은 컨테이너 네트워크 차단으로 내려받지 못해 눈으로 확인하지 못함
- CMS 반영은 대표님 동의 후 진행

**크리에이터 CMS 실제 자료 입력 (10/11, 대표님 승인)**
- 필드 추가: `키워드 4` (kiweodeu-4, 선택) — 조담인·승환 키워드 4개 대응
- 9명 전원 입력: 분류(10/7 메일), 한 줄 문구, 소개글, 키워드(#표기), 닉네임 3건 수정(🫧 이브⋆𝑬𝒗𝒆 🫧 / 🖤니니 NINI🐈‍⬛ / 🚀Chul 👨‍🚀 ZWJ 포함)
- 샘플 하이라이트 TikTok 링크는 대표님 지시로 우선 유지 (오픈 전 삭제 필요)
- 사진: Dropbox 임시 다운로드 링크 → Webflow `upload_image_by_url`로 업로드
  - Dropbox 폴더 실제 사진 수 28장 (조담인 8장, 앞선 보고의 7장은 오기)
  - 업로드 도구 시간 초과가 반복되어 대표님 지시로 중단 → 21장 업로드 (조담인 8, 이철희 5, 최성연 3, 최윤진 3, 노진희 1, 박정은 1)
  - 미업로드: 신솔 1, 승환 1, 김린아 5
- CMS 사진 연결 (6명)
  - 이철희: 카드 gym 셀카(02), 원형 얼굴 클로즈업(00), 갤러리 2장
  - 조담인: 카드 어두운 스튜디오(04), 갤러리 6장 (원형은 비움 → 카드 사진 사용)
  - 최윤진: 카드 골프 흰 썬캡(01), 원형 골프 검정 썬캡(02), 갤러리 2장
  - 최성연: 카드 셀카(01), 갤러리 2장 / 노진희·박정은: 카드 1장
- 사진에서 제외한 것: 조담인 02·06 (유튜브 화면 캡처, 타인 얼굴 포함·가로), 이철희 01 (잡지 로고·속옷), 이철희 03·04 (휴대폰 화면 캡처, 상태표시줄 포함), 최윤진 03 (TikTok 화면 캡처, 'AI로 생성된 콘텐츠' 표시)

### 2026-10-12 — 로컬 전환, 크리에이터 CMS 점검

**클라우드 → 로컬 전환**
- 로컬 Dropbox 폴더(`글로벌컴퍼니/allinweb-pageload`)에 저장소 받음, 브랜치 `claude/global-company-gsap-skill`
- 로컬 연결 상태: Dropbox·Gmail·Webflow 사용 가능, Figma는 인증 필요

**고객 확정 문구·분류와 Creators CMS 대조 (검토만, 사이트 변경 없음)**
- 대조 기준: 대표님이 전달한 "구성원별 소개 문구"(한 줄 문구·소개글·소개 키워드)와 "크리에이터 분류 필터"(주 분류)
- 결과: **9명 모두 한 줄 문구·소개글·키워드·주 분류가 고객 자료와 일치**. 키워드 4개인 조담인·승환은 `키워드 4`까지 입력됨
- 활동명·이모지, TikTok ID, 프로필 링크도 기존 값 유지 확인
- 일지와 달랐던 현황 (일지 미기록 작업으로 추정)
  - 사진: 신솔·승환·김린아 포함 **9명 모두 카드·원형·갤러리 사진과 하이라이트 썸네일 연결 완료** (새 사진은 `KakaoTalk_*` 파일명)
  - 게시 상태: **9명 모두 Draft 아님, 2026-10-12 약 20:50(한국 시간) 게시됨**
- 주의: 9명 모두 하이라이트 TikTok 링크가 아직 샘플 영상 → 상세 페이지가 라이브에 열려 있으면 샘플이 노출될 수 있음

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

---

## 7. 인수인계 (클라우드 세션 → 로컬, 10/11)

### 7-1. 로컬에서 시작하는 방법
1. `git clone https://github.com/gonskykim-dotcom/allinweb-pageload.git` → `git checkout claude/global-company-gsap-skill`
2. 로컬 Claude Code에 연결할 것: Webflow MCP, Figma MCP, Dropbox, Gmail (Google Drive는 선택)
3. Claude에게 `CLAUDE.md`와 이 작업일지를 먼저 읽게 한 뒤 작업 시작
4. Webflow 작업 내용은 Webflow 서버에 저장되어 있어 따로 옮길 것 없음

### 7-2. 작업 규칙 (요약)
- 답변은 한국어, 협의되지 않은 작업은 동의 후 진행 ("말씀주신 부분으로 진행하겠습니다")
- 검토만 요청한 경우 사이트 수정 금지
- Lumos 컴포넌트 + 변형(Variants) 우선 사용
- 컴포넌트 안의 컴포넌트는 연결 해제(unlink) 후 수정
- 컴포넌트로 안 되는 것은 연결 해제하거나 Lumos 변수로 새로 제작
- 작업할 때마다 이 일지에 기록 후 커밋·푸시

### 7-3. 주요 ID
**사이트·페이지**
| 항목 | ID |
|---|---|
| Webflow 사이트 | `6ac8f703fef5e75c9add8463` |
| Home 페이지 | `6ac8f703fef5e75c9add8431` |
| Home page_wrap | `4be9a37b-c87f-90d1-0eb1-5bdc213da5fb` |
| Home page_main | `62930284-d0d8-35d6-dd4f-4d4909c04dd0` |
| Figma 파일 키 | `iB6KIWwcJvNiGhCiEjm1Tv` |

**Home 섹션·컴포넌트** (순서: 내비 → Statement → LIVE Proof → CTA → Global Footer → Lumos Footer)
| 항목 | ID |
|---|---|
| Statement 섹션 | `02c547cd-f42c-2eba-1176-034115839736` |
| LIVE Proof 섹션 | `d552649a-ca57-690c-3e4f-eabadefdbed6` |
| CTA 섹션 | `b7e98ce6-4294-b563-5094-86005c37870a` |
| Global Footer 컴포넌트 (새로 만든 푸터, gfooter_* 클래스) | `bec83444-8471-b4f9-2546-433307d10a4a` |
| Global Footer 인스턴스 (Home) | `3ce76454-1de4-ae04-057d-762cbb90f0aa` |
| Global Footer 워드마크 이미지 | `c92e1bc3-617b-0330-7634-519a4069edc4` |
| Lumos Footer 인스턴스 (Home, 비교용) | `5e262a4e-3115-102d-e6c7-16041aa35847` |
| Lumos Footer 변형 "Global Company" | `706396f2-bd61-afe4-fbb8-3ecb733875c0` |
| Lumos Footer 메뉴 그리드 (연결 해제됨, `u-grid footer_menu_grid`) | `20b88990-7b60-d4eb-864f-ac2b7439cd8d` |
| Visual Image 변형 "Cover Transparent" (CTA 배경용) | `95f3a21d-a592-a750-96d9-fbf479fad936` |

**에셋**
| 항목 | ID |
|---|---|
| Global Company 워드마크 SVG | `6acb8c5a54f9656736c5b2b0` |
| CTA 배경 | `6acb819308b8632626f9e921` |
| 대표 정면 사진 | `6acb7b5bc1eea5af07eeafc1` |
| 크리에이터 사진 | 이름 `creator-<slug>-NN` (21장) |

**CMS**
| 항목 | ID |
|---|---|
| Creators | `6acb90cfb313d128cec38c3e` |
| Insights | `6acb90f7b914c960d334eb72` |
| Popups | `6acb90f8e028ee9ba1d8fe9f` |
| 크리에이터 항목 9개 (순서대로 이철희·조담인·승환·김린아·최윤진·박정은·노진희·신솔·최성연) | `6acb91deefe02dfe0f7554` + `bc, be, c0, c2, c4, c6, c8, ca, cc` |
| 분류 옵션 | 일상·소통 `f2d14b3666e639f0d88944715e67b55b` / 음악·보컬 `1c875ad6845c32083d5fb3b7bc102473` / 운동·피트니스 `8c5cad9409a4487b48d0ae82726fdce2` / 요리·먹방 `beb4fbd8c6a13bf41037427836d8910c` / 취미·라이프 `bba1461a1e5a9303601bbf5892e24250` |

**Lumos 변수 (자주 사용)**
| 용도 | ID |
|---|---|
| 배경 | `variable-3c7a6c5d-b346-0958-69b9-1a443ea05d8c` |
| 본문 텍스트 | `variable-7b07ac88-d28a-5c0a-7534-a6752a88d588` |
| 제목 강조(금색) | `variable-25bd0d95-1867-08bf-9f2f-eabc649f971e` |
| 보조 텍스트 | `variable-f8f04b3e-24f4-2aba-65ad-f4cbfe03254d` |
| 테두리 색 | `variable-375c0552-4fe6-af3e-8135-4c691ee51697` |
| gold-400 | `variable-e8305938-e678-73eb-eb8f-247b11361f01` |
| gold-700-o14 | `variable-fc3f4a07-8d05-f5f5-483b-abb4e16b33e7` |
| 제목 폰트 / 굵기 | `variable-88787e63-df77-6937-1a2a-782abb789123` / `variable-4b164c1c-8d1a-d4a3-2cae-137e7ca87326` |
| space 1 / 2 / 3 / 4 | `variable-5e62f431-67d5-8b18-e604-2447cdb2b716` / `variable-8380cdf9-4fff-ddb3-c837-bc12c334bc7d` / `variable-933e34a0-37cf-8815-1388-b217d407b2da` / `variable-97ded496-da13-cdd0-8025-9d1a1e00c3fe` |
| space 6 / 8 | `variable-962e621c-661a-9f49-c71d-02ade3d8dcc0` / `variable-9831d389-5f88-a61b-08d7-5428e0698435` |
| section-space large | `variable-b7808272-40b9-a59e-9fd8-59713fa8b96d` |
| 테두리 두께 | `variable-6a827233-04fc-6e0e-9b94-ad3b23777e0b` |

### 7-4. Webflow MCP 주의사항 (이번 세션에서 확인)
- 컴포넌트 정의 안의 중첩 인스턴스는 수정 불가 → `unlink_component_instance`(scope_component_id 지정)로 연결 해제 후 수정
- 인스턴스는 삽입·이동 기준(anchor)으로 쓸 수 없음
- 중첩 인스턴스의 Classes 속성으로 넣은 클래스에는 변형 스타일이 적용되지 않음
- TextBlock은 글자 없는 Block으로 생성됨 → 글자는 Paragraph 사용
- Block/DOM 요소에는 set_text 불가 → Paragraph를 새로 만들고 기존 요소 삭제
- `-webkit-background-clip` 속성 거부됨
- `w--current` 같은 Webflow 예약 클래스 이름은 깨짐 → 사용 금지
- 빈 div는 Designer에서 넓은 블록으로 보임 → 구분선은 border로 처리
- color-mix 오버레이는 스냅샷에서 회색으로 보임 (CTA는 오버레이 삭제, 이미지 opacity 0.3 + screen 블렌드로 해결)
- 컴포넌트 링크 속성은 url/email/phone/popover만 가능 (페이지 연결 불가 → Home은 url `/`)
- 이미지 업로드(`upload_image_by_url`)는 60초 시간 초과가 잦음 → 1~2장씩 업로드하고 `list_assets`로 결과 확인. 시간 초과 후에도 서버에서 계속 올라가는 경우가 있으니 중복 업로드 주의
- Dropbox 사진은 `download_link`(1회용 임시 링크, 최대 15분) → Webflow `upload_image_by_url` 순서로 가져옴 (클라우드 컨테이너에서는 직접 다운로드가 막혔음)
- Figma 에셋은 `download_assets`(svg) 후 Figma 에셋 URL로 Webflow 업로드 가능

### 7-5. 남은 작업
**CMS·콘텐츠**
- ~~신솔·승환·김린아 사진 7장 업로드 및 CMS 연결~~ → 10/12 확인 결과 9명 모두 사진 연결 완료
- 샘플 하이라이트 TikTok 링크 9개 → 오픈 전 삭제 (실제 영상 주소 받은 경우만 노출). **항목이 이미 게시 상태라 우선 처리 검토**
- 통계·경력·협업 이력: 실제 자료 없으면 숨김 처리
- 링크 기준 확인: 10/9 메일 "이름·활동명 또는 TikTok ID → 해당 프로필 연결"이 TikTok 프로필인지 상세 페이지인지 대표님께 확인

**10/9·10/10 메일 반영 사항**
- 숫자 카드: 소속 크리에이터 67명 / 에이전트 23명 / 총 90명 네트워크 / 기준 2026년 10월 ("직원 90명" 표기 금지)
- 크리에이터 영역 안내 문구: "홈페이지에는 소속 크리에이터 중 일부를 소개합니다."
- 상세 버튼: 'TikTok 프로필 보기'
- 대표 실적 카드: 제목 "대표 개인 TikTok LIVE 월간 최고 실적" / "5.43M 다이아 · 원화 환산 약 3,800만 원" / 안내 "1,000다이아당 7,000원을 적용한 참고 환산액이며, 실제 정산액과 다를 수 있습니다. 대표 개인의 최고 실적이며, 크리에이터별 성과와 수익은 다를 수 있습니다."
- 하단 모집 문구 통일: "처음이라도 괜찮습니다. 방송 방향 상담부터 첫 방송 준비, 진행과 시청자 소통, 방송 후 피드백까지 함께합니다."
- 메인 첫 화면: 중앙 대표 슈트, 왼쪽 조담인, 오른쪽 이철희 유지

**개발**
- Home에 남길 푸터 결정 (Global Footer / Lumos Footer)
- 크리에이터 섹션, 목록·상세 페이지, Insight, 팝업, 필터 JS
- 지원서: 필수·선택 동의 분리(사전 체크 금지), 선택 미동의 시 선택 정보 미전송, GA4에 개인정보 전송 금지
- 이전 잔여: 제목 금색 strong 처리, 대표 사진 원본 교체
- 일정: 10/26 개발 완료·임시 도메인 전달, 10/28 목표 완료
