---
description: 팔레트 토큰, 글꼴 스택, 반경 및 간격 토큰, 텍스트 역할 값, 구성 요소 속성 및 평가 스타일을 포함한 Content Composer 테마 JSON 스키마의 모든 속성에 대한 전체 참조입니다.
jcr-language: en_us
title: Adobe Learning Manager Content Composer 테마 JSON 속성 참조
source-git-commit: ea6d296fa99686136ab08d756a20570a4681d704
workflow-type: tm+mt
source-wordcount: '1899'
ht-degree: 5%

---


# Adobe Learning Manager Content Composer 테마 JSON 속성 참조

Content Composer 테마 JSON 파일의 모든 속성에 대한 설명 및 예제 값이 포함된 전체 참조입니다.

테마를 식별하고 설명하는 최상위 필드

## **메타데이터**

| **속성** | **유형** | **설명** | **슬레이트 값** |
|--------------|----------|----------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| ID | 문자열 | 고유 테마 식별자입니다. 소문자, 하이픈만 포함하거나 공백 또는 특수 문자는 사용하지 않습니다. 내부적으로 테마를 참조하는 데 사용됩니다. | 슬레이트 |
| name | 문자열 | 강의 테마 패널에 표시된 표시 이름. | 슬레이트 |
| 버전 | 문자열 | 의미 체계 버전 번호입니다. 새 테마에는 &quot;1.0.0&quot;을 사용하십시오. | &quot;1.0.0&quot; |
| 설명 | 문자열 | 테마의 시각적 특성에 대한 간단한 설명입니다. | &quot;크림색 배경, Adobe 빨간색 강조, Roboto Slab + Roboto 문자 시스템이 있는 따뜻하고 권위 있는 테마&quot; |
| 작성자 | 문자열 | 테마 작성자 또는 팀의 이름입니다. | &quot;Content Composer&quot; |
| 소스 | 문자열 | 테마 원점. 기본 제공 테마에 대해 &quot;제공&quot;되었습니다. 사용자가 만든 테마의 &quot;사용자 정의&quot; | &quot;custom&quot; |
| isDefault | 부울 | 이 테마가 새 강의에 자동으로 적용되는지 여부. 대부분의 경우 false로 설정합니다. | false |

## **foundation.palette**

테마의 색상 기초를 형성하는 7가지 핵심 색상 토큰입니다. 모든 요소 값은 하드 코딩된 16진수 값이 아닌 var(—tokenName)을 사용하여 이러한 토큰을 참조합니다.

| **속성** | **유형** | **설명** | **슬레이트 값** |
|------------------|------------|---------------------------------------------------------------------------------------------------------------------------|-----------------|
| 전경 | 16진수 색상 | 배경에 배치된 텍스트, 아이콘 및 UI 요소의 기본 전경색입니다. | #1A1A1A |
| 배경 | 16진수 색상 | 기본 코스 캔버스 및 슬라이드 배경색입니다. | #FAF7F2 |
| 악센트 | 16진수 색상 | 버튼, 선택한 상태, 진행률 표시기, 레슨 헤더 및 대화형 밝은 영역에 적용된 브랜드 강조 색상입니다. | #E8001C |
| backgroundSmooth | 16진수 색상 | 카드, 패널, 탐색 및 구성 요소 채우기의 보조 배경색입니다. | #F0EBE1 |
| 보조 | 16진수 색상 | 테두리, 구분선 및 비활성 UI 요소 색상입니다. | #D9D3C9 |
| textPrimary | 16진수 색상 | 모든 제목 및 본문 내용에 대한 기본 텍스트 색입니다. | #1A1A1A |
| textInverse | 16진수 색상 | 악센트 색상의 버튼 레이블과 같이 어둡거나 악센트 색상의 배경에 배치된 콘텐츠의 텍스트 색상입니다. | #FFFFFF |

## **foundation.fonts**

테마의 모든 텍스트 역할에 적용되는 두 개의 글꼴 스택입니다. var(—font-heading) 또는 var(—font-body)를 사용하여 요소 값을 참조합니다.

| **속성** | **유형** | **설명** | **슬레이트 값** |
|--------------|-------------------|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| 제목 | 글꼴 스택 문자열 | 레슨 제목, 주제 제목 및 표시 머리글에 대한 글꼴 모음입니다. 웹 적합 오류를 포함합니다. | &quot;Roboto Slab, Georgia, &#39;Times New Roman&#39;, serif&quot; |
| body | 글꼴 스택 문자열 | 단락 텍스트, 캡션, 퀴즈 질문 및 UI 레이블용 글꼴 모음입니다. 웹 적합 오류를 포함합니다. | &quot;Roboto, -apple-system, BlinkMacSystemFont, &#39;맑은 고딕&#39;, sans-serif&quot; |

## **foundation.spacing**

기준선으로 사용되는 가로 및 세로 간격 토큰입니다. 구성 요소는 horizontalSpacingScale 및 verticalSpacingScale 승수를 사용하여 크기를 조정합니다.

| **경로** | **유형** | **설명** | **슬레이트 값** |
|---------------|----------|-------------------------------------|-----------------|
| horizontal.xs | px 값 | 최소 수평 간격 단위 | 4px |
| horizontal.s | px 값 | 작은 가로 간격 단위 | 8px |
| horizontal.m | px 값 | 중간 수평 간격 단위 | 12px |
| horizontal.l | px 값 | 큰 가로 간격 단위 | 16px |
| horizontal.xl | px 값 | 매우 큰 수평 간격 단위 | 24px |
| vertical.xs | px 값 | 최소 수직 간격 단위 | 4px |
| 세로s | px 값 | 작은 수직 간격 단위 | 8px |
| vertical.m | px 값 | 중간 수직 간격 단위 | 16px |
| vertical.l | px 값 | 큰 수직 간격 단위 | 24px |
| vertical.xl | px 값 | 초대형 수직 간격 단위 | 32px |

## **foundation.radius**

구성 요소 및 카드의 모서리 라운딩을 제어하는 테두리 반경 토큰입니다.

| **속성** | **유형** | **설명** | **슬레이트 값** |
|--------------|----------|---------------------------------------------------------|-----------------|
| 없음 | px 값 | 라운딩 금지 - 날카로운 모퉁이. 항상 &quot;0px&quot;. | 0px |
| s | px 값 | 미세한 모퉁이 라운딩을 위한 작은 반경. | 4px |
| 분 | px 값 | 표준 카드 및 컴포넌트 라운딩을 위한 중간 반경 | 8px |
| l | px 값 | 눈에 띄는 라운딩을 위한 큰 반경. | 16px |
| 전체 | px 값 | 알약 또는 원 모양. 항상 &quot;9999px&quot; | 9999px |

## **foundation.logo**

| **속성** | **유형** | **설명** | **슬레이트 값** |
|--------------|----------------|----------------------------------------------------------------------------------------------|-----------------|
| 로고 | string 또는 null | 강의 헤더에 표시되는 로고 이미지의 URL 또는 파일 경로입니다. 로고가 없으면 null로 설정합니다. | null |

## **elements.text**

강의의 각 명명된 텍스트 역할에 대한 입력 체계 속성입니다. 모든 역할은 동일한 속성 집합을 공유합니다.

### **텍스트 역할**

| **역할** | **적용 대상** |
|--------------|------------------------------------------------------------------------------|
| lessonTitle | 레슨 시작 슬라이드의 기본 제목 |
| 주제 제목 | 각 항목 슬라이드의 맨 위에 있는 제목 |
| blockHeading | 아코디언 머리글 및 카드 제목과 같은 콘텐츠 구성 요소 내의 머리글 |
| 부제목 | 항목 슬라이드 내의 보조 제목 |
| 질문 | 퀴즈 및 지식 확인 질문 텍스트 |
| 캡션 | 이미지 및 미디어 블록 아래 캡션 |
| 단락 | 콘텐츠 슬라이드의 본문 텍스트 |
| buttonLabel | 버튼 및 CTA(Call-To-Action) 요소에 대한 텍스트 |

### **공유 텍스트 속성**

다음 속성은 위에 나열된 모든 텍스트 역할에 적용됩니다.

| **속성** | **유형** | **허용된 값** | **설명** |
|--------------------|-----------------------|--------------------------------------------------------------------|---------------------------------------------------------|
| fontFamily | CSS 변수 또는 글꼴 스택 | var(—font-heading), var(—font-body) 또는 전체 글꼴 스택 문자열 | 이 텍스트 역할에 대한 글꼴 모음입니다. |
| fontSize | px 값 | 모든 픽셀 값 | 글꼴 크기. |
| fontWeight | 문자열 | &quot;굵게&quot; 또는 &quot;보통&quot;만 - 숫자 값이 지원되지 않습니다. | 글꼴 두께. |
| fontStyle | 문자열 | &quot;normal&quot; 또는 &quot;italic&quot; | 글꼴 스타일입니다. |
| 색상 | CSS var 또는 hex | var(—tokenName) 또는 직접 16진수 값을 통한 모든 팔레트 토큰 | 텍스트 색상. |
| textAlign | 문자열 | &quot;left&quot;, &quot;center&quot; 또는 &quot;right&quot; | 가로 텍스트 정렬. |
| letterInterval | 문자열 | &quot;표준&quot;, px 값 또는 em 값 | 문자 사이의 간격입니다. |
| line높이 | 문자열 | 백분율 또는 단위 없는 값 | 선 Height. |
| textDecoration | 문자열 | &quot;none&quot;, &quot;underline&quot; 또는 &quot;line-through&quot; | 텍스트 장식. |
| text변형 | 문자열 | &quot;none&quot;, &quot;uppercase&quot;, &quot;lowercase&quot; 또는 &quot;capitalize&quot; | 텍스트 대소문자 변환. |
| paddingInlineStart | px 값 | 모든 픽셀 값 | 텍스트 블록에 적용된 왼쪽 패딩. |
| 단락 간격 | px 값 | 모든 픽셀 값 | 텍스트 블록 내의 각 단락 아래에 추가된 공백입니다. |

### **텍스트 역할 값 - 슬레이트 테마**

| **역할** | **fontFamily** | **fontSize** | **fontWeight** | **fontStyle** | **색상** | **textAlign** | **문자 간격** | **선 높이** | **textTransform** |
|--------------|---------------------|--------------|----------------|---------------|--------------------|---------------|-------------------|----------------|-------------------|
| lessonTitle | var(—font-heading) | 48px | 굵게 | 표준 | var(—textPrimary) | 가운데 | -0.01em | 130% | 없음 |
| 주제 제목 | var(—font-heading) | 40px | 표준 | 표준 | var(—textPrimary) | 왼쪽 | 0 | 135% | 없음 |
| blockHeading | var(—font-heading) | 24px | 굵게 | 표준 | var(—textPrimary) | 왼쪽 | 0 | 140% | 없음 |
| 부제목 | var(—font-body) | 20px | 굵게 | 표준 | var(—textPrimary) | 왼쪽 | 0.01em | 150% | 없음 |
| 질문 | var(—font-heading) | 24px | 표준 | 표준 | var(—textPrimary) | 왼쪽 | 0 | 150% | 없음 |
| 캡션 | var(—font-body) | 13px | 표준 | 표준 | var(—textPrimary) | 왼쪽 | 0.02em | 170% | 없음 |
| 단락 | var(—font-body) | 16px | 표준 | 표준 | var(—textPrimary) | 왼쪽 | 0.01em | 190% | 없음 |
| buttonLabel | var(—font-body) | 14px | 굵게 | 표준 | var(—textInverse) | 가운데 | 0.06em | 125% | 대문자 |

## **요소 - 구조적 표면**

강의의 고정 레이아웃 표면의 배경과 테두리를 제어하는 속성입니다.

| **요소** | **속성** | **유형** | **설명** | **슬레이트 값** |
|--------------|--------------|-------------------|---------------------------------------------------|----------------------------|
| 캔버스 | 배경 | CSS var | 기본 코스 캔버스 배경색 | var(—background) |
| 머리글 | 배경 | CSS var | 강의 헤더 바 배경색 | var(—background) |
| 머리글 | 테두리 | CSS 테두리 문자열 | 과정 헤더 바의 아래쪽 테두리 | 1px 단색 var(—secondary) |
| 바닥글 | 배경 | CSS var | 강의 바닥글 막대 배경색 | var(—background) |
| 바닥글 | 테두리 | CSS 테두리 문자열 | 강의 바닥글 막대의 위쪽 테두리 | 1px 단색 var(—secondary) |
| lessonHeader | 배경 | CSS var | 레슨 제목 헤더 영역의 배경색 | var(—accent) |
| 주제 | 배경 | CSS var | 각 항목 슬라이드의 배경색 | var(—background) |
| 주제 | 테두리 | CSS 테두리 문자열 | 항목 슬라이드 컨테이너 주위의 테두리 | 1px 단색 var(—secondary) |
| 내비게이션 | 배경 | CSS var | 레슨 탐색 패널의 배경색 | var(—backgroundSmooth) |
| 내비게이션 | 테두리 | CSS 테두리 문자열 | 레슨 탐색 패널의 테두리 | 1px 단색 var(—secondary) |
| 버튼 | 배경 | CSS var | 기본 작업 버튼의 배경색 | var(—accent) |
| 번호 매기기 | 배경 | CSS var | 페이지 매김 컨트롤의 배경색 | var(—backgroundSmooth) |

## **요소 - 공유 구성 요소 속성**

이러한 속성은 모든 콘텐츠 블록 구성 요소(paragraphBlock, videoBlock, imageGrid, 아코디언, 캐러셀, flipCard 및 타임라인)에 나타납니다.

| **속성** | **유형** | **설명** |
|------------------------|-------------------|---------------------------------------------------------------------------------------------------|
| 배경 | CSS 변수 또는 색상 | 구성 요소 블록의 외부 배경입니다. 일반적으로 &quot;투명&quot;입니다. |
| cardBackgroundColor | CSS 변수 또는 색상 | 구성 요소 내에서 개별 카드의 배경 채우기 |
| cardBorder | CSS 테두리 문자열 | 각 카드에 적용된 테두리. 전체 CSS 약식(예: &quot;1px solid var(—secondary)&quot;. |
| cardShadowOffset | 문자열 | 카드 그림자(예: &quot;0px 2px 6px&quot;)의 X 및 Y 오프셋 |
| cardShadowColor | CSS 변수 또는 색상 | 카드 그림자 색상입니다. |
| cardShadowOpacity | 백분율 문자열 | 카드 그림자 불투명도. 그림자를 제거하려면 &quot;0%&quot;로 설정합니다. |
| horizontalIntervalScale | 숫자 문자열 | 이 구성 요소의 가로 간격 토큰에 적용되는 승수입니다. &quot;1&quot;은 기본 간격을 사용합니다. |
| verticalIntervalScale | 숫자 문자열 | 이 구성 요소의 세로 간격 토큰에 적용되는 승수입니다. &quot;1&quot;은 기본 간격을 사용합니다. |
| radiusScale | 숫자 문자열 | 이 구성 요소의 반경 토큰에 적용된 승수입니다. &quot;1&quot;은 기본 반경을 사용합니다. |
| nestedAccentColor | CSS 변수 또는 색상 | 구성 요소 내에서 중첩된 요소의 강조 색상입니다. paragraphBlock에만 적용됩니다. |

### **공유 구성 요소 값 - 슬레이트 테마**

| **구성 요소** | **cardBackgroundColor** | **cardBorder** | **카드 그림자 불투명도** |
|----------------|-----------------------------|----------------------------|---------------------------|
| paragraphBlock | var(—backgroundSmooth) | 1px 단색 var(—secondary) | 8% |
| videoBlock | var(—backgroundSmooth) | 1px 단색 var(—secondary) | 8% |
| imageGrid | var(—backgroundSmooth) | 1px 단색 var(—accent) | 8% |
| 아코디언 | var(—backgroundSmooth) | 1px 단색 var(—secondary) | 8% |
| 회전목마 | var(—backgroundSmooth) | 1px 단색 var(—secondary) | 8% |
| flipCard | var(—backgroundSmooth) | 1px 단색 var(—secondary) | 8% |
| 타임라인 | var(—backgroundSmooth) | 1px 단색 var(—secondary) | 8% |

## **요소 - 구성 요소별 속성**

개별 구성 요소 유형에 고유한 등록 정보입니다.

| **구성 요소** | **속성** | **유형** | **설명** | **슬레이트 값** |
|----------------|--------------------------|----------|------------------------------------------------------------------|-------------------------|
| paragraphBlock | nestedAccentColor | CSS var | 단락 블록 안에 중첩된 요소의 강조 색상 | var(—accent) |
| flipCard | cardFrontBackgroundColor | CSS var | 뒤집기 카드 앞면의 배경색 | var(—backgroundSmooth) |
| flipCard | cardBackBackgroundColor | CSS var | 뒤집기 카드 뒷면의 배경색 - 나타내기 색상 | var(—accent) |
| flipCard | arrowColor | CSS var | 뒤집기 표시기 화살표 아이콘의 색상 | var(—textInverse) |
| 탭 | activeBg | CSS var | 현재 선택한 탭의 배경색 | var(—accent) |
| 탭 | inactiveBg | CSS var | 선택하지 않은 탭의 배경색 | var(—backgroundSmooth) |
| 탭 | 컨테이너Bg | CSS var | 탭 막대 컨테이너의 배경색 | var(—backgroundSmooth) |
| 타임라인 | trackColor | CSS var | 타임라인 노드 사이의 연결 선 색상 | var(—secondary) |
| 타임라인 | progressCompletedBg | CSS var | 완료된 타임라인 진행률 마커의 채우기 색상 | var(—accent) |
| 타임라인 | progressCurrentBorder | CSS var | 현재 타임라인 진행률 표시자의 테두리 색 | var(—accent) |
| 타임라인 | progressUnreachedBg | CSS var | 타임라인 마커의 채우기 색상에 아직 도달하지 않음 | var(—secondary) |
| 타임라인 | progressUnreachedBorder | CSS var | 타임라인 마커의 테두리 색상에 아직 도달하지 않음 | var(—backgroundSmooth) |

## **elements.assessment**

퀴즈 및 지식 검사 구성 요소에 대한 속성입니다.

| **속성** | **유형** | **설명** | **슬레이트 값** |
|----------------------------|----------------|------------------------------------------------------------------------------|-------------------------|
| 배경 | CSS var | 평가 블록의 외부 배경 | 투명도 |
| optionTextColor | CSS var | 대답 옵션 레이블의 텍스트 색상 | var(—textPrimary) |
| optionIndicatorColor | CSS var | 라디오 버튼 또는 확인란 표시기의 색상 | var(—accent) |
| optionSelectedColor | CSS var | 선택한 옵션 표시기에 적용된 색상 | var(—accent) |
| optionCheckmarkColor | CSS var | 선택한 옵션에 표시된 확인 표시 아이콘의 색상 | var(—textInverse) |
| optionBackgroundColor | CSS var | 각 답변 옵션의 배경색 | var(—background) |
| optionHoverBackgroundColor | CSS var | 마우스를 위로 가져가면 답변 옵션의 배경색입니다. | var(—backgroundSmooth) |
| buttonBackgroundColor | CSS var | [제출] 또는 [확인] 답변 버튼의 배경색 | var(—accent) |
| buttonTextColor | CSS var | [제출] 또는 [확인] 대답 단추 레이블의 텍스트 색상 | var(—textInverse) |
| buttonHoverBackgroundColor | CSS var | 마우스를 위로 가져가면 단추의 배경색입니다. | var(—accent) |
| feedbackCorrectColor | 16진수 색상 | 정답 피드백 패널의 배경색 | #D7F7E1 |
| feedbackIncorrectColor | 16진수 색상 | 오답 피드백 패널의 배경색 | #FFEBE8 |
| feedbackTextColor | 16진수 색상 | 피드백 패널 내 텍스트 색상 | #111111 |
| optionBorderCorrectColor | 16진수 색상 | 대답이 표시된 후 정답 옵션의 테두리 색 | #079355 |
| optionBorderIncorrectColor | 16진수 색상 | 답변이 표시된 후 잘못 선택한 옵션의 테두리 색입니다. | #D73220 |
| horizontalIntervalScale | 숫자 문자열 | 평가 구성 요소 내 수평 간격에 대한 승수 | &quot;1&quot; |
| verticalIntervalScale | 숫자 문자열 | 평가 구성 요소 내의 수직 간격에 대한 승수 | &quot;1&quot; |
| radiusScale | 숫자 문자열 | 평가 구성 요소 내 테두리 반경에 대한 승수 | &quot;1&quot; |

## **팔레트 토큰 var() 참조**

요소 값에 이러한 var() 표현식을 사용하여 팔레트 토큰을 참조합니다. 팔레트 토큰을 업데이트하면 해당 토큰을 사용하는 모든 요소가 자동으로 업데이트됩니다.

| **식** | **참조** |
|-------------------------|-------------------------------------|
| var(—foreground) | foundation.palette.foreground |
| var(—background) | foundation.palette.background |
| var(—accent) | foundation.palette.accent |
| var(—backgroundSmooth) | foundation.palette.backgroundSmooth |
| var(—secondary) | foundation.palette.secondary |
| var(—textPrimary) | foundation.palette.textPrimary |
| var(—textInverse) | foundation.palette.textInverse |
| var(—font-heading) | foundation.fonts.heading |
| var(—font-body) | foundation.fonts.body |

## 테마 json의 예

```
{
  "id": "slate",
  "name": "Slate",
  "version": "1.0.0",
  "description": "A warm, authoritative theme with cream background, Adobe red accents, and the Roboto Slab + Roboto type system",
  "author": "Content Composer",
  "source": "custom",
  "isDefault": false,
  "foundation": {
    "palette": {
      "foreground": "#1A1A1A",
      "background": "#FAF7F2",
      "accent": "#E8001C",
      "backgroundSubtle": "#F0EBE1",
      "secondary": "#D9D3C9",
      "textPrimary": "#1A1A1A",
      "textInverse": "#FFFFFF"
    },
    "fonts": {
      "heading": "Roboto Slab, Georgia, 'Times New Roman', serif",
      "body": "Roboto, -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif"
    },
    "spacing": {
      "horizontal": {
        "xs": "4px",
        "s": "8px",
        "m": "12px",
        "l": "16px",
        "xl": "24px"
      },
      "vertical": {
        "xs": "4px",
        "s": "8px",
        "m": "16px",
        "l": "24px",
        "xl": "32px"
      }
    },
    "radius": {
      "none": "0px",
      "s": "4px",
      "m": "8px",
      "l": "16px",
      "full": "9999px"
    },
    "logo": null
  },
  "elements": {
    "text": {
      "lessonTitle": {
        "fontFamily": "var(--font-heading)",
        "fontSize": "48px",
        "fontWeight": "bold",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "center",
        "letterSpacing": "-0.01em",
        "lineHeight": "130%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "topicTitle": {
        "fontFamily": "var(--font-heading)",
        "fontSize": "40px",
        "fontWeight": "normal",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "left",
        "letterSpacing": "0",
        "lineHeight": "135%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "blockHeading": {
        "fontFamily": "var(--font-heading)",
        "fontSize": "24px",
        "fontWeight": "bold",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "left",
        "letterSpacing": "0",
        "lineHeight": "140%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "subheading": {
        "fontFamily": "var(--font-body)",
        "fontSize": "20px",
        "fontWeight": "bold",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "left",
        "letterSpacing": "0.01em",
        "lineHeight": "150%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "question": {
        "fontFamily": "var(--font-heading)",
        "fontSize": "24px",
        "fontWeight": "normal",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "left",
        "letterSpacing": "0",
        "lineHeight": "150%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "caption": {
        "fontFamily": "var(--font-body)",
        "fontSize": "13px",
        "fontWeight": "normal",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "left",
        "letterSpacing": "0.02em",
        "lineHeight": "170%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "paragraph": {
        "fontFamily": "var(--font-body)",
        "fontSize": "16px",
        "fontWeight": "normal",
        "fontStyle": "normal",
        "color": "var(--textPrimary)",
        "textAlign": "left",
        "letterSpacing": "0.01em",
        "lineHeight": "190%",
        "textDecoration": "none",
        "textTransform": "none",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      },
      "buttonLabel": {
        "fontFamily": "var(--font-body)",
        "fontSize": "14px",
        "fontWeight": "bold",
        "fontStyle": "normal",
        "color": "var(--textInverse)",
        "textAlign": "center",
        "letterSpacing": "0.06em",
        "lineHeight": "125%",
        "textDecoration": "none",
        "textTransform": "uppercase",
        "paddingInlineStart": "0px",
        "paragraphSpacing": "0px"
      }
    },
    "canvas": {
      "background": "var(--background)"
    },
    "header": {
      "background": "var(--background)",
      "border": "1px solid var(--secondary)"
    },
    "footer": {
      "background": "var(--background)",
      "border": "1px solid var(--secondary)"
    },
    "lessonHeader": {
      "background": "var(--accent)"
    },
    "topic": {
      "background": "var(--background)",
      "border": "1px solid var(--secondary)"
    },
    "navigation": {
      "background": "var(--backgroundSubtle)",
      "border": "1px solid var(--secondary)"
    },
    "button": {
      "background": "var(--accent)"
    },
    "pagination": {
      "background": "var(--backgroundSubtle)",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "paragraphBlock": {
      "background": "transparent",
      "cardBackgroundColor": "var(--backgroundSubtle)",
      "cardBorder": "1px solid var(--secondary)",
      "cardShadowOffset": "0px 2px 6px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "nestedAccentColor": "var(--accent)",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "imageBlock": {
      "background": "transparent",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "videoBlock": {
      "background": "transparent",
      "cardBackgroundColor": "var(--backgroundSubtle)",
      "cardBorder": "1px solid var(--secondary)",
      "cardShadowOffset": "0px 2px 6px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "imageGrid": {
      "background": "transparent",
      "cardBackgroundColor": "var(--backgroundSubtle)",
      "cardBorder": "1px solid var(--accent)",
      "cardShadowOffset": "0px 2px 8px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "accordion": {
      "background": "transparent",
      "cardBackgroundColor": "var(--backgroundSubtle)",
      "cardBorder": "1px solid var(--secondary)",
      "cardShadowOffset": "0px 2px 6px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "carousel": {
      "background": "transparent",
      "cardBackgroundColor": "var(--backgroundSubtle)",
      "cardBorder": "1px solid var(--secondary)",
      "cardShadowOffset": "0px 2px 6px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "flipCard": {
      "background": "transparent",
      "cardFrontBackgroundColor": "var(--backgroundSubtle)",
      "cardBackBackgroundColor": "var(--accent)",
      "arrowColor": "var(--textInverse)",
      "cardBorder": "1px solid var(--secondary)",
      "cardShadowOffset": "0px 2px 6px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "tabs": {
      "background": "transparent",
      "activeBg": "var(--accent)",
      "inactiveBg": "var(--backgroundSubtle)",
      "containerBg": "var(--backgroundSubtle)",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "timeline": {
      "background": "transparent",
      "cardBackgroundColor": "var(--backgroundSubtle)",
      "cardBorder": "1px solid var(--secondary)",
      "cardShadowOffset": "0px 2px 6px",
      "cardShadowColor": "var(--foreground)",
      "cardShadowOpacity": "8%",
      "trackColor": "var(--secondary)",
      "progressCompletedBg": "var(--accent)",
      "progressCurrentBorder": "var(--accent)",
      "progressUnreachedBg": "var(--secondary)",
      "progressUnreachedBorder": "var(--backgroundSubtle)",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    },
    "assessment": {
      "background": "transparent",
      "optionTextColor": "var(--textPrimary)",
      "optionIndicatorColor": "var(--accent)",
      "optionSelectedColor": "var(--accent)",
      "optionCheckmarkColor": "var(--textInverse)",
      "optionBackgroundColor": "var(--background)",
      "optionHoverBackgroundColor": "var(--backgroundSubtle)",
      "buttonBackgroundColor": "var(--accent)",
      "buttonTextColor": "var(--textInverse)",
      "buttonHoverBackgroundColor": "var(--accent)",
      "feedbackCorrectColor": "#D7F7E1",
      "feedbackIncorrectColor": "#FFEBE8",
      "feedbackTextColor": "#111111",
      "optionBorderCorrectColor": "#079355",
      "optionBorderIncorrectColor": "#D73220",
      "horizontalSpacingScale": "1",
      "verticalSpacingScale": "1",
      "radiusScale": "1"
    }
  }
}
```
