---
jcr-language: en_us
title: Learning Manager에서 사용자가 자동으로 삭제됨
description: 책임자가 Learning Manager에서 사용자를 삭제하지 않았는데도 사용자가 삭제됩니다.
contentowner: nluke
source-git-commit: 3242a293fc4b2707044e11c342c984cbfb2fc434
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 55%

---



# Learning Manager에서 사용자가 자동으로 삭제됨 {#user-gets-auto-deleted-in-learning-manager}

## 문제

A **사용자** learning Manager에서 삭제됩니다. 그러나 책임자가 이러한 작업을 수행하지 않았습니다.

## 원인

Adobe Learning Manager에는 특정 시간 동안 시스템에 로그인하지 않은 사용자를 삭제할 수 있는 옵션이 있습니다.

## 설정 변경/적용 방법

### 내부 학습자용

1. **관리자**&#x200B;로 로그인합니다.
1. 아래 **구성**, 클릭 **설정** > **일반**.
1. 일반 설정 페이지에 **내부 사용자 자동 삭제** 옵션이 있습니다.
1. 다음을 수행합니다. **[!UICONTROL 편집]** 학습자가 시스템에 접속하지 않은 경우 자동으로 삭제하여 필드에 일수를 입력합니다.

   ![](assets/cp-autodelete-internal.png)

   *일수 편집*

>[!NOTE]
>
>   사용자를 자동으로 삭제하지 않으려면 이 입력란을 비워 둡니다.


1. 다음을 수행합니다. **[!UICONTROL 저장]** 설정을 유지합니다.

### 외부 학습자의 경우:

1. **관리자**&#x200B;로 로그인합니다.
1. 아래 **관리**, 클릭 **[!UICONTROL 사용자]** > **[!UICONTROL 외부]**.
1. 설정을 적용할 외부 사용자의 이름을 클릭합니다.

   그러면 **외부 등록 프로필 편집** 창이 열립니다.

1. 다음을 수행합니다. **[!UICONTROL 고급 설정]** 왼쪽 하단에 있습니다.

   ![](assets/cp-autodelete-external.png)

   *고급 설정 옵션을 선택합니다*

1. (으)로 **로그인 요구 사항** 시스템에 접속하지 않은 학습자가 자동으로 삭제될 일수를 입력합니다.
1. 다음을 수행합니다. **[!UICONTROL 저장]** 설정을 유지합니다.
