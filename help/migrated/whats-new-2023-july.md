---
title: 이 릴리스(2023년 7월)의 새로운 기능
description: Adobe Learning Manager의 새로운 기능과 개선 사항 알아보기
hidefromtoc: true
exl-id: c6f192b6-f377-47b2-9151-516ac8179543
source-git-commit: ebf4ea065ba799b957b8ce275fd1690f18b26556
workflow-type: tm+mt
source-wordcount: '2059'
ht-degree: 67%

---

# 이 릴리스(2023년 7월)의 새로운 기능

## 향상된 권장 사항

Adobe Learning Manager에 강의에 대한 새롭게 개선된 추천 시스템을 도입했습니다. 이 추천 기능은 AI 알고리즘과 제품, 역할, 레벨 등 사용자의 관심사를 활용해 개인화된 콘텐츠 추천을 제공한다.

자세한 내용은 [Adobe Learning Manager의 추천](recommendations-adobe-learning-manager.md)을 참조하십시오.

## 다중 등록

Adobe Learning Manager의 이번 릴리스에서는 학습자가 하나 이상의 기간에 둘 이상의 강의 인스턴스에 등록할 수 있도록 하는 학습자용 다중 등록을 도입합니다.

자세한 내용은 [다중 등록](/help/migrated/authors/feature-summary/courses.md)을 참조하십시오.

### 모바일 앱 또는 몰입형에서의 다중 등록

학습자는 모바일 앱/몰입형에서 다중 인스턴스에 등록할 수 없습니다. 모바일 앱 및 몰입형 모바일 웹에서는 다중 등록이 지원되지 않습니다.

>[!NOTE]
>
>다중 등록을 활성화하면 각 강의의 학습자 성적 증명서 보고서에 다중 행이 추가됩니다(각 인스턴스당 하나의 행).
>
>강의당 하나의 행만 예상하도록 보고 자동화를 설정한 경우 다중 등록 기능을 활성화하기 전에 보고 자동화에 필요한 조정을 수행해야 합니다.

### 다중 등록 인스턴스에서의 배지 형식

다중 등록 인스턴스에서 배지를 지원하기 위해 배지 형식이 `userId_badgeId_COURSE_courseId_courseInstanceId`(으)로 변경되었습니다.

### 헤드리스 모드를 사용하여 다중 등록에서 플레이어 실행

이번 릴리스에서는 헤드리스 플레이어와의 통신에 사용되는 라이브러리를 변경했습니다.

다중 등록에서는 개체 내에 래핑된 인수를 전달해야 합니다.

```
{{startplayer(argument_object) ,
where
argument_object=
{ loId = <loId>, accountId = <accountId>, userId =<userId>, accessToken = <accessToken>, domId = <elementId>, onModuleLoaded = fn(), isMultiEnrolled=<boolean>, instanceId=<instanceId> }
}}
```

## exavault 커넥터 사용 중단

이번 Adobe Learning Manager 릴리스에는 AWS Transfer 제품군의 SFTP 프로토콜을 사용하는 새 커넥터가 포함됩니다.

이러한 변경 사항은 ExaVault 커넥터를 대체하는 것으로 신규 사용자는 더 이상 ExaVault 커넥터를 사용할 수 없습니다. 오픈 소스 FTP 클라이언트를 사용하여 ExaVault를 대체할 수 있습니다. 자세한 내용은 [Adobe FTP 관리자에서 전환](transition-from-ftp-manager.md)을 참조하세요.

## 강의실 및 가상 세션에 대한 Outlook 미리 알림

학습자의 Outlook 일정에 추가된 Adobe Learning Manager에서 만든 강의실 및 가상 강의실 세션은 이제 Outlook의 미리 알림을 일관되게 지원합니다(Outlook의 모임 미리 알림과 유사).

## 강의에 스킬 할당 개선 사항

작성자용 스킬 할당 워크플로우가 개선되었습니다. 이제 강의 설정 페이지의 스킬 제안에 자동 완성 검색 기능이 추가됩니다. 작성자는 이제 처음 몇 글자를 입력하여 스킬을 검색할 수 있으며, 입력한 내용에 따라 제안이 스킬 드롭다운 목록에 표시됩니다. 이러한 개선 사항을 통해, 작성자는 전체 목록을 스크롤하여 스킬을 찾은 다음 강의에 할당할 필요가 없습니다.

## 관리자가 승인한 강의 워크플로우 개선

이제 관리자 승인 강의는 관리자와 학습자 모두에게 적절한 오류 정보를 제공합니다.

![오류 메시지](assets/error-messages.png)

이제 관리자는 강의 등록 요청을 승인할 수 없는 경우 정보(예: 등록 기한이 지남)와 함께 관련 오류 메시지를 확인할 수 있습니다. 학습자에게 오류와 교정 작업이 표시됩니다.

## 새 학습 계획 보고서

책임자/사용자 정의 책임자는 이제 계정의 모든 학습 계획 목록과 상태, 해당 사용자 그룹, 트리거 정보, 학습 계획 내에 포함된 강의/학습 경로 및 알림 메시지 정보와 같은 메타데이터를 내보낼 수 있습니다.

## 예정된 폐기 인스턴스를 추적하기 위한 보고서

교육 보고서에는 강의 또는 학습 경로에 있는 인스턴스의 완료 기한을 표시하는 추가 열이 포함되어 있어 책임자와 작성자가 중단될 인스턴스를 알고 필요한 조치를 취할 수 있습니다.

## 학습자의 강의 등급 캡처 개선 사항

사용자가 강의의 마지막 모듈을 완료하는 즉시 강의 평가 등급을 캡처하는 팝업이 표시됩니다.

![등급](assets/ratings.png)

## 전자 메일 템플릿 사용자 정의

Learning Manager의 전자 메일 템플릿에는 완전히 편집 가능한 섹션이 포함되어 있어 메시지 및 브랜딩 환경 설정에 따라 전자 메일 커뮤니케이션을 보다 유연하게 사용자 정의할 수 있습니다.

자세한 내용은 [전자 메일 템플릿 사용자 정의](/help/migrated/administrators/feature-summary/email-templates.md#flexibility-in-customizing-the-templates)를 참조하십시오.

## 예약 도우미 개선 사항

강의실 또는 가상 세션의 강사를 선택하는 프로세스를 세부적으로 조정합니다. 사용자 그룹 필터가 예약 도우미의 강사 필드에 추가되었습니다. 이제 작성자는 &#39;강사 스킬&#39; 및 위치, 언어, 지정 등과 같은 추가 매개 변수를 기반으로 강사를 필터링할 수 있습니다.

자세한 내용은 [스케줄링 도우미의 사용자 그룹 필터](/help/migrated/authors/feature-summary/courses.md#user-group-filter)를 참조하십시오.

## 학습 객체 중단 워크플로우의 개선 사항

이제 작성자는 강의의 **자동 중단** 날짜를 제공할 수 있습니다. 이렇게 하면 시간이 지남에 따라 카탈로그 인플레이션이 발생하지 않으며 강의로 돌아가서 수동으로 중단해야 하는 상황을 방지할 수 있습니다.

책임자는 계정 수준에서 &#39;중단된&#39; 학습 개체에 대한 액세스 특성을 결정할 수도 있습니다.

교육 보고서에는 각 학습 개체(설정된 경우)의 종료 날짜를 표시하는 새 열 **자동 종료 날짜**&#x200B;가 포함됩니다.

## 작성자별 카탈로그 레이블 값

작성자는 이제 강의를 만들거나 편집하는 동안 카탈로그 레이블에 대한 값을 추가할 수 있습니다. 책임자는 계정 레벨에서 이 기능을 활성화할 수 있습니다. 작성자가 새 카탈로그 레이블 값을 추가하면 이것이 자동 완성 검색의 일부가 됩니다.

![카탈로그 선택](assets/select-catalog.png)

## 책임자, 작성자 및 관리자 역할을 위한 강의 검색 개선

책임자, 작성자 및 관리자 역할에 대한 검색 개선 사항이 적용되었습니다. 이제 제목에 대한 키워드를 검색할 수 있습니다. 이 개선 사항은 강의, 학습 경로 및 인증에 적용됩니다.

## 마이그레이션 실패에 대한 알림

통합 책임자는 마이그레이션 중이나 PowerBI, FTP, Box 등의 데이터 커넥터를 사용하는 동안 가져오기 또는 내보내기 작업에 실패한 경우 전자 메일을 통해 알림을 받습니다.

## API를 통한 다중 관리자 구성

새 API가 다중 관리자 구성을 지원하기 위해 Managed Office API 집합에 추가되었습니다.

## 등록 API 개선 사항

대규모 일괄 등록을 지원하고 최적화하기 위한 등록 API가 개선되었습니다.

## 모바일 앱 - 오프라인 콘텐츠 보기

학습자는 오프라인 모드에서 콘텐츠를 다운로드하고 사용할 수 있습니다. 중첩되고 유연한 학습 경로는 오프라인 보기에서 지원되지 않습니다.

*이 릴리스에서는 영어 콘텐츠에 대해서만 오프라인 콘텐츠 보기가 지원됩니다.*

## 접근성

화면 판독기의 가독성을 최적화하는 개선 사항을 포함하여 접근성을 개선하기 위해 여러 개선 사항이 구현되었습니다.

## 모바일 앱 지원

다음 주요 릴리스에서는 Adobe Learning Manager 모바일 앱이 세 개의 최신 모바일 OS 버전만 지원합니다.

## LinkedIn의 콘텐츠

LinkedIn 콘텐츠가 Safari 브라우저의 몰입형 앱에서 예상대로 로드되지 않습니다. 해결 방법은 다음과 같습니다.

1. 장치에서 **[!UICONTROL 설정]** > **[!UICONTROL Safari]**&#x200B;를 선택합니다.
1. **사이트 간 추적 방지**&#x200B;를 사용 안 함으로 설정합니다.
1. **모든 쿠키 차단**&#x200B;을 사용 안 함으로 설정합니다.
1. 몰입형 앱에 로그인합니다.
1. 콘텐츠를 재생합니다.
1. 팝업을 허용합니다.

## 기타 개선 사항

### MS Teams에서 인스턴스 전환

학습자는 완료할 때까지 다른 강의 인스턴스로 전환하고 강의 진행률을 유지할 수 있습니다.

### MS Teams의 다중 등록 지원

학습자는 이전 인스턴스의 완료 상태와 관계없이 다른 강의 인스턴스에 등록할 수 있습니다. 이렇게 하면 학습자는 동일한 강의의 다중 인스턴스에 등록하게 됩니다.

### MS Teams에서 다중 등록을 지원하는 강의 노트

강의 노트는 다중 등록을 지원하기 위해 강의 인스턴스 레벨에서 사용할 수 있습니다.

## API 변경 사항

API 변경 사항에 대한 자세한 내용은 [Adobe Learning Manager API 참조](https://captivateprime.adobe.com/docs/primeapi/v2/)를 확인하십시오.

### 새로운 권장 사항에 대한 API 지원

**GET /계정**

prlRecommendation이 활성화된 경우 반환됩니다.

**요청**

`https://learningmanagerstage1.adobe.com/primeapi/v2/account`

**GET /data?filter.recommendationCriteria=product**

제품/항목 목록을 반환합니다. 결과는 모든 제품이 학습자에게 표시되는지 또는 제품/항목에 표시되는 카탈로그인지 확인하는 계정 설정에 따라 달라집니다.

**요청**

`https://learningmanagerqe.adobe.com/primeapi/v2/data?filter.recommendationCriteria=product&filter.showAllRecommenda`

**`GET /data?filter.recommendationCriteria=role`**

추천 역할 목록을 반환합니다.

**요청**

`https://learningmanagerqe.adobe.com/primeapi/v2/data?filter.recommendationCriteria=role&filter.showAllRecommendationCriteria=false`

**`GET /data?filter.recommendationCriteria=level`**

추천 역할 목록을 반환합니다.

**요청**

`https://learningmanagerqe.adobe.com/primeapi/v2/data?filter.recommendationCriteria=level&filter.showAllRecommendationCriteria=false`

**POST/검색/쿼리**

검색에는 쿼리의 제품 및 역할 매개변수도 포함됩니다. 쿼리와 본문은 변경되지 않습니다. 새 정렬 옵션을 추가합니다.

**요청**

`https://learningmanagerstage1.adobe.com/primeapi/v2/search/query?...`

**GET /학습 개체**

PRL 추천이 실시간인 경우 학습 개체 모델은 작성자 태그가 지정된 추천을 반환합니다.

**요청 URL**

`https://learningmanagerstage1.adobe.com/primeapi/v2/learningObjects?sort=recommendationScore&filter.recommendationProducts=...&filter.recommendationRoles=...&filter.excludeIgnoredRecommendations=true`

POST /learningObjects/query

다음 특성은 쿼리 호출 본문에서 지원됩니다.

```javascript {line-numbers="true"}
{
  "filter.announcedGroups": [
    "string"
  ],
  "filter.bookmarks": true,
  "filter.catalogIds": [
    "string"
  ],
  "filter.cityName": [
    "string"
  ],
  "filter.duration.range": [
    "string"
  ],
  "filter.effectiveModifiedDate.fromDate": "string",
  "filter.effectiveModifiedDate.toDate": "string",
  "filter.excludeIgnoredRecommendations": true,
  "filter.ignoreEnhancedLP": true,
  "filter.ignoreHigherOrderLOEnrollment": true,
  "filter.lang.subLOs": true,
  "filter.lang.twoLetterCode": true,
  "filter.learnerState": [
    "string"
  ],
  "filter.loFormat": [
    "string"
  ],
  "filter.loTypes": [
    "string"
  ],
  "filter.price": "string",
  "filter.priceRange": [
    "string"
  ],
  "filter.recommendationLevels": [
    "string"
  ],
  "filter.skill.level": [
    "string"
  ],
  "filter.skillName": [
    "string"
  ],
  "filter.tagName": [
    "string"
  ],
  "language": [
    "string"
  ],
  "preferredSortPartitionOrder": [
    "string"
  ],
  "showLoContentSource": true,
  "useCache": true,
  "filter.recommendationProducts": [
    {
      "levels": [
        "string"
      ],
      "name": "string"
    }
  ],
  "filter.recommendationRoles": [
    {
      "levels": [
        "string"
      ],
      "name": "string"
    }
  ]
}
```

**GET /recommendationProducts**

recommendationProduct Id로 PRL 제품을 검색합니다.

**요청 URL**

`https://learningmanagerstage1.adobe.com/primeapi/v2/recommendationProducts`

GET /recommendationRoles

recommendationProduct Id로 PRL 제품을 검색합니다. (학습 개체)의 표시된 역할만 반환됩니다.

**요청 URL**

`https://learningmanagerstage1.adobe.com/primeapi/v2/prlRecommendations/roles`

`POST /users/{id}/recommendationPreferences`

PRL 추천 환경 설정을 생성/다시 생성(덮어쓰기)합니다. 샘플 페이로드:

```javascript {line-numbers="true"}
{
    "data": {
        "id": "userRecommendationPreferences:14755328",
        "type": "userRecommendationPreferences",
        "attributes": {
            "products": [
                {
                    "id": "recommendationProduct:1",
                    "dateCreated": "2023-05-07T20:00:00.000Z"
                },
                {
                    "id": "recommendationProduct:37",
                    "dateCreated": "2023-05-07T21:00:00.000Z"
                }
            ],
            "roles": [
                {
                    "id": "recommendationRole:23",
                    "dateCreated": "2023-05-07'T'21:00:00.000'Z'"
                },
                {
                    "id": "recommendationRole:1",
                    "dateCreated": "2023-05-07'T'20:01:00.000'Z'"
                },
                {
                    "id": "recommendationRole:2",
                    "dateCreated": "2023-05-07'T'19:02:00.000'Z'"
                },
                 {
                    "id": "recommendationRole:3",
                    "dateCreated": "2023-05-07'T'18:02:00.000'Z'"
                },
                {
                    "id": "recommendationRole:20",
                    "dateCreated": "2023-05-07'T'17:02:00.000'Z'",
                    "levels": [
                        "INTERMEDIATE"
                    ]
                }
            ]
        }
    }
}
```

**`GET /users/{id}/recommendationPreferences`**

**요청 URL**

`https://learningmanagerstage1.adobe.com/primeapi/v2//users/123/recommendationPreferences`

**`DELETE /users/{id}/recommendationPreferences`**

제품 또는 역할에 대한 PRL 추천 사용자 환경 설정을 삭제합니다.

**요청 URL**

`https://learningmanagerstage1.adobe.com/primeapi/v2/users/123/recommendationPreferences?ids=recommendationRole:123,recommendationRole:234`

매개 변수 :

Ids = 삭제할 ID 목록

**PATCH /users/{id}/recommendationPreferences**

부분 추가/업데이트 샘플 페이로드:

```javascript {line-numbers="true"}
{
  "data": {
    "id": "userRecommendationPreferences:<USER_ID>",
    "type": "userRecommendationPreferences",
    "attributes": {
      "roles": [
        {
          "id": "recommendationRole:123",
          "type": "recommendationRole",
          "attributes": {
            "levels": [
              "INTERMEDIATE"
            ]
          }
        },
        {
          "id": "recommendationRole:123",
          "type": "recommendationRole",
          "attributes": {
            "levels": [
              "ADVANCED"
            ]
          }
        }
      ]
    }
  }
}
```

**POST /recommendationPreferences/learningObjects/{id}/ignore**

차단된 추천에 LO를 추가합니다.

**요청 URL**

`https://learningmanagerstage1.adobe.com/primeapi/v2/recommendationPreferences/learningObjects/{id}/ignored`

**`DELETE /recommendationPreferences/learningObjects/{id}/ignore`**

차단된 추천에서 LO를 삭제합니다.

**요청 URL**

`https://learningmanagerstage1.adobe.com/primeapi/v2/recommendationPreferences/learningObjects/{id}/ignored`

**`GET /users/{id}/recommendationStrips`**

prl 추천을 표시하는 데 사용할 모든 스트립을 검색합니다

### API에 대한 다중 등록 지원

**GET /primeapi/v2/account**

두 개의 새로운 속성이 추가되었습니다.

* instanceSwitchEnabled
* multiEnrollmentEnabled

**GET /users/{userId}/userNotifications**

새 메타데이터 속성의 알림에 강의 인스턴스 ID가 추가되었습니다.

**GET /학습 개체**

등록 관계는 1차 등록, 즉 최초 등록 또는 최초 완료만 표시합니다.

**`GET /learningObjects/{id}`**

등록 관계는 1차 등록, 즉 최초 등록 또는 최초 완료만 표시합니다.

**`GET /learningObjects/{loId}/instances/{loInstanceId}`**

새 관계가 LO 인스턴스 모델에 추가됩니다.

**`GET /enrollments/{id}`**

다중 등록 강의의 등록을 검색합니다.

**`DELETE /enrollments/{id}`**

특정 학습 개체 인스턴스에서 등록을 취소합니다.

**POST/등록**

다른 인스턴스에서의 등록을 지원합니다.

**GET/등록**

학습 개체의 1차 등록에 대해서만 등록을 가져옵니다.

**`GET /learningObjects/{id}/note`**

강의 노트 목록을 검색합니다.

**`GET /learningObjects/{lo_id}/instances/{loi_id}/note`**

강의 및 인스턴스에 대한 노트 목록을 검색합니다.

**`GET /learningObjects/{id}/resources/{loResourceId}/note`**

강의 리소스에 대한 노트 목록을 검색합니다.

**`POST /learningObjects/{id}/resources/{loResourceId}/note`**

지정된 강의 모듈에 노트를 추가합니다.

**`DELETE /learningObjects/{id}/resources/{loResourceId}/note/{noteId}`**

특정 인스턴스(loResource ID의 일부)에 대해 지정된 모듈에서 특정 노트를 삭제합니다.

**`GET /learningObjects/{id}/resources/{loResourceId}/note/{noteId}`**

지정된 인스턴스(loResourceId의 일부)에 대한 강의의 모듈에서 특정 노트를 검색합니다.

**`PATCH /learningObjects/{id}/resources/{loResourceId}/note/{noteId}`**

특정 인스턴스(loResource ID의 일부)에 대해 지정된 모듈의 특정 노트를 업데이트합니다.

**관리자 API 변경 내용**

* GET /users/{id}/enrollments
* POST /users/{id}/등록
* DELETE /users/{id}/enrollments/{enrollmentId}
* PATCH /users/{id}/enrollments/{enrollmentId}

### 끝점에 대한 필드 강제 적용

제품 및 역할은 적용된 경우에만 로드됩니다.

요청 예시

* GET `https://learningmanagerstage1.adobe.com/primeapi/v2/learningObjects/course%3A7418798?enforcedFields[learningObject]=products`
* GET `https://learningmanagerstage1.adobe.com/primeapi/v2/users/11255638/userBadges?include=model&page[offset]=0&page[limit]=10&sort=dateAchieved&enforcedFields[learningObject]=products,roles`

### 구현 간 API 변경 내용 검색(영어 로케일)

어간 생성은 한 단어를 그 어근 형태로 줄이는 과정이다. 이렇게 하면 검색 중 다양한 버전의 단어가 일치하게 됩니다. 예를 들어, 걷기와 걷기는 걷기라는 동일한 뿌리 단어로 구성될 수 있습니다. 한 단어에서 검색하면 두 단어 중 하나가 다른 단어와 일치합니다.

이 릴리스에서는 en_US, en_AU, en_GB 변형과 같은 영어 로케일에 대한 형태분석을 추가했습니다.

형태소 분석 속성에서는 검색 결과에 형태소 분석이 필요한지 여부를 언급합니다. 기본적으로 False로 설정됩니다.

API 쿼리 매개 변수:

* matchType=구문_and_match
* stemed=true

### V1 엔드 포인트 제거

이번 릴리스에서는 V1 API의 운영이 중단됩니다. 자세한 내용은 [개발자 설명서](/help/migrated/integration-admin/feature-summary/developer-manual.md)를 참조하십시오.

### 강의 등록 또는 등록 취소에 대한 알림

이 릴리스에서는 새 메타데이터 특성의 알림을 통해 강의 인스턴스 ID를 지원합니다.

### L1 피드백 지원

학습자는 다중 등록 기능의 각 인스턴스 레벨에서 피드백을 제공할 수 있습니다.

**API:** `POST /enrollments/{id}/l1Feedback`

### LO 적용 필드 목록

이 릴리스에서는 sections, prequisiteConstraints, prerequisiteLOs, subLOs, supplementaryResources, supplementaryLOs, instances, catalogLabels를 learningObject로 명시적으로 보내야 합니다.

For example,

`enforcedFields[learningObject]=prerequisiteLOs,instances`

### 다음 릴리스에서 사용이 중지되는 내용 알림

* 학습자 API에 대한 재정의 플래그.
* highlightResults=false의 기본값이 변경될 예정입니다. 또한 snippetType=courseName의 기본값을 변경하겠습니다.
* 검색 끝점에서 matchType=bool이 더 이상 사용되지 않습니다.
* autoCompleteMode에는 [사용되지 않음] 태그가 있으며 autoCompleteMode =false와 동일한 기능을 제공하기 위해 Match라는 matchType이 추가되었습니다.

### 다중 등록이 있는 배지 ID 형식

다중 등록 인스턴스 배지를 지원하기 위해 과정 배지의 형식을 `userId_badgeId_COURSE_courseId to userId_badgeId_COURSE_courseId_courseInstanceId`에서 변경하여 배지를 고유하게 식별합니다.

## 릴리스 정보

현재 및 이전 릴리스의 Learning Manager 웹 앱 및 장치 앱과 관련된 정보는 [릴리스 정보](/help/migrated/release-note/release-notes.md)를 참조하십시오.

## 이 릴리스의 알려진 문제 또는 제한 사항

이 릴리스의 제한 사항은 다음과 같습니다.

### 모바일 앱에서 오프라인 콘텐츠 보기

앱에서 오프라인 콘텐츠를 보는 동안 다음 사항은 지원되지 않습니다.

* 자유 선택 강의, 학습 계획 또는 인증
* 향상된 강의, 학습 계획 또는 인증.
* 멀티 퀴즈 지원 강의, 학습 계획 또는 인증
* Harvard Manage Mentor, Content Marketplace, GetAbstract 또는 LinkedIn 과정, 학습 계획 또는 인증.
* 전제 조건이 활성화된 학습 계획 및 인증서
* 중단된 강의, 학습 계획 또는 인증
* 기한이 만료된 강의, 학습 계획 또는 인증.
* 외부 인증서
* 전자상거래 지원 과정, 학습 계획 또는 인증.

오프라인 동기화에 문제가 있는 학습 경로, 강의 또는 인증은 다음과 같습니다.

* 모든 학습 경로
* 모든 내부 인증서
* POST 호출이 있는 콘텐츠

### 권장 사항

새 추천 시스템의 제품/역할/레벨에 대해 다음 사항은 지원되지 않습니다.

* Adobe Experience Manager, Teams, SFDC 및 임시 방문
* 모바일 앱은 추천 페이지의 제품 및 역할 편집을 지원하지 않습니다.
* 마이그레이션 중에는 매핑을 수행할 수 없습니다.
* linkedIn, 콘텐츠 마켓플레이스 및 기타 외부 강의, 학습 계획 또는 인증에 자동 태그 지정.
* 라이브 후 스킬 기반 또는 클래식으로 되돌리기
* 학습자 앱의 제품 및 역할 검색 메뉴
* 책임자 앱에서 강의, 학습 계획 또는 인증, 사용자의 일괄 매핑

## 시스템 요건

[Learning Manager 시스템 요건](/help/migrated/system-requirements.md)
