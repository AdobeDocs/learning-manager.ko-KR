---
description: 통합 설정이 Adobe Learning Manager과 서드파티 솔루션을 연결하는 방법에 대해 자세히 알아보기
jcr-language: en_us
title: Adobe Learning Manager의 통합 설정
source-git-commit: 03123dcd8d9066cdfcb0fe97e61acb3df625a23e
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 4%

---


# Adobe Learning Manager의 통합 설정

## 로그인 방법

Adobe Learning Manager은 내부 및 외부 사용자의 안전하고 유연한 액세스를 보장하기 위해 여러 가지 로그인 방법을 제공합니다. 관리자는 조직 요구 사항에 따라 이러한 로그인 방법을 구성할 수 있습니다.

사용 가능한 로그인 방법은 다음과 같습니다.

* Adobe Learning Manager ID
* Adobe ID
* 단일 인증

### 내부 사용자

내부 사용자 섹션에서는 내부 사용자를 위해 특별히 로그인 옵션을 구성할 수 있습니다. 내부 사용자는 Adobe ID 또는 SSO(Single Sign-On)를 사용하여 계정에 액세스할 수 있습니다.

**Adobe ID:**

* 내부 사용자는 자신의 Adobe ID 자격 증명을 사용하여 로그인할 수 있습니다.
* 이미 Adobe 서비스를 사용 중인 조직에 적합합니다.

**SSO(Single Sign-On):**

* 내부 사용자가 조직의 ID 공급자(IdP)를 사용할 수 있도록 SSO를 허용합니다.
* 원활한 로그인 경험을 위한 SAML 2.0 기반 인증을 지원합니다.

내부 사용자에 대한 SSO 로그인을 허용하려면 &#39;싱글 사인온(SSO) 다중 로그인 활성화&#39;를 선택하고 SSO 구성을 시작하십시오.

Adobe Learning Manager의 **[!UICONTROL SSO 활성 필드]**&#x200B;는 SSO(Single Sign-On) 구성을 특정 사용자 특성 또는 그룹에 매핑하는 데 사용됩니다. 조직, 위치 또는 기타 기준에 따라 내부 사용자에 대한 다중 SSO 설정을 활성화하도록 이 필드를 구성할 수 있습니다.

### 외부 사용자

Adobe Learning Manager의 외부 사용자 섹션에서는 Adobe Learning Manager 계정에 대한 제한된 액세스가 필요한 파트너 또는 에이전시와 같은 외부 학습자를 관리할 수 있습니다. 이 섹션에서는 등록 프로필을 만들고, 외부 사용자 그룹을 관리하고, 외부 학습자별 설정을 구성하는 도구를 제공합니다.

외부 사용자는 다음을 사용하여 로그인할 수 있습니다.

* Adobe ID: 외부 사용자는 자신의 Adobe ID 자격 증명을 사용하여 로그인할 수 있습니다.
* SSO(Single Sign-On): 관리자가 구성한 경우 외부 사용자는 SSO를 통해 로그인할 수 있습니다.
* Adobe Learning Manager ID: 외부 사용자는 Learning Manager 사용자 이름 및 암호를 만들어 플랫폼에 액세스할 수 있습니다.

**주요 사항:**

* 외부 사용자에 대해 하나 이상의 로그인 방법을 활성화할 수 있습니다.
* Adobe Learning Manager ID를 선택한 경우 외부 사용자는 자신의 자격 증명을 만들어야 합니다.
* 조직의 필요에 따라 외부 사용자에 대해 SSO를 구성할 수 있습니다.

### Adobe Learning Manager의 SSO 구성

Adobe Learning Manager은 SSO(Single Sign-On)를 지원하여 사용자가 한 번 인증하고 여러 애플리케이션에 액세스할 수 있도록 합니다. 관리자는 SAML 2.0 기반 공급자를 통해 내부 및 외부 사용자 모두에 대해 SSO를 구성할 수 있습니다.

자세한 내용은 [Adobe Learning Manager의 SSO 로그인](/help/migrated/administrators/feature-summary/multiple-sso-logins.md)을 참조하세요.

>[!NOTE]
>
>* 최대 20개의 SSO 구성을 계정에 추가할 수 있습니다.
>* SAML 2.0 기반 SSO 공급자에 대한 지원은 Adobe 지원에 문의하십시오.

## 데이터 소스

데이터 소스를 통해 사용자 또는 통합 책임자는 사용자 및 학습 데이터를 가져오고 동기화하기 위해 외부 시스템을 통합할 수 있습니다. 이 기능은 HRMS, Salesforce, FTP 등과 같은 시스템과 원활한 데이터 관리 및 동기화를 보장합니다.

**데이터 원본 형식의 예**

* **FTP 커넥터**: FTP 기반 데이터 원본을 사용하면 조직에서 보안 파일 전송 프로토콜을 통해 사용자 데이터 파일을 Adobe Learning Manager에 직접 업로드할 수 있습니다. 이러한 연결은 사용자 정보, 강의 등록 및 기타 대량 데이터 작업을 일괄 가져올 때 특히 유용합니다.
* **서드파티 통합**: Adobe Learning Manager은 사전 설치된 커넥터를 통해 다양한 기업 시스템과의 통합을 지원합니다. 이러한 통합에는 HR 관리 시스템, 고객 관계 관리 플랫폼 및 기타 학습 관리 시스템이 포함될 수 있습니다.
*** Salesforce 통합**: Salesforce 커넥터를 사용하여 Salesforce와 Adobe Learning Manager 간에 사용자 데이터, 과정 정보 및 학습 기록을 직접 동기화할 수 있습니다.

자세한 내용은 [Adobe Learning Manager의 커넥터](/help/migrated/integration-admin/feature-summary/connectors.md)를 참조하십시오.

## 피어 계정

Adobe Learning Manager의 피어 계정을 사용하면 구입한 시트를 공유하고 연결된 계정 전체의 보고서를 볼 수 있습니다. 이 기능은 다른 계정 간에 공동 작업하거나 리소스를 공유해야 하는 조직에 유용합니다.

자세한 내용은 Adobe Learning Manager의 [피어 계정](/help/migrated/administrators/feature-summary/peer-account.md)을 참조하세요.





