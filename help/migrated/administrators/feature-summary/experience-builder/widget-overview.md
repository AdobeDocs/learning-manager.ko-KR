---
title: Experience Builder의 위젯
jcr-language: en_us
description: Adobe Learning Manager Experience Builder의 위젯이 모듈식 구성 가능한 블록으로 사용자 정의 학습 페이지를 구축하는 방법을 알아봅니다. 콘텐츠 상자, 카탈로그, 배너와 같은 위젯을 추가, 구성 및 정렬하여 코딩 없이 인터랙티브한 브랜드 경험을 제작할 수 있습니다.
source-git-commit: b3124c47d56a50437cb284fe809828bcd4c4008d
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---


# 개요

위젯은 Adobe Learning Manager의 Experience Builder에서 모듈식 구성 가능한 콘텐츠 블록 또는 기능 요소입니다.
사용자 정의 학습 페이지의 핵심 구성 요소를 제공하여 코드 없이 학습 콘텐츠, 대화형 기능, 브랜딩 요소, 통합을 간편하게 추가할 수 있습니다.

## 위젯의 사용 방법

**위젯 선택**

페이지의 레이아웃(예: 1열 또는 2열 레이아웃)을 선택하면 각 빈 열에 **[!UICONTROL 위젯 추가]** 단추가 표시됩니다. 이를 선택하면 선택할 수 있는 위젯의 목록이 표시됩니다.

**위젯 구성**

각 위젯에는 고유한 구성 옵션 세트가 있습니다. 일반적으로 필수 제목과 선택적 설명을 제공합니다. 그 외에도 범주 위젯의 카탈로그를 선택하거나 콘텐츠 상자 위젯의 이미지를 업로드하는 등의 위젯 특정 설정을 구성합니다.

**위젯 정렬**

위젯을 드래그하거나 놓아 다른 열이나 행 간에 이동함으로써 페이지에서 위젯의 위치를 쉽게 변경할 수 있습니다.

>[!NOTE]
>
>한 페이지에는 최대 25개의 위젯이 포함될 수 있습니다. 이 제한에 도달하면 경고 메시지가 나타나고 **[!UICONTROL 위젯 추가]** 단추가 비활성화됩니다.


## 위젯 유형

* 학습 기반 위젯은 동적 상태이며 Adobe Learning Manager에서 직접 데이터를 가져옵니다(예: 강의 및 경로, 준수 상태).
* 사용자 정의 브랜딩을 만들고 페이지에 유연한 콘텐츠를 추가하는 데 도움이 되는 정적 또는 콘텐츠 위젯(예: HTML, 콘텐츠 상자)

| 위젯 | 설명 | 사용 사례 |
|---|---|---|
| [일정](/help/migrated/administrators/feature-summary/experience-builder/add-a-widget.md#add-a-calendar-widget) | 예정된 이벤트, 교육 세션, 기한 또는 워크샵을 일정 형식으로 표시합니다. | 학습자에게 예정된 학습, 실시간 이벤트 또는 마감일에 대한 알림을 계속 보냅니다. |
| [범주](/help/migrated/administrators/feature-summary/experience-builder/add-a-widget.md#add-a-category-widget) | 카탈로그, 제품 또는 역할의 학습 콘텐츠를 범주로 표시합니다. | 사용자가 주제, 부서 또는 스킬 영역별로 교육을 탐색할 수 있도록 지원합니다. |
| [준수 상태](/help/migrated/administrators/feature-summary/experience-builder/add-a-widget.md#add-a-compliance-status-widget) | 할당된 강의에 대한 학습자의 준수 또는 인증 상태를 표시합니다. | 필수 학습 요구 사항 준수를 모니터링하고 전달합니다. |
| [과정 및 경로](/help/migrated/administrators/feature-summary/experience-builder/add-a-widget.md#add-a-courses-and-paths-widget) | 사용자에게 적합한 추천 강의 및 학습 경로를 표시합니다. | 학습자에게 관련 과정과 경력 개발 경로를 안내한다. |
| [콘텐츠 상자](/help/migrated/administrators/feature-summary/experience-builder/add-a-widget.md#add-a-content-box-widget) | 텍스트, 이미지 또는 공지 등의 사용자 정의 내용을 추가합니다. | 학습 페이지에서 중요한 뉴스, 팁 또는 홍보 메시지를 공유합니다. |
| [게임화](/help/migrated/administrators/feature-summary/experience-builder/add-a-widget.md#add-a-gamification-widget) | 배지, 점수, 순위표 또는 기타 게임화 요소를 표시합니다. | 성취도와 경쟁을 강조하여 학습자의 참여를 유도하십시오. |
| [HTML](/help/migrated/administrators/feature-summary/experience-builder/add-a-widget.md#add-a-html-widget) | 사용자 지정 HTML 코드를 포함하여 다양한 요소 또는 통합을 추가할 수 있습니다. | 위젯, 양식 또는 서드파티 도구와 같은 유연한 콘텐츠 통합을 제공합니다. |
| [Iframe](/help/migrated/administrators/feature-summary/experience-builder/add-a-widget.md#add-a-iframe-widget) | 인터페이스 내에 외부 웹 페이지나 응용 프로그램을 포함합니다. | 플랫폼을 종료하지 않고도 외부 콘텐츠 또는 도구를 표시할 수 있습니다. |
| [내 학습](/help/migrated/administrators/feature-summary/experience-builder/add-a-widget.md#add-a-my-learning-widget) | 학습자의 진행 중인 강의 및 진행 상황에 대한 개인화된 보기를 표시합니다. | 학습자가 강의 완료 및 학습 목표를 추적할 수 있도록 도와줍니다. |
| [소셜 학습](/help/migrated/administrators/feature-summary/experience-builder/add-a-widget.md#add-a-social-learning-widget) | 포럼, 토론, 그룹 또는 소셜 공동 작업 도구에 대한 액세스를 제공합니다. | 동료의 상호 작용, 공동 작업 및 지식 공유를 장려합니다. |

