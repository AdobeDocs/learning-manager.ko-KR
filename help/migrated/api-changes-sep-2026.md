---
description: Adobe Learning Manager에서 개인화된 학습 경로를 나열하고, 검색하고, 등록하고, 삭제할 수 있는 공용 학습자 대상 API 엔드 포인트와 할당된 카탈로그를 통해 지정된 학습자가 하나 이상의 학습 개체에 직접 액세스할 수 있는지 확인하는 API 엔드 포인트.
jcr-language: en_us
title: 2026년 9월 API 변경 사항
source-git-commit: 328d899c05384ff522f7f6413d2a451139f066ee
workflow-type: tm+mt
source-wordcount: '1374'
ht-degree: 3%
---

# Adobe Learning Manager 2026년 9월 릴리스의 API 변경 사항

## 학습 객체의 카탈로그 액세스 확인을 위한 API

학습자가 학습 경로 또는 인증을 통해 해당 콘텐츠에 도달했는지 여부와 관계없이 현재 학습자가 하나 이상의 학습 개체에 대한 직접 카탈로그 액세스 권한을 보유하고 있는지 확인합니다.

### API의 목적

학습자가 학습 경로나 인증을 열 때 카탈로그를 통해 특정 강의에 직접 할당되지 않았더라도 그 안의 개별 강의를 찾아볼 수 있습니다. 이는 콘텐츠 발견을 지원합니다. 학습자는 학습 경로의 추적 여부를 결정하기 전에 학습 경로에 포함된 내용을 탐색할 수 있습니다.

그러나 이러한 방식으로 강의를 볼 수 있다고 해서 학습자가 강의에 자동으로 등록할 수 있는 것은 아닙니다. 등록은 학습자가 포함된 학습 경로를 통한 간접 액세스가 아니라 해당 특정 강의에 대한 직접 카탈로그 액세스 권한이 있는지 여부에 따라 달라집니다.

이 API를 사용하면 지정된 학습자에 대해 할당된 카탈로그를 통해 하나 이상의 학습 객체에 직접 액세스할 수 있는지 여부를 확인할 수 있습니다. 결과를 사용하여 등록 관련 UI를 제어합니다. 예를 들어 직접 카탈로그 액세스가 확인된 경우에만 등록 옵션을 표시하고, 두 경우 모두 강의 페이지 자체를 볼 수 있도록 유지합니다.

### 엔드 포인트

`GET /primeapi/v2/learningObjects/isMemberOfVisibleCatalogs`

| 속성 | 값 |
|---|---|
| **범위** | 학습자 읽기 액세스 |
| **응답 형식** | application/vnd.api+json |

### 쿼리 매개 변수

| 매개 변수 | 필수 | 유형 | 설명 |
|---|---|---|---|
| ids | 예 | 문자열 또는 배열 | 확인할 하나 이상의 학습 개체 ID. 단일 ID 또는 쉼표로 구분된 목록을 허용합니다. 요청당 최대 10개의 ID. |

### 요청 예시

```
GET /primeapi/v2/learningObjects/isMemberOfVisibleCatalogs?ids=course%3A2400159%2Ccourse%3A2400160%2Ccourse%3A2400161%2Ccourse%3A2400162
Accept: application/vnd.api+json
Authorization: oauth <access-token>
```

>[!NOTE]
>
>학습 개체 ID는 URL로 인코딩되어 있어야 합니다. course:2400159과 같은 ID의 콜론은 %3A로 인코딩되고 여러 ID를 구분하는 쉼표는 %2C로 인코딩됩니다.

### 예제 응답 - 200 OK

```json
{
  "course:2400162": false,
  "course:2400161": false,
  "course:2400160": true,
  "course:2400159": true
}
```

| 값 | 의미 |
|---|---|
| 참 | 호출하는 학습자는 이 학습 개체에 대한 직접 카탈로그 액세스 권한을 갖습니다. |
| false | 카탈로그를 통해 호출하는 학습자는 학습 개체를 직접 사용할 수 없습니다. 학습 경로 또는 액세스 권한이 있는 인증을 통해 연결 가능한 경우 학습자는 계속 볼 수 있습니다. |

### 응답 코드

| 상태 | 의미 |
|---|---|
| 200 | 요청이 성공했습니다. 응답에는 요청된 각 ID에 대한 결과가 포함되어 있습니다. |
| 400 | 일반적인 잘못된 요청 오류입니다. 예를 들어 10개 이상의 ID가 제공되었거나 ID의 형식이 잘못되었습니다. |
| 401 | 요청에 유효한 학습자 자격 증명이 없거나 잘못된 자격 증명으로 인해 액세스가 거부되었습니다. |

### 오류 응답 예

```json
{
  "status": "BAD_REQUEST",
  "title": "Bad request. Check url, params and headers",
  "source": {
    "info": "Either LO id is blank or not as per public api specification"
  }
}
```

### 통합에서 이 API 사용

일반적인 사용 사례는 학습자가 학습 경로에서 탐색하여 도달한 강의 페이지입니다. 학습자가 강의에 직접 카탈로그 액세스할 수 있는 경우에만 **등록** 동작을 표시하면서 강의 페이지 자체에 액세스할 수 있는 상태를 유지하려고 합니다.

1. 강의 페이지가 로드되면 강의의 학습 개체 ID로 이 엔드포인트를 호출합니다.
2. 해당 ID에 대해 응답이 true를 반환하면 **등록** 옵션을 표시합니다.
3. 응답이 false를 반환하면 강의 페이지, 제목, 설명 및 강의 세부 정보를 볼 수 있게 유지하지만 **등록** 옵션은 숨깁니다.

## 관리자 감사 추적 보고서용 작업 API {#apiaudittrailreport}

### API의 목적

관리자 감사 추적 보고서에는 다음에 대한 구성 변경 사항이 나열됩니다
Adobe Learning Manager 계정입니다. (예: 기본, 통합 또는
지정된 날짜 범위에 대한 고급 계정 설정. 감사 추적 보고서를 생성하려면 요청된 날짜 범위 및 설정 유형에 걸쳐 구성 변경 레코드를 쿼리하고 집계해야 합니다. 범위의 크기와 변경 볼륨에 따라, 동기 HTTP 요청의 시간 제한을 초과할 수 있습니다. 이 경우 클라이언트 또는 게이트웨이 시간 초과가 발생할 수 있습니다.

이를 방지하려면 일반 작업 API를 통해 보고서가 비동기적으로 생성됩니다.

1. **작업을 만듭니다.** 관리자는 보고서 유형, 날짜 범위 및 설정 유형을 지정하는 요청을 제출합니다. API는 보고서가 컴파일될 때까지 기다리지 않고 작업 ID를 즉시 반환합니다.

2. **작업을 폴링합니다.** 관리자는 주기적으로 작업을 ID로 검색하여 상태를 확인합니다. 작업이 완료되면 응답에는 해당 작업에 대한 결과 또는 참조가 포함됩니다.

### 기본 URL 및 규칙

| 항목 | 값 |
|---|---|
| 기본 경로 | `/primeapi/v2` |
| 콘텐츠 유형 | `application/vnd.api+json;charset=UTF-8`(JSON:API) |
| 인증 | Bearer OAuth 토큰, 계정 관리자로 범위 지정 |
| 계정 컨텍스트 | 호출 관리자의 계정을 식별하는 `x-acap-account` 헤더 |
| 폴링 | 고정 간격이 적용되지 않습니다. `status`이(가) 더 이상 `QUEUED` 또는 `IN_PROGRESS`이(가) 될 때까지 작업 상태 가져오기 끝점을 폴링합니다. |

### ID

작업을 만들 때 반환된 `id` 작업은 불투명 문자열입니다(예:
`4593`). 항상 만들기 작업을 통해 받은 `id` 값을 다시 전달하세요.
상태를 폴링할 때의 응답입니다. 구문 분석하거나 구문 분석하지 마십시오.

### 인증 범위

각 엔드포인트에는 다음 범위를 포함하는 OAuth 토큰이 필요합니다.
호출 사용자에게 계정 관리자 역할이 있어야 합니다.

- `admin:write` 보고서 작업 만들기(`ROLE_ADMIN` 필수)
- `admin:read`이(가) 작업의 상태 및 결과를 읽었습니다(`ROLE_ADMIN` 필수).

계정에 `ROLE_ADMIN`을(를) 보유하지 않은 호출자의 요청:
거부됨: [오류 처리](/help/migrated/api-changes-sep-2026.md#error-handling)를 참조하십시오.

### 끝점

#### 감사 추적 보고서 작업 만들기

`POST /primeapi/v2/jobs`

구성 변경 감사 추적 보고서를 생성하는 비동기 작업을 생성합니다.
지정된 날짜 범위 및 설정 유형에 대한 응답이 즉시 반환됩니다
작업 리소스가 `QUEUED` 상태인 경우 보고서 자체는
배경입니다.

범위: `admin:write`

| 매개 변수 | 위치 | 필수 | 설명 |
|---|---|---|---|
| `jobType` | body | 예 | 이 보고서의 경우 `generateConfigChangeAuditReport`이어야 합니다. |
| `payload.fromDate` | body | 예 | 보고 창의 시작, 오프셋(예: `2026-09-15T00:00:00.000+05:30`)이 있는 ISO-8601 |
| `payload.toDate` | body | 예 | 보고 창의 끝, 오프셋이 있는 ISO-8601(예: `2026-09-23T23:59:59.000+05:30`) |
| `payload.settingTypes` | body | 예 | 포함할 하나 이상의 설정 범주의 배열입니다. 지원되는 값은 `Basics`, `Integrations` 및 `Advanced`입니다. |

샘플 요청 본문

```json
{
  "data": {
    "type": "job",
    "attributes": {
      "jobType": "generateConfigChangeAuditReport",
      "payload": {
        "fromDate": "2026-09-15T00:00:00.000+05:30",
        "toDate": "2026-09-23T23:59:59.000+05:30",
        "settingTypes": ["Basics", "Integrations", "Advanced"]
      }
    }
  }
}
```

응답: `202 Created`. 응답 본문은 초기 상태의 작업 리소스입니다.
`QUEUED` 상태입니다.

```json
{
  "data": {
    "id": "4593",
    "type": "job",
    "attributes": {
      "jobType": "generateConfigChangeAuditReport",
      "status": "QUEUED",
      "dateCreated": "2026-09-23T18:12:04.000+05:30"
    }
  }
}
```

>[!NOTE]
>
>매우 큰 날짜 범위에 걸쳐 있는 `fromDate`/`toDate` 창 또는
>변경 기록이 긴 계정의 모든 설정 유형을 요청합니다.
>처리하는 데 시간이 오래 걸립니다. 대신 작업 상태 가져오기 끝점을 폴링합니다.
>고정 지연 후 보고서가 준비되었다고 가정합니다.

#### 감사 추적 보고서 작업의 상태 가져오기

`GET /primeapi/v2/jobs/{id}`

이전에 만든 작업의 현재 상태를 반환합니다. 작업 기간
아직 실행 중입니다. `attributes.status`은(는) `QUEUED` 또는 `IN_PROGRESS`이고
`attributes.result`이(가) 없습니다. 작업이 완료되면 `attributes.status`은(는)
`COMPLETED`, 보고서 위치가 `attributes.result`인 경우 또는
`FAILED`, 오류 세부 정보가 `attributes.error`에 있습니다.

범위: `admin:read`

| 매개 변수 | 위치 | 필수 | 설명 |
|---|---|---|---|
| `id` | 경로 | 예 | 작업을 만들 때 작업 ID가 반환되었습니다. |

작업이 아직 실행 중인 동안의 샘플 응답

```json
{
  "data": {
    "id": "4593",
    "type": "job",
    "attributes": {
      "jobType": "generateConfigChangeAuditReport",
      "status": "IN_PROGRESS",
      "dateCreated": "2026-09-23T18:12:04.000+05:30"
    }
  }
}
```

작업이 완료되면 응답 샘플

```json
{
  "data": {
    "id": "4593",
    "type": "job",
    "attributes": {
      "jobType": "generateConfigChangeAuditReport",
      "status": "COMPLETED",
      "dateCreated": "2026-09-23T18:12:04.000+05:30",
      "dateCompleted": "2026-09-23T18:12:41.000+05:30",
      "result": {
        "downloadUrl": "https://learningmanager.adobe.com/primeapi/v2/jobs/4593/download",
        "expiresAt": "2026-09-24T18:12:41.000+05:30"
      }
    }
  }
}
```

### 리소스 스키마

#### 작업 속성

| 필드 | 유형 | 설명 |
|---|---|---|
| `id` | 문자열 | 불투명 작업 ID |
| `jobType` | 문자열 | 이 보고서에 대한 `generateConfigChangeAuditReport` |
| `status` | 문자열 | `QUEUED`, `IN_PROGRESS`, `COMPLETED` 또는 `FAILED` |
| `dateCreated` | 문자열(ISO-8601) | 작업이 생성된 시기 |
| `dateCompleted` | 문자열(ISO-8601) | 작업이 완료되면 `status`이(가) `COMPLETED` 또는 `FAILED`이(가) 됩니다. |
| `payload` | 개체 | 작업이 생성된 요청 매개 변수(포함됨 - 아래 참조) |
| `result` | 개체 | 완료된 보고서를 다운로드할 위치: `status`이(가) `COMPLETED`인 경우에만 표시(포함 - 아래 참조) |
| `error` | 개체 | 오류 세부 정보: `status`이(가) `FAILED`인 경우에만 표시 |

#### 페이로드(포함, 만들기 요청 내)

| 필드 | 설명 |
|---|---|
| `fromDate` | 보고 창 시작 |
| `toDate` | 보고 창의 끝 |
| `settingTypes` | 보고서에 포함된 범주 설정: `Basics`, `Integrations`, `Advanced` |

#### 결과(완료된 작업 내에 포함됨)

| 필드 | 설명 |
|---|---|
| `downloadUrl` | 생성된 보고서를 다운로드할 수 있는 서명된 URL |
| `expiresAt` | `downloadUrl`이(가) 더 이상 유효하지 않을 경우 이 시간 이후에 새 링크를 가져오려면 새 상태 확인을 요청하십시오. |

### 오류 처리 {#audit-trail-report-error-handling}

다음 코드는 이러한 엔드포인트에 적용됩니다.

| HTTP 상태 | 오류 코드 | 발생 시 |
|---|---|---|
| 400 | `BAD_REQUEST` | `toDate`이(가) `fromDate`보다 이전이거나, `settingTypes`이(가) 비어 있거나, 지원되지 않는 값을 포함하거나, 날짜가 올바른 ISO-8601이 아닙니다. 끝점만 만듭니다. |
| 401 | `UNAUTHORIZED_ACCESS` | 토큰이 누락되었거나, 잘못되었거나, 만료되었습니다. |
| 403 | `FORBIDDEN` | 호출자가 계정에 `ROLE_ADMIN`을(를) 보유하고 있지 않습니다. |
| 400 | `OBJECT_DOESNT_EXIST` | Get by id: 작업이 없거나 ID의 형식이 잘못되었습니다. 두 경우 모두 동일한 응답으로 축소됩니다. |

오류 응답 예

```json
{
  "status": "BAD_REQUEST",
  "title": "Bad request. Check url, params and headers",
  "source": {
    "info": "toDate must be on or after fromDate"
  }
}
```

### 통합에서 이 API 사용

일반적인 사용 사례는 다음에서 관리자가 &quot;감사 추적 다운로드&quot; 작업을 진행하는 것입니다.
계정 설정 화면.

1. 관리자가 날짜 범위 및 하나 이상의 설정 유형을 선택하면
확인 후 해당 값으로 create-job 엔드포인트를 호출합니다.
2. 반환된 작업 `id`을(를) 저장하고 Get 작업 상태 끝점을
합리적인 간격(예: 몇 초마다).
3. `status`이(가) `QUEUED` 또는 `IN_PROGRESS`인 동안 진행 상태를 계속 표시합니다.
있습니다.
4. `status`이(가) `COMPLETED`이(가) 되면 `result.downloadUrl`을(를) 사용하여
`expiresAt`이(가) 통과하기 전에 관리자가 보고서를 다운로드합니다.
5. `status`이(가) `FAILED`이(가) 되면 관리자에게 `error`을(를) 표시하고 허용합니다.
다시 시도하십시오.
