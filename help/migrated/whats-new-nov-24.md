---
description: Adobe Learning Manager 2024년 11월 릴리스의 새로운 기능 및 개선 사항에 대해 알아봅니다
jcr-language: en_us
title: 새로운 기능 요약 2024년 11월
exl-id: 4dfe0e31-d202-4a6e-8c4f-43851218699f
source-git-commit: 7b84a4565ccf109ed4789f4963d6e250f5d0a852
workflow-type: tm+mt
source-wordcount: '3264'
ht-degree: 1%

---

# 새로운 기능 요약 2024년 11월 {#new-features-summary}

Adobe Learning Manager 2024년 11월 릴리스의 새로운 기능 및 개선 사항에 대해 알아봅니다.

* **AI 기반 검색:** 더 똑똑하고 문맥 인식 결과를 위한 어휘 및 의미 체계 검색을 결합합니다.
* **Webhook**: Webhook과 통합하여 실시간 정보를 특정 URL로 보냅니다.
* **학습 도구 상호 운용성(LTI)**: 다른 LMS 플랫폼과의 상호 운용성을 위해 LTI를 지원합니다.
* **신뢰할 수 있는 통합**: Credly를 통해 외부 배지를 관리하고 공유합니다.
* **준수 대시보드 개선 사항**: 대시보드를 다른 관리자와 공유하고 학습자 홈페이지에서 기본 준수 위젯을 설정합니다.
* **다중 언어 지원**: 강의실 및 가상 강의실 모듈에 대한 언어별 인스턴스를 만듭니다.
* **사용자 지정 역할**: 사용자 역할 및 권한에 대한 제어 기능이 향상되었습니다.
* **완료 주석**: 학습자를 완료로 표시할 때 주석을 추가합니다.
* **사용자 그룹 보고서**: 자세한 보고서로 사용자 그룹을 관리합니다.
* **대기자 명단 보고서**: 강의 인스턴스에 대한 대기자 명단 학습자 목록을 다운로드합니다.
* **접근성 향상**: 발행인란 및 회사 로고의 대체 텍스트 지원.
* **힌디어 지원**: 힌디어 인터페이스 언어 지원.
* **비속어 검사**: 금지된 단어가 포함된 소셜 게시물을 차단합니다.
* **전자 메일 템플릿 최적화**: 강사 할당 및 세션 취소를 위한 전자 메일 템플릿을 결합하고 최적화했습니다.
* **MS 팀 완료 조건**: VILT 세션의 최소 참석 시간을 설정합니다.
* **새 마이그레이션 워크플로**: 마이그레이션 변경 사항에는 강의 및 모듈의 완료 기준과 모듈을 폴더로 마이그레이션하는 내용이 포함됩니다.

>[!NOTE]
>
>이 릴리스의 새로운 기능에 대해 자세히 알아보려면 이 [웨비나](https://cdn.content.adobelearningmanageracademy.com/public/newlearner/newlearner_0dc0f1e8.html#/overviewPage?instanceId=11932477&amp;loId=11231360&amp;loType=course)를 확인하세요.

## Adobe Learning Manager에서 AI 기반 검색

Adobe Learning Manager은 학습자가 강의 또는 교육을 검색하는 방식을 혁신하고 있습니다. 어휘 검색과 의미 검색이 결합된 AI 기반 검색 기능을 도입한다. 이 검색은 이제 더 똑똑해졌는데, 특정 용어를 찾고 그 배후에 있는 문맥과 의도를 파악하기 때문이다. 고급 검색은 쿼리의 의미를 이해하고 관련 결과를 제공합니다. 가장 완벽한 결과 세트를 제공하기 위해 검색의 주요 초점을 식별합니다.

>[!NOTE]
>
>AI 기반 검색은 학습자만 사용할 수 있습니다.

자세한 내용은 이 문서 [고급 검색](/help/migrated/learners/feature-summary/advanced-search.md)을 참조하세요.

## Webhook

Adobe Learning Manager을 사용하면 Webhook과 통합하여 강의 등록, 강의 생성 및 기타 정보와 같은 실시간 정보를 특정 URL로 전송할 수 있습니다.

ALM의 Webhook을 사용하면 한 엔터티가 HTTP를 통해 다른 응용 프로그램으로 데이터를 자동으로 보낼 수 있습니다. 이를 지속적으로 요청하지 않고도 다른 애플리케이션에 정보를 제공할 수 있게 된다. 예를 들어 사용자가 LMS(교육 관리 시스템) 과정을 완료한 경우 Webhook은 해당 정보를 CRM 또는 보고 도구와 같은 다른 플랫폼으로 자동으로 전송할 수 있습니다. Webhook은 통합을 통해 프로세스를 자동화하고 시스템 간에 수동 업데이트의 필요성을 줄이는 데 주로 사용됩니다. 데이터를 전송할 콜백 URL을 제공하여 Webhook을 설정합니다.

자세한 내용은 이 문서 [Webhooks](/help/migrated/integration-admin/feature-summary/webhooks.md)을(를) 참조하십시오.

## 학습 도구 상호 운용성

이제 Adobe Learning Manager에서 LTI를 지원하여 Adobe Learning Manager과 다른 LMS(교육 관리 시스템) 간의 상호 운용성을 향상시킵니다.

### LTI란 무엇입니까?

LTI(Learning Tools Interoperability)는 서드파티 도구 및 콘텐츠 공급자가 LMS(교육 관리 시스템)와 연결할 수 있도록 하는 표준입니다. 사용자는 로그인하거나 다른 LMS로 이동하지 않고도 LMS 내에서 직접 외부 콘텐츠 공급자의 외부 학습 콘텐츠에 액세스할 수 있습니다.

**도구 공급자인 LTI**: 도구 공급자인 LTI를 사용하면 외부 시스템을 LMS와 통합할 수 있습니다. Adobe Learning Manager은 LTI 도구 공급자 역할을 하여 다른 LMS 플랫폼이 해당 LMS 내에서 직접 Adobe Learning Manager의 과정, 인증서 또는 학습 경로에 액세스할 수 있도록 합니다.

**도구 소비자로서의 LTI**: 도구 소비자로서의 LTI를 사용하면 LMS가 학습 도구 상호 운용성(LTI)을 통해 외부 도구를 통합할 수 있습니다. 이러한 시나리오에서, LMS는 외부 도구에 의해 제공되는 서비스의 소비자이다. Adobe Learning Manager은 LTI 도구 소비자 역할을 하여 서드파티 학습 도구를 통합할 수 있습니다. 이를 통해 Adobe Learning Manager 학습자는 Adobe Learning Manager 내 서드파티 도구의 강의, 인증서 또는 학습 경로를 사용할 수 있습니다.

자세한 내용은 이 문서 [학습 도구 상호 운용성](/help/migrated/integration-admin/feature-summary/learning-tools-interoperability.md)을 참조하십시오.

## 신빙하

ALM의 책임자를 사용하면 학습자가 다양한 소셜 미디어 채널에서 플랫폼의 외부 배지를 관리하고 공유할 수 있습니다.

### 신빙성 있는 것은 무엇인가?

Credly는 학습자와 조직이 배지나 인증과 같은 전문적인 성과를 획득하고, 공유하고, 검증할 수 있는 디지털 인증 플랫폼입니다. 학습자는 소셜 미디어 및 기타 장소에서 크레딧 프로필을 통해 배지를 관리하고 공유할 수 있습니다.

### Adobe Learning Manager과 완벽하게 통합

먼저 Adobe Learning Manager(ALM)에서 Credly 커넥터를 추가합니다. 다음으로 기존 배지를 Credly에서 마이그레이션하여 학습자 성과의 연속성을 보장하십시오. 마지막으로 Adobe Learning Manager에서 적절한 학습 경로에 맞는 스킬을 생성하여 학습자 개발 및 인식을 개선합니다.

자세한 내용은 이 문서 [신빙성](/help/migrated/integration-admin/feature-summary/credly-integration.md)을 참조하세요.

## 준수 대시보드

이번 릴리스에서 관리자는 이제 대시보드를 다른 관리자, 사용자 정의 관리자 및 스토어 관리자와 공유하여 준수 대시보드에 즉시 액세스할 수 있습니다. 이제 학습자 홈페이지에서 기본 준수 위젯을 설정하여 학습자가 준수 요구 사항을 추적할 수 있습니다. 자세한 내용은 이 문서 [준수 대시보드](/help/migrated/administrators/feature-summary/reports.md#share-compliance-dashboard-with-admins-and-custom-admins)를 참조하세요.

## 다국어 지원

이제 작성자는 ALM(Adobe Learning Manager)을 사용하여 강의실 및 가상 강의실 모듈에 언어 태그 지정을 사용하여 언어별 인스턴스를 만들 수 있습니다. 학습자는 원하는 언어로 CR/VC 모듈에 액세스할 수 있습니다. 예를 들어 작성자는 두 개의 인스턴스, 즉 영어와 프랑스어로 된 인스턴스로 CR/VC 모듈을 만들 수 있습니다. 학습자는 원하는 언어로 인스턴스를 선택할 수 있습니다.

자세한 내용은 이 문서 [다른 로케일에서 학습 개체 추가](/help/migrated/authors/feature-summary/add-new-language-learning-objects.md#multi-language-support-for-crvc-instances-with-language-tagging)를 참조하십시오.

## 사용자 정의 역할

사용자 정의 역할을 통해 관리자는 다양한 사용자 그룹에 대한 특정 역할과 책임을 정의하여 더 나은 관리와 제어를 보장할 수 있습니다. 이 릴리스를 통해 ALM은 다음 섹션을 보다 자세히 제어하여 사용자 정의 역할을 개선합니다.

* 사용자
* 강의
* 학습 경로
* 인증
* 작업 지원
* 카탈로그

관리자는 사용자 권한에 따라 정확한 권한을 할당하여 각 그룹이 관련 기능과 콘텐츠에만 액세스할 수 있도록 할 수 있습니다. 이렇게 향상된 컨트롤을 사용하면 주요 섹션을 보다 세부적으로 관리할 수 있습니다.

관리자로 로그인하고 **[!UICONTROL 사용자]** > **[!UICONTROL 사용자 지정 역할]**&#x200B;로 이동하여 사용자 지정 역할을 만들고 관리합니다.

자세한 내용은 이 문서 [사용자 지정 역할](/help/migrated/administrators/feature-summary/custom-role.md)을 참조하십시오.

## 완료 설명

관리자는 이제 강의, 학습 경로 또는 인증에서 학습자를 완료로 표시할 때 주석을 추가할 수 있습니다. 관리자는 한 명 또는 여러 학습자에 대한 주석을 동시에 추가할 수 있으며, 해당 주석은 [학습자 성적 증명서](/help/migrated/administrators/feature-summary/reports.md#learner-transcripts) 보고서에 나타납니다.

자세한 내용은 이 문서 [완료 댓글](/help/migrated/administrators/feature-summary/courses.md#completion-comments)을 참조하십시오.

## 사용자 그룹 보고서

Adobe Learning Manager의 새 **[!UICONTROL 사용자 그룹 보고서]**&#x200B;를 사용하면 관리자가 나갈 때 관리되지 않고 남아 있는 그룹에 대한 가시성을 제공하여 사용자 그룹을 관리할 수 있습니다. 관리자는 **[!UICONTROL 사용자]** > **[!UICONTROL 사용자 그룹]** 섹션의 보고서에 액세스할 수 있습니다. 다음을 포함하여 각 그룹에 대한 자세한 정보를 제공합니다.

* 사용자 그룹 유형
* 그룹 이름
* 설명
* 제작자 (이름)
* 제작자(이메일)
* 만든 날짜(UTC 시간대)
* 사용자 수

자세한 내용은 이 문서 [사용자 그룹 보고서](/help/migrated/administrators/feature-summary/add-users-user-groups.md#user-group-report)를 참조하세요.

## 대기자 명단 보고서

Adobe Learning Manager의 새로운 **[!UICONTROL 대기자 명단 보고서]**&#x200B;를 사용하면 관리자가 모든 강의 인스턴스에 대한 대기자 명단 학습자 목록을 다운로드할 수 있습니다. 관리자와 강사는 **[!UICONTROL 과정]** 또는 **[!UICONTROL 세션 개요]** 페이지의 **[!UICONTROL 대기자 명단]** 섹션에서 이 보고서에 액세스할 수 있습니다. 대기자 명단 보고서는 책임자 및 강사 섹션에서 다운로드할 수 있습니다.

대기자 명단 보고서에서 사용할 수 있는 열을 따릅니다.

* 강의 이름
* 인스턴스 이름
* 인스턴스 ID
* 인스턴스 상태
* 사용자 이름
* 이메일
* 고유 사용자 ID
* 등록 날짜(UTC 시간대)
* 상태
* 대기자 명단 수
* 대기자 명단 제한
* 시트 제한

관리자 및 강사 섹션에서 보고서를 다운로드하려면 이 문서 [대기자 명단 보고서(관리자)](/help/migrated/administrators/feature-summary/courses.md#waitlist-report) 및 [대기자 명단 보고서(강사)](/help/migrated/instructors/feature-summary/learners.md#waitlist-report)를 참조합니다.

## 학습자 홈페이지의 접근성

이제 Adobe Learning Manager이 모든 발행인란의 대체 텍스트를 지원하여 학습자의 접근성을 향상시킵니다. 이를 통해 특별한 필요가 있는 학습자는 화면 판독기를 사용하여 대체 텍스트를 읽고 이미지를 이해할 수 있습니다. 여러 언어를 선택하고 각 언어에 대한 대체 텍스트를 제공할 수 있습니다. 대체 텍스트를 해당 언어로 추가해야 합니다. 계정의 회사 로고에 회사 이름이 있는 대체 텍스트도 포함되어 있는지 확인합니다.
자세한 내용은 이 문서 [공지](/help/migrated/administrators/feature-summary/announcements.md#masthead)를 참조하십시오.

## 힌디어 지원

Adobe Learning Manager은 이제 힌디어를 플랫폼의 인터페이스 언어 중 하나로 도입하고 인도 내 플랫폼의 성장을 지원합니다. 원어민 힌디어 사용자를 지원하면 모든 기능, 보고서 및 전체 사용자 환경에 완전히 액세스할 수 있습니다.

>[!NOTE]
>
>시스템에서 PDF 형식으로 생성한 배지 인증서는 힌디어를 지원하지 않습니다.

인터페이스 언어를 변경하려면 다음 단계를 따르십시오.

1. **[!UICONTROL 관리자]**(으)로 로그인합니다.
2. **[!UICONTROL 프로필 설정]** > **[!UICONTROL 인터페이스 언어]**(으)로 이동합니다.
3. **[!UICONTROL 힌디어]**&#x200B;를 인터페이스 언어로 선택합니다.


## 소셜 게시물에 대한 욕설 확인

이제 Adobe Learning Manager은 학습자 앱에서 금지된 단어가 포함된 소셜 게시물을 차단합니다. 이는 특히 의료와 같은 민감한 분야에서 사물을 전문적이고 규정 준수하는 데 도움이 됩니다.

## 전자 메일 템플릿 최적화

### 강사가 할당되면 학습자에게 전자 메일 보내기

기존 전자 메일 **[!UICONTROL 강사로 추가됨]** 및 **[!UICONTROL VCProvider 세션 세부 정보]**&#x200B;가 하나의 전자 메일로 결합됨 **[!UICONTROL UserType으로 추가됨]**. **[!UICONTROL UserType]**&#x200B;은(는) 사용자의 역할에 따라 **[!UICONTROL 강사]** 또는 **[!UICONTROL 주최자]**&#x200B;가 됩니다. 이러한 이메일은 이전에는 UI에서 사용할 수 없었습니다. 이제 여러 항목이 하나의 전자 메일로 결합되어 UI에 추가되었습니다. 관리자는 **[!UICONTROL 전자 메일 템플릿]** 섹션에서 이 템플릿에 액세스할 수 있습니다. 기본적으로 모든 새 계정 및 기존 계정에 대해 활성화되지만 관리자는 동일한 섹션에서 비활성화하거나 활성화할 수 있습니다. 이 전자 메일은 Zoom, Teams, Connect 또는 기타 서비스 등 세션 생성 및 강사 할당 시마다 발송됩니다.

### 세션이 취소되면 학습자에게 전자 메일 보내기

세션에서 제거된 강사는 이제 세션 취소 이메일만 받게 됩니다. 이전에는 고객이 취소 이메일과 업데이트 이메일을 모두 수신했습니다. 세션에 남아 있는 강사는 세션에 대한 새 초대와 함께 세션 업데이트 이메일을 수신하게 됩니다.

## MS Teams 완료 조건

현재 학습자는 가상 강사 주도 교육(VILT) 세션에 몇 초만 참석해도 참석자로 표시됩니다. 이번 릴리스에서는 보다 정확한 출석을 보장하기 위해 팀 모듈의 완료 기준을 도입했습니다. 이제 작성자는 학습자의 출석을 집계하기 위해 VILT 세션에서 학습자가 소비해야 하는 최소 시간을 설정할 수 있습니다.

이 기능은 기본적으로 비활성화되어 있는 백엔드 기능입니다. CSM에 문의하여 활성화하십시오.

## 전자 메일 배달에 대한 새 IP 주소 업데이트

이메일 전송 안정성을 높이기 위해 기존 풀에 새 IP 주소를 추가합니다. 지속적인 이메일 커뮤니케이션을 위해 필요에 따라 조직의 이메일 설정을 업데이트하십시오.

현재 전자 메일 배달에는 다음 IP 주소가 사용됩니다.

* 149.72.162.66
* 167.89.5.155

다음 IP 주소가 이메일 배달 풀에 추가됩니다.

* 159.183.228.93
* 159.183.225.26
* 159.183.218.22
* 168.245.57.144

>[!NOTE]
>
>필요한 경우 IT 팀과 협력하여 허용된 URL 목록에 IP 주소를 추가하는 것이 좋습니다.

## 마이그레이션 변경 사항

마이그레이션 워크플로에서 변경된 사항은 다음과 같습니다.

* 모듈을 특정 폴더로 마이그레이션합니다.
* 모듈의 완료 조건을 추가했습니다.
* 강의의 완료 기준 추가

### 모듈 마이그레이션 변경 사항

모듈을 ALM으로 마이그레이션하면 기본적으로 공용 폴더에 저장됩니다. 이 릴리스에서는 [module_version.csv](assets/module_version.csv) 파일에 `folder`이라는 새 열을 추가했습니다. 관리자는 이 열을 사용하여 마이그레이션 후 모듈이 이동해야 하는 폴더 이름을 지정할 수 있습니다. 또한 관리자는 폴더 이름을 쉼표로 구분하여 나열하여 단일 모듈을 여러 폴더에 배치할 수 있습니다.

폴더 열은 문자열 데이터 유형을 사용하며 선택적 열입니다. 폴더 열의 조건은 다음과 같습니다.

* 추가하는 폴더 이름은 ALM 계정의 기존 콘텐츠 폴더여야 합니다.
* 값은 쉼표로 구분된 문자열이어야 합니다.
* 다른 폴더에 이미 있는 모듈에 대한 새 폴더 이름을 추가하면 새 값이 할당된 폴더를 덮어쓰거나 바꾸지 않습니다. 모듈은 새 폴더에 추가되고 기존 폴더에서도 사용할 수 있습니다.
* 값이 비어 있으면 폴더는 기본적으로 **[!UICONTROL 공용]**&#x200B;으로 설정됩니다.

자세한 내용은 [module_version csv 사양](assets/4-module_version.xlsx) 파일을 참조하십시오.

### 모듈 마이그레이션 변경 사항 - 완료 기준

관리자는 모듈 마이그레이션 중 모듈의 완료 조건을 지정할 수 있습니다. 이 릴리스에서는 [module_version.csv](assets/module_version.csv)에 새 열 `completionCriteria`, `viewPercent` 및 `quizData`을(를) 추가했습니다.

다음은 새 열에 대한 조건입니다.

1. `completionCriteria`:

   * 데이터 유형은 문자열 값이어야 하며 지원되는 값은 다음과 같습니다.
      * `LAUNCH_CONTENT`
      * `VIEW_PERCENT`
      * `QUIZ`
      * `MARK_COMPLETE`
   * 자가 진행식 모듈 유형에 대해서만 모듈 수준에서 완료 기준을 추가합니다.
   * 정적 내용에 대해 지원되는 값은 `LAUNCH_CONTENT` 및 `VIEW_PERCENT`입니다.
   * 대화형 콘텐츠에 대해 지원되는 값은 `LAUNCH_CONTENT`, `VIEW_PERCENT` 및 `QUIZ`입니다.
   * HTML5 콘텐츠에 대해 지원되는 값은 `LAUNCH_CONTENT` 및 `MARK_COMPLETE`입니다.

2. `viewPercent`:

   * 이 열의 데이터 형식은 정수여야 하며 값은 0에서 100 사이여야 합니다.
   * completionCriteria가 `VIEW_PERCENT`(으)로 설정된 경우 이 열에 필요한 보기 백분율을 입력하거나 비워 두십시오.

3. `quizData`:

   * 데이터 형식은 문자열 값이어야 하며 지원되는 값은 `QUIZ_ATTEMPTED`, `QUIZ_PASSED` 및 `QUIZPASSED_OR_LIMITREACHED`입니다.
   * `completionCriteria`이(가) `QUIZ`(으)로 설정되면 `quizData` 열에 적절한 퀴즈 값을 입력합니다.

자세한 내용은 [module_version csv 사양](assets/4-module_version.xlsx) 파일을 참조하십시오.

### 강의 마이그레이션 변경 사항 - 완료 기준

관리자는 강의 마이그레이션 중 강의 완료 기준을 지정할 수 있습니다. 이번 릴리스에서는 [course.csv](assets/course.csv)에 `completionCriteria`이라는 새 열을 추가했습니다.

다음은 `completionCriteria` 열의 조건입니다.

* 데이터 유형은 문자열 또는 숫자여야 하며 선택적 필드입니다.
* 값은 `ALL`, `X` 및 `SELECTEDMODULES`이어야 합니다.
* X는 0보다 크고 총 모듈 수보다 작아야 하는 정수 값입니다.
* `completionCriteria`을(를) `SELECTEDMODULES`(으)로 설정하는 경우 [course_module.csv](assets/course_module.csv) 파일에서 필수 모듈을 표시해야 합니다.
* `optionalCriteria` 열에서 `TRUE` 또는 `FALSE`을(를) 입력합니다. 값을 `TRUE`(으)로 설정하면 모듈이 필수로 설정됩니다.

자세한 내용은 [코스 csv 사양](assets/3-course.xlsx) 및 [코스_모듈 csv 사양](assets/6-course_module.xlsx) 파일을 참조하십시오.

## API 변경 사항

다음은 API 변경 사항입니다.

* **검색 API**:
   * 새로운 모드 필터: classicSearch 및 advanceSearch.
   * snippetTypes에 대한 새로운 loMetadata 옵션입니다.
* **공지 API**:
   * 발행인란 설명에 대한 altText 특성을 포함합니다.
* **인스턴스 API**:
   * 로캘 세부 정보를 검색하는 새 로캘 특성입니다.
* **욕설 확인**:
   * 소셜 게시물의 댓글 및 답변에서 금지된 단어를 확인하도록 API를 업데이트했습니다.
* **RPM 및 버스트 제한**:
   * 모든 API에 대한 RPM(분당 요청 수) 및 버스트 제한을 추가했습니다.
* **배지 API**:
   * 외부 배지에 대한 정보를 검색하는 새로운 특성 externalProvider입니다.
* **작업 API**:
   * 작업 API를 사용하여 사용자 그룹 보고서 및 사용자 정의 역할 감사 보고서를 다운로드합니다.

### 검색 API의 변경 사항

이제 검색 API에 두 가지 옵션(`classicSearch` 및 `advanceSearch`)이 있는 새 모드 필터가 있습니다. `snippetTypes`에 대한 새로운 `loMetadata` 옵션도 있습니다. 최상의 결과를 얻으려면 `advanceSearch` 모드를 사용할 때 `snippetTypes`에 `loMetadata`을(를) 포함하세요.

### 공지 API 변경 사항

이제 `GET /announcements API`에 발행인란 설명을 제공할 `altText` 특성이 포함됩니다.

#### cURL을 사용한 샘플 요청:

```
curl -X GET --header 'Accept: application/vnd.api+json' --header 'Authorization: oauth 12345678' 'https://abcd.adobe.com/primeapi/v2/announcements/123456'
```

#### 샘플 응답:

```
{
  "links": {
    "self": "https://abcd.adobe.com/primeapi/v2/announcements/123456"
  },
  "data": {
    "id": "12345",
    "type": "adminAnnouncement",
    "attributes": {
      "actionUrl": "google.com",
      "announcementType": "MASTHEAD",
      "expiryDate": "2038-01-19T03:14:07.000Z",
      "liveDate": "2024-07-31T11:11:30.000Z",
      "contentMetaData": [
        {
          "contentType": "IMAGE",
          "contentUrl": "https://abcd.adobe.com",
          "locale": "en-US",
          "altText": "Moonlight - english changed new",
          "thumbnailUrl": "https://abcd.adobe.com/"
        },      ]
    }
  }
}
```

### 인스턴스 API의 변경 사항

새 `locale` 특성이 로캘 세부 정보를 검색하기 위해 다음 API에 추가되었습니다.

* `GET /learningObjects/{loId}/instances/{loInstanceId}`
* `GET /learningObjects/{id}?include=instances,enrollment.loInstance`
* `GET /learningObjects?include=instances,enrollment.loInstance`
* `GET /learningObjects/{id}/relatedLOs?include=instances,enrollment.loInstance`
* `POST /learningObjects/query?include=instances,enrollment.loInstance`
* `POST /search/query?include=model.instances`
* `GET /search?include=model.instances`

#### cURL을 사용한 샘플 요청:

```
curl --location 'http://abcd.com/primeapi/v2/learningObjects/course:1234567/instances/course:1234567_1234567' \
```

#### 샘플 요청:

```
{
    "links": {
        "self": "http://abcd.com/primeapi/v2/learningObjects/course:1234567/instances/course:1234567_1234567"
    },
    "data": {
        "id": "course:1234567_1234567",
        "type": "learningObjectInstance",
        "attributes": {
            "dateCreated": "2024-02-27T09:21:25.000Z",
            "isAET": false,
            "isDefault": true,
            "isFlexible": false,
            "locale": "en-US",
            "state": "Active",
            "localizedMetadata": [
                {
                    "locale": "en-US",
                    "name": "Default instance"
                }
            ]
        },
        "relationships": {
            "learningObject": {
                "data": {
                    "id": "course:1234567",
                    "type": "learningObject"
                }
            },
            "loResources": {
                "data": [
                    {
                        "id": "course:123456_1234567_1234567_1",
                        "type": "learningObjectResource"
                    }
                ]
            }
        }
    }
}
```

### 욕설 확인을 위한 공개 API 변경 사항

다음 API가 소셜 게시물의 댓글 및 댓글에 대한 비속어 검사를 수행하도록 업데이트되었습니다.

* `POST /boards/{id}/posts `
* `PATCH /posts/{id}`
* `POST /posts/{id}/comments`
* `PATCH /comments/{id}`
* `POST /comments/{id}/replies`
* `PATCH /replies/{id}`

게시물에 제한된 단어가 있는 경우 다음 응답이 전송됩니다.

#### 샘플 응답:

```
{
  "status": "FORBIDDEN",
  "title": "BAD_WORD_FOUND",
  "source": {
    "info": "Unacceptable word found in post"
  }
}
```

### RPM 및 버스트 제한 변경

이 릴리스에서는 모든 API에 대해 RPM(Requests Per Minute) 및 버스트 제한이 추가되었습니다. 각 API의 최대 RPM은 Swagger 페이지에서 확인할 수 있습니다.

RPM은 API 서버로 1분 내에 보낼 수 있는 요청 수입니다. 버스트 제한은 일반적인 비율 제한을 넘어 짧은 시간 동안 더 많은 수의 요청을 허용합니다. 예를 들어 `learningObject` API에서는 분당 최대 15개의 요청을 사용할 수 있습니다. 이 한도를 초과하면 API에서 오류 메시지를 반환합니다.

### 배지 API 변경 사항

배지 ID 및 공급자 이름을 포함하여 외부 배지에 대한 정보를 검색하기 위해 새 특성 `externalProvider`이(가) 다음 API에 추가되었습니다.

* `GET /badges `
* `GET /badges/{id}`
* `GET /skills?include=levels.badge`
* `GET /skills/{id}?include=levels.badge`
* `GET /learningObjects/{loId}/instances/{loInstanceId}?include=badge`
* `GET /users/{userId}/userBadges`
* `GET /users/{userId}/userBadges/{id}`

#### cURL을 사용한 샘플 요청:

```
curl -X GET --header 'Accept: application/vnd.api+json' --header 'Authorization: oauth 123456789' 'https://abcd.adobe.com/primeapi/v2/badges/44'
```

#### 샘플 응답:

```
{
  "links": {
    "self": "https://abcd.adobe.com/primeapi/v2/badges/44"
  },
  "data": {
    "id": "44",
    "type": "badge",
    "attributes": {
      "imageUrl": "https://abcd.com/accountassets/1/badges/download.png",
      "name": "external badge",
      "state": "Active",
      "externalProvider": {
        "id": "1234sjd-b272-4de1-9b60-1234567",
        "provider": "credly"
      }
    }
  }
}
```

### 작업 API를 통해 사용자 그룹 및 사용자 정의 역할 감사 보고서 다운로드

사용자는 `Job API`을(를) 사용하여 **[!UICONTROL 사용자 그룹 보고서]** 및 **[!UICONTROL 사용자 지정 역할 감사 보고서]**&#x200B;를 다운로드할 수 있습니다.

#### 사용자 그룹 보고서 다운로드에 대한 샘플 요청:

```
curl -X POST --header 'Content-Type: application/vnd.api+json;charset=UTF-8' --header 'Accept: application/vnd.api+json' --header 'Authorization: oauth 12345678' -d '{ \ 
     "data": { \ 
         "type": "job", \ 
         "attributes": { \ 
             "jobType": "generateUserGroupReport" \ 
         } \ 
    } \ 
 }' 'https://abcd.adobe.com/primeapi/v2/jobs'
```

#### 사용자 정의 역할 감사 보고서 다운로드에 대한 샘플 요청:

```
curl -X POST --header 'Content-Type: application/vnd.api+json;charset=UTF-8' --header 'Accept: application/vnd.api+json' --header 'Authorization: oauth 1234567' -d '{
    "data": {
        "type": "job",
        "attributes": {
            "description": "description of your choice",
            "jobType": "generateCustomRoleAuditReport",
            "payload":{
                 "fromDate": "2020-01-01T18:30:00.000Z",
                 "toDate": "2024-09-31T18:30:00.000Z",
                 "locale":  "en-US"
            }
        }
   }
}
```

### 요청 본문 없음에 대한 오류 메시지

요청 본문은 필수 항목이지만 API에서 제공되지 않는 경우에 대한 특정 오류 메시지를 소개했습니다.

#### 샘플 오류 메시지:

```
{
    "status": "BAD_REQUEST",
    "title": "Generic Error"
}
```

## 보고 개선 사항

관리자는 **관리자** > **보고서** 섹션에서 이러한 보고 변경 내용을 찾을 수 있습니다.

### 학습 성적 증명서 보고서

**[!UICONTROL 학습 성적 증명서]** 보고서에는 두 개의 새 열이 포함됩니다.

* **[!UICONTROL 모듈 ID]**: 각 모듈의 고유 식별자를 표시합니다. 이 새 열은 기존 **[!UICONTROL 모듈]** 열 뒤에 추가되었습니다.
* **[!UICONTROL 강의 인스턴스 ID]**: 각 강의 인스턴스에 대한 고유 식별자를 표시합니다. 이 새 열은 기존 **[!UICONTROL 인스턴스]** 열 뒤에 추가되었습니다.
* **[!UICONTROL 완료 설명]**: 이 열은 관리자가 사용자 완료를 표시할 때 입력한 설명을 캡처합니다. 이 새 열은 보고서 끝에 추가되었습니다.


### 세션 요약 보고서

**[!UICONTROL 세션 요약]** 보고서에는 세 개의 새 열이 포함됩니다.

* **[!UICONTROL 모듈 ID]** 열이 **[!UICONTROL 세션 이름]** 열 앞에 추가되었습니다.
* **[!UICONTROL 세션 ID]** 열이 **[!UICONTROL 세션 이름]** 열 앞에 추가되었습니다.
* **[!UICONTROL 강의 인스턴스 ID]** 열이 **[!UICONTROL 인스턴스 이름]** 열 뒤에 추가되었습니다.
* **[!UICONTROL 완료 횟수]** 열이 **[!UICONTROL 등록 횟수]** 열 뒤에 추가되었습니다.

## 이번 업데이트에서 수정된 문제

* Android 및 iOS 장치에서 파일을 제출하는 동안 활동 모듈에서 비디오를 업로드하는 동안 발생한 오류를 수정했습니다.
* 모바일 앱에서 강의를 여는 문제(웹 버전이 올바르게 작동함)를 해결했습니다.
* Safari에서 작업 지원 및 기타 리소스를 보는 데 발생하는 문제를 해결했습니다.
* 사용자가 모바일 앱에서 작업 지원을 다운로드할 수 없던 문제가
* 패치 사용자 API에 대한 설명서에서 오류를 수정했습니다.
* 강의에서 세션이 삭제되었을 때 주최자가 전자 메일 알림을 받지 못하던 문제를 수정했습니다.
* 모듈이 강의에서 제거되고 다시 게시될 때 주최자가 세션 취소 이메일을 받지 못하는 문제를 수정했습니다.
* 외부 사용자 생성 시 이메일 주소에 특수 문자 &quot;+&quot; 및 &quot;-&quot;를 포함할 수 있도록 지원이 추가되었습니다.
* 사용자 스킬 보고서에 CSV 레코드 값에 큰따옴표가 포함된 경우 Marketo 커넥터 통합 보고서 동기화가 실패하는 문제를 수정했습니다.
* `/skills` 끝점이 관리자 API에 대해 올바른 상태를 반환하지만 학습자 API에 잘못되거나 캐시된 데이터가 일관되게 표시되는 문제를 수정했습니다.
* 계정에 Go1 커넥터가 설정되지 않은 경우 프리미엄 강의의 Go1 온보딩 실패 문제를 해결했습니다.
* 학습자가 이미 학습 경로(LP)를 완료한 경우 마이그레이션을 통해 해당 강의에 액세스할 수 없는 문제를 수정했습니다.
* 사용자의 관리자와 건너뛰기 수준 관리자가 모두 관리자 대신 SU(슈퍼 사용자)로 설정되어 CSV에 포함되지 않은 경우 증분 사용자 CSV가 실패하는 문제를 수정했습니다.
* 대시보드 보고서의 스토어 관리자에 대한 범위 문제를 수정했습니다.
* 초안 강의를 삭제할 때 xapi_iri가 제거되지 않는 문제를 수정했습니다.
* 특정 시나리오에서 고유 LO ID를 추가할 수 없는 문제를 수정했습니다.
* 학습 계획의 포함 가능 속성이 공유 학습 계획에서 올바르게 업데이트되지 않았던 문제를 수정했습니다.
* 학습자 보기에서 학습 경로의 총 표시 기간에 영향을 주는 문제를 해결했습니다.
* 학습자의 계정이 삭제된 후에도 자가 등록 링크를 통해 등록하거나 등록할 수 있도록 허용한 문제를 수정했습니다.
* 강의를 만드는 동안 강의 설명에 링크를 추가할 때 `www`이(가) 제거되는 문제를 수정했습니다.
* 정보 숨기기 및 작업 지원 다운로드가 제대로 작동하지 않던 문제가
* IP ID가 있는 자체 등록 링크를 통해 추가된 새 사용자에 대해 SSO(Single Sign-On)가 작동하지 않던 문제가
* 공지가 삭제된 후 알림 메시지 데이터를 가져올 수 없는 문제를 수정했습니다.
* 이메일로 사용자를 검색할 때 검색 결과가 충분하지 않는 문제를 수정했습니다.

## 시스템 요구 사항

[Adobe Learning Manager 시스템 요구 사항](/help/migrated/system-requirements.md)을 확인하십시오.

## 릴리스 정보

최신 릴리스 업데이트는 [릴리스 정보](/help/migrated/release-note/release-notes.md)를 확인하십시오.

## Adobe Learning Manager의 이전 릴리스

* [2024년 7월 릴리스](/help/migrated/whats-new-july-2024.md)
* [2024년 3월 릴리스](/help/migrated/whats-new-march-2024.md)
