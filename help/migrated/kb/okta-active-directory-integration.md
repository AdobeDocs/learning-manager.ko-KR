---
jcr-language: en_us
title: Adobe Learning Manager와 Okta Active Directory 통합
description: Adobe Learning Manager와 Okta Active Directory 통합
contentowner: nluke
exl-id: 6d7711a9-7a7f-49b7-8948-9a42407463b3
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 57%

---

# Adobe Learning Manager와 Okta Active Directory 통합 {#okta-active-directory-integration-with-adobe-learning-manager}

이 문서에서는 Adobe Learning Manager을 Okta Active Directory(AD)와 통합하는 방법을 익힐 수 있습니다. Adobe Learning Manager을 Okta AD와 통합할 경우 거둘 수 있는 효과:

* Okta AD에서 Learning Manager 사용자의 액세스를 확인하고 제어합니다.
* 사용자가 Okta AD 계정을 사용하여 Adobe Learning Manager에 자동으로 로그인할 수 있습니다.
* 계정을 한곳(Okta 포털)에서 관리할 수 있습니다.

Adobe Learning Manager는 IdP(Identity Provider) 및 SP(Service Provider) 관리형 SSO를 지원합니다.

## OKTA에서 응용 프로그램 생성

1. Okta AD에서 관리자로 로그인합니다.
1. **[!UICONTROL 응용 프로그램]**&#x200B;을 클릭합니다. 그러면 Okta에서 응용 프로그램 스토어가 열립니다.

   ![](assets/cp-application-store.png)

   *Okta에서 응용 프로그램 스토어 보기*

1. **[!UICONTROL 앱 통합 만들기]**&#x200B;를 클릭합니다.

   ![](assets/cp-app-integrations.png)

   *앱 통합 만들기 선택*

1. 새 앱 통합 창에서 **[!UICONTROL SAML 2.0]**&#x200B;을(를) 선택합니다.

   ![](assets/cp-saml2.0.png)

   *SAML2.0 옵션 선택*

1. **[!UICONTROL SAML 통합 만들기]** > **[!UICONTROL 일반 설정 페이지]**&#x200B;를 선택합니다. 응용 프로그램 이름을 입력합니다.

   응용 프로그램을 식별할 수 있는 고유한 이름을 사용하는 것이 좋습니다. 완료되면 **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

   ![](assets/cp-saml-integration.png)

   *응용 프로그램 이름 입력*

1. SAML 설정 구성 페이지에서 다음과 같은 단계를 따르십시오.

   **IDP 설정의 경우:**

   1. 단일 인증 URL 필드에 URL [https://learningmanager.adobe.com/saml/SSO](https://learningmanager.adobe.com/saml/SSO)을(를) 입력합니다.
   1. Audience URL 필드에 URL [https://learningmanager.adobe.com](https://learningmanager.adobe.com/)을(를) 입력합니다.
   1. **이름 ID 형식** 드롭다운 상자에서 **전자 메일 주소**&#x200B;를 선택합니다.
   1. **응용 프로그램 사용자 이름** 드롭다운 상자에서 Okta 사용자 이름을 선택합니다.
   1. 속성을 추가로 전송하고 싶은 경우, **속성 기술**(선택적 입력 항목)에서 속성을 추가할 수 있습니다.

   ![](assets/cp-saml-integration-step1.png)

   *SAML 특성 추가*

   SP 설정 **용:**

   1. 단일 인증 URL 필드에 URL [https://learningmanager.adobe.com/saml/SSO](https://learningmanager.adobe.com/saml/SSO)을(를) 입력합니다.
   1. Audience URL 필드에 URL [https://learningmanager.adobe.com](https://learningmanager.adobe.com/)을(를) 입력합니다.
   1. 이름 ID 형식 드롭다운 상자에서 **이메일 주소**&#x200B;를 선택합니다.
   1. 응용 프로그램 사용자 이름 드롭다운 상자에서 Okta 사용자 이름을 선택합니다.
   1. **고급 설정 표시**&#x200B;를 클릭합니다.
   1. **서명 알고리즘**&#x200B;에서 RSA-SHA256을 선택합니다.
   1. **어설션 알고리즘**&#x200B;에서 SHA256을 선택합니다.
   1. **어설션 암호화** 드롭다운 상자에서 **암호화**&#x200B;를 선택합니다.

   1. **암호화 인증서** 옵션에서 Adobe가 공유하는 인증서 파일을 업로드합니다.
   1. 속성을 추가로 전송하고 싶은 경우, **속성 기술**(선택적 입력 항목)에서 속성을 추가할 수 있습니다.

   ![](assets/cp-saml-integration-step2.png)

   *추가 특성 추가*

   완료되면 **[!UICONTROL 다음]**&#x200B;을 클릭합니다.

1. **피드백** 탭은 선택 사항입니다. 이 옵션을 선택하고 피드백을 입력한 후 **[!UICONTROL 완료]**&#x200B;를 클릭하세요.

   ![](assets/cp-saml-integration-step3.png)

   *SAML 설정 완료*

## IDP 관리형 URL 및 메타데이터 파일 추출

IdP/SP 관리형 URL 및 메타데이터 파일을 보려면 다음 단계를 수행합니다.

1. 이전에 생성한 응용 프로그램을 엽니다.
1. **Single Sign-On** 탭에서 **[!UICONTROL 지침 보기]**&#x200B;를 클릭합니다.

   ![](assets/cp-prime-sso.png)

   *SSO 탭 선택*

   **IDP의 경우:**

   1. ID 공급자 단일 인증 URL은 IdP 시작 URL입니다.
   1. **선택 사항** 필드에 있는 모든 텍스트를 복사합니다.
   1. 메모장을 열고 복사한 텍스트를 새 파일에 붙여넣습니다.
   1. **[!UICONTROL 파일]** > **[!UICONTROL 다른 이름으로 저장]** > &quot;filename.xml&quot;을 클릭합니다. 그러면 메타데이터 파일이 생성됩니다.

   **SP용:**

   1. ID 공급자 단일 인증 URL은 IdP 시작 URL입니다.
   1. ID 공급자 발급자는 개체 ID입니다.
   1. **선택 사항** 필드에 있는 모든 텍스트를 복사합니다.
   1. 메모장을 열고 복사한 텍스트를 새 파일에 붙여넣습니다.
   1. **[!UICONTROL 파일]** > **[!UICONTROL 다른 이름으로 저장]** > **[!UICONTROL filename.xml]**&#x200B;을 클릭합니다. 그러면 메타데이터 파일이 생성됩니다.

   ![](assets/cp-saml-integration-step4.png)

   *SP XML 파일 저장*

   이 파일을 XML 형식으로 저장해야 합니다.

## Adobe Learning Manager SSO 구성

Adobe Learning Manager SSO를 구성하려면 아래 문서에 설명된 단계를 따르십시오.

<!--

article not in TOC

[SSO Authentication](/help/migrated/kb/sso-authentication-for-learning-manager.md)
-->
