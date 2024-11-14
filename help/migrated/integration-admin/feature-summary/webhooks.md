---
jcr-language: en_us
title: Webhook
description: 강의 등록, 강의 생성 및 기타 정보와 같은 실시간 정보를 특정 URL로 전송하는 Webhook에 대해 알아봅니다.
contentowner: chandrum
exl-id: 472aaf2b-9c2f-4f43-a791-2b2d81e69471
source-git-commit: e4c3489db8207ead0416656161b918eba42f4582
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 0%

---

# Webhook

Webhook을 사용하면 특정 이벤트가 발생할 때 한 엔터티가 다른 엔터티로 실시간 데이터나 알림을 자동으로 보낼 수 있습니다. 이를 지속적으로 요청하지 않고도 다른 애플리케이션에 정보를 제공할 수 있게 된다. 예를 들어 사용자가 LMS(교육 관리 시스템) 과정을 완료한 경우 Webhook은 해당 정보를 CRM 또는 보고 도구와 같은 다른 플랫폼으로 자동으로 전송할 수 있습니다. Webhook은 통합을 통해 프로세스를 자동화하고 시스템 간에 수동 업데이트의 필요성을 줄이는 데 주로 사용됩니다. 데이터를 전송할 콜백 URL을 제공하여 Webhook을 설정합니다.

## Webhook 및 API

Webhook과 API는 모두 시스템이 서로 통신할 수 있도록 지원하지만 서로 다른 방식으로 작동합니다. API를 사용하면 사용자가 정보를 요청할 때만 정보가 공유됩니다. 예를 들어 학습자가 강의 진행률 데이터를 요구하는 경우 API에 요청을 보내고 API에서는 해당 정보를 제공합니다. 반면에 Webhook은 이벤트가 발생하면 데이터를 즉시 자동으로 전송합니다. 예를 들어 학습자가 강의를 완료하면 수동 요청 없이 리스너 URL로 데이터가 즉시 전송됩니다.

## 실시간 API란?

실시간 API를 사용하면 이벤트가 발생할 때 애플리케이션이 데이터를 즉시 교환할 수 있습니다. 사용자가 정보를 요청하면 대기하는 기존 API와 달리 실시간 API는 그 순간 데이터를 공유한다. Webhook은 실시간 API로 작동하며 지정된 이벤트가 발생할 때마다 데이터를 즉시 공유하도록 지원합니다. 실시간 API는 수동 요청 없이도 이러한 데이터 전송이 즉시 이루어지도록 하여 시스템을 즉시 업데이트할 수 있습니다.

## Webhook 이벤트

Webhook 이벤트는 데이터를 리스너 URL로 자동으로 전송하는 시스템에서 발생하는 특정 작업입니다. 예를 들어 학습자가 강의에 등록하면 Webhook 이벤트가 트리거되고 등록 세부 정보가 수신자 URL로 전송됩니다.
Webhook 이벤트는 다음 두 가지 범주로 분류됩니다.

* **실시간 이벤트**: 이벤트가 처리되어 실시간으로 대상 URL로 전송됩니다
* **실시간이 아닌 이벤트**: 이벤트는 배치로 처리되며 실시간이 아닌 지정된 시간에 전송됩니다

## 리스너 URL

리스너 URL은 이벤트가 발생할 때 데이터 정보를 수신하는 엔드 포인트 또는 대상입니다. 사용자가 강의에 등록하는 등 특정 이벤트가 발생하면 수동 요청 없이 세부 정보가 자동으로 이 URL로 전송됩니다. 리스너 URL은 이러한 모든 업데이트가 전달되는 주소입니다.
Webhook은 관련 정보를 JSON 형식으로 전송합니다. 다음은 Adobe Learning Manager에서 트리거된 이벤트에 대한 샘플 페이로드입니다.

```
{
  "accountId": 1010,
  "events": [
    {
      "eventId": "d5fb7071-10a9-46b2-9f9e-79dde346c052",
      "eventName": "COURSE_ENROLLMENT_BATCH",
      "timestamp": 1727414643000,
      "eventInfo": "1727414643000-047210-84242-0",
      "data": {
        "userId": 4279332,
        "loId": "course:7374992",
        "loInstanceId": "course:7376092_10250977",
        "loType": "course",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateEnrolled": 1727414643
      }
    }
  ]
}
```

## Webhook 생성 및 관리 - 통합 관리자

Adobe Learning Manager에서 Webhooks 통합을 만들려면 아래 단계를 따르십시오.

1. **[!UICONTROL 통합 관리자]**(으)로 로그인합니다.
2. 홈페이지에서 **[!UICONTROL Webhook]** > **[!UICONTROL Webhook 추가]**&#x200B;를 선택합니다.

   ![](assets/create-webhook.png)
   _Webhook 추가_

3. Webhook의 **[!UICONTROL 이름]** 및 **[!UICONTROL 설명]**&#x200B;을 입력합니다.
4. 이벤트 데이터를 전달할 **[!UICONTROL 대상 URL]**(으)로 수신기 URL을 입력하십시오.
5. 인증 방법 중 하나를 선택합니다.
Webhooks에서의 인증은 수신기 URL로 전송된 데이터가 신뢰할 수 있는 소스에서 오는지 확인하는 보안 방법입니다.
   * **[!UICONTROL 없음]**: 인증이 필요하지 않습니다.
   * **[!UICONTROL 기본]**: 자격 증명 기반 인증입니다. 사용자 이름과 암호를 입력합니다.
   * **[!UICONTROL 서명]**: 시스템에서 특수 서명을 만들고 Webhook 데이터에 추가합니다. 수신 서버는 이 코드를 확인하여 데이터가 진짜이고 변경되지 않았는지 확인합니다. 서명을 생성하고 인증에 사용합니다. JSON으로 서명을 다운로드합니다.
6. **[!UICONTROL 트리거 이벤트]** 드롭다운에서 Webhook 이벤트를 선택합니다.

   >[!NOTE]
   >
   >Webhook 추가 페이지에서 Webhook 테스트 옵션을 선택하여 Webhook을 테스트할 수도 있습니다.

7. **[!UICONTROL 활성화 상태]** 토글을 선택하여 Webhook을 활성화합니다. 활성화되면 선택한 이벤트가 발생할 때마다 데이터가 전달됩니다.

>[!NOTE]
>
>최대 5개의 Webhook을 만들고 관리할 수 있습니다.

### Webhook 편집 - 통합 관리자

Adobe Learning Manager에서 Webhook을 편집하려면 다음 단계를 따르십시오.

1. **[!UICONTROL 통합 관리자]**(으)로 로그인합니다.
2. 홈페이지에서 **[!UICONTROL Webhooks]**&#x200B;을(를) 선택합니다.
3. 편집할 Webhook을 선택합니다.

   ![](assets/edit-webhook.png)
   _Webhook 편집_
4. **[!UICONTROL 편집]**&#x200B;을 선택하여 Webhook 세부 정보를 수정하고 **[!UICONTROL 저장]**&#x200B;을 선택합니다.

### Webhook 제거 - 통합 관리자

Adobe Learning Manager에서 Webhook을 편집하려면 다음 단계를 따르십시오.

1. **[!UICONTROL 통합 관리자]**(으)로 로그인합니다.
2. 홈페이지에서 **[!UICONTROL Webhooks]**&#x200B;을(를) 선택합니다.
3. 삭제할 Webhook을 선택합니다.
4. Webhook을 제거하려면 **[!UICONTROL 삭제]**&#x200B;를 선택합니다.

![](assets/delete-webhooks.png)
_Webhook 제거_

### Webhook 사용 중지 - 통합 관리자

Webhook을 종료하려면 다음 단계를 따르십시오.

1. **[!UICONTROL 통합 관리자]**(으)로 로그인합니다.
2. 홈페이지에서 **[!UICONTROL Webhooks]**&#x200B;을(를) 선택합니다.
3. 편집할 Webhook을 선택합니다.
4. **[!UICONTROL 편집]**&#x200B;을 선택하고 **[!UICONTROL 활성화 상태]**&#x200B;를 비활성화하여 Webhook을 종료합니다.

![](assets/retire-webhook.png)
_Webhook 사용 중지_
