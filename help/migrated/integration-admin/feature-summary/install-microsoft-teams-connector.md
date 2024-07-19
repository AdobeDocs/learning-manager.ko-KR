---
description: Adobe Learning Manager에 Microsoft Teams 커넥터 설치
jcr-language: en_us
title: Adobe Learning Manager에 Microsoft Teams 커넥터 설치
contentowner: saghosh
exl-id: 68092187-ac69-4727-a3dc-f3047a1e164d
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '1258'
ht-degree: 24%

---

# Adobe Learning Manager에 Microsoft Teams 커넥터 설치

## 개요

Microsoft® Teams®는 문서 공유, 온라인 회의 및 기타 비즈니스 통신 기능을 모두 지원하는 지속적인 채팅 방식의 협업 플랫폼입니다.

Adobe Learning Manager은 Microsoft Teams 회의를 Learning Manager와 통합하는 데 사용할 수 있는 가상 강의실 커넥터를 사용합니다.

Microsoft Teams 커넥터는 Learning Manager와 Microsoft Teams 시스템을 연결하여 자동으로 가상 회의 동기화를 활성화합니다. 다음 목록에서 Microsoft Teams 커넥터 기능을 설명합니다.

**Microsoft Teams을 사용하여 가상 세션 설정**

이 커넥터는 Adobe Learning Manager 계정을 Microsoft Teams 계정과 통합하는 데 도움을 줍니다. 통합되었으면 커넥터를 사용하여 Learning Manager의 작성자는 Microsoft Teams를 Learning Manager에서 작성된 가상 강의실 모듈의 기술 서비스 제공자로 사용할 수 있습니다.

**Microsoft Teams이 가상 수업에 입장할 때 학습자를 인증할 수 있도록 허용**

이 커넥터는 회의를 생성하는 동안 Learning Manager에서 Microsoft Teams 회의 주최자를 설정할 때 유용합니다. 회의 주최자는 로비를 관리하여 회의 입장을 제한하거나 허용하며 Microsoft Teams에서 제공하는 다른 회의 옵션도 제어할 수 있습니다.

**자동화된 사용자 완료 동기화 사용**

자동화된 Microsoft Teams 완료 동기화 프로세스를 통해 Learning Manager 책임자는 완료 기록과 사용자 회의 녹화 URL을 자동으로 가져올 수 있습니다.

## Microsoft Teams의 역할

여러 참가자가 있는 회의를 주최하는 경우 참가자가 회의에서 무엇을 할 수 있는지 알 수 있도록 각 참가자에게 역할을 할당할 수 있습니다.

**발표자** 및 **참석자** 역할 중에서 선택할 수 있습니다.

자세한 내용은 [Teams 회의에서의 역할 - Microsoft](https://support.microsoft.com/ko-kr/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)을 참조하세요.

## Microsoft Teams 커넥터 설정

>[!NOTE]
>
>아래에 &lt;Developer/Optional>로 표시된 항목은 선택 사항이며 사용자에게 제작 테넌트가 없는 경우 대부분 Microsoft으로 평가판/개발자 테넌트를 설정할 때 사용됩니다. 이는 팀 책임자가 대부분 이미 수행했으므로 선택 사항입니다.

## 개발자 E5 Microsoft 계정 만들기 &lt;Developer/Optional>

Office 365 E3 또는 Office 365 E5가 있는 경우 Microsoft Teams 커넥터에 액세스할 수 있습니다. Office 365 E5를 사용하는 것이 좋습니다.

* [Microsoft 플랜 페이지](https://www.microsoft.com/en-in/microsoft-365/enterprise/compare-office-365-plans?&amp;ef_id=CjwKCAjw8cCGBhB6EiwAgORey9Tjrae-dyAsBrzvXdVJ5WCcoQ55wySzUBMoo-EkPt7CoIqAtcWc0xoC9RcQAvD_BwE:G:s&amp;OCID=AID2100137_SEM_CjwKCAjw8cCGBhB6EiwAgORey9Tjrae-dyAsBrzvXdVJ5WCcoQ55wySzUBMoo-EkPt7CoIqAtcWc0xoC9RcQAvD_BwE:G:s&amp;lnkd=Google_O365SMB_Brand&amp;gclid=CjwKCAjw8cCGBhB6EiwAgORey9Tjrae-dyAsBrzvXdVJ5WCcoQ55wySzUBMoo-EkPt7CoIqAtcWc0xoC9RcQAvD_BwE) 를 방문하십시오. 웹페이지에서 E3 또는 E5 계정을 구매하거나 무료 평가판을 클릭합니다.

* 필수 정보를 제공하여 계정을 만듭니다.

>[!NOTE]
>
>계정은 `<username>@<company name>.onmicrosoft.com` 형식을 사용해야 합니다.

## Microsoft Teams 커넥터용 응용 프로그램 생성

1. [Microsoft Azure® 포털](https://portal.azure.com/)을 방문하세요.
1. 이전 섹션에서 생성한 Microsoft E5 계정으로 로그인합니다.
1. **Azure Active Directory**&#x200B;을(를) 검색합니다.
1. **[!UICONTROL 앱 등록]**&#x200B;을 클릭합니다.
1. **[!UICONTROL 새 등록]**&#x200B;을 클릭하고 다음 세부 정보를 입력한 다음 응용 프로그램을 등록합니다.

   1. **이름** - 원하는 이름입니다.
   1. **지원되는 계정 유형** - 모든 조직 디렉터리의 계정(모든 Azure Active Directory - 다중 테넌트)입니다.
   1. **리디렉션 URI(선택 사항)** - 회신 URL을 가리키는 선택 사항 필드입니다.

1. **필수** 열에서 통합 중 추가로 사용되는 다음 ID를 적어둡니다.

   1. **응용 프로그램(클라이언트) ID**
   1. **디렉터리(테넌트) ID**

1. 클라이언트 자격 증명을 검색하고 **[!UICONTROL 인증서 또는 시크릿 추가]**&#x200B;를 클릭합니다.
1. **[!UICONTROL 새 클라이언트 암호]**&#x200B;를 클릭하고 다음 세부 정보를 추가합니다.

   1. **설명** - 이름을 입력하십시오.
   1. **만료** - 값을 설정합니다(권장 값은 24개월입니다. 이전 자격 증명이 만료되면 새 클라이언트 자격 증명이 생성되었는지 확인합니다).

통합 중 추가로 사용되는 클라이언트 시크릿을 기록합니다.

## Microsoft Teams 커넥터에 대한 액세스 권한 받기

1. [Microsoft Azure Portal](https://portal.azure.com/)을 방문합니다.
1. 이전에 생성한 Microsoft E5로 로그인합니다.
1. **Azure Active Directory**&#x200B;을(를) 검색합니다.
1. **[!UICONTROL 앱 등록]**&#x200B;을 클릭합니다.
1. 이전 섹션에서 생성한 앱을 클릭합니다.
1. **[!UICONTROL API 권한]**&#x200B;을 클릭합니다.
1. **[!UICONTROL 권한 추가]**&#x200B;를 클릭합니다.
1. **[!UICONTROL Microsoft 그래프]** > **[!UICONTROL 응용 프로그램 권한]**&#x200B;을 선택하고 다음 권한을 추가합니다.

   1. Chat.Read.All
   1. Directory.Read.All
   1. OnlineMeetingArtifact.Read.All
   1. OnlineMeetings.Read.All
   1. OnlineMeetings.ReadWrite.All
   1. User.Read.All

1. **[!UICONTROL Adobe에 대한 관리자 액세스 권한 부여]**&#x200B;를 클릭합니다.
1. **[!UICONTROL 앱 역할]** > **[!UICONTROL 앱 역할 만들기]**&#x200B;를 클릭합니다.
1. 다음 값을 입력합니다.

   1. **표시 이름** - API/권한 이름(예: Calendars.ReadWrite)이 표시되는 이름입니다.

   1. **허용된 구성원 유형** - 사용자와 응용 프로그램(사용자/그룹 + 응용 프로그램)을 모두 지정합니다.

   1. **값** - API/권한 이름(예: Calendars.ReadWrite)이 표시되는 이름입니다.

   1. **설명** - API/권한 이름(예: Calendars.ReadWrite)이 표시되는 이름입니다.

   1. **이 앱 역할을 사용하시겠습니까?** - 이 확인란을 선택합니다.

1. 추가된 API/권한 9개 모두 이전 단계를 반복합니다.

## PowerShell 스크립트를 사용하여 액세스 정책 구성

PowerShell 스크립트를 실행하여 Microsoft Teams 커넥터에 대한 응용 프로그램 액세스 정책을 구성하려면 이 [문서](https://docs.microsoft.com/ko-kr/graph/cloud-communication-online-meeting-application-access-policy)에 설명된 절차를 따르십시오.

이 절차를 통해 커넥터가 Microsoft Teams 온라인 회의에 액세스할 수 있습니다.

>[!NOTE]
>
>위 문서에서 선택 사항인 5단계도 실행하여 활성 사용자에게 Learning Manager 작성자 앱에서 주최자 역할을 부여할 수 있도록 합니다. 이 단계를 실행하지 않으면 사용자는 주최자가 되기 위해 필요한 액세스 권한이 없으므로 회의 생성에 실패합니다(Microsoft API는 주최자를 Teams 회의의 생성자로 간주).

## Learning Manager에서 Microsoft Teams 커넥터 설정

1. Learning Manager에 통합 책임자로 로그인합니다.

1. 커넥터 페이지에서 Microsoft Teams 커넥터를 선택하고 **[!UICONTROL 연결]**&#x200B;을 클릭합니다.

1. 다음 값을 입력합니다.

   1. **연결 이름** - 작성자가 세션을 만드는 동안 표시할 이름을 지정합니다.

   1. **Microsoft Teams 테넌트 ID** - 앞서 결정된 값을 입력합니다.

   1. **Microsoft Teams 클라이언트 ID** - 앞서 결정된 값을 입력하십시오.

   1. **Microsoft Teams 클라이언트 암호** - 앞서 결정된 값을 입력하십시오.

   1. **Microsoft Teams 관리자 사용자 전자 메일** - 기본 주최자 전자 메일을 입력하십시오. Learning Manager 작성자 앱에 주최자가 명시적으로 선택되지 않으면 이 사용자(일반적으로 서비스 사용자)는 회의 생성자가 됩니다.

## 사용자에게 라이선스를 할당합니다 &lt;Developer/Optional>

1. [https://admin.microsoft.com/#/homepage](https://admin.microsoft.com/#/homepage)을(를) 방문합니다.
1. **[!UICONTROL 사용자]** > **[!UICONTROL 활성 사용자]**&#x200B;를 클릭합니다.
1. Microsoft Teams 액세스 권한을 제공하려는 사용자의 **[!UICONTROL 사용자용 추가 작업]**&#x200B;을 클릭합니다.
1. **[!UICONTROL 제품 라이선스 관리]**&#x200B;를 클릭합니다.
1. 오디오 회의 없이 Office 365 E5 라이선스를 활성화합니다.

## 세션 기록

세션 기록에 사용되는 API는 보호된 API입니다. API에 액세스하려면 Microsoft에 액세스를 요청해야 합니다. 자세한 내용은 이 [문서](https://docs.microsoft.com/ko-kr/graph/teams-protected-apis)를 참조하세요.

이 문서에서는

*&quot;보호된 API에 대한 액세스를 요청하려면 다음 [요청 양식](https://aka.ms/teamsgraph/requestaccess)을 작성하십시오. 매주 수요일에 액세스 요청을 검토하며 매주 금요일에 승인을 배포합니다. 미국의 주요 공휴일이 있는 주간은 예외이며 해당 주간에 제출된 사항은 공휴일이 끝난 그다음 주에 처리됩니다. 요청이 승인되었는지 확인하려면 다음 주 월요일에 응용 프로그램 액세스를 테스트하십시오.&quot;*

학습자의 경우 기록 URL이 VC 강의 개요 페이지에 표시됩니다.

강의를 완료한 지 30분이 지나면 학습자의 출석이 표시됩니다.

## 자주 묻는 질문

+++주최자와 발표자는 누구입니까?

Microsoft Teams이 지원하는 다양한 역할과 기능은 Microsoft의 [설명서](https://support.microsoft.com/ko-kr/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)를 참조하십시오.

+++

+++주최자는 Learning Manager와 Microsoft Teams 모두에 등록된 사용자만 될 수 있습니까?

예, 주최자는 Learning Manager와 Microsoft Teams에 모두 등록된 사용자여야 합니다. 또한 주최자는 통합 책임자 앱에서 구성된 동일한 Microsoft 테넌트의 일부여야 합니다.

+++

+++발표자는 Learning Manager와 Microsoft Teams 모두에 등록된 사용자만 될 수 있습니까?

예, 발표자는 Learning Manager와 Microsoft Teams 모두의 일부여야 합니다. 발표자는 Azure Active Directory ID가 있어야 합니다(주최자와 동일한 테넌트 또는 다른 테넌트의 일부일 수 있음). 또한 익명의 사용자(Active Directory에 속하지 않고 사용자 이름으로 로그인하는 사용자)도 회의 중 주최자/기존 발표자가 발표자로 임명할 수 있습니다.

+++

+++Microsoft Teams은 회의, 웨비나 및 라이브 이벤트를 포함합니다. Teams 커넥터는 어떤 것을 지원합니까?

현재 Teams 커넥터는 Microsoft Teams 회의만 지원합니다. 자세한 내용은 이 [문서](https://docs.microsoft.com/ko-kr/microsoftteams/quick-start-meetings-live-events)를 참조하세요.

+++
