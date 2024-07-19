---
jcr-language: en_us
title: Learning Manager에서 사용자가 자동으로 삭제됨
description: 책임자가 Learning Manager에서 사용자를 삭제하지 않았는데도 사용자가 삭제됩니다.
contentowner: nluke
exl-id: 9e293da3-bcbf-4798-b391-aef53ef8d946
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 61%

---

# Learning Manager에서 사용자가 자동으로 삭제됨 {#user-gets-auto-deleted-in-learning-manager}

## 문제

책임자가 Learning Manager에서 사용자를 삭제하지 않았는데도 사용자가 삭제됩니다.

## 원인

Adobe Learning Manager에는 특정 시간 동안 시스템에 로그인하지 않은 사용자를 삭제할 수 있는 옵션이 있습니다.

## 설정 변경/적용 방법

### 내부 학습자용

1. **관리자**&#x200B;로 로그인합니다.
1. **구성**&#x200B;에서 **설정** > **일반**&#x200B;을 클릭합니다.
1. 일반 설정 페이지에 **내부 사용자 자동 삭제** 옵션이 있습니다.
1. **[!UICONTROL 편집]**&#x200B;을 클릭하여 시스템에 접속하지 않은 학습자가 자동으로 삭제될 일수를 입력합니다.

   ![](assets/cp-autodelete-internal.png)

   *일 수 편집*

>[!NOTE]
>
>   사용자를 자동으로 삭제하지 않으려면 이 입력란을 비워 둡니다.


1. **[!UICONTROL 저장]**&#x200B;을 클릭하여 변경한 설정을 유지합니다.

### 외부 학습자의 경우:

1. **관리자**&#x200B;로 로그인합니다.
1. **관리**&#x200B;에서 **[!UICONTROL 사용자]** > **[!UICONTROL 외부]**&#x200B;를 클릭합니다.
1. 설정을 적용할 외부 사용자의 이름을 클릭합니다.

   그러면 **외부 등록 프로필 편집** 창이 열립니다.

1. 왼쪽 하단 모서리에 있는 **[!UICONTROL 고급 설정]**&#x200B;을 클릭합니다.

   ![](assets/cp-autodelete-external.png)

   *고급 설정 옵션 선택*

1. 시스템에 접속하지 않은 학습자가 자동으로 삭제될 일수를 **로그인 요구 사항** 필드에 입력합니다.
1. **[!UICONTROL 저장]**&#x200B;을 클릭하여 변경한 설정을 유지합니다.
