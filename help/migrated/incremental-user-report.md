---
description: 관리자는 증분 사용자 보고서 작업 API를 사용하여 지정된 날짜 범위 내에서 데이터가 변경된 사용자만 내보낼 수 있습니다. 이렇게 하면 전체 사용자 내보내기가 필요 없으며 신규 또는 업데이트된 사용자 레코드를 보다 효율적으로 동기화할 수 있습니다.
jcr-language: en_us
title: 증분 사용자 보고서(작업 API)
source-git-commit: d61e81b0df6a6043b938c65adaabecb5699c2ce9
workflow-type: tm+mt
source-wordcount: '1602'
ht-degree: 1%

---


# 증분 사용자 보고서(작업 API)

## 개요

Adobe Learning Manager의 증분 사용자 보고서는 관리자와 통합 개발자가 지정된 날짜 및 시간 범위 내에서 데이터가 변경된 사용자만 내보낼 수 있는 새로운 작업 API 기능입니다. 매번 전체 사용자 목록을 가져오는 대신 신규 또는 수정된 사용자만 포함하는 대상 분할 영역을 요청할 수 있습니다.

이 문서에서는 다음을 다룹니다.

- 증분 보고가 있는 이유와 그 사용 시기
- 변경 내용 추적 모델을 포함하여 기능의 작동 방식
- 증분 사용자 보고서를 위한 새 작업 API(페이로드, 매개 변수, 번호 매기기)
- 대규모 계정 처리 방법 (5,00,000명 이상의 사용자)
- 추적된 필드와 추적되지 않은 필드
- 제한 사항 및 목표 미달성

## 증분 보고를 사용하는 이유

이 섹션에서는 기능에 대한 동기를 설명하고 증분 또는 전체 내보내기가 통합에 가장 적합한지 결정하는 데 도움이 됩니다.

## 전체 사용자 내보내기 문제

현재 전체 사용자 내보내기(generateUsers 작업 유형)는 실행 시마다 계정의 모든 사용자를 반환합니다. 대기업 계정의 경우 다음과 같은 두 가지 중요한 문제가 발생합니다.

| 고객 | 사용자 볼륨 |
|----------|-------------|
| 고객 A | 210만 사용자 |
| 고객 B | 사용자 700만 명 |
| 고객 C | 100만 명 이상의 사용자 |
| 고객 D | 770만 사용자(마이그레이션) |


* 이 경우 내보내기 파이프라인은 데이터를 가져오고 처리하고 저장하는 동안 CPU 사용률이 약 90%로 실행됩니다.
* 다운스트림 대시보드(PowerBI, Salesforce, 사용자 정의 통합)는 매번 실행 시 변경되지 않은 사용자 레코드를 다시 인제스트하여 대역폭과 처리 시간을 낭비합니다.
* &#39;마지막 내보내기 이후 변경된 사용자는 누구입니까?&#39;라고 물을 방법이 없습니다. 를 참조하십시오.

## 증분 보고를 사용하는 경우

외부 시스템을 Adobe Learning Manager 사용자 데이터와 동기화된 상태로 유지해야 하는 경우 증분 내보내기를 사용합니다. 일반적인 사용 사례:

* 사용자 프로필 변경으로 기업 대시보드(PowerBI, Tableau, SFDC)를 최신 상태로 유지
* 역할, 상태 또는 메타데이터 변경 사항이 있는 다운스트림 ID 관리 시스템 제공
* 전체 재로드 대신 야간 또는 시간별로 델타 동기화 파이프라인을 실행합니다.
* 수백만 명의 사용자가 있는 계정의 API 로드 및 데이터 전송 비용 절감

신뢰할 수 있는 기준선이 필요한 경우(예: 첫 번째 설정 시 또는 동기화 간의 긴 간격 후) 전체 내보내기(generateUsers)를 사용합니다.

| 내보내기 모드 | 사용할 때... |
|-------------|-----------|
| 전체 내보내기(generateUsers) | 초기 부트스트랩, 사용자가 50,000명 미만인 계정, 누락된 동기화 기간 후 복구 |
| 증분 내보내기(generateUserIncrementalReport) | 정기적인 델타 동기화, 대규모 계정, 변경된 기록만 필요한 파이프라인 |

## 현재 전체 사용자 보고서

(generateUsers) 이 섹션은 참조를 위해 기존 작업 API 사용자 보고서를 문서화합니다. 이미 잘 알고 있는 경우에는 다음 섹션으로 건너뜁니다.

## 작동 방식

현재 사용자 CSV 보고서가 작업 API를 통해 작업으로 제출됩니다. Snaplogic 파이프라인은 작업을 선택하고 CAPTIVATE 데이터베이스(user, usergroup, usergroup_user 테이블)에 대해 MySQL 쿼리를 실행한 다음 CSV 파일을 생성합니다.

## 사용 가능한 필터

페이로드는 세 가지 선택적 필터를 지원합니다.

* `expandMetadata` - 메타데이터를 별도의 열로 내보내려면 true를 전달합니다.
* `fetchActiveUsers` - 활성 사용자만 내보내려면 true를 전달합니다.
* `peerAccountId` - 피어 계정에 대한 사용자 보고서를 생성합니다.

## CSV 열

내보낸 CSV에는 다음 열이 포함됩니다.

```
internalUserID, userEmail, customerDefinedUniqueUserId, name, managerEmail,

userType, state, excludedFromGamification, pointsEarned, profile, roles,

dateCreated, lastLoginDate, dateDeleted, uiLocale, contentLocale,

timeZoneCode, userSource, group, AF_location, AF_login, AF_externalaf,

lastSocialActivityDate
```

## 요청 페이로드

작업 유형: generateUsers. 관리자 역할만 해당됩니다.

```
{

  "data": {

    "type": "job",

    "attributes": {

      "description": "<description of your choice>",

      "jobType": "generateUsers",

      "payload": {

        "expandMetadata": "<true to export metadata as separate column>",

        "fetchActiveUsers": "<true to export ACTIVE users only>",

        "peerAccountId": "<peerAccountId for peer account report>"

      }

    }

  }

}
```

## 제한 사항

* 날짜 기반 필터링 없음 - 모든 실행은 모든 사용자를 내보냅니다.
* 대규모 계정에서는 실현 가능하지 않음 - 최대 100만 명의 사용자 파이프라인 리소스 소모
* 변동분 또는 델타 기능이 없습니다.

## 증분 사용자 보고서(generateUserIncrementalReport)

이 섹션에서는 M46에 도입된 새로운 증분 사용자 보고서 기능을 설명합니다. 이 문서의 주요 제목입니다.

## 증분 내보내기란 무엇입니까?

증분 내보내기는 추적된 데이터가 지정된 시작 및 종료 날짜-시간 창 내에서 변경된 사용자만 반환합니다. 백엔드는 각 사용자의 추적된 필드에 대해 마지막으로 수정된 타임스탬프를 저장한다. 특정 창에 대한 보고서를 요청하면 가장 최근의 변경 내용이 해당 창에 속하는 사용자만 포함됩니다.

## 변경 내용 추적 모델의 작동 방식

Adobe Learning Manager에서는 사용자의 추적된 필드가 변경될 때마다 업데이트되는 마지막으로 수정된 타임스탬프를 유지 관리합니다.

start_date_time 및 end_date_time이 있는 증분 보고서를 요청하면 마지막으로 수정한 타임스탬프가 [start_date_time, end_date_time] 내에 속하는 사용자가 반환됩니다. 사용자가 창 내와 창 이후 모두 수정된 경우(예: end_date_time 이후 다시 변경된 경우), 마지막으로 수정된 타임스탬프가 이제 창 외부에 있기 때문에 해당 사용자는 보고서에 포함되지 않습니다.

>[!NOTE]
>
>즉, 증분 내보내기가 지정된 창에 최신 변경 내용이 있는 사용자를 캡처합니다. 창 도중 어떤 시점에서든 영향을 받은 모든 사용자는 캡처되지 않습니다.

## 변경 내용을 추적한 필드

다음 필드 중 하나가 변경된 경우 사용자가 증분 보고서에 포함됩니다.

| 필드 | 노트 |
|---|---|
| userEmail | 사용자의 이메일 주소 |
| name | 사용자의 이름 |
| managerId | 사용자 테이블은 managerId를 저장합니다. managerId가 변경되면 필드에 변경된 것으로 플래그가 지정됩니다. 관리자의 이메일만 변경되는 경우(동일한 managerId) 이 필드는 변경된 것으로 간주되지 않습니다. |
| 문자 | 내부 또는 외부 사용자 분류 |
| 상태 | 활성 또는 삭제됨 |
| profile | 사용자 프로필 할당 |
| 역할 | 역할 추가 또는 삭제 |
| uiLocale | 사용자 인터페이스 로케일 |
| contentLocale | 콘텐츠 로케일 |
| timeZoneCode | 사용자 표준 시간대 |
| 활성 필드(AF_*) | 구성된 모든 활성 필드(예: AF_location, AF_login) |
| 메타데이터 | 구성된 모든 메타데이터 필드 |

## 변경 사항이 추적되지 않는 필드

다음 필드는 CSV 출력에 표시되지만 변경 시 증분 내보내기에 대한 포함은 트리거되지 않습니다.

* excludedFromGamification
* pointsEarned
* lastLoginDate
* dateDeleted
* dateCreated
* userSource
* lastSocialActivityDate

## 출력 형식

증분 CSV 보고서에는 전체 사용자 CSV 보고서와 동일한 열과 형식이 있습니다. 내보낸 사용자에 대해 변경된 필드에 관계없이 모든 활성 필드 및 메타데이터 열을 포함하여 모든 열이 동일한 순서로 표시됩니다.

>[!NOTE]
>
>새 활성 필드가 추가되거나 기존 필드가 제거되면 해당 변경의 영향을 받는 모든 사용자가 다음 증분 내보내기에 나타납니다. 새 활성 필드의 새 열은 보고서 끝에 추가되므로 열 위치에 입력된 기존 통합이 중단되지 않습니다.

## 증분 사용자 보고서를 위한 새 작업 API

증분 사용자 보고서는 작업 API를 사용하여 지정된 날짜 및 시간 기간 내에 추적된 데이터가 변경된 사용자를 포함하는 CSV 파일을 생성합니다. 큰 결과 집합의 경우 이 문서의 뒷부분에 설명된 것과 동일한 페이지 매김 모델을 사용합니다. 각 요청에서 동일한 날짜 창을 제출하고 이전 응답에서 받은 마지막 userId를 fromUserId로 전달하여 다음 청크를 검색합니다.

## 작업 유형

작업 유형: generateUserIncrementalReport

## 요청 페이로드

```
{

    "data": {

        "type": "job",

        "attributes": {

            "description": "description of your choice",

            "jobType": "generateUserIncrementalReport",

            "payload":{

                 "fullExport": <Pass true to export all users. If fullExport is true, fromDate and toDate are ignored>,

                 "expandMetadata": <Pass true to export metadata as separate columns>,

                 "fromDate": <Start of the change window in ISO format, for example 2020-01-01T18:30:00.000Z>,

                 "toDate": <End of the change window in ISO format, for example 2020-01-31T18:30:00.000Z>,

                 "fromUserId": <For paginated requests, pass the last userId received in the previous response>

            }

        }

   }

}
```

## 페이로드 매개 변수

| 매개 변수 | 유형 | 설명 |
|---|---|---|
| fromDate | 문자열(ISO 8601) | 증분 내보내기에 필요합니다. 변경 창의 시작 ISO 8601 형식을 사용합니다. |
| toDate | 문자열(ISO 8601) | 증분 내보내기에 필요합니다. 변경 창의 끝입니다. ISO 8601 형식을 사용합니다. |
| fromUserId | 문자열 | 선택 사항입니다. 페이지가 지정된 요청의 경우 이전 응답에서 받은 마지막 userId를 fromUserId로 전달합니다. 첫 번째 요청에는 이 매개 변수를 생략합니다. |
| expandMetdata | 부울 | 선택 사항입니다. true이면 메타데이터를 별도의 열로 내보냅니다. |

증분 내보내기의 경우 `fromDate` 및 `toDate`을(를) 전달하여 변경 창을 정의합니다. 결과 집합이 하나의 청크보다 큰 경우 동일한 `fromDate` 및 `toDate`을(를) 보내고 이전 응답에서 마지막 `userId`을(를) `fromUserId`(으)로 전달하여 페이지 매기기를 계속합니다. fullExport가 true이면 날짜 창이 무시되고 API가 전체 사용자 내보내기를 생성합니다.

## 대규모 계정 처리(50만 명 이상의 사용자)

사용자 보고서는 데이터 플랫폼 파이프라인을 사용하여 생성되며 큰 계정을 지원하기 위해 청크로 출력됩니다. 증분 내보내기가 500,000명 이상의 사용자를 포함하는 경우 보고서의 페이지가 지정됩니다.

## 번호 매기기 모델

큰 증분 내보내기에 대한 모든 페이지를 검색하려면 각 요청에서 동일한 startDateTime 및 endDateTime을 전달하고 이전 청크에서 받은 마지막 사용자의 userId를 fromUserId로 전달합니다. API는 전달된 fromUserId보다 큰 userId를 가진 다음 최대 500,000명의 사용자 집합을 반환합니다.

## 페이지 매김 작업 과정

1단계: fromUserId 없이 첫 번째 요청을 제출합니다.

```
// First request – no fromUserId

{

  "payload": {

    "startDateTime": "2026-05-01T00:00:00Z",

    "endDateTime": "2026-05-31T23:59:59Z"

  }

}
```

2단계: 첫 번째 청크(최대 500,000명의 사용자) 받기 응답의 마지막 userId를 확인합니다.

3단계: 다음 요청을 제출하여 fromUserId와 동일한 날짜 창과 이전 응답의 마지막 userId를 전달합니다.

```
// Subsequent request – pass last userId from previous response as fromUserId

{

  "payload": {

    "startDateTime": "2026-05-01T00:00:00Z",

    "endDateTime": "2026-05-31T23:59:59Z",

    "fromUserId": "<last userId from previous response>"

  }

}
```

4단계: 응답이 500,000개 미만의 레코드를 반환하여 마지막 페이지에 도달했음을 나타낼 때까지 반복합니다.

| 요청 | fromUserId 매개 변수 |
|---|---|
| 첫 페이지 | fromUserId 생략 |
| 두 번째 페이지 | 첫 페이지의 마지막 userId를 fromUserId로 전달 |
| 세 번째 페이지 | 두 번째 페이지의 마지막 userId를 fromUserId로 전달 |
| ... (계속) | ... |
| 마지막 페이지 | 응답에 포함된 레코드가 500,000개 미만입니다. |

>[!NOTE]
>
>단일 내보내기 실행에 대해 페이지화된 모든 요청에서 `startDateTime` 및 `endDateTime`이(가) 동일하게 유지되는지 확인하십시오. 날짜 창 중간 페이지 매기기를 변경하면 일관성 없는 결과가 발생합니다.

## 제한 사항

증분 사용자 보고서의 범위가 의도적으로 지정됩니다. 다음 기능은 범위를 벗어납니다.

* 사용자 감사 보고서 아님 - 변경된 특정 필드가 나열되지 않습니다.
* 이전/새 값 비교 없음 - 보고서에는 현재 필드 값만 표시됩니다.
* 변경당 타임스탬프 없음 - 개별 필드 수정 시간이 표시되지 않습니다.
* 변경 횟수에 대한 표시가 없습니다. 사용자가 한 번 수정되고 사용자가 10번 수정되는 경우 내보내기에 동일하게 나타납니다.
* 기존 보고서 형식은 변경되지 않습니다. CSV 열 구조는 전체 사용자 보고서와 동일합니다.

## 커넥터 통합

증분 사용자 보고서는 Adobe Learning Manager 커넥터(PowerBI, Salesforce 등)에서 일반 동기화 파이프라인에서 전체 사용자 보고서를 대체하기 위한 드롭인으로 사용하도록 설계되었습니다. 이렇게 하면 현재 generateUsers를 사용하는 커넥터가 다운스트림 데이터 스키마를 변경하지 않고 증분 모델로 마이그레이션할 수 있습니다.

* 출력 CSV는 전체 사용자 보고서와 열 호환됩니다.
* 커넥터는 델타 동기화를 위해 증분 보고서를 사용하고 부트스트랩 또는 복구를 위해 전체 보고서로 전환할 수 있습니다.
* 커넥터 통합 지원(PowerBI, SFDC)
