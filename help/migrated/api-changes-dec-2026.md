---
description: 게시판 구독 설정 및 구독자 API를 사용하여 다이제스트 전자 메일을 구성하고 게시판 구독자를 관리하는 방법을 알아봅니다
jcr-language: en_us
title: 2026년 11월 API 변경 사항
exl-id: 9b2d3856-810c-4352-bf18-667f698d4d70
source-git-commit: 4234f3cc3b9d77a7f9d197d2df2160ec62edd6d6
workflow-type: tm+mt
source-wordcount: '5724'
ht-degree: 4%
---

# 2026년 12월 API 변경 사항

## 토론 게시판 강사 알림용 API {#api-discussion-board-instructors}

이 문서에서는 토론 게시판 강사 알림을 지원하는 새로운 API에 대해 설명합니다. 강사와 코호트 관리자를 토론 게시판에 구독하고 다이제스트 전자 메일에 나타나는 활동을 제어하는 데 사용합니다.

### API 시퀀스 {#api-sequence}

API는 두 그룹으로 나뉩니다. `boardSubscriptionSettings` API는 계정 수준에서 작동합니다. 구독자 API는 게시판 수준에서 작동합니다. 다음 순서로 API를 사용합니다.

| 단계 | API | 용도 | 범위 |
|---|---|---|---|
| 1 | [`POST /boardSubscriptionSettings`](#api-create-settings) | 계정 수준 설정을 지정합니다. | `admin:write` |
| 2 | [`PATCH /boardSubscriptionSettings`](#api-update-settings) | 계정 수준 설정을 업데이트합니다. | `admin:write` |
| 3 | [`GET /boardSubscriptionSettings`](#api-get-settings) | 계정 수준 설정을 검색합니다. | `admin:read` |
| 4 | [`GET /boards/{id}/subscribers`](#api-get-subscribers) | 게시판에 가입한 사용자 목록을 가져옵니다. | `admin:read` |
| 5 | [`POST /boards/{id}/subscribers`](#api-subscribe-users) | 게시판에 사용자 구독. | `admin:write` |
| 6 | [`DELETE /boards/{id}/subscribers/{userId}`](#api-unsubscribe-user) | 게시판에서 사용자 구독을 취소합니다. | `admin:write` |

### 인증 및 권한

OAuth로 인증하고 `admin:read` 및 `admin:write` 범위를 가진 모든 사용자가 이러한 API를 호출할 수 있습니다. API는 다음 OAuth 범위를 사용합니다.

* `admin:read`: 구독자를 나열하고 알림 설정을 읽습니다(`GET`개 요청).
* `admin:write`: 알림 설정을 만들거나 변경하고 구독자(`POST`, `PATCH` 및 `DELETE`개 요청)를 추가하거나 제거합니다.

>[!NOTE]
>
>알림이 전송되면 게시판 액세스가 다시 선택됩니다. 구독자가 게시판에 대한 액세스 권한을 상실한 경우 해당 게시판에 대한 배달을 건너뛰지만 구독은 유지됩니다. 액세스가 반환되면 배달이 다시 시작됩니다.

### 제한 사항 및 고려 사항

* 추가할 수 있는 구독자 수가 제한되어 있습니다.
* 다이제스트는 페이지 매김 없이 단일 전자 메일로 전송되며 전자 메일 본문에는 크기 제한이 있습니다. 사용량이 많은 보드의 경우, 6시간마다 관리가능한 각 전자 메일을 유지하는 다이제스트 빈도를 선택합니다.
* 다이제스트 링크는 로그인한 사용자에 대해서만 게시물, 댓글 또는 답변을 엽니다.

## 계정 수준 설정을 만들기 위한 API {#api-create-settings}

### API의 목적 {#purpose-create-settings}

이 API를 사용하여 처음으로 보드 구독 알림에 대한 계정 수준 설정을 지정하십시오. 설정은 계정 전체에서 알림 다이제스트가 생성되는 방식을 제어합니다.

* 알림을 생성하는 토론 게시판 이벤트
* 다이제스트 전자 메일을 보낸 빈도
* 게시물, 댓글, 답글 및 투표가 포함되는지 여부.

나중에 설정을 변경하려면 [`PATCH /boardSubscriptionSettings`](#api-update-settings)을(를) 사용하십시오.

### 엔드 포인트 {#endpoint-create-settings}

```http
POST /primeapi/v2/boardSubscriptionSettings
```

| 속성 | 값 |
|---|---|
| 범위 | `admin:write` |
| 요청 형식 | `application/vnd.api+json;charset=UTF-8` |
| 응답 형식 | `application/vnd.api+json;charset=UTF-8` |

### 요청 본문 {#request-body-create-settings}

설정을 `boardSubscriptionSettings` 리소스의 특성으로 보냅니다.

| 필드 | 유형 | 설명 |
|---|---|---|
| `notifyNewPost` | 부울 | 게시판에 새 게시물이 추가된 경우 구독자에게 알릴지 여부입니다. |
| `notifyComment` | 부울 | 게시물에 댓글이 추가된 경우 구독자에게 알릴지 여부입니다. |
| `notifyReply` | 부울 | 주석에 응답이 추가된 경우 구독자에게 알릴지 여부입니다. |
| `digestFrequencyHours` | 정수 | 다이제스트 전자 메일이 전송되는 빈도(시간)입니다. 유효한 값은 1에서 168(1주) 사이입니다. 예를 들어 24명은 일일 다이제스트를 보내고 168명은 주간 다이제스트를 보냅니다. |

### 요청 예시 {#example-request-create-settings}

```bash
curl -X POST \
--header 'Content-Type: application/vnd.api+json;charset=UTF-8' \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth <access-token>' \
-d '{
  "data": {
    "type": "boardSubscriptionSettings",
    "attributes": {
      "notifyNewPost": true,
      "notifyComment": true,
      "notifyReply": true,
      "digestFrequencyHours": 24
    }
  }
}' \
'https://learningmanager.adobe.com/primeapi/v2/boardSubscriptionSettings'
```

### 예제 응답 - 201 생성됨 {#example-response-create-settings}

```json
{
  "links": {
    "self": "https://learningmanager.adobe.com/primeapi/v2/boardSubscriptionSettings"
  },
  "data": {
    "id": "1010",
    "type": "boardSubscriptionSettings",
    "attributes": {
      "digestFrequencyHours": 24,
      "notifyComment": true,
      "notifyNewPost": true,
      "notifyReply": true
    }
  }
}
```

### 응답 코드 {#response-codes-create-settings}

| 상태 | 의미 |
|---|---|
| 201 | 요청이 성공했습니다. 계정 수준 설정이 생성되었습니다. |
| 400 | 일반적인 잘못된 요청 오류입니다. |
| 401 | 요청에 올바른 자격 증명이 없거나 잘못된 자격 증명으로 인해 액세스가 거부되었습니다. |

## 계정 수준 설정을 업데이트하는 API {#api-update-settings}

### API의 목적 {#purpose-update-settings}

이 API를 사용하여 [`POST /boardSubscriptionSettings`](#api-create-settings)(으)로 만든 계정 수준 설정을 업데이트합니다. 예를 들어 다이제스트 주파수를 변경하거나 이벤트 유형을 켜거나 끌 수 있습니다.

### 엔드 포인트 {#endpoint-update-settings}

```http
PATCH /primeapi/v2/boardSubscriptionSettings
```

| 속성 | 값 |
|---|---|
| 범위 | `admin:write` |
| 요청 형식 | `application/vnd.api+json;charset=UTF-8` |
| 응답 형식 | `application/vnd.api+json;charset=UTF-8` |

### 요청 본문 {#request-body-update-settings}

변경할 특성을 만들기 API `notifyNewPost`, `notifyComment`, `notifyReply` 및 `digestFrequencyHours`과(와) 같은 형식으로 보냅니다. 보내지 않는 특성은 현재 값을 유지합니다. 각 특성에 대한 설명은 [계정 수준 설정을 만들기 위한 API](#api-create-settings)를 참조하십시오.

### 요청 예시 {#example-request-update-settings}

```bash
curl -X PATCH \
--header 'Content-Type: application/vnd.api+json;charset=UTF-8' \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth <access-token>' \
-d '{
  "data": {
    "type": "boardSubscriptionSettings",
    "attributes": {
      "notifyReply": true,
      "digestFrequencyHours": 12
    }
  }
}' \
'https://learningmanager.adobe.com/primeapi/v2/boardSubscriptionSettings'
```

### 예제 응답 - 200 OK {#example-response-update-settings}

```json
{
  "links": {
    "self": "https://learningmanager.adobe.com/primeapi/v2/boardSubscriptionSettings"
  },
  "data": {
    "id": "1010",
    "type": "boardSubscriptionSettings",
    "attributes": {
      "digestFrequencyHours": 12,
      "notifyComment": true,
      "notifyNewPost": true,
      "notifyReply": true
    }
  }
}
```

### 응답 코드 {#response-codes-update-settings}

| 상태 | 의미 |
|---|---|
| 200 | 요청이 성공했습니다. 계정 수준 설정이 업데이트되었으며, 응답에는 현재 설정이 포함되어 있습니다. |
| 400 | 일반적인 잘못된 요청 오류입니다. |
| 401 | 요청에 올바른 자격 증명이 없거나 잘못된 자격 증명으로 인해 액세스가 거부되었습니다. |

## 계정 수준 설정을 검색하는 API {#api-get-settings}

### API의 목적 {#purpose-get-settings}

사용자가 게시판을 구독하면 Adobe Learning Manager은 다이제스트 전자 메일을 통해 해당 게시판의 활동에 대해 알릴 수 있습니다. 계정 수준 설정은 알림을 트리거하는 활동 유형과 다이제스트를 전송하는 빈도를 결정합니다.

이 API를 사용하면 해당 설정을 검색할 수 있습니다. 응용 프로그램에서 현재 알림 구성을 표시하거나 설정에 종속된 기능을 빌드하기 전에 설정을 확인하는 데 사용합니다.

### 엔드 포인트 {#endpoint-get-settings}

```http
GET /primeapi/v2/boardSubscriptionSettings
```

| 속성 | 값 |
|---|---|
| 범위 | `admin:read` |
| 응답 형식 | `application/vnd.api+json;charset=UTF-8` |

### 요청 예시 {#example-request-get-settings}

```bash
curl -X GET \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth <access-token>' \
'https://learningmanager.adobe.com/primeapi/v2/boardSubscriptionSettings'
```

### 예제 응답 - 200 OK {#example-response-get-settings}

```json
{
  "links": {
    "self": "https://learningmanager.adobe.com/primeapi/v2/boardSubscriptionSettings"
  },
  "data": {
    "id": "1010",
    "type": "boardSubscriptionSettings",
    "attributes": {
      "digestFrequencyHours": 24,
      "notifyComment": true,
      "notifyNewPost": true,
      "notifyReply": true
    }
  }
}
```

### 리소스 스키마 {#resource-schema-get-settings}

**`boardSubscriptionSettings`특성**

| 필드 | 유형 | 설명 |
|---|---|---|
| `notifyNewPost` | 부울 | 게시판에 새 게시물이 추가된 경우 구독자에게 알릴지 여부입니다. |
| `notifyComment` | 부울 | 게시물에 댓글이 추가된 경우 구독자에게 알릴지 여부입니다. |
| `notifyReply` | 부울 | 주석에 응답이 추가된 경우 구독자에게 알릴지 여부입니다. |
| `digestFrequencyHours` | 정수 | 다이제스트 전자 메일이 전송되는 빈도(시간)입니다. 유효한 값은 1에서 168(1주) 사이입니다. 이 값을 사용하여 다이제스트 전자 메일을 예상하는 빈도를 사용자에게 알립니다. 예를 들어, 값이 24이면 &quot;Daily&quot;를 표시하고 값이 168이면 &quot;Weekly&quot;를 표시합니다. |

### 응답 코드 {#response-codes-get-settings}

| 상태 | 의미 |
|---|---|
| 200 | 요청이 성공했습니다. 응답에는 계정 수준 게시판 구독 설정이 포함되어 있습니다. |
| 400 | 일반적인 잘못된 요청 오류입니다. |
| 401 | 요청에 올바른 자격 증명이 없거나 잘못된 자격 증명으로 인해 액세스가 거부되었습니다. |

### 통합에서 이 API 사용 {#integration-get-settings}

일반적인 사용 사례는 계정에 대해 게시판 구독 이메일이 구성된 방법을 보여 주는 알림 환경 설정 화면입니다.

1. 응용 프로그램의 알림 기본 설정 화면이 로드되면 `GET /boardSubscriptionSettings`에 문의하십시오.
1. 알림을 트리거하는 활동 유형과 응답 값을 사용하여 다이제스트 전자 메일이 전송되는 빈도를 표시합니다.

## 보드 구독자를 검색하는 API {#api-get-subscribers}

### API의 목적 {#purpose-get-subscribers}

특정 보드에 가입되어 있는 사용자 목록을 검색합니다. 게시판에 가입한 사용자에게 게시판의 새 활동에 대한 알림이 전송됩니다. 이 API는 특정 보드에 현재 가입되어 있는 사용자와 각 가입이 생성된 시기 및 사용자에 대한 세부 정보를 반환합니다.

이 API를 사용하여 응용 프로그램에 가입자 목록을 표시하거나, 게시판에 대한 업데이트를 받는 사람을 감사하거나, 게시판 구독 데이터를 외부 시스템과 동기화할 수 있습니다.

응답에 페이지가 지정됩니다. `page[offset]` 및 `page[limit]` 쿼리 매개 변수를 사용하여 큰 구독자 목록을 이동합니다. 반환된 데이터는 요청된 보드에서 호출하는 사용자의 권한에 따라 다릅니다.

### 엔드 포인트 {#endpoint-get-subscribers}

```http
GET /primeapi/v2/boards/{id}/subscribers
```

| 속성 | 값 |
|---|---|
| 범위 | `admin:read` |
| 응답 형식 | `application/vnd.api+json;charset=UTF-8` |

### 매개 변수 {#parameters-get-subscribers}

| 매개 변수 | 위치 | 필수 | 기본값 | 설명 |
|---|---|---|---|---|
| `id` | 경로 | 예 | N/A | 구독자를 검색할 보드의 ID입니다. 액세스는 호출자의 게시판 권한에 따라 다릅니다. |
| `page[offset]` | 쿼리 | 아니오 | 0 | 반환할 레코드의 시작 위치입니다. |
| `page[limit]` | 쿼리 | 아니오 | 10 | 페이지당 반환할 구독자 수입니다. 허용되는 최대값은 200입니다. |

### 요청 예시 {#example-request-get-subscribers}

```bash
curl -X GET \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth <access-token>' \
'https://learningmanager.adobe.com/primeapi/v2/boards/1234/subscribers?page[offset]=0&page[limit]=50'
```

### 예제 응답 - 200 OK {#example-response-get-subscribers}

```json
{
  "data": [
    {
      "id": "1234:5678",
      "type": "boardSubscriber",
      "attributes": {
        "boardId": 1234,
        "dateSubscribed": 1757000000000,
        "subscribedByUserId": 5678,
        "user": {
          "id": "5678",
          "name": "Jane Doe",
          "email": "jane.doe@example.com",
          "avatarUrl": "https://example.com/avatars/5678.png",
          "bio": "Learning enthusiast",
          "contentLocale": "en-US",
          "uiLocale": "en-US",
          "timeZoneCode": "PST",
          "userType": "INTERNAL",
          "state": "ACTIVE",
          "profile": "Learner",
          "roles": ["Learner"],
          "gamificationEnabled": true,
          "pointsEarned": 120,
          "pointsRedeemed": 20,
          "enrollOnClick": true,
          "preferredResolution": "720p",
          "lastLoginDate": "2026-09-23T18:12:04.000Z"
        }
      }
    }
  ]
}
```

### 리소스 스키마 {#resource-schema-get-subscribers}

응답에는 새 리소스 `boardSubscriber`이(가) 포함되어 있습니다. 해당 특성은 `boardId`, `dateSubscribed`, `subscribedByUserId` 및 `user`을(를) 포함합니다. 포함된 사용자 객체에는 사용자 ID, 이름, 전자 메일, 프로필 및 역할과 같은 가입자 정보와 기타 사용자 메타데이터가 있습니다.

**`boardSubscriber`특성**

| 필드 | 유형 | 설명 |
|---|---|---|
| `id` | 문자열 | 불투명 구독 ID. |
| `type` | 문자열 | 리소스 유형입니다. |
| `boardId` | 수 | 사용자가 구독하는 보드의 ID입니다. |
| `dateSubscribed` | 수 | 사용자가 보드를 구독했을 때의 타임스탬프입니다. |
| `subscribedByUserId` | 수 | 구독을 생성한 사용자의 ID입니다. |
| `user` | 개체 | 구독한 사용자에 대한 세부 정보(포함됨, 아래 참조). |

**`user`(포함, 구독자 내부)**

| 필드 | 유형 | 설명 |
|---|---|---|
| `id` | 문자열 | 불투명 사용자 ID. |
| `name` | 문자열 | 사용자의 표시 이름입니다. |
| `email` | 문자열 | 사용자의 이메일 주소입니다. |
| `avatarUrl` | 문자열 | 사용자 프로필 사진의 URL |
| `bio` | 문자열 | 사용자에 대한 간단한 전기입니다. |
| `binUserId` | 문자열 | 사용자의 내부 식별자. |
| `userUniqueId` | 문자열 | 계정에서 사용자의 고유 식별자. |
| `userType` | 문자열 | 사용자의 유형(예: 내부 또는 외부) |
| `state` | 문자열 | 사용자 계정의 현재 상태입니다. |
| `profile` | 문자열 | 사용자에게 할당된 프로필입니다. |
| `roles` | 문자열 배열 | 사용자가 보유한 역할. |
| `contentLocale` | 문자열 | 사용자가 콘텐츠 보기를 선호하는 로케일입니다. |
| `uiLocale` | 문자열 | 사용자 인터페이스에 사용되는 로케일입니다. |
| `timeZoneCode` | 문자열 | 사용자에 대해 구성된 표준 시간대 |
| `preferredResolution` | 문자열 | 사용자의 기본 비디오 해상도입니다. |
| `enrollOnClick` | 부울 | 사용자가 학습 개체를 선택할 때 자동으로 등록되는지 여부입니다. |
| `gamificationEnabled` | 부울 | 사용자에게 게임화 기능을 사용할지 여부를 지정합니다. |
| `pointsEarned` | 수 | 사용자가 획득한 총 게임화 점수입니다. |
| `pointsRedeemed` | 수 | 사용자가 교환한 총 게임화 점수입니다. |
| `lastLoginDate` | 문자열 | 사용자의 가장 최근 로그인 날짜 및 시간입니다. |
| `fields` | 개체 | 사용자 정의 사용자 필드 및 해당 값 |
| `metadata` | 개체 | 사용자와 연결된 추가 메타데이터입니다. |

### 응답 코드 {#response-codes-get-subscribers}

| 상태 | 의미 |
|---|---|
| 200 | 요청이 성공했습니다. 응답에는 이사회의 구독자가 포함됩니다. |
| 400 | 일반적인 잘못된 요청 오류입니다. 예를 들어, 게시판 ID나 번호 매기기 값의 형식이 잘못되었습니다. |
| 401 | 요청에 올바른 자격 증명이 없거나 잘못된 자격 증명으로 인해 액세스가 거부되었습니다. |

### 통합에서 이 API 사용 {#integration-get-subscribers}

일반적인 사용 사례는 보드에 대한 업데이트를 받는 모든 사람을 표시하는 관리자 또는 중재자 보기입니다.

1. 보기가 로드되면 보드 ID와 레이아웃에 맞는 `page[limit]` 값(최대 200)으로 이 끝점을 호출합니다.
1. 각 구독자에 대한 `user.name`, `user.email` 및 `dateSubscribed` 값을 표시합니다.
1. 반환된 레코드 수가 `page[limit]`인 경우 더 많은 구독자가 있을 수 있습니다. 끝점을 다시 호출하여 요청한 레코드보다 적은 레코드를 반환할 때까지 페이지 크기만큼 `page[offset]`을(를) 늘립니다.

## 사용자를 보드에 가입시키는 API {#api-subscribe-users}

### API의 목적 {#purpose-subscribe-users}

토론 게시판에 대한 다이제스트 전자 메일을 받을 수 있도록 한 명 이상의 사용자를 구독하십시오. 사용자 ID, 이메일 주소(계정 내 사용자 ID로 확인됨) 또는 둘 다를 기준으로 사용자를 식별합니다. 단일 요청에서 여러 사용자를 추가할 수 있습니다. [일괄 구독](#bulk-subscriptions)을 참조하세요.

### 엔드 포인트 {#endpoint-subscribe-users}

```http
POST /primeapi/v2/boards/{id}/subscribers
```

| 속성 | 값 |
|---|---|
| 범위 | `admin:write` |
| 요청 형식 | `application/vnd.api+json;charset=UTF-8` |
| 응답 형식 | `application/vnd.api+json;charset=UTF-8` |

### 매개 변수 {#parameters-subscribe-users}

| 매개 변수 | 위치 | 필수 | 설명 |
|---|---|---|---|
| `id` | 경로 | 예 | 사용자를 구독할 게시판의 ID입니다. |

### 요청 본문 {#request-body-subscribe-users}

사용자를 `boardSubscriberBulkRequest` 리소스의 특성으로 보냅니다. `userIds` 또는 `emails` 중 하나 이상이 필요합니다.

| 필드 | 유형 | 설명 |
|---|---|---|
| `data.attributes.userIds` | 숫자의 배열 | 구독할 사용자의 ID입니다. |
| `data.attributes.emails` | 문자열 배열 | 구독할 사용자의 이메일 주소입니다. 각 주소는 계정 내의 사용자 ID로 확인됩니다. |

### 요청 예시 {#example-request-subscribe-users}

```bash
curl -X POST \
--header 'Content-Type: application/vnd.api+json;charset=UTF-8' \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth <access-token>' \
-d '{
  "data": {
    "type": "boardSubscriberBulkRequest",
    "attributes": {
      "userIds": [
        1234,
        5678
      ],
      "emails": [
        "abc@xyz.com"
      ]
    }
  }
}' \
'https://learningmanager.adobe.com/primeapi/v2/boards/1010/subscribers'
```

### 예제 응답 - 207 다중 상태 {#example-response-subscribe-users}

```json
{
  "added": [
    {
      "userId": "12345",
      "status": "SUCCESS"
    }
  ],
  "failed": [
    {
      "userId": "78910",
      "errorCode": "NO_BOARD_ACCESS"
    }
  ]
}
```

**응답 특성**

| 필드 | 유형 | 설명 |
|---|---|---|
| `added` | 배열 | 구독한 사용자입니다. 각 항목에는 `userId` 및 `status`이(가) 있습니다. 이미 구독했던 사용자도 여기에 성공으로 보고됩니다. |
| `failed` | 배열 | 구독할 수 없는 사용자입니다. 각 항목에는 `userId` 및 `errorCode`이(가) 있습니다(예: `NO_BOARD_ACCESS`). |

### 응답 코드 {#response-codes-subscribe-users}

| 상태 | 의미 |
|---|---|
| 207 | 다중 상태. 요청이 처리되었으며 응답에는 `added` 및 `failed`의 각 사용자에 대한 결과가 나열됩니다. |
| 400 | 일반적인 잘못된 요청 오류입니다. |
| 401 | 요청에 올바른 자격 증명이 없거나 잘못된 자격 증명으로 인해 액세스가 거부되었습니다. |
| 404 | 게시판과 같은 요청된 리소스를 찾을 수 없습니다. |
| 409 | 보드가 비활성, 삭제 또는 종료되어 전체 요청이 거부됩니다. |

### 일괄 구독 {#bulk-subscriptions}

일괄 구독을 사용하여 한 번에 여러 사용자를 토론 게시판에 추가할 수 있습니다. 일괄 구독을 통해 구독자를 관리하는 데 필요한 API 호출 수를 줄일 수 있습니다. 다음과 같은 경우에 유용합니다.

* 강사는 여러 코호트를 관리합니다.
* 코호트 관리자는 여러 토론 게시판에 액세스할 수 있어야 합니다.
* 외부 시스템은 보드 가입을 일괄 동기화합니다.
* 코호트 생성 시 여러 강사를 구독해야 합니다.

#### 일괄 추가 동작

대량 요청에는 사용자 ID, 전자 메일 주소 또는 이 두 가지를 조합하여 사용할 수 있습니다. 각 사용자는 독립적으로 처리됩니다.

#### 멱등 거동

대량 추가는 멱등 행렬입니다. 사용자가 이미 보드에 가입되어 있는 경우 요청이 성공하고 중복 가입이 생성되지 않으며 기존 가입은 변경되지 않습니다. 이를 통해 클라이언트는 요청을 안전하게 재시도할 수 있습니다.

#### 부분적 성공

일부 사용자는 가입할 수 있지만 다른 사용자는 유효성 검사에 실패합니다. 하나 이상의 사용자가 잘못되었으므로 작업이 실패하지 않습니다.

| 사례 | 결과 |
|---|---|
| 사용자가 존재하며, 이 게시판에 대한 이용 권한이 있음 | 성공 |
| 사용자가 이미 구독하고 있습니다. | 성공 |
| 사용자가 보드에 대한 액세스 권한이 없습니다. | 실패(`NO_BOARD_ACCESS`) |
| 사용자가 없습니다. | 실패 |
| 사용자가 비활성 상태입니다. | 실패 |
| 사용자가 삭제되었습니다. | 실패 |

#### 응답 형식

대량 구독은 [예제 응답](#example-response-subscribe-users)과 같이 각 사용자에 대해 `added` 결과 및 `failed` 결과를 포함하는 HTTP 207 다중 상태를 반환합니다.

#### 일반적인 유효성 검사 실패

* **사용자가 게시판에 액세스할 수 없습니다.** 사용자가 게시판을 볼 수 없으면 해당 사용자에 대해 `NO_BOARD_ACCESS`이(가) 반환됩니다. 나머지 사용자는 계속 정상적으로 처리됩니다.
* **게시판이 비활성 상태이거나, 삭제되었거나, 중단되었습니다.** 게시판이 구독에 적합하지 않으면 HTTP 409 충돌로 요청이 거부됩니다.
* **사용자가 잘못되었습니다.** 사용자 계정이 없거나 비활성 상태이거나 삭제된 경우 해당 사용자에 대한 실패 항목을 반환합니다.

## 게시판에서 사용자 구독을 취소하는 API {#api-unsubscribe-user}

### API의 목적 {#purpose-unsubscribe-user}

토론 게시판에서 사용자 구독을 취소합니다. 구독이 제거되면 사용자는 더 이상 해당 게시판에 대한 알림 및 다이제스트 전자 메일을 수신하지 않습니다.

### 엔드 포인트 {#endpoint-unsubscribe-user}

```http
DELETE /primeapi/v2/boards/{id}/subscribers/{userId}
```

| 속성 | 값 |
|---|---|
| 범위 | `admin:write` |
| 응답 형식 | `application/vnd.api+json;charset=UTF-8` |

### 매개 변수 {#parameters-unsubscribe-user}

| 매개 변수 | 위치 | 필수 | 설명 |
|---|---|---|---|
| `id` | 경로 | 예 | 게시판의 ID입니다. |
| `userId` | 경로 | 예 | 구독을 취소할 사용자 ID입니다. |

### 요청 예시 {#example-request-unsubscribe-user}

```bash
curl -X DELETE \
--header 'Accept: application/vnd.api+json' \
--header 'Authorization: oauth <access-token>' \
'https://learningmanager.adobe.com/primeapi/v2/boards/1234/subscribers/5678'
```

### 예제 응답 - 204 내용 없음 {#example-response-unsubscribe-user}

응답에 본문이 없습니다.

### 응답 코드 {#response-codes-unsubscribe-user}

| 상태 | 의미 |
|---|---|
| 204 | 요청이 성공했습니다. 사용자가 보드에서 구독을 취소했습니다. |
| 400 | 일반적인 잘못된 요청 오류입니다. |
| 401 | 요청에 올바른 자격 증명이 없거나 잘못된 자격 증명으로 인해 액세스가 거부되었습니다. |
| 404 | 게시판 또는 구독과 같은 요청된 리소스를 찾을 수 없습니다. |

## 책갈피 API 순서 지정 및 중단된 콘텐츠 처리 {#bookmark-api-ordering-retired-content}

### API의 목적

학습자는 다시 방문하고 싶은 교육에 책갈피를 표시합니다. 이렇게 변경하기 전에 책갈피 API가 특정 순서 없이 책갈피를 반환했습니다. 통합, 특히 헤드리스 구현에서는 가장 최근에 저장된 책갈피를 먼저 표시할 수 없습니다. 책갈피가 많은 학습자는 최근 항목을 찾으려면 이전 항목을 스크롤해야 합니다.

중단된 학습 객체의 책갈피도 목록에 남아 있습니다. 하나를 선택하면 &quot;페이지를 찾을 수 없습니다&quot; 오류가 발생합니다.

이 변경은 두 가지 방법으로 책갈피 API를 개선합니다.

* 책갈피는 가장 최신 순서대로 시간 순서대로 반환됩니다.
* 중단된 학습 객체에 대한 책갈피는 더 이상 반환되지 않습니다.

새 끝점, 매개 변수 또는 응답 특성이 도입되지 않았습니다. 기존 통합은 변경 없이 계속 작동합니다.

### 기본 URL 및 규칙

책갈피 API는 다음 기본 경로 및 규칙을 사용합니다.

| 항목 | 값 |
|---|---|
| 기본 경로 | `/primeapi/v2` |
| 콘텐츠 유형 | `application/vnd.api+json` |
| 인증 | 학습자 읽기 액세스 권한이 있는 OAuth 토큰 |
| 기본 순서 | 최신 책갈피 먼저 |
| 새 매개 변수 | 없음 |
| 응답 구조 | 변경되지 않음 |

### 엔드포인트

#### 책갈피를 반환하는 끝점

다음 끝점은 책갈피를 새 순서로 반환합니다.

| 엔드 포인트 | 반환 |
|---|---|
| `GET /primeapi/v2/learningObjects?filter.bookmarks=true` | 학습자에게 책갈피가 지정된 학습 개체 |
| `GET /primeapi/v2/bookmarks` | 학습자의 책갈피 |

#### 책갈피가 지정된 학습 개체를 순서대로 가져오기

`GET /primeapi/v2/learningObjects?filter.bookmarks=true`

<!-- Content Review by Claude: Please confirm the endpoint list. The dev-to-QE hand-off confirms ordering for GET /learningObjects?filter.bookmarks=true. The PRD (ALMER-442) also lists GET /primeapi/v2/bookmarks. Please also confirm the OAuth scope. -->

호출하는 학습자에게 책갈피가 지정된 학습 개체를 반환합니다. 가장 최근에 책갈피를 표시한 항목이 첫 번째이고, 가장 오래된 항목이 마지막 항목입니다.

**범위:** 학습자 읽기 액세스

끝점은 다음 쿼리 매개 변수를 허용합니다.

| 매개 변수 | 위치 | 필수 | 설명 |
|---|---|---|---|
| `filter.bookmarks` | 쿼리 | 예 | 학습자에게 책갈피가 지정된 학습 개체만 반환하려면 `true`(으)로 설정합니다. |

**샘플 요청**

```http
GET /primeapi/v2/learningObjects?filter.bookmarks=true
Accept: application/vnd.api+json
Authorization: oauth <access-token>
```

**샘플 200 OK 응답**

학습자에게 책갈피 표시된 Adobe Analytics 시작하기, 두 번째 Workspace 프로젝트 빌드 및 Adobe Analytics의 고급 세그먼테이션 응답에는 최신 항목부터 가장 오래된 항목까지 나열됩니다. 다른 특성은 간결성을 위해 생략하였다.

```json
{
  "data": [
    {
      "id": "course:2400162",
      "type": "learningObject",
      "attributes": {
        "name": "Advanced Segmentation in Adobe Analytics"
      }
    },
    {
      "id": "course:2400160",
      "type": "learningObject",
      "attributes": {
        "name": "Building Workspace Projects"
      }
    },
    {
      "id": "course:2400159",
      "type": "learningObject",
      "attributes": {
        "name": "Getting Started with Adobe Analytics"
      }
    }
  ]
}
```

>[!NOTE]
>
>새 순서는 기본 동작이며 모든 계정에 적용됩니다.

### 책갈피 순서 지정

#### 책갈피 순서 지정 방법

책갈피는 학습자가 저장한 날짜를 기준으로 최신부터 최신까지 정렬됩니다. 예를 들어, 학습자가 강의 A, 강의 B, 강의 C에 책갈피를 지정하면 응답에 강의 C, 강의 B, 강의 A가 순서대로 나열됩니다.

인스턴스의 10번째 위치에 나타나는 책갈피 표시된 LO가 &quot;저장되지 않음&quot;이고 나중에 다시 책갈피 표시된 경우 최근 책갈피 및 목록의 처음에 표시됩니다.

이전에 클라이언트에서 책갈피를 정렬한 통합은 해당 논리를 제거하고 반환된 순서대로 결과를 표시할 수 있습니다.

### 중단된 콘텐츠 처리

#### 중단된 학습 객체 처리 방법

중단된 학습 개체에 대한 책갈피는 학습자가 학습 개체에 등록되었는지 여부에 관계없이 응답에서 반환되지 않습니다.

책갈피가 지정된 중단된 학습 개체는 학습자가 등록되지 않으면 표시되지 않습니다.

학습자에게 더 이상 &quot;페이지를 찾을 수 없음&quot; 오류가 발생하는 책갈피가 표시되지 않습니다. 책갈피는 결과에서 숨겨지고 삭제되지는 않습니다.

### 호환성

이 변경은 기존 API 소비자를 위반하지 않습니다.

* 끝점과 해당 매개 변수는 변경되지 않습니다.
* 응답 구조는 변경되지 않으며 어떤 특성도 추가되거나 제거되지 않습니다.
* 결과의 순서와 중단된 학습 개체를 제외하는 것만이 이전 동작과 다릅니다.

### 통합에서 이 API 사용

일반적인 사용 사례는 헤드리스 학습자 경험의 &#39;나중을 위해 저장됨&#39; 목록입니다. 학습자가 중단된 콘텐츠로의 링크 없이 가장 최근의 책갈피를 먼저 볼 수 있도록 해야 합니다.

1. 학습자가 목록을 열면 `GET /primeapi/v2/learningObjects?filter.bookmarks=true`에 전화합니다.
2. 반환된 순서대로 학습 객체를 표시합니다. 첫 번째 항목은 가장 최근에 책갈피가 추가된 항목입니다.
3. 해결 방법으로 추가한 클라이언트측 정렬 또는 폐기된 콘텐츠 필터링을 제거합니다.
4. 응답의 항목 수를 사용하여 책갈피의 개수를 표시합니다. 중단된 학습 객체에 대한 책갈피는 더 이상 포함되지 않습니다.

### 학습자 앱의 학습자 준수 위젯에 다중 등록된 인스턴스에 대한 API 지원 {#api-multienrolled-instances-lc-widget}

공개 API는 기존 등록 끝점에서 선택적 쿼리 매개 변수를 통해 이 동작을 지원합니다. 매개 변수를 생략하면 API는 이전과 동일한 결과를 반환하므로 헤드리스 구현을 비롯한 기존 통합은 변경되지 않고 계속 작동합니다.

**엔드 포인트**

GET /primeapi/v2/enrollments

**쿼리 매개 변수**

includeMultiInstanceEnrollments(선택 사항)

**쿼리**

https://learningmanagerstage1.adobe.com/primeapi/v2/enrollments?page\[limit\]=10&filter.loTypes=course&includeHierarchicalEnrollments=false&includeMultiInstanceEnrollments=true&sort=dateEnrolled

**값**

맞아. 기본적으로 False입니다.

**응답 본문**

{

&quot;links&quot;: {

&quot;self&quot;: &quot;[https://learningmanagerstage1.adobe.com/primeapi/v2/enrollments?page\[limit\]=10&amp;filter.loTypes=course&amp;sort=dateEnrolled&amp;includeHierarchicalEnrollments=false&amp;includeMultiInstanceEnrollments=true](https://learningmanagerstage1.adobe.com/primeapi/v2/enrollments?page%5blimit%5d=10&filter.loTypes=course&sort=dateEnrolled&includeHierarchicalEnrollments=false&includeMultiInstanceEnrollments=true)&quot;,

&quot;next&quot;: &quot;[https://learningmanagerstage1.adobe.com/primeapi/v2/enrollments?page\[limit\]=10&amp;filter.loTypes=course&amp;sort=dateEnrolled&amp;includeHierarchicalEnrollments=false&amp;includeMultiInstanceEnrollments=true&amp;page\[cursor\]=eyJjb3Vyc2VNdWx0aSI6MCwiam9iQWlkIjowLCJjb3Vyc2UiOjEwLCJsZWFybmluZ1Byb2dyYw0iOjAsImNlcnRpRpRpRpRpRp pb24iOjB9](https://learningmanagerstage1.adobe.com/primeapi/v2/enrollments?page%5blimit%5d=10&filter.loTypes=course&sort=dateEnrolled&includeHierarchicalEnrollments=false&includeMultiInstanceEnrollments=true&page%5bcursor%5d=eyJjb3Vyc2VNdWx0aSI6MCwiam9iQWlkIjowLCJjb3Vyc2UiOjEwLCJsZWFybmluZ1Byb2dyYW0iOjAsImNlcnRpZmljYXRpb24iOjB9)&quot;

},

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:15067_30122_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;completionDeadline&quot;: &quot;2026-02-24T10:50:45.000Z&quot;,

&quot;enrollmentSource&quot;: &quot;MGR_APPROVAL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;PENDING_APPROVAL&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:15067&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:15067_30122&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:15067_30122_41715_1_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

},

{

&quot;id&quot;: &quot;course:1108800_1997400_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;enrollmentSource&quot;: &quot;SELF_ENROLL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;PENDING_APPROVAL&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:1108800&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:1108800_1997400&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:1108800_1997400_2174574_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

},

{

&quot;id&quot;: &quot;course:2027668_3707328_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;enrollmentSource&quot;: &quot;MGR_APPROVAL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;PENDING_APPROVAL&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2027668&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2027668_3707328&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:2027668_3707328_2665897_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

},

{

&quot;id&quot;: &quot;course:2030067_3709862_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;enrollmentSource&quot;: &quot;MGR_APPROVAL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;PENDING_APPROVAL&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2030067&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2030067_3709862&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:2030067_3709862_2668467_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

},

{

&quot;id&quot;: &quot;course:3081896_5749155_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;enrollmentSource&quot;: &quot;MGR_APPROVAL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;PENDING_APPROVAL&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:3081896&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:3081896_5749155&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:3081896_5749155_3737554_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

},

{

&quot;id&quot;: &quot;course:3081896_5749155_3737555_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

},

{

&quot;id&quot;: &quot;course:2037893_3717940_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;enrollmentSource&quot;: &quot;MGR_APPROVAL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;PENDING_APPROVAL&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2037893&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2037893_3717940&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:2037893_3717940_3676856_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

},

{

&quot;id&quot;: &quot;course:3049434_5713130_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;completionDeadline&quot;: &quot;2020-05-05T18:29:59.000Z&quot;,

&quot;enrollmentSource&quot;: &quot;MGR_APPROVAL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;PENDING_APPROVAL&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:3049434&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:3049434_5713130&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:3049434_5713130_3693595_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

},

{

&quot;id&quot;: &quot;course:2001397_3679403_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;enrollmentSource&quot;: &quot;MGR_APPROVAL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;PENDING_APPROVAL&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2001397&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2001397_3679403&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:2001397_3679403_2635974_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

},

{

&quot;id&quot;: &quot;course:2037862_3717900_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;enrollmentSource&quot;: &quot;MGR_APPROVAL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;PENDING_APPROVAL&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2037862&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2037862_3717900&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:2037862_3717900_3676816_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

},

{

&quot;id&quot;: &quot;course:2037837_3717863_3400468&quot;,

&quot;type&quot;: &quot;learningObjectInstanceEnrollment&quot;,

&quot;attributes&quot;: {

&quot;completionDeadline&quot;: &quot;2020-02-29T18:29:59.000Z&quot;,

&quot;enrollmentSource&quot;: &quot;SELF_ENROLL&quot;,

&quot;hasPassed&quot;: false,

&quot;progressPercent&quot;: 0,

&quot;score&quot;: 0,

&quot;state&quot;: &quot;OTHER&quot;

},

&quot;relationships&quot;: {

&quot;learner&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;3400468&quot;,

&quot;type&quot;: &quot;user&quot;

}

},

&quot;learningObject&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2037837&quot;,

&quot;type&quot;: &quot;learningObject&quot;

}

},

&quot;loInstance&quot;: {

&quot;data&quot;: {

&quot;id&quot;: &quot;course:2037837_3717863&quot;,

&quot;type&quot;: &quot;learningObjectInstance&quot;

}

},

&quot;loResourceGrades&quot;: {

&quot;data&quot;: \[

{

&quot;id&quot;: &quot;course:2037837_3717863_3597363_0_3400468&quot;,

&quot;type&quot;: &quot;learningObjectResourceGrade&quot;

}

\]

}

}

}

\]

}

## 학습 과정 등록의 마지막 액세스 날짜 {#api-last-access-date-lp-enrollment}

Adobe Learning Manager에서는 학습 경로 등록에 마지막 액세스 날짜와 같은 사용자 정의 메타데이터를 저장할 수 있습니다. API를 통해 메타데이터를 설정하고 읽습니다. 이렇게 하면 할당한 학습 경로에 대한 시간 바운드 액세스를 추적할 수 있습니다.

## 학습 경로 등록 메타데이터 정보

API를 통해 강의 등록에 대한 마지막 액세스 날짜를 이미 설정할 수 있습니다. 해당 날짜는 학습자가 강의에 액세스할 수 있는 기간을 제어합니다. 이제 학습 경로 등록은 일반 메타데이터 필드를 지원하므로 마지막 액세스 날짜 또는 추적할 다른 값을 저장할 수 있습니다.

필드를 켜거나 특수 헤더를 보낼 필요가 없습니다. 이 필드는 사용자가 설정할 때까지 비어 있습니다.

>[!NOTE]
>
>메타데이터는 사용자의 추적을 위한 것입니다. Adobe Learning Manager은 학습자가 학습 경로 또는 강의를 열어도 업데이트되지 않으며 학습 경로에 대한 액세스를 제어하지 않습니다. 또한 경로의 강의에도 전파되지 않습니다. 각 강의에는 고유한 마지막 액세스 날짜가 유지되므로, 같은 경로에 있는 강의에는 다른 날짜가 표시될 수 있습니다. 계속해서 강의 레벨 액세스 만료를 별도로 관리합니다.

### 메타데이터 규칙 {#metadata-rules}

* 값은 JSON 개체여야 합니다. 문자열, 숫자, 부울 또는 배열은 메시지 `metadata must be a JSON object`과(와) 함께 400 오류를 반환합니다.
* 아무 키나 사용할 수 있습니다. Adobe Learning Manager은 키 또는 값의 유효성을 검사하지 않으며 날짜 형식을 시행하지 않습니다. 이 문서의 예제는 강의 날짜와 동일한 형식인 에포크 밀리초를 사용합니다.
* PATCH 요청은 전체 메타데이터 객체를 바꿉니다. 기존 값과 병합되지 않으므로 생략하는 키가 제거됩니다.
* `"metadata": null`을(를) 설정하면 모든 메타데이터가 지워지고 200이 반환됩니다.
* `attributes` 개체가 비어 있거나 `metadata` 키가 없는 요청에서는 저장된 메타데이터가 변경되지 않습니다.
* 메타데이터가 설정되지 않았거나 지우면 `metadata` 키가 응답에 없습니다.

## 기존 등록의 메타데이터 설정

관리자 토큰을 사용합니다.

다음 엔드포인트로 PATCH 요청을 보냅니다. 여기서 `{enrollmentId}`은(는) `learningProgram:<lpId><instanceId><userId>` 형식의 학습 경로 등록 ID입니다.

```
PATCH /primeapi/v2/users/{userId}/enrollments/{enrollmentId}
```

이 요청 본문 사용:

```json
{
  "data": {
    "id": "<enrollmentId>",
    "type": "learningObjectInstanceEnrollment",
    "attributes": {
      "metadata": {
        "lastAccessDate": 1745337600000
      }
    }
  }
}
```

### 학습자 등록 시 메타데이터 설정

관리자 토큰을 사용합니다.

학습 경로 및 POST ID와 함께 인스턴스 요청을 보냅니다. 요청 본문에 선택적 `metadata` 개체를 포함합니다.

```
POST /primeapi/v2/users/{userId}/enrollments?loId=<lpId>&loInstanceId=<instanceId>
```

* `metadata`이(가) JSON 개체가 아니면 400을 반환하고 사용자가 등록되지 않습니다.
* 사용자가 이미 등록되어 있으면 200을 반환하고 아무것도 변경하지 않습니다. 기존 등록에 대한 메타데이터를 변경하려면 PATCH 요청을 사용합니다.
* 응답에는 메타데이터가 포함되지 않습니다. 읽으라는 GET 요청을 보냅니다.

### 메타데이터 검색

책임자 또는 학습자 토큰으로 메타데이터를 검색할 수 있습니다. 토큰 유형별로 요청이 다릅니다.

| 토큰 | 1개 등록 받기 | 학습 경로 등록 나열 |
|---|---|---|
| 책임자 | `GET /primeapi/v2/users/{userId}/enrollments/{enrollmentId}` | `GET /primeapi/v2/users/{userId}/enrollments?filter.loTypes=learningProgram` |
| Prime에서 | `GET /primeapi/v2/enrollments/{enrollmentId}`<br>`GET /primeapi/v2/learningObjects/{id}?include=enrollment` | `GET /primeapi/v2/enrollments?filter.loTypes=learningProgram` |

>[!NOTE]
>
>`include=enrollment` 매개 변수는 학습자 토큰에서만 작동합니다. 관리자 역할에는 지원되지 않습니다.

응답에서 학습 경로 등록이 있는 `metadata` 개체를 반환합니다.

### 헤드리스 및 외부 포털에서 메타데이터 사용

외부 포털 및 통합은 동일한 API 호출을 사용합니다. 포털에서 사용하는 토큰과 일치하는 요청을 사용합니다.

* **포털에 값 표시:** 위 테이블에서 토큰 유형에 대한 GET 요청을 보내고 응답에서 `metadata` 개체를 읽습니다.
* **상거래 플랫폼과 같은 외부 시스템에서 값을 업데이트하십시오.** 관리자 토큰으로 PATCH 요청을 보냅니다.

## 작업 API: generateCustomReport를 사용하여 Report Builder 보고서 내보내기 {#api-job-report-builder-exports}

Adobe Learning Manager 2026년 12월 릴리스에서는 새 작업 유형 `generateCustomReport`을(를) 작업 API에 추가합니다. 보고서 ID를 전달하여 Report Builder에서 만든 모든 보고서를 자동화된 방식으로 내보낼 수 있습니다.

이제 Report Builder의 새로운 L2 퀴즈 데이터 집합과 결합하여 다음을 수행할 수 있습니다.

* 각 과정에 대해 `generateQuizReport`을(를) 한 번 실행하는 대신 하나의 보고서에서 여러 과정 및 모듈에 걸쳐 질문 수준(L2) 퀴즈 데이터를 내보냅니다.
* 반복 내보내기(예: 데이터 웨어하우스 또는 BI 도구로 매일 증분 내보내기)를 자동화합니다.

`generateQuizReport`을(를) 포함한 기존 작업 유형이 변경되지 않았습니다.

### 시작하기 전에

* 관리자여야 합니다. `generateCustomReport` 작업 유형을 다른 역할에서 사용할 수 없습니다.
* 먼저 Report Builder에서 보고서를 만들고 저장합니다. L2 퀴즈 데이터의 경우 L2 퀴즈 데이터 세트에서 보고서를 작성하고 질문 텍스트, 학습자 응답, 점수, 시도 횟수 및 답변 날짜 등 필요한 질문 수준 필드를 포함합니다.
* 보고서의 ID를 메모합니다. 요청에 `reportId`(으)로 전달했습니다.

### 직업 만들기

**엔드 포인트**

```
POST /primeapi/v2/jobs
```

**요청 본문**

```json
{
  "data": {
    "type": "job",
    "attributes": {
      "description": "Daily L2 quiz export",
      "jobType": "generateCustomReport",
      "payload": {
        "reportId": "1478"
      }
    }
  }
}
```

**특성**

| 특성 | 필수 | 설명 |
|---|---|---|
| `jobType` | 예 | `generateCustomReport`이어야 합니다. |
| `payload.reportId` | 예 | 문자열로 저장된 Report Builder 보고서의 ID입니다. 문자열로 전달된 양의 정수여야 합니다(예: `"1478"`). 숫자, 0, 음수, 10진수 또는 빈 값을 보내면 오류가 반환됩니다. |
| `description` | 아니오 | 작업에 대해 선택한 항목에 대한 설명입니다. |
| `callbackUrl` | 아니오 | 작업 완료 시 호출할 URL입니다. 다른 작업 유형과 동일한 방식으로 작동합니다. |
| `payload.filters` | 아니오 | 아래 섹션을 참조하십시오. |

### 날짜 필터 재정의(선택 사항) {#override-date-filter}

```json
"payload": {
  "reportId": "1478",
  "filters": [
    { "columnName": "L2 Quiz - Response - Timestamp", "operator": "gte", "val": "2026-11-15T00:00:00.000Z" }
  ]
}
```

* 이 실행에만 보고서의 저장된 날짜 필터가 바뀝니다. 내보내기는 작업이 실행되는 시간까지 `val`(포함)을(를) 포함합니다.
* `columnName`은(는) `<Dataset name> - <Field name>` 형식을 사용합니다. 보고서에 이미 있는 날짜 필터와 일치해야 합니다. 대/소문자를 구분하지 않지만 간격과 하이픈은 정확히 일치해야 합니다.
* `operator`은(는) 선택 사항이며 `gte`만 허용됩니다.
* `val`은(는) 지난 7일 이내의 ISO 8601 UTC 시간입니다. 시간은 두 번째 시간까지 잘립니다.
* 여러 열을 재정의할 수 있습니다. 빈 목록은 저장된 필터가 사용되었음을 의미합니다.
* 사용 사례: 이전 내보내기가 끝난 지점에서 시작되는 일일 증분 내보내기.

### 작업을 생성할 때 반환된 오류

| 원인 | 메시지 |
|---|---|
| `reportId`개 없음 | `reportId is required` |
| `reportId`은(는) 양의 정수 문자열이 아닙니다. | `reportId must be a positive integer string` |
| ISO 형식이 아닌 날짜 | `filters.val must be in ISO format, e.g. 2020-01-01T18:30:00.000Z` |
| 7일 이상 또는 향후 | `filters.val must be within the last 7 days` |
| `gte` 이외의 연산자 | `filters.operator must be gte` |
| 동일한 열이 두 번 제공됨 | `Duplicate filter column: <column>` |
| 보고서의 열이 필터가 아닙니다. | `Unsupported custom report filter column: <column>` |
| 동일한 보고서에 대한 작업이 아직 실행 중입니다. | `There exists an similar job with id = <jobId> which has not finished yet` |

작업이 실행될 때 저장된 보고서 정의의 문제만 감지됩니다. 이 경우 작업 상태가 `Failed`이(가) 되며 이유가 반환되지 않습니다.

### 보고서 요구 사항

보고서가 다음 조건을 충족하지 않으면 작업이 실패하고 오류 메시지가 표시됩니다.

* 보고서 정의에는 상대 날짜 필터(예: 최근 7일)가 포함됩니다.
* 보고서의 모든 날짜 필터는 하나가 아닌 7일 이하를 포함해야 합니다.
* 시작 및 종료 날짜가 설정된 고정 날짜 범위는 지원되지 않으며 작업이 실패합니다.
* 날짜 필터가 없는 보고서는 실패합니다. 여기에는 날짜 필드가 없는 데이터 집합에 빌드된 보고서가 포함됩니다.

>[!NOTE]
>
>POST 요청이 즉시 검증됩니다. 잘못된 요청이 HTTP 400으로 거부되었으며 이유는 `source.info`에 있습니다.

### 작업 상태를 확인하고 보고서를 다운로드합니다

**엔드 포인트**

```
GET /primeapi/v2/jobs/{jobId}
```

응답에는 다른 작업 유형과 동일한 구조가 사용됩니다. 작업이 완료되면 `status.code`은(는) `Completed`이고 `status.data.s3Url`에 다운로드 링크가 포함됩니다.

```json
{
  "data": {
    "type": "job",
    "id": "12345",
    "attributes": {
      "jobType": "generateCustomReport",
      "payload": {
        "reportId": "1478"
      },
      "status": {
        "code": "Completed",
        "data": {
          "s3Url": "valid for 7 days"
        }
      }
    }
  }
}
```

API에서 `Submitted`, `Completed` 및 `Failed`을(를) 반환합니다. 파일이 이름이 `report.csv`인 단일 CSV입니다.

>[!NOTE]
>
>다운로드 URL은 7일 동안 유효합니다. 작업이 완료되는 즉시 파일을 다운로드합니다.

>[!IMPORTANT]
>
>링크가 있으면 누구나 로그인하지 않고도 파일을 다운로드할 수 있습니다. 포함된 데이터를 그대로 링크를 처리합니다.

**실패한 작업 샘플**

```json
"status": { "code": "Failed" }
```

### 제한

한 번에 하나의 보고서에 대한 `generateCustomReport` 작업만 실행할 수 있습니다. 첫 번째 요청이 완료될 때까지 두 번째 요청이 거부됩니다.

### L2 퀴즈 보고서 출력

Report Builder의 L2 퀴즈 데이터 집합에서 보고서를 만들고 `generateCustomReport`을(를) 사용하여 내보내면 출력에는 다음과 같은 특성이 있습니다.

* 출력은 이름이 `report.csv`인 단일 CSV 파일입니다. 모듈은 파일의 열입니다. 강의를 선택하면 보고서에는 퀴즈 모듈만 반환됩니다.
* 각 행은 한 질문에 대한 한 학습자의 응답을 한 번에 나타냅니다.
* 표준 Report Builder 간격(약 15분마다)으로 데이터가 새로 고쳐집니다.
* 날짜 및 시간 값이 계정의 표준 시간대에 있습니다. 열 머리글에 표준 시간대가 표시됩니다(예: `L2 Quiz - Response - Timestamp (America/Argentina/Salta)`).

### L2 퀴즈 데이터 세트의 필드

| 카테고리 | 필드 |
|---|---|
| Prime에서 | 사용자 ID |
| 강의 | 강의 ID, 강의 인스턴스 ID, 강의 이름 |
| 모듈 | 모듈 ID, 모듈 이름, 모듈 버전 |
| 질문 | 질문 ID, 질문 텍스트, 정답, 상호 작용 유형 |
| 응답 | 응답 응답, 달성 점수, 가능한 최대 점수, 정답, 응답 타임스탬프 |
| 시도 횟수 | 시도 횟수 |

>[!NOTE]
>
>L2 퀴즈 데이터 집합은 다른 Report Builder 데이터 집합에 연결되지 않습니다. 학습자 이름, 이메일, 관리자 및 사용자 정의 속성은 이 보고서에서 사용할 수 없습니다. 행을 학습자와 일치시키려면 사용자 ID를 사용합니다.

`generateCustomReport`을(를) 사용하여 다른 Report Builder 데이터 집합에 빌드된 보고서를 내보낼 수도 있습니다. 출력에서 사용할 수 있는 필드는 데이터 세트에 따라 다릅니다.

## Zoom 커넥터 생성 및 관리 API

이러한 API를 사용하여 Adobe Learning Manager에서 Zoom 연결을 관리할 수 있습니다. 기존 연결을 검색하고, Zoom 자격 증명을 저장하고, 연결을 생성 또는 업데이트하고, 사용자 그룹 및 사용자 정의 역할에 대한 액세스 권한을 구성하고, 연결을 활성화 또는 비활성화할 수 있습니다.

### Zoom 커넥터 API 설정

Zoom 커넥터를 설정하고 관리하려면 4개의 API 호출이 필요합니다. 다음 순서로 만듭니다.

| 단계 | API | 기능 |
|---|---|---|
| 1 | `POST /ctr/authcred/uuid/20012` | Zoom 자격 증명을 저장합니다. |
| 2 | `POST /ctr/app/esconnect` | 확대/축소 연결을 만들거나 기존 연결을 업데이트합니다. |
| 3 | `PUT /ctr/xtsa/{connectionId}/access` | 연결을 사용할 수 있는 사용자 그룹 및 사용자 지정 역할을 설정합니다. |
| 4 | `POST /ctr/xtsas/{connectionId}/enable` | 연결을 설정하거나 해제합니다. |

>[!NOTE]
>
>이러한 API는 로그인한 통합 책임자 세션을 사용합니다. API 키 또는 OAuth 토큰을 사용하지 않습니다.

### 기본 URL 및 규칙

Zoom 커넥터 API는 다음 규칙을 사용합니다.

| 항목 | 값 |
|---|---|
| 기본 URL | `https://learningmanagerstage1.adobe.com` |
| 콘텐츠 유형 | `application/json` |
| 인증 | 로그인한 통합 책임자의 세션 |
| 필수 헤더 | `content-type`, `accept`, `x-acap-caller-role: ROLE_INTEGRATIONADMIN`, `x-csrf-token` 및 `Cookie` |
| 확대/축소를 위한 통합 카탈로그 UUID | `20012` |
| 연결 제한 | 50개의 확대/축소 연결 |

`x-csrf-token` 값은 통합 관리자 페이지 HTML에 `csrfToken`(으)로 포함됩니다. `Cookie` 헤더는 로그인한 관리자의 세션 쿠키를 전달합니다.

### 시작하기 전에

- 통합 책임자로 로그인합니다.
- Zoom 서버-서버 OAuth 앱을 만듭니다. 해당 클라이언트 ID, 클라이언트 암호 및 계정 ID를 기록해 둡니다. 또한 Zoom 수퍼 관리자의 이메일 주소가 필요합니다.
- `GET /ctr/xtsas/canCreateAccount/25`(으)로 전화 걸기. 다른 Zoom 연결을 만들 수 있으면 `true`이(가) 반환됩니다.

### 1단계: Zoom 자격 증명 저장 {#save-credentials}

연결을 만들거나 업데이트하기 전에 이 API를 호출합니다. 커넥터가 Zoom에 연결하는 데 사용하는 자격 증명을 저장합니다.

```
POST /ctr/authcred/uuid/20012
```

기존 연결을 업데이트하려면 `connectionId` 쿼리 매개 변수를 추가하십시오.

```
POST /ctr/authcred/uuid/20012?connectionId={connectionId}
```

요청 본문은 JSON 텍스트로서의 자격 증명입니다. 중첩된 개체가 아닌 JSON을 포함하는 JSON 문자열입니다. 외부 견적을 포함합니다.

| 키 | 설명 |
|---|---|
| `clientId` | Zoom 앱의 클라이언트 ID입니다. |
| `clientSecret` | Zoom 앱의 클라이언트 비밀입니다. 이 값은 민감합니다. |
| `accountId` | Zoom 계정 ID. |
| `superAdmin` | Zoom 슈퍼 관리자의 이메일 주소입니다. |

샘플 요청 본문:

```
"{\"clientId\":\"<ZOOM_CLIENT_ID>\", \"clientSecret\":\"<ZOOM_CLIENT_SECRET>\", \"accountId\":\"<ZOOM_ACCOUNT_ID>\", \"superAdmin\":\"<ADMIN_EMAIL>\"}"
```

샘플 `200 OK` 응답:

```json
{
  "code": 0,
  "description": "Success"
}
```

`code: 0`은(는) 자격 증명이 저장되었음을 의미합니다.

### 2단계: Zoom 연결 만들기 또는 업데이트 {#create-connection}

이 API는 Zoom 연결을 생성합니다. 동일한 끝점이 기존 연결도 업데이트합니다.

```
POST /ctr/app/esconnect
```

요청 본문에는 다음 필드가 있습니다.

| 필드 | 필수 | 설명 |
|---|---|---|
| `UUID` | 예 | 통합 카탈로그 UUID. 확대/축소에 `20012`을(를) 사용합니다. |
| `listOfConnections` | 예 | 만들 연결입니다. 한 개 항목 보내기. |
| `listOfConnections[].name` | 예 | 커넥터의 표시 이름입니다(예: `Zoom_Partner_X`). |
| `listOfConnections[].tag` | 예 | 커넥터를 만들 때 빈 문자열(`""`)을 보냅니다. 업데이트할 때 생략합니다. |
| `listOfConnections[].credentialsJson` | 예 | JSON 텍스트인 자격 증명입니다. 1단계에서 보낸 것과 동일한 문자열을 사용합니다. |
| `listOfConnections[].schedules` | 예 | 동기화 일정입니다. `objectUUID` 10002, `priority` 1 및 `type` 1을(를) 보냅니다. |
| `listOfConnections[].id` | 업데이트만 | 업데이트할 연결의 ID입니다(예: `3474737`). |

샘플 요청 본문:

```json
{
  "UUID": 20012,
  "listOfConnections": [
    {
      "name": "Zoom_Example",
      "tag": "",
      "credentialsJson": "{\"clientId\":\"<ZOOM_CLIENT_ID>\", \"clientSecret\":\"<ZOOM_CLIENT_SECRET>\", \"accountId\":\"<ZOOM_ACCOUNT_ID>\", \"superAdmin\":\"<ADMIN_EMAIL>\"}",
      "schedules": [
        { "objectUUID": 10002, "priority": 1, "type": 1 }
      ]
    }
  ]
}
```

샘플 `200 OK` 응답:

```json
[3474737]
```

응답은 새 연결의 ID가 포함된 JSON 배열입니다. 3단계와 4단계 및 후속 호출에서 이 ID를 사용합니다.

### 비교 생성 및 업데이트

| 차이 | 생성을 | 업데이트 |
|---|---|---|
| `listOfConnections[].id` | 보내지 않음 | 연결 ID |
| `listOfConnections[].tag` | `""` | 보내지 않음 |
| 1단계에서 자격 증명 호출 | `POST /ctr/authcred/uuid/20012` | `POST /ctr/authcred/uuid/20012?connectionId={id}` |

### 3단계: 연결을 사용할 수 있는 사용자 설정 {#set-access}

이 API는 연결을 사용할 수 있는 사용자 그룹 및 사용자 지정 역할을 정의합니다.

```
PUT /ctr/xtsa/{connectionId}/access
```

경로에서는 하나의 연결에 단수 `xtsa`을(를) 사용합니다. plural `xtsas`은(는) 연결 컬렉션입니다.

요청 본문은 JSON 배열입니다. 각 항목은 하나의 사용자 그룹 또는 사용자 정의 역할에 대한 액세스 권한을 부여합니다.

| 필드 | 필수 | 설명 |
|---|---|---|
| `accessType` | 예 | `USER_GROUP` 또는 `CUSTOM_ROLE`. |
| `accessId` | 예 | 문자열로 된 사용자 그룹 또는 사용자 정의 역할의 ID입니다. |

샘플 요청 본문:

```json
[
  { "accessType": "USER_GROUP", "accessId": "<groupId>" },
  { "accessType": "CUSTOM_ROLE", "accessId": "<roleId>" }
]
```

액세스 목록이 저장되면 API에서 본문이 없는 `204 No Content`을(를) 반환합니다.

>[!NOTE]
>
>이 요청은 전체 액세스 목록을 대체합니다. 추가되지 않습니다. 몸 안에 없는 모든 것은 접근 권한이 상실됩니다. 모든 액세스 권한을 제거하려면 빈 배열(`[]`)을 보내십시오.

### 4단계: 연결 활성화 또는 비활성화 {#enable-disable}

이 API는 연결을 설정하거나 해제합니다. 연결 상태를 변경해야 할 때마다 연결을 만든 후 사용합니다.

```
POST /ctr/xtsas/{connectionId}/enable
```

경로에는 목록 및 삭제 호출과 같은 plural `xtsas`이(가) 사용됩니다. 3단계의 액세스 호출은 단수 `xtsa`을(를) 사용합니다.

| Path 매개 변수 | 유형 | 설명 |
|---|---|---|
| `connectionId` | 번호 | 연결의 ID입니다. `GET /ctr/xtsas`이(가) 반환한 `id`이며 2단계에서 반환된 ID입니다. |

요청 본문에는 다음 필드가 있습니다.

| 필드 | 유형 | 필수 | 설명 |
|---|---|---|---|
| `objectUUID` | 번호 | 예 | 연결의 동기화 개체입니다. 2단계에서 `schedules[].objectUUID`에 보낸 값과 동일한 `10002`을(를) 사용합니다. |
| `operation` | 번호 | 예 | `1`을(를) 보냅니다. |
| `val` | 부울 | 예 | 연결의 새 상태입니다. 연결을 사용하지 않도록 설정하려면 `false`을(를) 보내세요. `true`을(를) 보내 활성화하세요. |

연결을 비활성화하는 샘플 요청 본문:

```json
{
  "objectUUID": 10002,
  "operation": 1,
  "val": false
}
```

연결을 활성화하는 샘플 요청 본문:

```json
{
  "objectUUID": 10002,
  "operation": 1,
  "val": true
}
```

연결을 비활성화하는 샘플 요청:

```bash
curl -X POST 'https://learningmanagerstage1.adobe.com/ctr/xtsas/<connectionId>/enable' \
  -H 'accept: application/json' \
  -H 'content-type: application/json' \
  -H 'x-acap-caller-role: ROLE_INTEGRATIONADMIN' \
  -H 'x-csrf-token: <CSRF_TOKEN>' \
  -H 'Cookie: <SESSION_COOKIES>' \
  --data '{"objectUUID":10002,"operation":1,"val":false}'
```

새 상태를 확인하려면 `GET /ctr/xtsas`을(를) 호출하고 `id`까지 연결을 찾은 다음 해당 `enabled` 플래그를 확인하십시오.

>[!NOTE]
>
>`x-acap-caller-role` 헤더는 활성 프로필의 역할과 일치해야 합니다. 이러한 API의 경우 `ROLE_INTEGRATIONADMIN`을(를) 사용하십시오.

### 연결을 만든 후 관리

연결 ID로 다음 호출을 사용할 수 있습니다.

| 용도 | 통화 |
|---|---|
| 연결 사용 또는 사용 안 함 | `POST /ctr/xtsas/{connectionId}/enable` |
| 한 연결의 액세스 목록 읽기 | `GET /ctr/xtsa/{connectionId}/access` |
| 모든 확대/축소 연결에 대한 읽기 액세스 | `GET /ctr/xtsas/access?UUID=20012` |
| 모든 연결을 나열합니다. 확대/축소 연결에 `extsysRefId` 25가 있습니다. | `GET /ctr/xtsas` |
| 연결 보기 | `GET /ctr/app/connection/{id}/object/10002` |
| 연결 영구 삭제 | `DELETE /ctr/xtsas/{id}` |

>[!NOTE]
>
>view 호출은 클라이언트 시크릿을 일반 텍스트로 반환합니다. 클라이언트 암호를 민감한 항목으로 처리하고 노출된 경우 회전합니다. HAR 파일 및 복사된 cURL 명령을 포함하여 세션 쿠키, CSRF 토큰 또는 자격 증명을 커밋하거나 공유하지 마십시오.

### 통합에서 다음 API 사용

일반적인 사용 사례는 새 계정 또는 파트너에 대한 Zoom 커넥터 자동 설정입니다.

1. 다른 연결을 만들 수 있는지 확인하려면 `GET /ctr/xtsas/canCreateAccount/25`에 문의하세요.
2. Zoom 자격 증명으로 `POST /ctr/authcred/uuid/20012`을(를) 호출합니다.
3. 커넥터 이름, 동일한 자격 증명 문자열 및 동기화 예약으로 `POST /ctr/app/esconnect`을(를) 호출합니다. 응답에서 연결 ID를 읽습니다.
4. 연결을 사용할 수 있는 사용자 그룹 및 사용자 지정 역할로 `PUT /ctr/xtsa/{connectionId}/access`을(를) 호출합니다.
5. `val`을(를) `true` 또는 `false`(으)로 설정하여 `POST /ctr/xtsas/{connectionId}/enable`에 전화하여 연결을 사용하거나 사용하지 않도록 설정하십시오. 그런 다음 `GET /ctr/xtsas`을(를) 호출하고 `enabled` 플래그를 확인하여 상태를 확인합니다.
6. 자격 증명을 나중에 변경하려면 연결 ID로 2단계와 3단계를 반복합니다.


