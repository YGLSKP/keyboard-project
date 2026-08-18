# Keyboard Service Design System

> 한국어 인앱 키보드 서비스의 디자인 토큰 및 컴포넌트 정의
> 
> 플랫폼: Android (모바일 375×812px)  
> 대상: 30-40대 일반 사용자  
> 스타일: 미니멀, 기능 중심

---

## Color Tokens

### Primary Background
- **keyboard-bg**: `#d9dadd` — 키보드 전체 배경 (회색)
- **key-bg**: `#ffffff` — 일반 키 배경 (흰색)
- **func-key-bg**: `#b6b8bc` — 기능 키 배경 (짙은 회색)
- **input-bg**: `#ffffff` — 입력 영역 배경
- **nav-bg**: `#ffffff` — 하단 네비게이션 배경

### Interactive States
- **key-bg-active**: `#c5c6c9` — 키 누름 상태
- **func-key-bg-active**: `#9a9da1` — 기능 키 누름 상태

### Text & Borders
- **text-primary**: `#1a1a1a` — 주 텍스트 (검은색)
- **text-secondary**: `#3a3a3a` — 보조 텍스트 (짙은 회색)
- **text-tertiary**: `#888888` — 약한 텍스트 (스페이스, 힌트)
- **text-icon**: `#4a4a4a` — 네비게이션 아이콘 (회색)
- **text-icon-secondary**: `#6a6a6a` — 아이콘 세부 (더 어두운 회색)
- **border-light**: `#c5c6c9` — 경계선 (배너)
- **border-subtle**: `#f0f0f0` — 미묘한 경계선

---

## Typography

### Font Family
```
-apple-system, BlinkMacSystemFont, 
"Apple SD Gothic Neo", "Malgun Gothic", 
"맑은 고딕", sans-serif
```
> iOS/Android 시스템 폰트 → Google NotoSansCJK → 맑은 고딕 순서 폴백

### Font Sizes & Weights

| 컨텍스트 | 크기 | 웨이트 | 용도 |
|---|---|---|---|
| **status-bar** | 13px | 600 | SKT, 시간 |
| **battery-text** | 11px | 400 | 배터리 퍼센트 |
| **key-numeric** | 18px | 400 | 숫자 키 (1-9, 0) |
| **key-hangul** | 17px | 400 | 한글 자모 (ㅂ, ㅈ...) |
| **key-small** | 13px | 400 | 쉼표, 마침표 |
| **key-space** | 13px | 400 | 스페이스 라벨 |
| **func-key** | 15px | 400 | 시프트, 백스페이스 |
| **nav-icon** | 18px | 400 | 네비게이션 아이콘 |
| **nav-icon-recent** | 14px | 300 | 최근 앱 아이콘 |

---

## Spacing Scale

### Padding & Margins

| 항목 | 값 | 설명 |
|---|---|---|
| **status-bar-px** | 0 18px | 좌우 패딩 |
| **banner-px** | 0 16px | 배너 좌우 패딩 |
| **keyboard-px** | 4px 4px 8px | 키보드 전체 (상 좌우 하) |
| **key-row-px** | 0 (기본), 0 18px (행 2) | 키 행 패딩 |

### Gaps & Distances

| 항목 | 값 | 설명 |
|---|---|---|
| **key-gap** | 4px | 키 사이 간격 (가로) |
| **row-gap** | 6px | 행 사이 간격 (세로) |
| **status-left-gap** | 6px | 상태바 좌측 요소 간격 |
| **status-right-gap** | 4px | 상태바 우측 요소 간격 |
| **battery-gap** | 3px | 배터리 아이콘 간격 |
| **icon-gap** | space-around | 네비게이션 아이콘 균등 배치 |

---

## Component Tokens

### Status Bar
```css
height: 28px;
padding: 0 18px;
background: default (투명 또는 시스템 기본)
font-size: 13px;
font-weight: 600;
color: #1a1a1a;
```

### Banner (Keyboard Header)
```css
height: 48px;
background: #d9dadd;
padding: 0 16px;
border-bottom: 1px solid #c5c6c9;
display: flex;
align-items: center;
justify-content: flex-end;
```

**하위 요소:**
- **banner-close**: width 24px, height 24px, font-size 20px, color #2a2a2a

### Input Area
```css
flex: 1;
background: #ffffff;
/* 빈 영역, 스크롤 가능 */
```

### Suggestion Bar (Emoji/Recommendation)
```css
height: 56px;
background: #d9dadd;
display: flex;
align-items: center;
justify-content: center;
padding: 0;
```

**하위 요소:**
- **dot**: width 14px, height 14px, border-radius 50%, background #5a5a5a
- **dot-gap**: space-around (균등 배치)

### Keyboard
```css
background: #d9dadd;
padding: 4px 4px 8px;
display: flex;
flex-direction: column;
gap: 6px;
```

**Key Row:**
```css
display: flex;
gap: 4px;
width: 100%;
```

**Key (일반)**
```css
flex: 1;
height: 40px;
background: #ffffff;
border-radius: 5px;
display: flex;
align-items: center;
justify-content: center;
font-size: 18px (숫자) | 17px (한글);
color: #1a1a1a;
font-weight: 400;
cursor: pointer;
transition: background 0.1s ease;
```

**Key States:**
- **default**: background #ffffff
- **active**: background #c5c6c9

**Key Variants:**

| 변형 | flex | background | font-size | 설명 |
|---|---|---|---|---|
| **hangul** | 1 | #ffffff | 17px | 한글 자모 |
| **small** | 1 | #ffffff | 13px | 쉼표, 마침표 |
| **func** | 1.4 | #b6b8bc | 15px | 시프트, 백스페이스 |
| **func-active** | 1.4 | #9a9da1 | 15px | 기능 키 누름 |
| **symbol** | 1.2 | #b6b8bc | 13px | !@# 기호 |
| **space** | 4.2 | #ffffff | 13px | 스페이스 |

### Navigation Bar (Bottom)
```css
height: 48px;
background: #ffffff;
display: flex;
align-items: center;
justify-content: space-around;
padding: 0;
margin: 0;
border-top: none;
```

**Nav Icon:**
```css
font-size: 18px;
line-height: 1;
color: #4a4a4a;
display: flex;
align-items: center;
justify-content: center;
```

**Nav Icon Variants:**

| 변형 | 크기 | 설명 |
|---|---|---|
| **apps** | 18×18px | 3×3 그리드 아이콘 |
| **recent** | 자유 | "|||" 텍스트, font-size 14px |
| **home** | 16×16px | 원형 테두리 (border 1.5px) |
| **down** | 자유 | "⌄" 화살표, font-size 14px |

---

## Interaction & States

### Key Press
- **Duration**: 0.1s ease
- **Change**: background color 전환
- **Haptic**: 시각적 피드백 (색 변경으로 표현)

### Multi-touch
- 동시 여러 키 인식 (구현 레벨)

---

## Layout Specifications

### Device Frame
- **Width**: 375px (iOS/Android 표준)
- **Height**: 812px (세로 모드)
- **Border**: 1px solid #d4d4d4
- **Border-radius**: 4px

### Keyboard Height Calculation
```
Total: 812px
= Status Bar (28px)
+ Input Area (가변, flex: 1)
+ Banner (48px)
+ Suggestion Bar (56px)
+ Keyboard (4px + 5행×40px + 4행×6px + 8px)
+ Nav Bar (48px)
```

### Keyboard Row Heights
```
숫자 행: 40px + 4px gap
자모 행 1: 40px + 4px gap
자모 행 2: 40px + 4px gap (좌우 18px indent)
자모 행 3: 40px + 4px gap
기능 행: 40px + 8px 하단 패딩
```

---

## Icon Specifications

### System Icons (Unicode/CSS)
- **shift**: `⇧` (U+21E7)
- **backspace**: `⌫` (U+2326)
- **enter**: `↵` (U+21B5)
- **globe**: `🌐` (U+1F310, 그레이스케일 필터)

### Custom Icons
- **apps-grid**: 9개 작은 사각형 (3×3 배치), gap 2px
- **recent-apps**: 세로 3개 선 `|||`, letter-spacing -1px
- **home**: 원형 테두리
- **back**: 역방향 화살표 `⌄`

---

## Dark Mode (선택사항, 향후)

> 다크모드 토큰은 아직 정의되지 않음. 필요시 추가:
> - keyboard-bg-dark: `#2a2a2a`
> - key-bg-dark: `#3a3a3a`
> - text-primary-dark: `#ffffff`
> 등

---

## Accessibility

- **Minimum Touch Target**: 44px × 44px (권장)
  - 현재 키: 40px (높이는 충분하나, 너비는 flex에 따라 조정)
  
- **Color Contrast**:
  - 텍스트 vs 배경: WCAG AA 이상 확보
  - #1a1a1a on #ffffff: 높음 ✓
  - #1a1a1a on #d9dadd: 중간 ✓

- **Keyboard Navigation**: 모바일이므로 미적용

---

## Implementation Notes

### CSS Variables (선택사항)
```css
:root {
  --color-keyboard-bg: #d9dadd;
  --color-key-bg: #ffffff;
  --color-func-bg: #b6b8bc;
  --color-text-primary: #1a1a1a;
  
  --spacing-key-gap: 4px;
  --spacing-row-gap: 6px;
  
  --font-size-key: 18px;
  --font-size-hangul: 17px;
  
  --radius-key: 5px;
  --height-key: 40px;
}
```

### Responsive Breakpoints
- 현재: 375px (고정)
- 확장 예정: 390px (Pixel), 430px (Galaxy 등)

### Browser Support
- iOS Safari (최신 2개 버전)
- Chrome/Firefox (최신 2개 버전)
- Samsung Internet (최신)
- 웹킷 프리픽스(`-webkit-`) 포함

---

## Version History

| 버전 | 날짜 | 변경 사항 |
|---|---|---|
| 1.0 | 2026-06-26 | 초기 버전 (keyboard-v2.html 기반) |

---

## Related Files

- `keyboard-v2.html` — 구현 레퍼런스
- `CLAUDE.md` — 프로젝트 컨벤션
- 다른 화면 와이어프레임 (향후 추가)
