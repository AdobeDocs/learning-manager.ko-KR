---
jcr-language: en_us
title: Salesforce용 Learning Manager 앱
description: Salesforce는 영업 및 마케팅 팀 중에서 가장 인기 있는 CRM 솔루션 중 하나입니다. Salesforce의 Adobe Learning Manager 앱을 사용하여 사용자가 Salesforce 인터페이스에서 학습 콘텐츠에 액세스하도록 허용할 수 있습니다. 사용자는 Salesforce에서 강의, 학습 프로그램, 작업 지원 등 할당된 학습 콘텐트에 액세스할 수 있습니다. 사용자는 등록에 대한 알림 및 책임자의 공지를 받을 수도 있습니다.
contentowner: jayakarr
exl-id: 2efdf01e-43fb-4377-9334-2727c5358c76
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 57%

---

# Salesforce용 Learning Manager 앱

## 개요 {#overview}

Salesforce™은 영업 및 마케팅 팀 사이에서 가장 인기 있는 CRM 솔루션 중 하나입니다. Salesforce의 Adobe Learning Manager 앱을 사용하여 사용자가 Salesforce 인터페이스에서 학습 콘텐츠에 액세스하도록 허용할 수 있습니다. 사용자는 Salesforce에서 강의, 학습 프로그램, 작업 지원 등 할당된 학습 콘텐트에 액세스할 수 있습니다. 사용자는 등록에 대한 알림 및 책임자의 공지를 받을 수도 있습니다.

현재 Salesforce 앱을 사용할 수 없습니다. Salesforce App Exchange에서 승인 보류 중입니다. 앱 베타 버전 미리 보기에 관심이 있다면 계정 관리자 또는 Learning Manager 지원팀에 문의하십시오.

## 설치 및 설정 {#installationandsetup}

다음 단계를 따라서 Learning Manager Salesforce 앱 설치 및 설정 방법을 알아보십시오.

### 필수 구성 요소 {#prerequisites}

1. 조직의 통합 책임자가 Salesforce 앱을 승인해야 합니다. 통합 책임자 역할을 위한 Learning Manager 응용 프로그램의 특별 응용 프로그램 섹션에서 이 앱을 찾을 수 있습니다.
1. 조직의 Salesforce 계정에 액세스합니다. 앱을 설치해야 합니다. 일반적으로 조직의 Salesforce 책임자는 해당 앱을 설치하는 사람입니다. 귀하가 Learning Manager 통합 책임자이며 Salesforce 계정이 없는 경우 조직의 Salesforce 책임자에게 문의하십시오.

### 설치 단계 {#installationsteps}

1. 계정 관리자 또는 고객 성공 관리자에게 Learning Manager 계정 ID를 제공하여 이 앱의 사용을 허용해 달라고 요청합니다. 또한 설치 가능한 Salesforce용 Learning Manager 학습자 앱 패키지 CSM을 요청합니다.

1. 통합 책임자로 Learning Manager 계정에 로그인한 다음 계정에 Salesforce 앱이 활성화되었는지 확인합니다.

1. Salesforce 계정에 Learning Manager 앱을 설치하려면, 계정 관리자 또는 고객 성공 관리자로부터 제공받은 설치 가능한 패키지를 사용하십시오. 이 앱을 설치할 때 Salesforce 계정에 대한 관리자 권한이 있어야 합니다.

1. 스냅숏에 표시된 대로 적절한 옵션을 선택하고 **[!UICONTROL 설치]**&#x200B;를 클릭하십시오.

   ![](assets/install-options.png)

   *관리자 전용 설치 옵션을 선택합니다*

   **특정 프로필용으로 설치**&#x200B;를 선택한 경우 목록에서 하나 이상의 프로필을 선택하십시오.

1. 표시되는 팝업에서 **[!UICONTROL 계속]**&#x200B;을 클릭하여 서드파티 액세스를 확인합니다.

   앱이 성공적으로 설치되었다는 확인 메시지가 나타납니다. **완료**&#x200B;를 클릭합니다.

## 홈페이지에 알림 요소 추가 {#addnotificationcomponenttothehomepage}

Learning Manager 팀은 Salesforce 책임자가 홈페이지 레이아웃에 Learning Manager 알림 요소를 추가할 것을 권장합니다. 해당 요소는 Salesforce 사용자가 사용자 앱의 컨텍스트에 있지 않을 때도 Learning Manager에서 할당에 대한 알림 및 기타 공지를 받을 수 있게 해줍니다.

홈페이지 레이아웃에 Learning Manager 알림 요소를 추가하려면 다음 단계를 따르십시오.

1. 오른쪽 상단에서 **[!UICONTROL 설정]**&#x200B;을 클릭합니다. 홈 페이지 레이아웃 옵션은 아래 스냅샷과 같이 왼쪽 창에 나타납니다.

   ![](assets/homepage-component.png)

   *홈 페이지 레이아웃 선택*

1. 원하는 레이아웃을 선택하고 **[!UICONTROL 편집]**&#x200B;을 클릭하세요.
1. 페이지에 나타나는 Adobe Learning Manager 알림 옵션을 선택하고 **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. 왼쪽 창에 나타나는 구성 요소의 순서를 선택하고 미리 본 다음 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.

Learning Manager 앱에 로그인하여 학습자로 Salesforce를 사용하는 방법을 알아보려면, [Salesforce 앱 도움말](../../learners/feature-summary/sfdc-app.md)을 참조하십시오.
