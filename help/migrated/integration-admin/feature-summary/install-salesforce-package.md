---
jcr-language: en_us
title: Salesforce 패키지 설치
description: Learning Manager는 Salesforce 앱 패키지를 제공합니다. SFDC에 Salesforce 앱 패키지를 설치하고 구성한 영업 직원은 SFDC 포털에서 교육 활동을 수행할 수 있습니다. 이 앱을 설치한 SFDC 사용자는 새로운 교육 과정을 탐구하고, 권장 사항을 확인하며, SFDC 포털에서 바로 이와 같은 컨텐츠를 확인할 수 있습니다. 또한 사용자는 SFDC 포털 내의 앱 내에서 바로 마스트헤드 형태로 관리자가 보낸 공지 사항을 받습니다.
contentowner: saghosh
exl-id: 2b1c32e7-81af-4c13-a2bd-66684cde084e
source-git-commit: fb946ae98dce45156e2f4c1cf992319405403ea9
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 47%

---

# Salesforce 패키지 설치

## 개요

Learning Manager는 Salesforce 앱 패키지를 제공합니다. SFDC에 Salesforce 앱 패키지를 설치하고 구성한 영업 직원은 SFDC 포털에서 교육 활동을 수행할 수 있습니다. 이 앱을 설치한 SFDC 사용자는 새로운 교육 과정을 탐구하고, 권장 사항을 확인하며, SFDC 포털에서 바로 이와 같은 컨텐츠를 확인할 수 있습니다. 또한 사용자는 SFDC 포털 내의 앱 내에서 바로 마스트헤드 형태로 관리자가 보낸 공지 사항을 받습니다.

### Learning Manager 앱에서 설정

1. Learning Manager 책임자 계정에 통합 책임자 권한으로 로그인합니다.
1. Applications(애플리케이션&#x200B;]**> Featured Apps(**[!UICONTROL &#x200B;추천 앱&#x200B;]**)를 클릭합니다**[!UICONTROL .
1. Salesforce ]**를 클릭합니다**[!UICONTROL .
1. Salesforce 앱 페이지에서 설명에 언급된 응용 프로그램 ID(클라이언트 ID라고도 함) 및 클라이언트 암호를 기록해 둡니다.
1. 승인을&#x200B;]**클릭하면**[!UICONTROL &#x200B;앱이 성공적으로 승인되어야 합니다.
1. Developer Resources ]**>**[!UICONTROL  Access Tokens for Testing and Development(테스트 및 개발을&#x200B;]**위한 액세스 토큰)를 클릭합니다**[!UICONTROL .
1. OAuth 코드 가져오기 섹션에서 클라이언트 ID 및 범위를 admin:read,admin:write로 설정해야 합니다. 제출을&#x200B;]**클릭합니다**[!UICONTROL .
1. 새로 고침 토큰 얻기 섹션에 클라이언트 ID와 클라이언트 비밀번호를 입력합니다. Submit(제출&#x200B;]**)을 클릭하고**[!UICONTROL &#x200B;새로 고침 토큰을 기록해 둡니다.

### Salesforce 앱에서 계정 개설

1. Salesforce 등록 페이지에서 계정을 개설할 수 있습니다. Developer 또는 Enterprise Edition에서 Salesforce 계정을 만들어야 합니다.  [개발자 등록 URL](https://developer.salesforce.com/signup)입니다. Learning Manager에 사용한 이메일 ID를 사용하여 Salesforce에 등록해야 합니다.
1. 확인 이메일을 통해 사용자의 계정을 확인합니다.
1. 비밀번호를 등록하고 Salesforce에 로그인합니다.
1. 로그인 후 Salesforce URL을 기록해 둡니다(예: site.lightning.force.com).

### Learning Manager 패키지 설치

Captivate Prime 패키지를 설치하려면 먼저 Salesforce의 기존 패키지를 삭제해야 합니다. 기존 패키지를 제거하기 전에 아래에 보이는 것처럼 설정을 활성화해야 합니다. 이 설정을 적용하지 않으면 Captivate Prime 패키지를 설치할 수 없습니다.

![](assets/uninstall-package.png)

*Learning Manager 패키지 설치*

>[!NOTE]
>
>Adobe Learning Manager 앱은 Salesforce Lightning 보기에서만 지원됩니다.

1. Learning Manager 패키지 URL](https://test.salesforce.com/packaging/installPackage.apexp?p0=04tDb000000LRvP)을 [시작합니다.
1. 로그인&#x200B;**페이지에서 [사용자 지정 도메인]** 사용]을 **클릭합니다**[!UICONTROL .

1. 패키지 URL을 입력하고 계속&#x200B;]**을 클릭합니다**[!UICONTROL . 설치 페이지에 관리자 전용으로 설치 옵션이 선택되어 있어야 합니다. 이 옵션을 변경하지 마십시오.
1. Ins tall **을클릭합니다**. 패키지가 설치되면 [완료&#x200B;]**]를 클릭합니다**[!UICONTROL . &#39;설치된 패키지&#39; 페이지로 이동하면 설치된 Adobe Learning Manager 패키지를 확인할 수 있습니다.

1. &#39;설정&#39; 옆에 있는 &#39;앱 시작 관리자&#39;로 이동하여 &#39;Adobe Learning Manager&#39;를 검색합니다.
1. 앱을 구성하려면 구성을&#x200B;]**클릭합니다**[!UICONTROL .
1. 새로 만들기를&#x200B;]**클릭하고**[!UICONTROL &#x200B;다음 세부 정보를 추가합니다.

   * **Config:** 원하는 구성 이름을 입력합니다.
   * **ClientID**: 첫 번째 섹션에서 가져온 값을 입력합니다.
   * **ClientSecret:** 첫 번째 섹션에서 가져온 값을 입력합니다.
   * **RefreshToken:** 첫 번째 섹션에서 가져온 값을 입력합니다.
   * **LearningManagerBaseURL:** Learning Manager가 호스팅되는 사이트의 URL입니다.
   * **리디렉션 비활성화:** Learning Manager에서 학습자 홈페이지로의 리디렉션을 비활성화합니다.

>[!NOTE]
>
>단일 구성만 만들 수 있습니다. 다른 구성을 추가하려고 하면 오류 메시지가 표시됩니다. 구성은 Salesforce 계정을 학습자 계정과 매핑합니다.

### 원격 사이트 설정 추가

1. 페이지의 오른쪽 상단에서 [설정&#x200B;]**]을 클릭합니다**[!UICONTROL .
1. 빠른 찾기&#x200B;**에서**&#x200B;원격 사이트 설정을 검색합니다.
1. 새 원격 사이트를&#x200B;]**클릭합니다**[!UICONTROL .
1. 다음 세부 정보를 입력합니다.

   1. **원격 사이트 이름:** 원하는 사이트 이름을 입력합니다.
   1. **원격 사이트 URL:** Learning Manager가 호스팅되는 사이트의 URL입니다.

1. Learning Manager를 실행합니다.

### Salesforce 신뢰할 수 있는 URL에 Adobe 도메인 추가

Adobe 도메인을 신뢰할 수 있는 URL에 추가하려면 다음 단계를 따르십시오.

1. Salesforce 콘솔에서 설치&#x200B;]**>**[!UICONTROL &#x200B;빠른 찾기&#x200B;]**로**[!UICONTROL &#x200B;이동합니다.
1. 신뢰할 수 있는 URL ]**을**[!UICONTROL &#x200B;검색하고 새 신뢰할 수 있는 URL ]**을 선택합니다**[!UICONTROL .
1. API 이름&#x200B;]**필드에 이름을**[!UICONTROL &#x200B;입력합니다.
1. URL 필드에 입력합니다 `*.adobe.com` .
1. CSP 지시&#x200B;**문에서**&#x200B;모든 확인란을 선택하고 변경 사항을 저장합니다.
1. Salesforce 앱의 새로 고침 토큰을 편집하고 저장합니다.
1. Salesforce 앱을 다시 실행합니다.

### Learning Manager 앱 알림 활성화

1. 오른쪽 상단에서 [설정&#x200B;**]을 클릭합니다**.
1. &#39;사용자 정의 알림&#39;을 검색합니다.
1. New(새로 만들기&#x200B;]**)를 클릭합니다**[!UICONTROL .
1. 다음 세부 사항을 입력합니다.

   1. **사용자 지정 알림 이름:** LearningManagerNotification
   1. **API 이름:** LearningManagerNotification

1. 지원되는 채널로 데스크톱&#x200B;**및**&#x200B;모바일&#x200B;**을 모두**&#x200B;선택합니다.

1. **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
1. 모바일 장치용 푸시 알림을 활성화하려면 다음 단계를 따르십시오.

   1. 휴대폰에 Salesforce 모바일 앱을 설치합니다.
   1. 자격 증명을 사용하여 앱에 로그인합니다.
   1. Setup **>** Notification Delivery Settings **로**&#x200B;이동합니다.
   1. iOS 및 Android용 Salesforce를 추가합니다.

### Salesforce에서 Learning Manager 제거

1. Salesforce 앱에서 설치된 패키지로 이동합니다.
1. 제거&#x200B;]**를 클릭합니다**[!UICONTROL .

## Salesforce 사용자용 Learning Manager 구성

Learning Manager 앱은 Salesforce 계정에 있는 사용자도 사용할 수 있습니다. Salesforce 책임자는 프로필을 기반으로 사용자를 추가할 수 있습니다. Salesforce 프로필은 Learning Manager의 프로필과 유사합니다. 예를 들어, 책임자, 통합 책임자, 강사 등입니다. Salesforce 책임자는 또한 사용자 정의 프로필을 만들 수 있습니다.

### 프로필

Salesforce 책임자는 프로필을 사용자에게 할당하거나 사용자 정의 프로필을 만들 수 있습니다.

>[!NOTE]
>
>사용자는 Salesforce와 Learning Manager 모두에 있어야 합니다.

![](assets/create-profile.png)

*학습자에게 프로필 할당*

학습자를 추가할 경우에는 학습자에게 특정 프로필을 할당해야 합니다. 그런 다음 해당 프로필로 이동하여 필요한 액세스 권한을 부여합니다.

학습자가 Learning Manager 앱을 볼 수 있도록 하려면 모든 학습자가 앱을 사용할 수 있도록 설정해야 합니다.

다음 단계는 Learning Manager 앱에 액세스 권한을 제공하는 것입니다.

![](assets/permission-set.png)

*Learning Manager 앱에 접근할 수 있는 권한 추가*

패키지를 설치하면 새 권한 세트인 **Adobe Learning Manager User**&#x200B;가 생성됩니다. 권한 집합으로 이동한 다음 사용자를 추가합니다.

사용자를 선택하고 그에 따라 권한을 할당합니다. 학습자는 이제 Learning Manager 앱에 액세스할 수 있습니다.

이제 사용자의 표준 프로필 같은 프로필을 선택하고 프로필을 클릭합니다. 편집을&#x200B;]**클릭하고****[!UICONTROL 사용자 정의 앱 설정** 섹션에서 Adobe Learning Manager **확인란을**&#x200B;활성화합니다. 그러면 사용자가 앱에 액세스할 수 있습니다.

**사용자 정의 탭 설정** 섹션의 **학습자 홈** 드롭다운 목록에서 **[!UICONTROL 기본값]** 옵션을 선택합니다.

반드시 모든 프로필에서 앱을 볼 수 있도록 해야 합니다.

저장을&#x200B;]**클릭하면**[!UICONTROL &#x200B;모든 프로필에 속한 학습자가 Learning Manager 앱에 액세스합니다.
