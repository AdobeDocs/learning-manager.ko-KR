---
description: Adobe Learning Manager은 다중 SSO 구성을 통해 내부 및 외부 사용자에게 여러 가지 로그인 방식을 지원할 수 있습니다.
title: SSO 다중 로그인
contentowner: saghosh
exl-id: 398816e8-a144-459b-8c39-6517ce4573b4
source-git-commit: f964dd3f1adeadb76f4843c9af229ce5f09afde1
workflow-type: tm+mt
source-wordcount: '794'
ht-degree: 38%

---

# SSO 다중 로그인 {#multiple-sso-logins}

책임자는 내부 및 외부 사용자를 대상으로 여러 가지 로그인 방식을 구성할 수 있습니다. Adobe Learning Manager는 책임자가 필요와 사용 사례에 따라 로그인 방법을 구성할 수 있는 SSO 다중 로그인을 지원합니다.

따라서 책임자가 위치, 조직 등에 따라 다양한 사용자 그룹을 대상으로 각기 다른 SSO를 구성할 수 있습니다.

최대 20개의 SSO 구성을 계정에 추가할 수 있습니다. 내부 및 외부 사용자 모두에게 SSO를 설정하는 데 사용할 수 있습니다.

>[!NOTE]
>
>다중 SSO를 활성화하면 자가 등록 프로필에서 값 또는 사용자 그룹을 선택할 수 있습니다. 값을 선택하면 사용자가 0인 사용자 그룹이 생성됩니다. 해당 사용자 그룹에는 사용자가 없습니다. 다음 CSV를 가져오면 이 사용자 그룹이 제거됩니다.

## SSO 다중 로그인 활성화

SSO 다중 로그인을 활성화하려면 **설정** > **로그인 방법**&#x200B;을 선택하십시오.

설정 페이지에서 내부 또는 외부 사용자에 대해 &#39;**[!UICONTROL 다중 SSO(Single Sign-On) 활성화]**&#39; 확인란을 선택합니다.

다중 SSO가 활성화되면 &#39;기본 로그인 방법&#39;으로 선택한 로그인 방법이 SSO 구성에 연결되지 않은 사용자 그룹/프로필의 기본 로그인 유형이 됩니다. Adobe ID, SSO 또는 ALM ID(외부 사용자)을 기본적인 로그인 방식으로 설정할 수 있습니다.

>[!NOTE]
>
>필요한 권한을 가진 관리자 및 사용자 정의 관리자는 다음 단계를 수행할 수 있습니다.

SSO를 구성하려면 다음 단계를 따르십시오.

1. &#39;싱글 사인온(SSO) 구성&#39;을 클릭합니다.
1. &#39;새 SSO 구성 추가&#39;를 클릭합니다.\
   ![](assets/sso.png)
1. &#39;SSO 구성&#39; 대화 상자에서 다음을 추가합니다.

   * SSO의 이름을 입력합니다.
   * SSO-IDP 시작 또는 SP 시작 유형을 선택합니다.

      * IDP 시작을 선택한 경우 IDP URL을 입력합니다. 이 URL은 응용 프로그램의 고유 식별자로 사용되는데, URL 정보는 IDP 서비스 제공자를 통해 입수할 수 있습니다. 모든 Adobe Learning Manager 사용자가 로그인한 후 리디렉션되는 URL입니다.
      * IDP 공급자로부터 입수한 IDP 메타데이터 XML을 업로드합니다. 이 파일에는 Adobe Learning Manager가 SAML 검증 요청을 수락하는 데 사용할 수 있는 IdP에 관한 정보가 포함되어 있습니다.
      * SP 시작을 선택한 경우 엔티티 ID를 입력합니다. 엔터티 ID는 서비스 공급자(SP)가 제공하는 URL입니다.
      * SP 로그인 URL을 입력합니다. 이 URL은 사용자가 응용 프로그램에 로그인하는 데 사용됩니다.

1. SSO 구성이 목록에 추가됩니다.

## 내부 사용자용 SSO 설정

### CSV에서 가져온 사용자

아래 단계를 따르십시오.

1. 활성 필드와 해당 값이 포함된 CSV를 가져옵니다.
1. &#39;설정&#39; > &#39;로그인 방법&#39;을 클릭합니다.
1. 로그인에 대해 **[!UICONTROL 다중 SSO(Single Sign-On) 사용]** 확인란을 선택합니다.
1. SSO 구성을 활성 필드의 값에 연결합니다.
1. 설정을 저장합니다. CSV를 다시 가져옵니다.

### 단일 사용자

아래 단계를 따르십시오.

1. &#39;설정&#39; > &#39;로그인 방법&#39;을 클릭합니다.
1. 로그인에 대해 **[!UICONTROL 다중 SSO(Single Sign-On) 사용]** 확인란을 선택합니다.
1. SSO의 활성 필드를 선택합니다.
1. SSO 구성을 필드의 값에 연결합니다.
1. 설정을 저장합니다. 단일 사용자를 추가하고 활성 필드에 값을 할당합니다.

### 자체 등록 사용자

아래 단계를 따르십시오.

1. &#39;설정&#39; > &#39;로그인 방법&#39;을 클릭합니다.
1. 로그인에 대해 **[!UICONTROL 다중 SSO(Single Sign-On) 사용]** 확인란을 선택합니다.
1. SSO 구성을 필드의 값에 연결합니다.
1. 설정을 저장합니다. 단일 사용자를 추가하고 활성 필드에 값을 할당합니다.
1. 자체 등록 프로필을 추가합니다.
1. 구성된 SSO 필드 값을 선택합니다.

프로필 설정을 저장한 후 복사된 URL이 사용자를 프로필에 대해 선택한 값에 연결된 SSO로 리디렉션합니다.

### 외부 사용자용 SSO 설정

아래 단계를 따르십시오.

1. 외부 프로필을 만듭니다.
1. &#39;설정&#39; > &#39;로그인 방법&#39;을 클릭합니다.
1. 로그인에 대해 **[!UICONTROL 다중 SSO(Single Sign-On) 사용]** 확인란을 선택합니다.
1. SSO 구성을 생성된 외부 프로필에 연결합니다.
1. 설정을 저장합니다.

프로필 설정을 저장한 후 저장된 외부 프로필 URL이 사용자를 프로필에 연결된 SSO로 리디렉션합니다.

## 자주 묻는 질문

+++ 사용자에 대한 다중 SSO는 누가 활성화할 수 있습니까?

책임자와 사용자 정의 책임자가 다중 SSO를 활성화할 수 있습니다.
+++

+++기존 또는 새로운 단일 값 활성 필드를 사용할 수 있습니까?

그렇습니다. 기존 또는 새로운 단일 값 활성 필드를 사용하여 다중 SSO를 설정할 수 있습니다.
+++

+++CSV에 비활성화된 필드가 있는 경우 다중 SSO를 설정할 수 없습니까?

아닙니다. 비활성화된 필드는 SSO 설정에 영향을 미치지 않습니다. 사용자는 이미 구성된 SSO로 리디렉션됩니다.
+++

+++책임자가 다중 SSO를 설정하는 동안 페이지의 활성 필드에 새 값을 추가할 수 있습니까?

예, 책임자는 활성 필드에 새 값을 추가할 수 있습니다.
+++

+++SSO에 연결된 필드를 비활성화하거나 삭제할 수 있습니까?

예. SSO 설정 페이지에서 필드의 연결을 해제할 때까지 SSO에 연결된 필드를 비활성화하거나 삭제할 수 있습니다.
+++
