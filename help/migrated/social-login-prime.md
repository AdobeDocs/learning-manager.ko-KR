---
jcr-language: en_us
title: Learning Manager의 소셜 로그인
description: Learning Manager의 소셜 로그인
contentowner: saghosh
preview: true
source-git-commit: ccdb222228f76fdae63ebb0a808824ad6ac1db7f
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---



# Learning Manager의 소셜 로그인

facebook, LinkedIn 또는 Twitter 자격 증명을 사용하여 Learning Manager에 로그인할 수 있습니다.

## 소셜 로그인 설정 {#setupsociallogin}

1. 계정을 설정하도록 원하시면 고객 성공 관리자에게 문의하십시오.

   그렇지 않으면 아래 단계를 따르십시오.

1. 소셜 로그인을 설정할 계정을 검색합니다.
1. 로그인을 SSO로 변경합니다.
1. [고급]을 클릭합니다. 다음 JSON을 지정합니다.

   ```
   \{"linkedIn":true,"microsoft":true,"twitter":true,"facebook":true,"editingAllowed":true
   ```

   잘못된 JSON인 경우 예외가 발생합니다.

   이 소셜 로그인 기능은 내부 사용자에게만 사용됩니다.

