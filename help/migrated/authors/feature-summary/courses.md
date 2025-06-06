---
description: Learning Manager 강의, 인증, 학습 프로그램을 생성하는 방법을 알아보려면 이 문서를 읽어 보십시오.
jcr-language: en_us
title: 강의 생성, 수정 및 게시
contentowner: manochan
exl-id: c5257796-0afa-4021-bd17-d3f1e9a86948
source-git-commit: f964dd3f1adeadb76f4843c9af229ce5f09afde1
workflow-type: tm+mt
source-wordcount: '7163'
ht-degree: 71%

---

# 강의 생성, 수정 및 게시

Learning Manager 강의, 인증, 학습 프로그램을 생성하는 방법을 알아보려면 이 문서를 읽어 보십시오.

작성자는 강의, 인증 및 학습 계획 등의 학습 객체를 생성할 수 있습니다. 학습자는 이러한 학습 객체를 수료할 수 있으며 책임자는 학습자의 진행 과정을 추적할 수 있습니다.

## Learning Manager의 강의 {#coursesincaptivateprime}

작성자는 가상 교육, 자가 진행식 교육, 강의실 교육 및 활동과 관련된 하나 이상의 모듈을 사용하여 Adobe Learning Manager에서 원하는 강의를 생성할 수 있습니다. 책임자는 이러한 강의를 활용하여 강의 인스턴스를 만들고 학습자를 등록하고 배지를 할당하고 해당 강의에 대한 피드백을 제공할 수 있습니다. 또한 이러한 강의를 사용하여 학습 프로그램, 학습 계획 및 인증을 생성할 수 있습니다.

작성자는 e러닝 도구를 사용하여 생성한 e러닝 콘텐츠를 가져올 수 있습니다. 비디오 파일을 포함하여 PDF, doc, docx, PPT 및 PPTX 강의 형식을 지원합니다.

## 강의 생성 - 기본 워크플로우 {#createacoursebasicworkflow}

강의를 생성하려면 아래 단계를 따르십시오.

1. 작성자로 Adobe Learning Manager에 로그인합니다. 작성자에게만 강의를 생성할 권한이 있습니다. 이제 시작 페이지에서 **[!UICONTROL 강의 생성]**&#x200B;을 클릭합니다.
1. **강의 개요** 페이지에서 강의 이름을 입력합니다. 이제 해당 강의에 대한 간단한 설명(강의 카드에 표시)을 입력합니다. 해당 설명은 140자를 넘지 않아야 합니다. 그런 다음 강의에 대한 자세한 개요(강의 세부 사항 페이지에 표시)를 입력합니다. 해당 설명은 1500자를 초과하지 않아야 합니다.

   작성자는 강의에 모듈을 추가하는 동안 모듈의 설명을 볼 수 있습니다.

1. 강의에 다른 언어를 제공하려면 창 왼쪽 상단 모서리의 &#39;새 언어 추가&#39;를 클릭합니다. 강의에 적용할 하나 이상의 언어를 선택합니다. **[!UICONTROL &#39;저장&#39;]**&#x200B;을 클릭합니다. 자세한 내용은 [다른 언어용 콘텐츠 추가](/help/migrated/authors/feature-summary/content-library.md)를 참조하십시오.
1. **강의 설정 수정**-

   1. 강의 설정 페이지에서 강의를 위한 스킬을 선택합니다. 스킬 드롭다운 목록에서 필요한 스킬을 선택합니다. 그런 다음 레벨 드롭다운 목록에서 필요한 레벨을 선택합니다.
   1. 강의 스킬, 레벨을 선택한 다음 스킬에 대한 점수를 설정합니다. 필요한 경우 스킬을 더 추가합니다.
   1. **등록 유형** 드롭다운 목록에서 등록 유형을 선택합니다.

   등록 유형은 다음과 같습니다.

   * **관리자 지정:** 관리자만 해당 강의를 지정할 수 있습니다. 학습자는 해당 유형의 강의에 등록할 수 없습니다.
   * **관리자 승인:** 관리자가 이 강의를 승인합니다. 학습자는 해당 강의에 등록할 수 있지만 관리자의 승인 없이는 해당 유형의 강의에 직접 등록할 수 없습니다. 학습자가 이 유형의 강의에 참여하면 관리자에게 알림 요청이 전송됩니다. 관리자가 승인하면 학습자에게 해당 강의가 등록됨으로 목록화됩니다.
   * **자가 등록:** 학습자는 해당 유형의 강의에 직접 등록할 수 있습니다.

1. 변경 사항을 저장하려면 **[!UICONTROL 저장]**&#x200B;을 클릭합니다. 강의를 게시하려면 **[!UICONTROL Publish]**&#x200B;를 클릭하세요.

## 강의 생성 - 고급 워크플로우 {#createacourseadvancedworkflow}

1. 작성자로 Adobe Learning Manager에 로그인합니다. 작성자에게만 강의를 생성할 권한이 있습니다. 이제 시작 페이지에서 **[!UICONTROL 강의 생성]**&#x200B;을 클릭합니다.
1. **강의 개요** 페이지에서 강의 이름을 입력합니다. 이제 해당 강의에 대한 간단한 설명(강의 카드에 표시)을 입력합니다. 해당 설명은 140자를 넘지 않아야 합니다. 그런 다음 강의에 대한 자세한 개요(강의 세부 사항 페이지에 표시)를 입력합니다. 해당 설명은 1500자를 초과하지 않아야 합니다.
1. 강의에 다른 언어를 제공하려면 창 왼쪽 상단 모서리의 &#39;새 언어 추가&#39;를 클릭합니다. 강의에 적용할 하나 이상의 언어를 선택합니다. **[!UICONTROL &#39;저장&#39;]**&#x200B;을 클릭합니다. 자세한 내용은 [다른 언어용 콘텐츠 추가](/help/migrated/authors/feature-summary/content-library.md)를 참조하십시오.
1. **강의 설정 수정**-

   1. 강의 설정 페이지에서 강의를 위한 스킬을 선택합니다. 스킬 드롭다운 목록에서 필요한 스킬을 선택합니다. 그런 다음 레벨 드롭다운 목록에서 필요한 레벨을 선택합니다.
   1. 강의 스킬, 레벨을 선택한 다음 스킬에 대한 점수를 설정합니다. 필요한 경우 스킬을 더 추가합니다.
   1. 필요한 경우, 사용자 정의 준수 레이블을 강의에 추가합니다. [강의/학습 경로/인증에 준수 레이블 추가](/help/migrated/authors/feature-summary/courses.md#add-compliance-labels-to-courselearning-pathcertification)를 참조하십시오.
   1. **등록 유형** 드롭다운 목록에서 등록 유형을 선택합니다.

   등록 유형은 다음과 같습니다.

   * **관리자 지정:** 관리자만 해당 강의를 지정할 수 있습니다. 학습자는 해당 유형의 강의에 등록할 수 없습니다.
   * **관리자 승인:** 관리자가 이 강의를 승인합니다. 학습자는 해당 강의에 등록할 수 있지만 관리자의 승인 없이는 해당 유형의 강의에 직접 등록할 수 없습니다. 학습자가 이 유형의 강의에 참여하면 관리자에게 알림 요청이 전송됩니다. 관리자가 승인하면 학습자에게 해당 강의가 등록됨으로 목록화됩니다.
   * **자가 등록:** 학습자는 해당 유형의 강의에 직접 등록할 수 있습니다.

1. 강의의 가격을 설정할 것인지 무료로 제공할 것인지 선택합니다. 강의를 유료로 제공하려면 **[!UICONTROL 유료]** 옵션을 선택하고 가격을 지정합니다. 그러면 강의 카드와 학습자용 강의 개요 페이지에 가격이 표시됩니다.

   참고: 이 옵션은 Adobe Commerce 커넥터가 구성된 경우에만 사용할 수 있습니다.

1. 학습자가 등록한 강의를 직접 취소할 수 있게 하려면 **학습자가 직접 등록을 취소할 수 있음** 확인란을 선택합니다.

1. **인스턴스 구성**

   이 옵션을 활성화하면 진행 중 상태의 학습자가 다른 인스턴스를 방문하여 등록할 수 있습니다. 학습자는 이전 인스턴스의 진행률을 유지할 수 있습니다.

   강의를 게시한 후 설정 페이지로 돌아오면 옵션을 더 이상 편집할 수 없습니다.

   다음 강의 유형에 대해 옵션을 활성화할 수 있습니다.

   * 자가 진행식
   * 강의실
   * 활동
   * 혼합

   참고: 강의를 복제하는 동안 소스 강의에서 인스턴스 구성 옵션을 활성화한 경우, 대상 강의에서 옵션은 비활성화된 상태로 유지됩니다.

   **인스턴스 전환이**&#x200B;에 대해 지원되지 않습니다.

   * 유료 과정
   * 관리자 지정 등록 유형 강의

   카탈로그를 통해 공유되는 경우 인스턴스 전환 구성은 피어 계정으로 전달되지 않고, 대상 강의에서 옵션은 비활성화된 상태로 유지됩니다.

1. **여러 등록**

   이를 통해 한 기간 또는 다른 기간에 둘 이상의 강의 인스턴스에 학습자를 등록할 수 있습니다.

   학습자의 다양한 강의 등록 간에 전환하려면 **다중 등록** 토글을 활성화합니다. 인스턴스 전환을 활성화한 경우 다중 등록을 사용할 수 없습니다.

1. 강의를 수강하기 전에 완료해야 하는 전제 조건 강의를 선택합니다. 강의 필드를 클릭한 다음 강의 목록에서 선택합니다.
1. 필수 전제 과정을 필수 항목으로 지정하려면 **사용** **필수 구성 요소** 확인란을 활성화합니다.
1. 강의와 관련된 키워드를 태그로 추가합니다. 학습자는 태그를 통해 검색 중 귀하의 강의를 쉽게 찾을 수 있습니다. 이 모든 태그는 추가한 모듈에 따라 자동으로 추가됩니다. 이 강의에 추가하려는 다른 태그가 있으면 계속 입력할 수 있습니다.
1. 강의와 관련된 키워드를 태그로 추가합니다. 학습자는 태그를 통해 검색 중 귀하의 강의를 쉽게 찾을 수 있습니다. 이 모든 태그는 추가한 모듈에 따라 자동으로 추가됩니다. 이 강의에 추가하려는 다른 태그가 있으면 계속 입력할 수 있습니다.
1. 자동 사용 중지 필드에서 강의를 중단할 날짜를 선택합니다. 책임자는 먼저 자동 중단 옵션을 활성화해야 합니다.
1. 변경 사항을 저장하려면 **[!UICONTROL 저장]**&#x200B;을 클릭합니다. 강의를 게시하려면 **[!UICONTROL Publish]**&#x200B;를 클릭하세요.

### 강의/학습 경로/인증에 준수 레이블 추가 {#add-custom-compliance-label}

강의에 준수 레이블을 추가하려면 다음 단계를 따르십시오.

1. 작성자 앱에서 **[!UICONTROL 과정]**/**[!UICONTROL 학습 경로]**/**[!UICONTROL 인증]**&#x200B;으로 이동하고 **[!UICONTROL 추가]**&#x200B;를 선택합니다.
1. 이름과 기타 세부 정보(예: 설명, 스킬)를 입력합니다.
1. **[!UICONTROL 사용자 지정 준수]** 텍스트 상자에 준수 레이블을 입력하고 선택합니다.

   ![](assets/add-compliance-label.png)
   _사용자 지정 준수 추가_

   >[!IMPORTANT]
   >
   >사용자 정의 준수를 추가할 때 강의 기한을 설정해야 합니다.

   >[!NOTE]
   >
   >최대 50개의 강의, 학습 경로 또는 인증에서 사용자 정의 준수 유형 레이블에 대해 동일한 값을 가질 수 있습니다.

1. 강의/학습 경로/인증을 저장하고 게시합니다.
이제 강의/학습 경로/인증이 준수 유형으로 간주됩니다. 책임자는 준수 대시보드에 이 강의를 추가하고 관리자와 공유하여 진행 상황을 추적할 수 있습니다

>[!NOTE]
>
>작성자는 기존의 강의/학습 경로/인증을 편집하여 준수 레이블을 추가할 수도 있습니다.

## 게임화 점수

강의 및 강의 인스턴스 레벨에서 게임화 점수를 할당할 수 있습니다. 이를 통해 다양한 강의 또는 인스턴스에 점수를 부여할 수 있습니다. 학습자는 특정 강의를 수강하거나 다른 강의보다 특정 강의 인스턴스를 선호할 수 있습니다.

1. 강의 인스턴스 레벨에서 **[!UICONTROL 게임화 점수]**&#x200B;를 선택합니다.

![게임화 점수](assets/select-gamification-points-new.png)

*게임화 점수 설정*

1. **[!UICONTROL 편집]**&#x200B;을 선택합니다.
1. 강의 레벨 설정 사용 을 선택하면 다음 옵션이 표시됩니다.

   * **[!UICONTROL 완료 시]**: 강의를 완료할 때 학습자가 100점을 획득하도록 하려면 이 토글을 선택합니다.
   * **추가 규칙**

      * **[!UICONTROL 조기 완료]**: 이 옵션을 선택하면 강의를 완료하는 처음 30명의 학습자에게 100점이 부여됩니다.
      * **[!UICONTROL 적시 완료]**: 이 옵션을 선택하면 학습자가 999일 이내에 강의를 완료할 경우 100점이 부여됩니다.

1. **[!UICONTROL 사용자 정의 설정 사용]**&#x200B;을 선택하는 경우 다음 옵션이 표시됩니다.

   * **[!UICONTROL 완료 시]**: 학습자가 강의를 완료할 때 100점을 획득하도록 하려면 이 토글을 선택합니다.
   * **추가 규칙**

      * **[!UICONTROL 조기 완료]**: 이 옵션을 선택하면 특정 점수를 부여할 학습자 수를 결정할 수 있습니다.
      * **[!UICONTROL 적시 완료]**: 이 옵션을 선택하면 학습자가 지정된 시간 내에 강의를 완료했을 때 부여될 점수를 결정할 수 있습니다.

   ![게임화 점수](assets/gamification-custom-settings.png)

   *조기 및 적시 완료 설정*

1. **[!UICONTROL 저장]**&#x200B;을 선택합니다.

## 종합 학습 리소스

작성자는 학습 계획 레벨에서 학습 리소스를 집계할지 아니면 개별 강의 레벨에 그대로 둘지 여부를 결정할 수 있습니다.

작성자는 **[!UICONTROL 학습 경로]** > **[!UICONTROL 설정]**&#x200B;을 선택합니다. **[!UICONTROL 편집]**&#x200B;을 클릭합니다.

**[!UICONTROL 리소스]** 섹션에서 &#39;학습 경로 레벨에서 집계된 구성 강의 리소스 표시&#39; 확인란이 활성화된 경우 강의 레벨에 있는 리소스가 학습 경로 레벨에 표시되는지 표시됩니다.

>[!NOTE]
>
>책임자는 학습 경로의 설정 페이지에서 이 옵션을 활성화할 수도 있습니다. 이 옵션은 학습 경로 레벨에 표시되는 강의 레벨에 있는 리소스를 표시합니다.

## 스케줄링 도우미

강사 및 강의실 예약의 충돌을 관리합니다. 강사를 강의에 할당하기 전에 강사가 이용할 수 있는 시간과 날짜를 알고 싶다면 일정 관리 도우미 를 사용합니다.

강의를 생성할 때 VC 또는 CR 강의의 경우 스케줄링 지원을 누릅니다.

![일정 도우미 선택](assets/scheduling-assistant.png)

*일정 도우미 시작*

스케줄링 도우미 창이 실행됩니다.

![일정 도우미 화면](assets/scheduling-assistant-window.png)

*일정 도우미 대화 상자*

스케줄링 도우미에서 다음을 수행할 수 있습니다.

* 강사의 이름으로 강사를 검색합니다.
* 강사의 스킬로 강사를 검색합니다.

### 이름으로 강사 검색

강사 필드에 강사의 이름을 입력하거나 부분 강사 이름을 검색합니다. 강사를 선택할 수 있는 강사 목록이 나타납니다.

![이름으로 강사 검색](assets/search-instructor.png)

*강사 검색*

여러 명의 강사를 선택할 수 있지만, 한 번에 한 명의 강사만 할당할 수 있습니다. 선택한 시간이 시간 충돌 창에서 강조 표시됩니다. 강사 옆에 십자 아이콘이 나타나고 이를 클릭하여 강사를 제거합니다.

![여러 강사 선택](assets/busy-times.png)

*여러 강사 검색*

### 스킬로 강사 검색

단일 또는 다중 스킬로 강사를 검색합니다. 검색에 AND 연산자를 사용합니다.

스킬은 스킬 레벨이 아닌 부분 또는 전체 스킬 이름으로만 검색할 수 있습니다.

도우미에서 강사 이름과 위치 및 인원 제한을 입력합니다.

강사 검색 상자 오른쪽에 있는 필터 아이콘을 클릭하면 표시되는 스킬도 검색할 수 있습니다. 아래 스크린샷에 버튼이 표시됩니다.

![강사를 위한 스킬 입력](assets/scheduling-assistant-instructor-skill.png)

*스킬별로 강사 검색*

### 사용자 그룹 필터

강사 필드에서 필터를 선택합니다. **[!UICONTROL 사용자 그룹]** 필터가 있으며, 작성자 또는 사용자 정의 작성자는 사용자 그룹 값을 사용하여 올바른 강사를 찾을 수 있습니다.

두 필터를 모두 적용하면 사용자 그룹에 속하고 선택한 스킬을 보유한 강사 목록이 표시됩니다.

이는 강의 또는 인스턴스 페이지의 일정 도우미Scheduling Assistant에 적용됩니다.

![일정 도우미](assets/scheduling-assistant-2.png)

*사용자 그룹별 필터링*

### 인스턴스 페이지

또한 아래에 표시된 대로 인스턴스 페이지에서 스케줄링 도우미에 액세스할 수도 있습니다.

스케줄링 도우미는 인스턴스 페이지에서도 관리자와 사용자 정의 책임자/작성자도 사용할 수 있습니다.

![인스턴스 페이지에서 일정 도우미](assets/instances-scheduling.png)

*인스턴스 페이지에서 강사 예약*

### 위치 검색

강의실 이름과 위치 영역 이름을 모듈 및 일정 관리 페이지에서 모두 지정하여 위치를 검색할 수 있습니다.

## 서식 있는 텍스트 서식

강의, 학습 프로그램, 인증 또는 작업 지원을 만드는 동안 작성자는 텍스트, 이미지와 같은 다양한 유형의 콘텐츠를 입력하거나 다양한 텍스트 서식 옵션을 적용할 수 있습니다.

강의를 만들 때 강의 개요 필드에서 서식 있는 텍스트 편집기를 볼 수 있습니다. 콘텐츠 형식 지정, 이미지 추가, 하이퍼링크 추가 등을 할 수 있습니다.

![](assets/rich-text-editor-author.png)

*서식 있는 텍스트 편집기 시작*

마찬가지로 다음 내용을 작성할 때 서식 있는 텍스트 편집기를 사용해서 설명을 수정할 수 있습니다.

**학습 프로그램**

![](assets/lp-rte-new.png)

*학습 프로그램에 서식 있는 텍스트 편집기 사용*

**인증**

![](assets/cert-rte-new.png)

*인증에 서식 있는 텍스트 편집기 사용*

**작업 지원**

![](assets/job-aid-rte-new.png)

*작업 지원에 서식 있는 텍스트 편집기 사용*

또한 다른 언어에 대해 서식 있는 텍스트 편집기를 사용할 수 있습니다.

## 헤드리스 사용자 인터페이스용 서식 있는 텍스트 설명 지원

### CSS가 필요한 이유는 무엇입니까?

서식 있는 텍스트는 HTML 태그로 구성됩니다. 태그를 그대로 렌더링하면 브라우저에서 기본 스타일을 적용합니다. 이것은 종종 회사의 스타일 지침과 맞지 않습니다. 지침을 충족하려면 CSS가 필요합니다.

### 기본 스타일

첨부된 CSS 스타일시트에는 Learning Manager에서 적용한 스타일이 포함되어 있습니다. 스타일은 대부분의 사용 사례를 고려하여 조정됩니다. 첨부된 CSS 파일을 다운로드하고 규칙 및 빌드 시스템에 따라 웹 앱으로 가져옵니다. 정의된 CSS 클래스는 ql-editor 클래스에서 네임스페이스 지정되어 있으며 기존 스타일을 방해하지 않습니다.

### 스타일 사용자 정의

기본 스타일은 모든 사용자의 요구를 충족시키지 못할 수도 있습니다. 사용자 정의는 제공된 CSS를 재정의하여 수행할 수 있습니다. 모든 스타일은 ql-editor에서 하위 항목 선택기로 래핑됩니다. 다음 클래스가 사용됩니다.

* 들여쓰기: **li.ql-indent-$number**. $number는 1~9 사이의 숫자입니다.
* 크기: **ql-size-small**, **ql-size-large**, **ql-size-huge**

* 맞춤: **ql-align-center**, **ql-align-justify**, **ql-align-right**

* 색상: **ql-color-$color**. $color는 흰색, 빨간색, 주황색, 노란색, 녹색, 파란색, 자주색입니다.
* 배경색: **ql-bg-$color**. $color는 검은색, 빨간색, 주황색, 노란색, 녹색, 파란색, 자주색입니다
* html 태그: p, ol, ul, pre, blockquote, h1, h2, h3, h4, h5, h6

[사용자 정의에 사용할 CSS 파일입니다.](assets/ql-headless.css)

### 서식 있는 텍스트 개요 렌더링을 지원하도록 API 수정

고객은 헤드리스 인터페이스를 개발할 때 현재 개발 중인 사용자 인터페이스에 학습 객체를 표시해야 합니다. 이를 위해 [GET /learningObjects](https://learningmanagereu.adobe.com/docs/primeapi/v2/#!/learning_object/get_learningObjects) API로 표시하는 방법이 주로 사용됩니다. 이제 Learning Manager가 개요 필드에 &#39;서식 있는 텍스트&#39;가 표시되도록 지원하므로 API 응답 의 학습 객체 데이터 모델 역시 동일한 내용을 표시합니다. 아래 API 응답 모델 섹션의 &#39;richTextOverview&#39; 필드를 참조하십시오. 또한 이전에 표시된 필드(&quot;개요&quot;)는 이전 버전과의 호환성을 위해 변경되지 않습니다.

```
{ 
 "data": [ 
 { 
 "id": "string", 
 "type": "string", 
 "attributes": { 
 … 
 "localizedMetadata": [ 
 { 
 "description": "string", 
 "locale": "string", 
 "name": "string", 
 "overview": "string", 
 "richTextOverview": "string" 
 } 
 ], 
 … 
 }, 
 "relationships": { 
 … 
 } 
 } 
 } 
 ] 
} 
```

이미 개요 필드를 사용하고 있는 고객의 헤드리스 인터페이스는 영향을 받지 않으므로 이전과 마찬가지로 일반 텍스트가 표시됩니다. 서식 있는 텍스트의 개요를 활용하려면 Author UI에 서식 있는 형식의 학습 객체 개요를 만들어야 합니다. 그러면 Learning Manager가 API 응답 모델에 계속 표시되어 온 일반 텍스트와 별개로 서식 있는 텍스트 개요를 반환하기 시작합니다.

단, UI에서 서식 있는 텍스트를 렌더링하려면 CSS를 추가해야 합니다. 이 부분은 다음 섹션에서 자세히 설명합니다.

## 여러 번 시도 허용 {#allowmultipleattempts}

책임자가 다중 시도를 활성화한 경우 작성자는 강의 또는 모듈 레벨에 대화형 e러닝 모듈에 대한 다중 시도를 구성할 수 있습니다.

![](assets/allow-multipe-attempts.png)

*대화형 e-러닝 모듈에 대한 다중 시도 구성*

<table>
 <tbody>
  <tr>
   <td>
    <p><b>옵션</b></p></td>
   <td>
    <p><b>설명</b></p></td>
  </tr>
  <tr>
   <td>
    <p>다음에 대한 시도 횟수 설정</p></td>
   <td>
    <p>모듈에 대한 시도 횟수를 무한으로 또는 지정된 횟수만큼 설정할 수 있습니다.<span style="font-size: 0.8125rem;">활성화되면 시도 정보가 학습자에게 표시됩니다. 학습자는 '다시 시도' 단추를 클릭하여 모듈을 다시 시도할 수 있습니다.</span></p></td>
  </tr>
  <tr>
   <td>
    <p>모듈을 완료 또는 통과하면 새로운 시도 중지</p></td>
   <td>
    <p>학습자가 새 시도 옵션을 선택하지 못하도록 중지 시점을 구성하려면 "모듈이 완료되거나 전달되면 새 시도 중지" 확인란을 활성화합니다. '재시도' 옵션은 모듈을 성공적으로 완료하면 학습자 보기에서 제거됩니다.</p></td>
  </tr>
  <tr>
   <td>
    <p>시도 간 모듈 잠금 0:0:1 형식: 일/시간/분</p></td>
   <td>
    <p>"<b>시도 간 모듈 잠금 0:0:1 형식: 일/시간/분</b>" 확인란을 활성화하여 시도 간 특정 시간 동안 모듈을 잠글 수 있습니다. 모듈이 잠겨 있으면 학습자는 제공된 잠금 시간이 경과할 때까지 모듈을 방문할 수 없습니다. </p>
    <p>'<b>플레이어 닫기</b>' 또는 '<b>완료</b>' 확인란을 선택하여 시도 종료 조건을 정의할 수 있습니다.</p></td>
  </tr>
  <tr>
   <td>
    <p>플레이어 닫기</p></td>
   <td>
    <p>조건을 '<b>플레이어 닫기</b>'로 선택하면 모든 모듈 시작이 새로운 시도로 간주됩니다. 학습자가 플레이어를 닫을 때 모듈 잠금 세부 정보 및 시도 세부 정보가 표시됩니다.</p></td>
  </tr>
  <tr>
   <td>
    <p>완료</p></td>
   <td>
    <p>시도 종료가 <b>완료</b>를 기반으로 하면 콘텐츠 성공 조건을 기준으로 산출됩니다. 학습자는 콘텐츠에서 완료 정보가 전송될 때까지 모듈을 다시 시도할 수 없게 됩니다. 시도가 종료되면 학습자는 모듈 잠금 및 시도 세부 정보를 확인할 수 있습니다.</p></td>
  </tr>
  <tr>
   <td>
    <p>모듈 완료 시간 제한 설정</p></td>
   <td>
    <p>작성자는 "<b>모듈을 완료하도록 시간 제한 설정</b>" 확인란을 선택하여 모듈을 완료하는 시간 제한을 설정할 수 있습니다.</p>
    <p>플레이어를 실행할 때마다 매번 새로운 시도로 간주되며 실행하는 동안 학습자에게 시간 세부 정보가 표시됩니다.</p>
    <p><b>참고:</b><span style="font-size: 0.8125rem;">지정된 시간이 경과하면 시도가 자동으로 종료됩니다. 플레이어를 닫을 경우에도 현재 시도가 종료됩니다.</span></p></td>
  </tr>
  <tr>
   <td>
    <p>모듈 레벨에서의 다중 시도</p></td>
   <td>
    <p>'다음에 대해 시도 설정' 드롭다운 목록에서 시도를 '모듈 레벨'로 선택하면 개별 모듈 레벨에서 옵션을 구성할 수 있습니다.</p></td>
  </tr>
 </tbody>
</table>

## 강의 모듈 {#coursemodules}

### 모듈 추가 {#addmodules}

이제 콘텐츠, 사전 학습 및 시험 모듈을 추가할 수 있습니다. **콘텐츠** 모듈은 강의를 구성하는 주요 모듈입니다. **사전 학습** 모듈에는 학습자가 강의를 준비하는 데 도움을 주는 몇 가지 기본 정보가 포함되어 있습니다. 이러한 모듈은 학습자가 강의를 완료하는 필수 요소는 아닙니다. **시험** 모듈은 학습자가 이미 콘텐츠를 알고 있고 준수 요구 사항을 충족하기 위해 테스트해 보려는 경우 콘텐츠를 건너뛰고 테스트를 수행하는 데 도움이 됩니다.

콘텐츠 모듈을 추가하려면 아래 단계를 따르십시오.

1. **[!UICONTROL 모듈 추가]**&#x200B;를 클릭합니다. 모듈을 추가하는 네 가지 옵션이 표시됩니다. 첫 번째 옵션은 자가 진행식 모듈을 추가하는 것입니다. 이 모듈을 통해 Adobe Learning Manager에서 모듈 라이브러리를 만들고 추가할 수 있습니다. 두 번째 옵션은 가상 강의실을 설정하는 것입니다. 세 번째 옵션은 강의실 모듈을 설정하는 것이며 네 번째는 활동 모듈입니다.

   ![](assets/select-module-type.png)

   *강의에 대한 모듈 추가*

   **자가 진행식 모듈:** 이 모드에서는 자신의 속도에 맞게 강의 모듈을 시작하고 완료할 수 있습니다. 자신의 일정을 설정할 수 있습니다.

   옵션을 클릭하면 이미 모듈 라이브러리에 추가된 자가 진행식 모듈 목록을 볼 수 있습니다. 여기서 목록을 스크롤하여 추가할 항목을 선택하거나 검색 필드 또는 모듈 태그에 모듈의 이름을 입력하여 모듈을 검색할 수 있습니다.

   모듈을 선택했으면 **[!UICONTROL 추가]**&#x200B;를 클릭합니다. 이러한 모듈은 이제 콘텐츠 섹션 아래 표시됩니다.

   모듈의 순서 또한 조정할 수 있습니다. 모든 모듈을 끌어서 위 또는 아래로 이동하고 모듈을 올바른 순서로 배열하십시오.

   **가상 강의실 모듈:** 이 모드에서는 학습자가 실시간 온라인 수업에 출석하며 훈련된 강사의 지원을 받습니다. 제목, 설명을 입력하고 세션 기간을 설정하십시오. 회의 URL과 강사를 지정하여 세션을 진행할 수도 있습니다. 변경 사항을 저장하려면 **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

   ![](assets/1st-image.png)

   *VC 모듈 추가*

   가상 교실 구성 대화 상자를 사용하여 강의를 생성할 때 **컨퍼런스 시스템**&#x200B;을 생성한 Teams 연결에 설정합니다. 이벤트에 대한 회의 주최자를 원하는지 여부를 선택합니다.

   회의 주최자에 대해 **예**&#x200B;를 선택한 경우 주최자 이름을 입력해야 합니다. 이름을 입력하고 주최자를 선택합니다.

   **로비 우회**

   * **예**&#x200B;를 선택하면 모든 학습자가 회의에 참여할 수 있습니다.
   * **아니요**&#x200B;를 선택하면 주최자에게 학습자의 회의 참여를 허용하거나 차단하는 요청이 전송됩니다.

   **참고:** 학습자는 Microsoft Teams를 사용할 수 있어야 합니다. 그러나 학습자는 Learning Manager에 게스트로 참여할 수 있습니다.

   **강의실 모듈:** 이 모드에서는 학습자가 직접 수업에 출석하며 훈련된 강사의 지원을 받습니다. 제목, 설명을 입력하고 세션 기간을 설정하십시오. 강의실 위치와 강사를 지정하여 세션을 진행할 수도 있습니다. 변경 사항을 저장하려면 **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

   ![](assets/classroom-module.png)

   *강의실 모듈 추가*

   가상 교실 구성 대화 상자에서 강의를 생성할 때 컨퍼런스 시스템을 생성한 Microsoft Teams 연결에 설정합니다. 이벤트에 대한 회의 주최자를 원하는지 여부를 선택합니다.

   회의 주최자에 대해 [예]를 선택한 경우 주최자 이름을 입력해야 합니다. 주최자의 이름을 입력하고 주최자를 선택하십시오.

   **로비 우회**

   * [예]를 선택하면 모든 학습자가 회의에 참여할 수 있습니다.
   * [아니요]를 선택하면 주최자에게 학습자의 회의 참여를 허용하거나 차단하는 요청이 전송됩니다.

   **참고:** 학습자가 게스트로 Microsoft Teams에 가입하려면 전자 메일을 입력해야 합니다. 전자 메일이 Learning Manager에 있어야 합니다.

   **활동 모듈:** 이 모드에서 학습자는 Workshop, Exercise, Questionnaire 및 기타 학습 활동 등의 활동 세트를 완료해야 합니다. 참고로 제목, 설명 및 외부 URL을 입력합니다. 변경 사항을 저장하려면 **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

   ![](assets/activity-module.png)

   *활동 모듈 추가*

   활동 유형 파일 제출 및 xAPI 기반 모듈에 대한 강의에서 활동 모듈을 추가하는 동안 지속 기간을 지정할 수 있습니다.

1. 마찬가지로 사전 학습 및 시험 모드에 모듈을 추가합니다.
1. 정렬되지 않음 또는 정렬됨 중 원하는 모듈의 나열 순서를 선택합니다.

   **정렬됨**&#x200B;을 선택하는 경우 모듈은 생성 순서대로 나타납니다. **정렬되지 않음**&#x200B;을 선택하는 경우 모듈은 순서대로 나열되지 않습니다. 학습자는 원하는 순서로 모듈을 완료할 수 있습니다.

1. 필수 모듈 드롭다운 목록에서 학습자가 강의를 수료하기 위해 수강해야 하는 모듈 수를 선택합니다.
1. 강의의 표지 이미지와 배너 이미지를 추가합니다. 카탈로그는 책임자가 작성합니다. 자세한 내용은 [카탈로그](/help/migrated/administrators/feature-summary/catalogs.md)를 참조하십시오.

   **참고:** 권장 치수는 다음과 같습니다.

   * **표지 이미지:** 300px x 300px
   * **배너 이미지:** 1600px x 140px

1. 페이지의 오른쪽 상단 모서리에서 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

#### 활동 모듈에 HTML 링크 추가

작성자는 활동 모듈에 HTML 링크를 추가하고 완료 기준을 설정할 수 있습니다. HTML 링크를 추가하고 완료 기준을 설정하려면 다음 단계를 따르십시오.

1. 작성자 앱에서 홈 페이지에서 **[!UICONTROL 강의 만들기]**&#x200B;를 선택합니다.
1. **[!UICONTROL 과정 카탈로그]** 화면에서 **[!UICONTROL 추가]** 선택
1. 강의의 이름과 설명을 입력합니다.
1. **[!UICONTROL 모듈]** 옵션에서 **[!UICONTROL 모듈 추가]** > **[!UICONTROL 활동 모듈]**&#x200B;을 선택합니다.
1. **[!UICONTROL 활동 모듈]** 프롬프트에서 이름과 설명을 입력합니다.
1. **[!UICONTROL 유형]**&#x200B;을 **[!UICONTROL 외부 URL]**(으)로 선택합니다.
1. **[!UICONTROL 완료 조건]** 옵션에서 다음 옵션 중 하나를 선택합니다.
   * **[!UICONTROL 학습자 완료 표시]**: Fluidic Player에서 학습자는 강의를 완료로 표시할 수 있습니다.
   * **[!UICONTROL 콘텐츠 시작 시]**: 학습자가 강의를 시작하면 자동으로 완료로 표시됩니다.

   ![](assets/completion-criteria-activity-module.png)
   _완료 조건_

1. **[!UICONTROL 추가]**&#x200B;를 선택하고 과정을 게시합니다.

## 체크리스트 {#create-checklist}

평가는 LMS의 중요한 측면입니다. 온라인 평가는 주제에 대한 학습자의 이해를 평가하는 가장 좋은 방법 중 하나입니다. 그러나 종종, 그 사람이 그 일을 하는 동안, 그가 필요한 일을 수행하는 것을 관찰함으로써 그 사람의 이해력을 평가하는 것이 필요합니다.

일별 기준으로 수행해야 하는 작업에 대한 평가를 받는 상점 직원 또는 창고 근무자를 고려하십시오. 커피 머신을 수리하기 위해 수행된 단계 또는 재료 포장에 포함된 단계가 될 수 있습니다. 강사는 체크리스트를 기반으로 이러한 작업에 대한 직원을 평가하고 평가 활동에서 합격 또는 불합격으로 평가할 수 있습니다.

### 체크리스트 만들기 {#createachecklist}

작성자만 체크리스트를 만들 수 있습니다. 체크리스트는 활동 모듈의 유형입니다. 활동 모듈을 설정하는 동안 작성자는 아래와 같이 활동을 **체크리스트**(으)로 선택할 수 있습니다.

![](assets/checklist-option.png)

*검사 목록 만들기*

**체크리스트** 옵션을 선택하면 몇 가지 추가 옵션이 표시됩니다.

**체크리스트 유형:** **예/아니요** 또는 **1-5** 옵션을 선택합니다. 예/아니요를 선택하는 경우 체크리스트에는 예 또는 아니요로만 대답할 수 있는 질문이 포함됩니다. 1-5에서 선택한 경우 Likert 체크리스트를 볼 수 있고 여기에서 5점 범위의 질문을 평가할 수 있습니다.

**합격 기준:**

<table>
 <tbody>
  <tr>
   <td>
    <p><b>예/아니요</b>를 선택한 경우...</p></td>
   <td>
    <p><b>1-5</b>를 선택한 경우...</p></td>
  </tr>
  <tr>
   <td>
    <p>'예' 응답의 수만큼 합격 기준을 설정합니다. 예를 들면 3을 입력하고 학습자가 강의를 합격하는 경우, 강사가 평가할 때 3개 이상의 <b>예 </b>응답을 받은 경우가 있습니다.</p></td>
   <td>
    <p>1-5 사이 번호의 임계값으로 합격 기준을 설정합니다. 예를 들면 2와 4를 입력하고 학습자가 강의를 합격하는 경우, <b>4</b> 이상의 점수가 있는 <b>2</b>개 이상의 평가를 받은 경우가 있습니다.</p></td>
  </tr>
 </tbody>
</table>

학습자를 평가할 강사를 선택합니다.

또한 주석 또는 메모가 있는 경우 **강사에게 메모** 텍스트 필드에 추가할 수 있습니다.

이제 체크리스트 질문을 추가합니다. **[!UICONTROL 추가]**&#x200B;를 클릭합니다. 최대 150개의 질문만 추가할 수 있습니다.

![](assets/add-checklist-questions.png)

*체크리스트 질문 추가*

더 많은 질문을 추가하려면 **[!UICONTROL 더 추가]**&#x200B;를 클릭합니다.

변경 사항을 저장하고, 모듈을 추가하고, 강의를 게시합니다.

### 스킬 추가 {#addskills}

이 페이지에서 다음 세부 정보를 입력합니다.

1. 강의 스킬, 레벨을 선택한 다음 스킬에 대한 점수를 설정합니다. 필요한 경우 스킬을 더 추가합니다.

   ![](assets/course-skills.png)

   *강의에 스킬 추가*

1. 등록 유형을 선택합니다. 옵션은 다음과 같습니다.

   * **관리자 지정:** 관리자만 해당 강의를 지정할 수 있습니다. 학습자는 해당 유형의 강의에 등록할 수 없습니다.
   * **관리자 승인:** 관리자가 이 강의를 승인합니다. 학습자는 해당 강의에 등록할 수 있지만 관리자의 승인 없이는 해당 유형의 강의에 직접 등록할 수 없습니다. 학습자가 이 유형의 강의에 참여하면 관리자에게 알림 요청이 전송됩니다. 관리자가 승인하면 학습자에게 해당 강의가 등록됨으로 목록화됩니다.
   * **자가 등록:** 학습자는 해당 유형의 강의에 직접 등록할 수 있습니다.

1. 학습자가 등록한 강의를 직접 취소할 수 있게 하려면 **학습자가 직접 등록을 취소할 수 있음** 확인란을 선택합니다.
1. 강의를 수강하기 전에 완료해야 하는 전제 조건 강의를 선택합니다. 강의 필드를 클릭한 다음 강의 목록에서 선택합니다.

   ![](assets/prerequisite-courses.png)

   *필수 강의 추가*

1. 강의 전제 조건을 필수로 설정하려면 **사전 전제 조건** 확인란을 선택합니다.
1. 강의와 관련된 키워드를 태그로 추가합니다. 학습자는 태그를 통해 검색 중 귀하의 강의를 쉽게 찾을 수 있습니다. 이 모든 태그는 추가한 모듈에 따라 자동으로 추가됩니다. 이 강의에 추가하려는 다른 태그가 있으면 계속 입력할 수 있습니다.
1. 텍스트 영역을 클릭하고 제안에서 프로필을 선택하여 강의 대상 참가자의 프로필을 추가합니다.
1. 강의에 대한 리소스 파일을 추가 자료로 추가합니다. 텍스트, 비디오 또는 오디오 파일 자료를 드래그합니다.
1. 이제 이 강의가 프로필에 추천 강의로 추가된 학습자는 이 강의를 수강할 수 있습니다. 이 섹션에서는 학습자를 위한 추가 리소스를 첨부할 수도 있습니다. 학습자는 나중에 참조할 수 있도록 이러한 파일을 다운로드할 수 있습니다. 이러한 모든 변경 사항을 완료하면 오른쪽 상단에 있는 **[!UICONTROL 저장]**&#x200B;을 클릭합니다. 이렇게 하면 강의가 초안으로 저장됩니다. 강의는 기본적으로 초안으로 저장됩니다.

## 모듈에 강사 할당 {#assigninstructorsformodules}

1. 강의 모듈을 생성했다면 모듈에 강사를 할당할 수 있습니다. &#39;작성자&#39; 대시보드에서 **[!UICONTROL 강의 카탈로그]**&#x200B;를 클릭합니다.
1. 강사를 할당할 모듈이 있는 강의를 클릭합니다.
1. **모듈 추가** 섹션에서 강사를 할당할 모듈을 클릭합니다.
1. **강사** 필드에 강사 역할을 할당할 사용자의 사용자 이름을 기재합니다.

   ![](assets/instructor-field.png)

   *사용자에게 강사 역할 할당*

1. 업데이트를 사용하여 강의를 다시 게시하려면 **[!UICONTROL 다시 게시]**&#x200B;를 클릭하세요.

## 관찰 체크리스트

이제 강사뿐만 아니라 관리자도 체크리스트 모듈을 검토할 수 있습니다. 인력 관리자 및 스토어 관리자 또는 위치 관리자와 같은 비계층 관리자도 체크리스트를 검토하고 완료할 수 있습니다.

강의 작성자는 체크리스트 모듈을 설정하는 동안 &quot;검토자&quot; 섹션에서 이러한 역할 옵션을 선택하여 인물 관리자와 비계층적 관리자(해당하는 경우)를 검토자로 추가할 수 있습니다. 강의 인스턴스 레벨에서 수행할 수 있습니다.

![관리자용 체크리스트](assets/manager-checklist.png)

*활동 모듈에 검토자 추가*

&quot;**[!UICONTROL +관리자]**&quot; 옵션을 선택하면 조직 계층 구조의 학습자 관리자가 자동으로 체크리스트를 검토할 수 있습니다. 관리자 이름을 개별적으로 검색하여 추가할 필요는 없습니다.

계정 책임자가 활성 필드 옵션을 사용하여 비계층 관리자 역할(예: 위치 관리자 또는 사이트 관리자)을 설정한 경우, 해당 관리자 역할을 선택하여 체크리스트를 검토할 수 있습니다.

관리자 이름을 개별적으로 검색하여 추가할 필요는 없습니다. 학습자가 체크리스트 강의에 등록하면 선택한 강사와 함께 검토를 위해 자동으로 관리자/스토어 관리자에게 알림을 보냅니다. 이 작업 과정을 통해 작성자는 개별 관리자의 이름을 언급하지 않아도 됩니다.

위에 제공된 샘플 스크린샷에서 &quot;**[!UICONTROL +스토어 관리자]**&quot; 옵션을 선택하면 학습자에게 정렬된 비계층 관리자가 자동으로 체크리스트를 검토할 수 있습니다. 여기서 &quot;스토어&quot;는 관리자가 정의한 활성 필드로 대체됩니다.

체크리스트 모듈 업데이트에는 학습자가 체크리스트 모듈이 있는 강의에 등록 시 강사 및 관리자에게 전송되는 알림도 포함됩니다. 검토자는 Learning Manager 알림 센터 및 강사/관리자 대시보드에서 체크리스트 동작이 예정되어 있다는 알림을 수신합니다.

<!--![View notification for enrollment](assets/checklist-notification.png)-->

검토자는 강사/관리자로 로그인할 때 체크리스트 메뉴 및 알림 메뉴에서 보류 중인 모든 체크리스트 검토 항목에 대한 정보를 확인할 수 있습니다.

![인증서 승인](assets/pending-task-managers.png)

*인증 승인*

검토자는 [검토 체크리스트]를 클릭한 후 평가를 완료할 수 있습니다.

![보류 중인 체크리스트 검토 항목 검토](assets/evaluation-checklist.png)

*보류 중인 체크리스트 검토 항목 검토*

보고는 학습자 평가, 검토자 이름 및 전자 메일에 대한 자세한 정보가 포함된 체크리스트에서 다운로드할 수 있습니다.

체크리스트 보고서 csv에는 다음과 같은 새 필드와 업데이트된 필드가 있습니다.

* 강사 이름 대신 검토자 이름
* 강사 전자 메일 대신 검토자 전자 메일
* 검토자 역할 - 가능한 값은 관리자, 스토어/위치 관리자, 강사입니다.

## 강의 미리 보기 {#previewacourse}

강의가 생성되어 초안으로 저장되면 강의를 학습자로 미리 본 다음 강의 카탈로그에서 사용할 수 있도록 게시할 수 있습니다.

강의를 미리 보려면 **[!UICONTROL 학습자로 미리 보기]**&#x200B;를 클릭합니다.

![학습자로 강의 미리 보기](assets/preview-as-a-learner.png)

*학습자로 강의 미리 보기*

이를 실행하면 강의 **개요** 페이지가 열리며 강의와 관련된 모듈, 주문 및 기타 세부 정보가 표시됩니다.

![](assets/overview-page.png)

*모듈 및 기타 관련 세부 정보 보기*

학습자가 이 과정을 어떻게 경험할 수 있을지 보려면 각 모듈을 클릭하여 재생해 보십시오. 그러면 Fluidic Player에서 강의가 시작됩니다.

## 강의 게시 {#publishacourse}

강의를 학습자로 미리 본 후에 학습자가 사용할 수 있도록 강의를 게시할 수 있습니다. 강의는 여전히 초안 모드에 있습니다.

일반적인 강의 사용 주기는 다음과 같습니다.

* **초안** - 작성자가 강의 생성 및 저장을 완료하면 이 상태인 경우 학습자는 강의를 사용할 수 없습니다.
* **게시됨** - 작성자가 강의 게시를 완료한 경우. 이 상태인 경우 학습자는 강의에 등록할 수 있습니다. 이 상태의 강의는 편집할 수도 있습니다.
* **중단됨** - 강의를 게시한 후 작성자가 학습자 카탈로그에 강의가 나타나는 것을 원하지 않으면 강의를 중단 상태로 변경할 수 있습니다.
* **삭제됨** - Adobe Learning Manager 응용 프로그램에서 완전히 제거된 상태의 강의입니다. 작성자만 초안 또는 중단됨 상태의 강의를 삭제할 수 있습니다.

![](assets/typical-course-lifecycle.png)

*과정 수명 주기의 워크플로*

생성한 강의를 게시하려면 페이지의 오른쪽 상단 모서리에서 **[!UICONTROL 게시]**&#x200B;를 클릭합니다.

![](assets/publish-a-course.png)

*Publish a 과정*

확인 팝업 메시지가 나타나면 **[!UICONTROL 확인]**&#x200B;을 클릭합니다.

이제 해당 강의를 강의 카탈로그에서 사용할 수 있습니다.

## 강의 보기 {#viewacourse}

작성자로 사용할 수 있는 모든 강의 목록을 볼 수 있습니다. Learning Manager 계정에서 모든 강의를 보려면 &#39;강의 카탈로그&#39;를 클릭합니다. Learning Manager에서 작성한 모든 강의를 보려면 **[!UICONTROL 내 강의]**&#x200B;를 클릭합니다.

강의 카드에서 옵션에 마우스를 가져가 **[!UICONTROL 강의 보기]**&#x200B;를 클릭합니다.

![](assets/view-a-course.png)

*강의 보기*

강의 정보 창이 표시됩니다. 강의는 읽기 전용 모드에 있습니다. 강의를 수정하려면 **[!UICONTROL 편집]**&#x200B;을 클릭합니다.

## 강의 중단 {#retireacourse}

강의를 중단하면 학습자가 등록했거나 이미 완료한 경우에도 숨겨집니다. 강의를 중단하는 경우 새 학습자를 강의에 등록할 수 없습니다. 이미 등록한 학습자는 강의를 수강할 수 있습니다.

강의를 중단하려면 강의 카드에서 옵션에 마우스를 가져가 강의 중단을 클릭합니다.

![](assets/retiring-course.png)

*강의 사용 중지*

확인 팝업이 나타나면 **[!UICONTROL 예]**&#x200B;를 클릭합니다.

## 강의 복제 {#duplicateacourse}

강의의 사본을 만들고 강의를 수정할 수 있습니다. 강의를 백업하려는 경우 강의를 복제할 수 있습니다.

## 강의 검색 {#searchforcourses}

Adobe Learning Manager에서는 원하는 강의를 빠르고 쉽게 찾을 수 있습니다. 다음과 같은 방법으로 강의를 검색할 수 있습니다.

**검색 필드:** **강의 카탈로그** 페이지의 오른쪽 상단 모서리에 있는 검색 창을 클릭합니다. 강의 이름 또는 강의와 관련된 키워드를 입력합니다. 강의 생성 중 추가된 태그를 사용하여 검색할 수도 있습니다. 강의 검색 필드 내에서 태그를 검색할 수 있습니다. 즉, 검색 필드에 입력하면 태그가 표시됩니다.

![](assets/search-field.png)

*강의 검색*

**강의 필터 목록:** 전체, 게시됨, 초안, 중단됨 등의 상태로 강의에 필터를 적용할 수 있습니다. 선택에 따라, 필터가 적용된 강의 목록을 보고 필요한 강의를 선택할 수 있습니다.

작성자는 강의를 정렬하여 더 쉽게 필요한 강의를 찾을 수 있습니다. **[!UICONTROL 정렬 기준]**&#x200B;을 클릭하고 알파벳 오름차순, 알파벳 내림차순, 강의 생성 날짜, 강의 업데이트 날짜 및 강의 효과를 선택합니다.

![](assets/filter-list-of-courses.png)

*강의 목록 필터링*

## 학습자 강의 등록 {#enrolllearnersinacourse}

책임자만 강의에 대한 학습자 등록 권한을 보유하므로 학습자를 강의에 등록하거나 관리자가 강의의 학습자를 추천하도록 허용하려면 책임자 모드로 전환해야 합니다.

책임자 모드로 전환하려면

1. 프로필 사진을 클릭한 다음 책임자를 선택합니다.
1. 책임자 모드에서 왼쪽 창의 **[!UICONTROL 강의]**&#x200B;를 클릭합니다. 이 페이지에서는 Learning Manager 계정의 모든 작성자가 만든 모든 강의를 볼 수 있습니다.
1. 학습자를 등록하기 위해 강의 카드에 마우스를 올리면 **학습자 등록** 옵션이 표시됩니다. 이 옵션을 클릭합니다.

   ![](assets/enroll-learners.png)

   *강의에 학습자 등록*

1. 학습자 등록 대화 상자에서 오른쪽 상단 모서리의 **기본 인스턴스** 옵션이 선택되어 있는 것을 볼 수 있습니다. 작성자가 강의를 생성하면 강의의 기본 인스턴스가 생성됩니다.

   ![](assets/default-instance.png)

   *강의의 기본 인스턴스 보기*

1. 학습자 포함 필드에서 학습자의 이름을 입력하고 학습자를 선택합니다. 여기에서 사용자 그룹을 추가할 수도 있습니다. Learning Manager 계정에 모든 학습자를 등록하려면 모두 입력을 시작합니다. 학습자를 팀에 등록할 수도 있습니다.

   ![](assets/include-learners.png)

   *강의에 학습자 추가*

1. 학습자를 강의에서 제외하려면 **학습자 제외** 필드에 해당 학습자의 이름을 입력합니다.
1. 학습자를 등록한 다음 **[!UICONTROL 계속]**&#x200B;을 클릭합니다. 학습자 등록 대화 상자에서 등록에 대한 요약을 확인할 수 있습니다.

   ![](assets/summary-of-enrollment.png)

   *강의 등록 요약 보기*

1. 강의에 모든 학습자를 등록하려면 **[!UICONTROL 등록]**&#x200B;을 클릭합니다. 이제 학습자가 강의에 성공적으로 등록되었습니다. 해당 학습자에게 과정을 수강할 수 있다는 알림이 전송됩니다. 학습자를 더 등록하려면 등록 절차를 반복합니다.

## Connect VC 모듈의 강의 인스턴스 페이지 변경 사항 {#connect-vc}

Connect 강의를 검색하는 동안 다음 두 가지 유형의 회의실을 생성할 수 있습니다.

* 동적
* 지속

지속 URL은 항상 고정됩니다. 그러나 Connect 및 자체 회의실이 없는 사용자인 경우, 실행 시 반드시 동적 회의실을 사용해야 합니다. 그런 다음 사람들이 회의에 참여할 수 있습니다.

![](assets/dynamic-room-options.png)

*동적 회의실 옵션*

이제 **강의 인스턴스** 페이지에서 지속 회의실의 url을 변경할 수 있습니다.

<!--| ![](assets/persistentroomdropdown.png) | ![](assets/courseinstancepage-persistentroom.png) |
|---|---|-->

## 학습자 강의 등록 취소 {#unenrolllearnersfromacourse}

강의를 생성하는 동안 작성자는 **학습자가 직접 등록을 취소할 수 있음** 옵션을 활성화하여 강의를 수강하는 학습자가 직접 등록을 취소하게 할 수 있습니다.

책임자가 강의에서 학습자의 등록을 취소할 수도 있습니다.

![](assets/unenroll-learners.png)

*강의에서 학습자 등록 취소*

자세한 내용은 [학습자 등록 취소](/help/migrated/administrators/feature-summary/courses.md)를 참조하십시오.

## Captivate 및 Presenter 강의 모듈 추가 {#addcoursemodulesforcaptivateandpresenter}

Adobe Captivate 및 Adobe Presenter 소프트웨어에서 &#39;게시&#39; 메뉴를 사용하여 Learning Manager에 강의 모듈을 게시할 수도 있습니다.

1. Captivate에서 **[!UICONTROL Publish]** > **[!UICONTROL Learning Manager로 Publish]**&#x200B;를 클릭합니다.
1. 서브 도메인 이름 또는 전자 메일 ID를 입력하고 **[!UICONTROL 제출]**&#x200B;을 클릭합니다. 여러 계정을 갖고 있는 경우 계정을 선택하라는 메시지가 나타납니다.
1. Adobe 자격 증명으로 로그인합니다. Adobe ID가 없다면 **[!UICONTROL 계정 만들기]**&#x200B;를 클릭합니다. 인증을 하면 모듈 게시 페이지로 이동합니다.
1. 모듈에 대한 기본 정보를 입력한 다음 &#39;게시&#39;를 클릭합니다.

Learning Manager 모듈 페이지에 게시된 모듈이 표시됩니다. 자세한 내용은 [Adobe Learning Manager에 프로젝트 게시](https://helpx.adobe.com/kr/captivate/classic/publish-project-to-captivate-prime.html)를 참조하십시오.

## 강의 효과 {#courseeffectiveness}

강의 효과 점수는 작성자가 학습자의 필요를 충족하지 못하는 강의를 평가하고 그에 따라 수정하도록 도와줍니다. 강의가 학습자에게 유용했는지 파악하기 위해 강의 효과를 평가합니다. 강의 효과는 강의 콘텐츠에 대한 학습자 피드백을 조합한 결과입니다. 학습자에 대한 강의 퀴즈 결과와 강의 학습을 기반으로 학습자를 평가하는 관리자의 피드백.

**내 강의**&#x200B;에서 작성자는 아래 스냅샷과 같이 강의 축소판에서 강의 효과 등급 또한 볼 수 있습니다. 이 강의의 등급은 100으로 표시돼 있습니다.

<!--![](assets/course-rating.png)-->

강의 효과 등급 값은 L1, L2 및 L3 피드백 값을 고려하여 산출됩니다. 각 피드백의 내용을 확인하려면 강의 효과 값을 클릭합니다. 아래와 같이 팝업 메뉴가 나타납니다.

![](assets/how-course-effectivenessiscalculated.png)

*강의 효과 계산*

샘플 스냅샷에서는 총 사용자 1명 중 1명이 3개 유형의 피드백을 전부 받았으며 점수는 100/100입니다. 표에서 빠진 피드백을 파악하여 전체 효과를 개선할 수 있습니다. 강의 효과 계산 방법을 보려면 팝업의 오른쪽 아래 모서리에 있는 아래로 화살표를 클릭합니다.

<!--![](assets/how-course-effectivenessiscalculated1.png)-->

위에 표시된 원형 도표에서 볼 수 있듯이 관리자의 L3 피드백에는 가중치가 부여됩니다.

## 인증 및 학습 프로그램 {#certificationsandlearningprograms}

작성자와 책임자는 작성자 앱에서 학습자를 위한 인증 및 학습 프로그램을 생성할 수 있습니다. 홈페이지에서 인증 또는 학습 프로그램을 클릭하면 각 학습 객체를 생성할 수 있습니다.

인증 및 학습 프로그램을 만들고 관리하는 방법에 대한 자세한 내용은 [인증](/help/migrated/administrators/feature-summary/certifications.md) 및 [학습 프로그램](/help/migrated/administrators/feature-summary/learning-programs.md)을 참조하세요.

## 외부 인증을 위한 필수 강의 {#mandatorycoursesforexternalcertification}

Learning Manager 초기 릴리스에서는 외부 인증에서 학습자가 강의를 완료하는 것이 인증서를 완료하는 필수 요건이 아니었습니다.

이제 교육과정 탭에서 **필수 강의를 인증서 완료를 위한 필수 요건으로 설정** 옵션을 활성화하여 강의를 필수 강의로 지정할 수 있습니다.

![](assets/set-required-coursesasmandatory.png)

*인증서 완료를 위한 필수 강의 설정*

강의가 필수로 설정되는 경우:

* 관리자의 제출 페이지에는 학습자가 강의를 완료한 이후에만 학습자 목록이 표시됩니다.
* 학습자는 강의를 완료해야만 파일을 업로드할 수 있습니다.

## 자주 묻는 질문 {#frequentlyaskedquestions}

+++강의의 &#39;관리자 지정 검색&#39;을 제거하려면 어떻게 해야 합니까?

다음 단계를 수행하십시오.

1. Learning Manager에 작성자로 로그인합니다.
1. 강의를 엽니다.
1. 왼쪽 창에서 **[!UICONTROL 설정]** > **[!UICONTROL 편집]**&#x200B;을 클릭합니다.
1. **등록 유형** 드롭다운 목록에서 등록 유형을 **관리자 지정**&#x200B;에서 **관리자 승인** 또는 **자가 등록**&#x200B;으로 변경합니다.

1. 등록 유형을 변경한 후 강의를 다시 게시합니다.

+++

+++과정을 결합하는 방법?

학습 프로그램을 통해 강의를 결합할 수 있습니다.

1. Learning Manager에 책임자로 로그인합니다.
1. 왼쪽 창의 **[!UICONTROL 학습 프로그램]**&#x200B;을 클릭합니다.
1. 학습 프로그램을 추가하려면 **[!UICONTROL 추가]**&#x200B;를 클릭합니다.
1. 학습 프로그램의 세부 정보를 입력하고 학습 프로그램을 저장하려면 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
1. 학습 프로그램을 생성한 후 **[!UICONTROL 카탈로그]**&#x200B;를 클릭합니다.
1. 강의 카드에서 아래와 같이 **[!UICONTROL 추가]**&#x200B;를 클릭합니다. 학습 프로그램에 추가하려는 강의 수만큼 해당 과정을 반복합니다.

![](assets/add-catalog.png)

학습 프로그램에서 필요한 모든 과정을 추가한 후 **[!UICONTROL 게시]**&#x200B;를 클릭합니다.

학습 프로그램에서는 자가 등록 강의만 추가할 수 있으며 관리자 지정 또는 관리자 승인 강의는 추가할 수 없습니다. 이는 Learning Manager의 기본 동작입니다.

+++

+++모든 학습자가 모든 강의를 볼 수 없도록 하려면 어떻게 해야 합니까?

카탈로그를 통해 설정할 수 있습니다. 기본 카탈로그에는 기본적으로 Learning Manager에 추가된 모든 강의가 포함됩니다.

기본 카탈로그를 비활성화한 다음 사용자 정의 카탈로그를 생성해야 합니다.

1. Learning Manager에 책임자로 로그인합니다.
1. 왼쪽 창의 **[!UICONTROL 카탈로그]**&#x200B;를 클릭합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭하여 카탈로그를 생성합니다. 세부 정보를 입력하고 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

1. 새로 생성된 카탈로그 옵션에서 학습 프로그램, 인증 또는 강의와 같이 추가할 수 있는 다양한 유형의 학습을 선택할 수 있습니다.
1. 학습 프로그램 섹션에서 **[!UICONTROL 콘텐츠 추가]**&#x200B;를 클릭합니다.
1. 왼쪽 창에서 지정하려는 대상자에 따라 **[!UICONTROL 내부적으로 공유]** 또는 **[!UICONTROL 외부적으로 공유]**&#x200B;를 클릭합니다.

1. 사용자 그룹을 추가하려면 **[!UICONTROL 사용자 그룹 추가]**&#x200B;를 클릭합니다.
1. 카탈로그 페이지에서 **D[!UICONTROL 기본 카탈로그]**&#x200B;를 비활성화하고 만든 카탈로그를 활성화하십시오.

![](assets/enable-custom-catalog.png)

+++

+++완료한 강의를 다시 등록하려면 어떻게 해야 합니까?

강의 완료는 되돌릴 수 없습니다. 학습자는 완료한 강의를 **다시 등록할 수 없습니다**.

+++

+++학습자가 강의를 완료한 후 다시 보려면 어떻게 해야 합니까?

해당 강의에서 재방문 버튼을 클릭하면 완료 후 강의를 다시 볼 수 있습니다.

아래 단계를 따르십시오.

1. 학습자로 로그인합니다.
1. 완료한 강의를 엽니다.
1. **[!UICONTROL 재방문]**&#x200B;을 클릭합니다.

+++

+++강의에 리소스 파일을 추가하는 방법은 무엇입니까?

강의를 생성하는 동안 학습자가 추가 교육 자료에 액세스할 수 있도록 강의와 관련된 강의에 비디오, 오디오, pdf 또는 텍스트 파일을 추가할 수 있습니다.

![](assets/add-resources.png)

+++

+++모듈에서 여러 번 시도를 설정하는 방법

**사전 요구 사항:** 관리자는 관리 앱의 **설정 > 일반**&#x200B;에서 **다중 시도** 옵션을 활성화해야 합니다.

작성자는 강의 개요 페이지에서 **여러 번 시도 허용** 옵션을 활성화합니다.

자세한 내용은 [여러 번 시도에 대한 섹션](courses.md#Allowmultipleattempts)을 참조하십시오.

+++

+++Adobe Learning Manager에 업로드된 콘텐츠를 다운로드하고 해당 콘텐츠를 수정할 수 있습니까?

아니요. Learning Manager에 업로드된 콘텐츠는 게시된 zip 파일이며, 소스 파일이 아닙니다. 따라서, 콘텐츠를 다운로드하더라도, 해당 콘텐츠는 제작 도구로 편집할 수 없습니다. 콘텐츠를 수정하려면 소스 파일이 필요합니다.

+++
