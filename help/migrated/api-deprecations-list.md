---
jcr-language: en_us
title: Adobe Learning Manager에서 API 사용 중단
description: Adobe Learning Manager의 API가 발전함에 따라 API는 주기적으로 재구성되거나 업그레이드됩니다. API가 발전하면 이전 API는 더 이상 사용되지 않으며 결국 제거됩니다. 이 페이지에는 더 이상 사용되지 않는 API 버전에서 보다 안정적이고 새로운 API 버전으로 마이그레이션할 때 알아야 하는 정보가 포함되어 있습니다.
contentowner: saghosh
exl-id: 0fe9a3cb-9114-42d6-81ae-1a4f28c984fa
source-git-commit: 670d0477b246af2a0257e41eca799817e391b348
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 32%

---

# Adobe Learning Manager에서 API 사용 중단 및 변경 사항

## Adobe Learning Manager 2024년 3월 릴리스의 API 중단

<!-- ### Changes in Rate Limits

With the next release of Adobe Learning Manager, we're restructuring API rate limits for new accounts. For existing accounts, only the Admin APIs will be rate-limited. After 90 days (about 3 months), we will restructure rate limits for all APIs, but existing accounts will be whitelisted according to current usage. Existing accounts need to revisit their learner API usage. 

For new accounts, if they want to increase the rate limits, they must contact the Customer Success team of ALM. 

#### Which APIs will be rate limited 

For new accounts, all Admin, Learner, and Search APIs will have rate limits and burst enforced.  

The API burst rate or burst limit refers to the maximum number of requests allowed to be made to an API in a short burst within a limited timeframe. 

The following table lists the rate and burst limits for the APIs.

<table>
    <tr>
        <th>API</th>
        <th>Number of requests-RPM</th>
        <th>Number of requests-Burst</th>
    </tr>
    <tr>
        <td>Admin</td>
        <td>5</td>
        <td>5</td>
    </tr>
    <tr>
        <td>Learner</td>
        <td>20</td>
        <td>5</td>
    </tr>
    <tr>
        <td>Search</td>
        <td>50</td>
        <td>5</td>
    </tr>
</table>
-->

### 오프셋 제한 변경 사항

오프셋 값에 의해 검색되는 레코드가 많고 전체 성능이 저하되기 때문에 제한 사항을 적용합니다. **500** 기록. 다음 릴리스에서는 책임자와 학습자 모두 **GET 사용자** API에서 최대 값을 반환합니다. **500** 기록.

가져올 레코드가 더 필요하면 **GET 작업** API.

<!--### Exclude paths 

At present, Learning Manager APIs follow a graph data structure, which allows you to fetch data by traversing the API model through includes. Even though you could traverse an API up to seven levels, fetching the data using a single API call is computationally expensive. 

We recommend that all existing and new customers make small calls multiple times instead of one large call. This approach will prevent unwanted data from being loaded in the call. 

We want to enforce these restrictions on new accounts and maintain a whitelist of existing accounts.-->

#### 더 이상 사용되지 않는 경로

다음 경로는 사용되지 않습니다.

* /learningObject
   * 사용되지 않는 경로:
      * enrollment.loInstance.loResources.resources
      * instances.loResources.resources
   * 새 패스:
      * enrollment.loInstance.loResources
      * instances.loResources

* /learningObject/{id}
   * 사용되지 않는 경로:
      * enrollment.instances.subLoInstances.learningObject
   * 새 경로:
      * enrollment.instances.subLoInstances

* /등록
   * 사용되지 않는 경로:
      * loInstance.learningObject.enrollment
   * 새 경로:
      * loInstance.learningObject

* /learningObject/{id}
   * 사용되지 않는 경로:
      * instance.subLoInstances.learningObject.enrollment.loResourceGrades
   * 새 경로:
      * instance.subLoInstances

<!--### Instance summary count changes 

Currently, in the LO summary endpoint, you fetch the number of all possible instances. For example, for a course, you can view the number of enrollments and waitlists in the response for **GET /learningObjects/{loId}/instances/{loInstanceId}/summary**. You can then view the completionCount and enrollmentCount in the response. If the course is a VC or classroom, you can also view its seat limit and waitlist limit. 

The process of retrieving the completion and enrollment counts is computationally expensive, therefore the calculation is done on a request basis. If the data is not present in the cache, the data is reloaded, which is computationally intensive. If there are many users enrolling in a course, the counts will be large, and effectively impacts CPU performance. 

In the next release of Adobe Learning Manager, in the LO Instance summary endpoint, the completionCount, enrollmentCount, seatLimit, and waitlistCount are cached. The cached information persists till there are changes in enrollments or unenrollments. For counts exceeding 1000 enrollments, we'll assume the estimated counts, and invalidate the results for all existing and new accounts.

>[!NOTE]
>
>For counts, such as, completionCount, enrollmentCount, seatLimit, and waitlistCount exceeding1000, it's advisable to interpret them as estimates rather than precise figures, as these will be retrieved from cache.-->

### 이름순으로 정렬

Adobe Learning Manager의 다음 릴리스에서는 name 및 -name 이 다음 API의 정렬 필드에서 더 이상 사용되지 않습니다.

* GET /userGroups/{userGroupId}/users
* GET /users

>[!NOTE]
>
>모든 기존 및 새 계정에 대해 이름 및 -name을 기준으로 정렬하는 것은 더 이상 사용되지 않습니다.


## Adobe Learning Manager 2023년 11월 릴리스의 API 중단

### 플래그 재정의

Adobe Learning Manager의 2023년 11월 릴리스에서는 API에서 오버라이드 플래그를 중단했습니다. 재정의 플래그는 공개 API 사양의 일부가 아니며 백엔드 테스트용으로 제작된 것입니다. 이제 학습자 API에 대한 플래그가 중단됩니다. 그러나 해당 플래그는 책임자 API에서는 계속 유효합니다.

학습자 API에 대한 플래그를 해제하려는 이유는 재정의 플래그가 학습자 API를 통해 대량의 데이터를 가져오는 중이었기 때문입니다.

앞으로는 재정의 플래그가 있으므로, 다음의 학습자 API는 중단됩니다.

_/primeapi/v2/users?page[오프셋]=0(&amp;p)[제한]=10&amp;sort=id&amp;override=TRUE_

### 스킬 기반 새 권장 사항에 대한 API 변경 사항

Adobe Learning Manager는 고객 및 파트너가 활성화된 계정에 대한 권장 사항을 개선합니다. 이와 같은 권장 사항 알고리즘의 개선은 강의, 학습 경로, 인증 등에 대한 평가 알고리즘의 변경을 통해 콘텐츠 검색에 대한 더 나은 사용자 경험을 제공합니다.

알고리즘은 더 이상 피어 기반 추천을 허용하지 않습니다. 변경 사항은 기존 사용자에게는 영향을 주지 않지만 산업 정렬 옵션은 계속 존재합니다. 사용자 정의 옵션의 경우, Adobe Learning Manager에서는 더 이상 사용자 정의 피어 기반 선택을 허용하지 않습니다.

이제 피어 그룹은 계정이 되고 학습자는 그룹의 트렌딩 항목을 표시하는 문자열을 볼 수 있습니다. 모든 권장 사항은 설명 가능합니다. 예를 들어, 특정 주제에 관한 내용을 보는 경우, 스트립의 카드에 강의 이유가 표시됩니다.

### 알림 공지 보고서의 변경 사항

Adobe Learning Manager의 이전 릴리스에서는 알림 공지 보고서에 필터가 없습니다. Adobe Learning Manager에서 계정의 모든 알림을 다운로드했습니다.

2023년 11월 릴리스에는 지정된 기간 내에 알림을 다운로드할 수 있는 날짜 필터가 추가되었습니다.  단, 보고서는 지난 6개월 동안만 다운로드할 수 있습니다.

### GET /사용자 끝점에서 높은 오프셋 값의 사용 중단

시스템 성능을 개선하고 리소스 활용률을 보다 효과적으로 관리하기 위해 Adobe은 GET/사용자 끝점에서 두 항목에 대해 더 이상 사용되지 않는 높은 오프셋 값을 가집니다 **관리자** 및 **학습자** 범위. 다음을 사용하는 것이 좋습니다. **작업 API** 을 눌러 오프셋 값이 있는 레코드를 검색합니다.

