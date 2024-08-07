---
description: 이 문서는 Learning Manager 계정에 로그인하도록 SSO 인증을 구성하는 데 도움이 됩니다.
jcr-language: en_us
title: SSO 인증을 사용하여 Learning Manager에 로그인
contentowner: dvenkate
source-git-commit: a186a600e632e9a564c4ff30d1897c2cdf0d5aac
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 70%

---



# SSO 인증을 사용하여 Learning Manager에 로그인

이 문서는 Learning Manager 계정에 로그인하도록 SSO 인증을 구성하는 데 도움이 됩니다.

SSO 인증을 구성하려면 다음 단계를 수행하십시오.

1. **[!UICONTROL 설정]** > **[!UICONTROL 로그인 방법]**&#x200B;을 엽니다.

   ![](assets/login-methods.png)

1. 요구 사항에 따라 **[!UICONTROL 내부 사용자]** 또는 **[!UICONTROL 외부 사용자]**&#x200B;를 선택합니다.
1. **[!UICONTROL 로그인]** 옵션 옆에 있는 드롭다운을 클릭하고 **[!UICONTROL SSO(Single Sign-On)]**&#x200B;을 선택합니다.

   ![](assets/single-sign-on.png)

1. SSO(단일 사인온) 설정을 조정하려면 **[!UICONTROL 변경]**&#x200B;을 클릭하십시오.

   ![](assets/change.png)

1. 서비스 공급자가 제공한 **[!UICONTROL IDP 시작 인증 URL]**&#x200B;을(를) 입력하고 **[!UICONTROL IDP 메타데이터 XML 파일]**&#x200B;을 클릭하여 XML 파일을 업로드합니다.

   ![](assets/sso-configuration.png)

   Learning Manager에서 구성하는 SSO는 SAML 2.0을 지원해야 합니다.

   이제 SSO 인증을 사용하여 Learning Manager에 로그인할 수 있습니다.

