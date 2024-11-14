---
jcr-language: en_us
title: Webhook 사용 안내서
description: Webhook 사용, 모범 사례 및 제한 사항에 대해 알아보기
contentowner: chandrum
source-git-commit: d7f7652c38c3eb623be083fd2fdde36eec25c1e4
workflow-type: tm+mt
source-wordcount: '3377'
ht-degree: 1%

---

# Webhook 사용 안내서

Webhook은 웹 응용 프로그램이 실시간으로 자동으로 서로 통신하는 방법입니다.

사용자가 정보를 요청하면 대기하는 기존 API와 달리 실시간 API는 그 순간 데이터를 공유한다. Webhook은 실시간 API로 작동하며 지정된 이벤트가 발생할 때마다 데이터를 즉시 공유하도록 지원합니다.

## 개체로 이동

Webhook 이벤트를 이해하려면 먼저 관련 엔티티와 이러한 이벤트의 트리거 조건을 인식해야 합니다.

### 학습 객체

다음은 학습 객체(강의, 학습 경로 또는 인증)에 대해 지원되는 이벤트입니다.

#### 초안

UI에서 학습 개체를 만들 때마다 학습 개체는 **초안** 모드로 시작됩니다. 이는 학습 객체가 아직 게시되지 않았으며 학습자에게 표시되지 않음을 의미합니다. 학습 개체가 초안으로 유지되는 한 **LEARNING_OBJECT_DRAFT** 이벤트가 트리거됩니다. 초안에 대한 연속 업데이트도 이 이벤트를 트리거합니다.

#### 업데이트

학습 개체가 게시되면 상태가 **초안**&#x200B;에서 **게시됨**(으)로 변경됩니다. 이 전환 중에 학습 개체가 **초안**&#x200B;에서 **게시**(으)로 수정되고 있으므로 Webhook은 **LEARNING_OBJECT_MODIFICATION** 이벤트를 생성합니다. 이후의 모든 LO 수정 및 업데이트는 **LEARNING_OBJECT_MODIFICATION** 이벤트도 트리거합니다.

학습 개체가 중단되면 **LEARNING_OBJECT_MODIFICATION** 이벤트도 트리거됩니다. 이 중단된 작업은 기본 인스턴스가 업데이트된 것으로 표시합니다. 상위 학습 개체가 중단된 상태이면 기본 인스턴스가 중단됩니다.

#### 삭제

학습 개체를 삭제하면 **LEARNING_OBJECT_DELETION** 이벤트가 생성됩니다. 이 이벤트는 학습 객체가 삭제되어 학습자가 더 이상 액세스할 수 없음을 나타냅니다.

실시간 이벤트 외에 학습 개체 이벤트에도 배치(비실시간) 상대가 있으며, 이는 **LEARNING_OBJECT_MODIFICATION_BATCH** 이벤트의 일부로 트리거됩니다. 이 이벤트는 마이그레이션 작업 과정을 통해 학습 객체를 생성하거나 수정하는 동안 발생합니다. 학습 객체 초안 및 삭제 작업은 마이그레이션을 통해 지원되지 않으므로 이러한 작업에 해당하는 초안 또는 삭제 이벤트가 없습니다.

### 학습 객체 인스턴스

학습 객체 인스턴스에 대해 지원되는 이벤트는 다음과 같습니다.

#### 업데이트

인스턴스가 만들어지면 **LEARNING_OBJECT_INSTANCE_MODIFICATION** 이벤트가 생성됩니다. Adobe Learning Manager의 학습 개체 인스턴스가 **초안** 상태가 아니므로 Adobe Learning Manager에서는 **LEARNING_OBJECT_INSTANCE_DRAFT 이벤트**&#x200B;를 지원하지 않습니다. 이 이벤트는 인스턴스가 생성, 수정 또는 폐기될 때마다 생성됩니다.

인스턴스가 생성, 업데이트 또는 중단될 때 생성되는 것 외에도 이 이벤트는 상위 학습 개체가 **중단됨**(으)로 표시될 때 자동으로 생성됩니다. 학습 개체가 중단되면 기본 인스턴스도 **중단**&#x200B;으로 표시해야 하기 때문입니다.

#### 삭제

인스턴스를 삭제하면 **LEARNING_OBJECT_INSTANCE_DELETION** 이벤트가 생성됩니다. 이 이벤트는 자가 진행식 모듈이 포함된 강의 인스턴스에만 적용되며 Adobe Learning Manager에서는 관리자가 모듈 유형이 자가 진행형인 강의 인스턴스만 삭제할 수 있습니다. Adobe Learning Manager은 학습 경로 인스턴스 또는 인증 인스턴스가 아닌 다른 유형의 강의 모듈에 대한 명시적 삭제를 지원하지 않습니다.

학습 개체 인스턴스에도 **LEARNING_OBJECT_INSTANCE_MODIFICATION_BATCH** 이벤트의 일부로 표시되는 비실시간 상대가 있습니다. 이 이벤트는 마이그레이션 작업 과정을 통해 학습 객체 인스턴스를 생성하거나 수정하는 동안 트리거됩니다. 학습 객체 인스턴스에 대한 초안 또는 삭제 작업은 마이그레이션에서 지원되지 않으므로 해당 초안 또는 삭제 이벤트를 사용할 수 없습니다.

### 등록

학습자가 등록 작업을 수행하면 실시간 등록 이벤트가 트리거됩니다. 학습 객체 유형에 따라 실시간 등록 이벤트는 다음 범주 중 하나에 해당할 수 있습니다.

* COURSE_ENROLLMENT
* LEARNING_PATH_ENROLLMENT
* CERTIFICATION_ENROLLMENT

등록 이벤트에는 이러한 실시간 이벤트 외에 배치 대응이 있습니다. 책임자, 관리자 또는 플랫폼에서 등록이 트리거될 때마다 실시간이 아닌 등록 이벤트가 트리거됩니다. 학습 객체 유형에 따라 일괄 등록 이벤트는 다음 중 하나가 될 수 있습니다.

* COURSE_ENROLLMENT_BATCH
* LEARNING_PATH_ENROLLMENT_BATCH
* CERTIFICATION_ENROLLMENT_BATCH

### 등록 취소

학습자가 등록 취소 작업을 수행하면 실시간 등록 취소 이벤트가 트리거됩니다. 학습 객체 유형에 따라 실시간 등록 취소 이벤트는 다음 범주 중 하나에 해당할 수 있습니다.

* COURSE_UNREGISTRATION
* LEARNING_PATH_UNREGISTRATION
* CERTIFICATION_UNENROLLMENT

이러한 이벤트 외에도 일괄 등록 취소 이벤트도 있습니다. 관리자, 관리자 또는 플랫폼에서 등록 취소를 표시할 때마다 비실시간 등록 취소 이벤트가 트리거됩니다. 학습 객체 유형에 따라 일괄 등록 취소 이벤트는 다음 중 하나가 될 수 있습니다.

* COURSE_UNENROLLMENT_BATCH
* LEARNING_PATH_UNENROLLMENT_BATCH
* CERTIFICATION_UNENROLLMENT_BATCH

### 완료

실시간 완료 이벤트는 학습자가 학습 객체를 완료할 때마다 트리거됩니다. 학습 객체 유형에 따라 실시간 완료 이벤트는 다음 범주 중 하나에 해당할 수 있습니다.

* COURSE_COMPLETED
* LEARNING_PATH_COMPLETE
* CERTIFICATION_COMPLETED

이러한 실시간 이벤트 외에도 일괄 완료 이벤트도 있습니다. 예를 들어, 책임자, 관리자 또는 플랫폼이 학습 객체를 완료로 표시하면 비실시간 완료 이벤트가 트리거됩니다. 학습 객체 유형에 따라 일괄 완료 이벤트는 다음 범주 중 하나에 속할 수 있습니다.

* COURSE_COMPLETED_BATCH
* LEARNING_PATH_COMPLETED_일괄 처리
* CERTIFICATION_COMPLETED_BATCH

### 학습자 진행률

학습자가 학습 객체에 등록하고 모듈을 시작할 때마다 진행 상황이 추적됩니다. 이 데이터는 **LEARNER_PROGRESS** 이벤트에 포함되어 있습니다. 진행률 추적이 실시간이 아닌 복잡한 집계 논리에 의존하기 때문에 이벤트는 최대 15분 지연될 수 있다.

### 통계

강의 인스턴스에 대한 좌석 또는 대기자 명단 가용성이 변경될 때마다 **CI_STATS** 실시간 이벤트가 트리거됩니다. 이 데이터는 인스턴스 레벨에서만 캡처됩니다. 또한 이 이벤트는 강의 및 인스턴스에 대한 특성인 시트 및 대기자 명단 가용성이므로 다른 학습 경로 또는 인증에 대해서는 트리거되지 않으며 강의에 대해서도 트리거됩니다.

## 이벤트 순서 지정

Adobe Learning Manager은 각 계정에 대해 이벤트가 정렬되도록 합니다. 그러나 등록 또는 완료와 진행 이벤트 간에 메시지를 상호 연결할 때 불일치가 있을 수 있습니다. 진행률 추적이 실시간이 아닌 복잡한 집계 논리에 의존하기 때문에 학습자 진행률 이벤트가 최대 15분 지연될 수 있기 때문에 발생하는 현상입니다. 또한 진행 이벤트는 다른 데이터 소스에서 제공되므로 등록 및 완료 이벤트와 관련하여 순서를 보장할 수 없습니다. 따라서 Adobe Learning Manager에서는 이러한 이벤트를 들을 때 클라이언트에 대한 모범 사례를 제공합니다.

완료 이벤트가 학습자 진행 이벤트보다 먼저 발생하는 경우 클라이언트는 학습자 진행 이벤트를 무시할 수 있습니다. 학습자 진행 이벤트는 최대 15분까지 지연될 수 있는 반면, 완료 이벤트는 진행 이벤트가 수신되기 전에 트리거될 수 있기 때문이다. 완료 이벤트를 수신한다는 것은 학습 객체가 종료되었음을 나타내므로 진행률이 100%에 도달했음을 의미한다.

드물지만 학습자 진행 이벤트 후에 등록 이벤트가 발생하는 경우 클라이언트는 등록 이벤트를 무시할 수 있습니다. 학습자가 학습 개체에 등록한 후에만 진행 상황을 추적할 수 있기 때문입니다. 즉, Progress 이벤트를 받으면 학습 객체가 시작되었음을 나타내며, 학습자는 등록에 성공한 후에만 진행됩니다.

## 실시간 이벤트 및 일괄 처리된 이벤트

특정 이벤트는 위에서 언급한 바와 같이, 실시간 및 비실시간 대응 관계를 갖는다. 실시간 이벤트를 언제 구독해야 하는지, 비실시간 이벤트를 언제 구독해야 하는지에 대한 질문이 있을 수 있다. 다음은 위에서 설명한 엔티티를 기반으로 따를 수 있는 지침입니다.

### 실시간 이벤트

| S.No | Webhook 이벤트 | 설명 |
|---|---|---|
| 1 | CI_STATS | 강의 인스턴스에 대한 인원 또는 대기자 명단 가용성이 변경되면 트리거됩니다. |
| 2 | COURSE_ENROLLMENT | 학습자가 강의에 등록할 때 트리거됩니다. |
| 3 | COURSE_COMPLETED | 학습자가 강의를 완료했을 때 트리거됩니다. |
| 4 | LEARNING_PATH_ENROLLMENT | 학습자가 학습 경로에 등록하면 트리거됩니다. |
| 5 | LEARNING_PATH_COMPLETE | 학습자가 학습 경로를 완료할 때 트리거됩니다. |
| 6 | CERTIFICATION_ENROLLMENT | 학습자가 인증에 등록하면 트리거됩니다. |
| 7 | CERTIFICATION_COMPLETED | 학습자가 인증을 완료하면 트리거됩니다. |
| 8 | COURSE_UNREGISTRATION | 학습자가 강의에서 등록 취소할 때 트리거됩니다. |
| 9 | LEARNING_PATH_UNREGISTRATION | 학습자가 학습 경로에서 등록 취소하면 트리거됩니다. |
| 10 | CERTIFICATION_UNENROLLMENT | 학습자가 인증에서 등록 취소할 때 트리거됩니다. |
| 11 | 학습 개체_초안 | 초안 상태의 학습 객체를 생성하는 동안 트리거됩니다. |
| 12 | LEARNING_OBJECT_DELETION | 학습 객체를 삭제하는 동안 트리거됩니다. |
| 13 | 학습 개체 수정 | 학습 객체를 수정하는 동안 트리거됩니다. |
| 14 | LEARNING_OBJECT_INSTANCE_MODIFICATION | 학습 객체 인스턴스를 생성하거나 수정하는 동안 트리거됩니다.<div><b>참고:</b> 강의를 게시한 후에만 강의 인스턴스를 사용하는 것이 좋습니다.</div> |
| 15 | LEARNING_OBJECT_INSTANCE_DELETION | 학습 객체 인스턴스를 삭제하는 동안 트리거됩니다. |

### 비실시간 이벤트

| S.No | Webhook 이벤트 | 설명 |
|---|---|---|
| 1 | COURSE_ENROLLMENT_BATCH | 책임자/관리자/플랫폼이 학습자를 강의에 등록할 때 트리거됩니다. |
| 2 | COURSE_COMPLETED_BATCH | 책임자/관리자/플랫폼이 강의를 완료로 표시하면 트리거됩니다. |
| 3 | LEARNING_PATH_ENROLLMENT_BATCH | 책임자/관리자/플랫폼이 학습자를 학습 경로에 등록할 때 트리거됩니다. |
| 4 | LEARNING_PATH_COMPLETED_일괄 처리 | 책임자/관리자가 학습 경로를 완료로 표시하면 트리거됩니다. |
| 5 | CERTIFICATION_ENROLLMENT_BATCH | 책임자/관리자/플랫폼이 학습자를 인증에 등록하면 트리거됩니다. |
| 6 | CERTIFICATION_COMPLETED_BATCH | 관리자/관리자/플랫폼이 인증을 완료로 표시할 때 트리거됩니다. |
| 7 | LEARNER_PROGRESS | 모듈이 완료될 때 학습자의 진행률을 추적합니다. |
| 8 | COURSE_UNENROLLMENT_BATCH | 책임자/관리자/플랫폼이 학습자를 강의에서 등록 취소할 때 트리거됩니다. |
| 9 | LEARNING_PATH_UNENROLLMENT_BATCH | 책임자/관리자/플랫폼이 학습 경로에서 학습자의 등록을 취소하면 트리거됩니다. |
| 10 | CERTIFICATION_UNENROLLMENT_BATCH | 책임자/관리자/플랫폼이 학습자를 인증에서 등록 취소할 때 트리거됩니다. |
| 11 | LEARNING_OBJECT_MODIFICATION_BATCH | 마이그레이션 작업 과정을 통해 학습 객체를 수정하는 동안 트리거됩니다. |
| 12 | LEARNING_OBJECT_INSTANCE_MODIFICATION_BATCH | 마이그레이션 작업 과정을 통해 학습 객체 인스턴스를 생성하거나 수정하는 동안 트리거됩니다. |

### 학습 객체 및 인스턴스

* 관리자, 작성자 등의 역할별로 UI 작업을 통해 수행된 학습 객체에 대한 변경 사항을 듣고 싶을 때마다 실시간 이벤트를 구독하십시오.
* 마이그레이션 작업 과정을 통해 생성된 학습 객체에 대한 변경 사항을 듣고 싶은 때마다 실시간이 아닌 이벤트 또는 일괄 처리된 이벤트를 구독하십시오.

### 등록, 등록 취소 및 완료

* 학습자가 수행한 등록, 등록 취소 또는 완료를 수신 대기할 때마다 실시간 이벤트를 구독합니다.
* Admin, Manager, Platform 등으로 표시된 등록, 등록 취소 또는 완료를 수신하려는 경우 실시간이 아닌 이벤트 또는 일괄 처리된 이벤트를 구독하십시오.

### 학습자 진행률

* 학습자의 진행률 변경 내용을 들으려면 언제든지 이벤트를 구독하십시오.

>[!NOTE]
>
>위의 시나리오(등록, 등록 취소, 완료 및 진행)에서 userId 및 loInstanceId로 구성된 속성 조합은 레코드를 고유하게 식별할 수 있습니다.

### 강의 인스턴스 통계

* 좌석 또는 대기자 명단 가용성의 변경 사항을 수신 대기하고 싶을 때마다 실시간 **CI_STATS** 이벤트를 구독합니다.

## Webhook 이벤트 페이로드

Webhooks 응답 페이로드의 일부로 Adobe Learning Manager은 엔터티를 고유하게 식별하는 데 필요한 특성을 내보냅니다. 이는 공용 API에서 사용하는 표준에 따라 동일한 형식으로 방출되므로 Webhook 데이터가 공용 API 데이터와 동기화됩니다. 다양한 이벤트에 대한 페이로드를 보려면 [샘플 페이로드](/help/migrated/integration-admin/feature-summary/webhooks-usage-guide.md#sample-payloads-for-the-events)를 확인하십시오.

## Webhook을 사용하여 외부 DB 또는 알림 서비스 빌드

Webhook이 유용한 사용 사례 중 하나는 고객 측에서 데이터베이스를 구축하는 것입니다. Adobe Learning Manager에는 자체 데이터베이스와 스키마가 있지만 고객은 액세스할 수 없습니다.

문제는 고객이 Webhook의 이벤트를 사용하여 데이터베이스를 구축할 수 있는 방법은 무엇입니까?

Adobe Learning Manager에서는 테이블 레코드 및 스키마를 직접 표시하지 않으므로 고객은 Webhooks 솔루션을 사용하여 이벤트를 사용하여 외부 데이터베이스를 빌드할 수 있습니다. 이번 릴리스에서는 학습 객체, 학습 객체 인스턴스, 등록, 등록 취소, 완료, 진행률 및 강의 인스턴스 통계에 대한 이벤트를 제공합니다.

### 학습 객체 이벤트에서 데이터베이스 빌드

학습 개체 이벤트는 엔터티를 식별하기 위해 `loId` 및 `loType`을(를) 노출합니다. 그러나 이러한 속성만으로는 외부 학습 객체 데이터베이스를 구축하기에 충분하지 않다. 고객은 학습 개체를 자세히 설명하기 위한 추가 필드가 필요합니다.
추가 데이터를 가져오는 방법에는 두 가지가 있습니다.

#### 교육 데이터 보고서를 생성하여 모든 데이터 가져오기

학습용 개체를 마이그레이션과 같은 작업 과정을 통해 대량으로 생성할 때 이 방법을 사용해야 합니다. 여기서 목표는 마이그레이션 작업 과정의 일부로 수집된 모든 학습 개체로 **[!UICONTROL 교육 데이터]** 보고서를 생성하는 것입니다. 가져오기 프로세스를 최적화하려면 내보내기 시작 시간을 마이그레이션이 트리거된 시간으로 설정하는 것이 좋습니다. 이렇게 하면 고객의 데이터베이스에서 기록 데이터를 이미 사용할 수 있으므로 마이그레이션을 통해 가져온 학습 객체만 보고서에 내보낼 수 있습니다.

#### 공개 API GET /learningObjects - 관리자 범위에서 정보를 쿼리합니다.

실시간 워크플로우를 통해 학습 객체를 만들 때 이러한 접근 방식을 사용해야 합니다. 고객은 이벤트를 통해 내보낸 학습 개체를 일괄 처리하고 이러한 학습 개체 ID를 전달하여 `GET /learningObjects` API를 쿼리하려면 자체 캐싱 레이어가 있어야 합니다. 캐싱 계층을 사용하는 이유는 공용 API 속도 제한이 초과되지 않도록 하기 위해서입니다. 현재 ` GET /learningObject`개 API에 대해 시간당 500개 요청으로 설정된 관리자 비율 제한이 있습니다. 이 한도를 초과하면 공용 API 서비스가 **HTTP 429 요청 횟수 초과 메시지**&#x200B;로 응답합니다.

### 학습 개체 인스턴스 및 CI_STATS 이벤트에서 데이터베이스 빌드

학습 개체 인스턴스 이벤트가 강의 및 학습 경로에 대한 `loInstanceId`, `loId` 및 `loType` 특성을 방출합니다. 마찬가지로 **CI_STATS** 이벤트는 `seatLimit`, `seatAvailability`, `waitListLimit`, `waitlistAvailability` 등이 강의에만 적용되므로 강의에만 적용됩니다.

특정 사용 사례에서는 인스턴스 이름, 상태 등과 같은 추가 인스턴스 데이터가 필요합니다. 추가 인스턴스 데이터를 가져오려면 다음 방법을 따라야 합니다.

#### public-api GET /learningobjects - 관리 범위에서 정보를 쿼리합니다.

고객은 위에 언급된 대로 `GET /learningObjects` API를 인스턴스 정보를 가져오기 위해 포함된 인스턴스와 함께 사용할 수 있습니다. 요금 제한이 위반되지 않도록 [섹션](/help/migrated/integration-admin/feature-summary/webhooks-usage-guide.md#query-the-information-from-the-public-api-get-learningobjects-admin-scope)에 언급된 접근 방식을 따라야 합니다.


>[!NOTE]
>
>1. 인증에는 ALM의 인스턴스 개념이 없습니다.
>2. 동일한 정보를 학습 객체 인스턴스 이벤트의 일부로 이미 가져왔으므로 CI_STATS에 대한 추가 데이터를 가져올 필요가 없습니다.

### 등록, 등록 취소, 완료 및 진행 이벤트에서 데이터베이스 빌드

학습자 등록, 등록 취소, 완료 및 진행률은 Adobe Learning Manager에서 별도의 이벤트로 표시됩니다. 학습자는 `userId` 특성으로 식별됩니다. 그러나 고객 측의 다운스트림 워크플로우에 이름, 이메일 등과 같은 추가 학습자 정보가 필요한 특정 시나리오가 있을 수 있습니다. 이 데이터를 가져오려면 고객은 아래에 설명된 접근 방식을 따를 수 있습니다.

#### 관리자 또는 커넥터에서 사용자 보고서 내보내기

이 접근법은 일괄 등록, 일괄 등록 취소 등과 같은 대량 작업 과정이 관련될 때마다 따라야 합니다. Adobe Learning Manager의 사용자 보고서에는 사용자와 관련된 모든 정보가 포함됩니다. Webhook 이벤트에서 얻은 `userId`을(를) 연관시켜 고객은 이 보고서를 조회하여(고객 측에서 데이터베이스, 캐시 또는 API 엔드포인트로 노출될 수 있음) 이름, 이메일, UUID 등과 같은 추가 세부 정보를 가져올 수 있습니다. 이 접근 방식은 매주 또는 매일 사용자를 동기화하는 데 사용될 수 있다.

#### 공개 API GET /사용자 - 관리 범위에서 정보 쿼리

위의 보고서에서 사용자를 사용할 수 없는 경우 이러한 접근 방식을 따를 수 있습니다. 방법 1과 방법 2를 조합하면 이전에 만든 모든 기존 사용자를 **[!UICONTROL 사용자 보고서]**&#x200B;에서 다룰 수 있고 새로 만든 사용자는 API에서 가져올 수 있습니다. **[!UICONTROL 사용자 보고서]**&#x200B;에 데이터가 없으면 고객은 userIds를 입력 인수로 `GET /users` API에 보내 사용자 정보를 가져올 수 있습니다. 동일한 사용자 집합에 대해 공용 API가 반복적으로 호출되지 않도록 하기 위해 이 정보를 고객 측에서 캐시해야 합니다. 현재 GET /사용자 API에 대한 관리자 요금 제한은 시간당 500개 요청으로 설정되어 있습니다. 이 한도를 초과하는 모든 요청에는 **HTTP 429 요청 수가 너무 많음** 응답이 표시됩니다.

## 내결함성

ALM Webhook 시스템의 내결함성은 가입자에게 이벤트 손실, 중복 이벤트 및 주문 외 전달과 같은 잠재적인 문제를 처리하도록 권장하는 기능을 제공합니다.

ALM의 연결 제한 시간은 10초로 구성되어 있고 소켓 제한 시간은 5초로 구성되어 있습니다. 기대는 고객이 메시지를 받는 즉시 이를 인정한다는 것이다. 이는 메시지를 처리하는 동안 클라이언트가 지연되지 않도록 하기 위한 것입니다. 일부 다운스트림 처리가 시간이 많이 소요되는 경우, 클라이언트는 여전히 이벤트를 즉시 승인하고 최종 시점에서 다운스트림 처리를 처리해야 합니다.

### 데이터 보유

이벤트는 7일 동안 보관됩니다. 이 시간 내에 처리되지 않으면 영구적으로 손실됩니다. 마지막 날에 복구가 이루어지고 더 많은 시간이 필요한 경우 시스템은 보존 기간을 연장하지 않습니다.
이벤트가 소비되는 것보다 더 빠르게 생성되면 일부 이벤트가 유실될 수 있습니다. 흔치 않은 일이지만 가입자는 장기적인 이슈가 되지 않도록 모니터링을 해야 한다.

### Webhook 비활성화

가입자가 Webhook 이벤트에 응답하지 않으면 ALM 시스템은 지수 백오프를 사용하여 Webhook을 재시도하여 가입자를 압도하지 않습니다.

재시도 프로세스는 초기 간격 5초로 시작됩니다. 가입자가 응답하지 않으면 대기 시간은 10초, 20초, 40초, 80초로 두 배 늘어나 결국 최대 5분까지 늘어난다. 5분이 되면 시스템은 7일의 보존 기간이 끝날 때까지 5분마다 계속 다시 시도합니다. 이 전체 기간 동안 구독자가 여전히 응답하지 않으면 Webhook이 자동으로 비활성화됩니다. 미리 알림 이메일이 정기적으로 구독자에게 전송됩니다.

### 중복 이벤트

구독자가 이벤트 처리 후 응답하는 데 5초 이상 걸리는 경우 시스템에서 동일한 이벤트를 다시 처리하려고 시도할 수 있습니다. 이벤트 ID를 사용하여 이미 처리된 이벤트를 추적하는 것이 좋습니다. 또한 이벤트를 보낸 후 이벤트를 처리하기 전에 Webhook이 충돌하는 경우 동일한 이벤트 그룹이 다시 시도될 수 있습니다. 일괄 처리 ID 또는 개별 이벤트 ID를 사용하여 중복을 인식하고 무시하는 것이 좋습니다.

### 순서가 틀린 이벤트

ALM은 이벤트를 올바른 순서로 유지하려고 하지만 특히 실시간 및 비실시간 이벤트 간에 이벤트가 순서에 맞지 않게 전달될 수 있습니다.

책임자가 한 번에 여러 학습자를 강의에 등록하면 등록 이벤트가 실시간이 아닌 것으로 표시됩니다. 그러나 학습자가 강의를 빨리 완료하면 완료 이벤트가 실시간으로 표시되고 등록 이벤트 전에 전달될 수 있습니다.

### 내결함성 권장 사항

이러한 오류를 방지하려면 구독자는 Webhook 이벤트를 적극적으로 모니터링하고 누락된 이벤트, 중복 배달 또는 순서가 잘못된 시퀀스 등의 문제에 대한 알림을 설정해야 합니다.

## Webhook 이벤트에 대한 특정 지침

1. LEARNER_PROGRESS 이벤트를 먼저 받으면 아래에 나열된 이벤트를 무시합니다.

   * COURSE_ENROLLMENT
   * COURSE_ENROLLMENT_BATCH
   * LEARNING_PATH_ENROLLMENT
   * LEARNING_PATH_ENROLLMENT_BATCH
   * CERTIFICATION_ENROLLMENT
   * CERTIFICATION_ENROLLMENT_BATCH

2. 다음 이벤트 다음에 오는 경우 LEARNER_PROGRESS 이벤트를 무시합니다.

   * COURSE_COMPLETED
   * COURSE_COMPLETED_BATCH
   * LEARNING_PATH_COMPLETE
   * LEARNING_PATH_COMPLETED_일괄 처리
   * CERTIFICATION_COMPLETED
   * CERTIFICATION_COMPLETED_BATCH

3. 타임스탬프 필드를 사용하여 LEARNER_PROGRESS 이벤트를 제외하고 이벤트를 무시할지 또는 처리할지 여부를 결정합니다.

## Webhook 이벤트 소비 모범 사례

* Webhook 솔루션은 속도와 짧은 대기 시간이 필수적인 높은 처리량의 시스템을 처리하는 데 사용됩니다. 따라서 고객은 이벤트가 접수되는 즉시 해당 이벤트가 승인되도록 해야 합니다. 보고서, API 또는 기타 작업에서 데이터를 가져오는 등 고객 측에서 추가 처리가 필요한 경우에도 이벤트가 수신되는 즉시 승인이 전송되어야 하며, 이벤트를 나중에 처리하는 것은 클라이언트에 달려 있습니다.
* 이전 승인을 받은 후에만 후속 이벤트가 발생하므로 가능한 한 빨리 이벤트를 승인하지 않으면 이벤트의 실시간 특성에 영향을 미칠 수 있습니다.
* 클라이언트는 HTTP 202 Accepted 상태 코드로 응답하여 이벤트가 수락되었음을 승인할 수 있습니다.

## 제한 사항

* 작업 지원은 일반적으로 학습자가 다른 학습 객체를 완료하는 데 도움이 되는 데 사용되므로 LO 범주 아래의 Webhook 이벤트에는 고려되지 않습니다.
* 학습 객체 인스턴스의 종료는 업데이트 이벤트로 간주됩니다. 인스턴스의 삭제 이벤트는 삭제되지 않고 중지만 될 수 있으므로 존재하지 않습니다.
* 세션 변경 사항은 인스턴스 업데이트 이벤트의 일부로 캡처됩니다. 이는 강의에만 적용됩니다. 학습 경로 인스턴스 또는 인증 인스턴스에 대한 하위 수준 엔티티의 상향 전파는 없습니다.
* 학습 경로에 강의가 포함되어 있고 학습자가 학습 경로를 통해 강의를 완료하면 강의와 학습 경로에 대해 각각 하나씩 두 개의 **LearnerProgress** 이벤트가 생성됩니다.
* 특정 작업 과정은 기간 및 전달 유형과 같은 학습 객체의 속성을 비동기적으로 계산합니다. 따라서 이러한 학습 객체에 대한 이벤트는 cron 작업 처리가 완료되면 생성됩니다.

## 이벤트에 대한 샘플 페이로드

+++CI_STATS

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "12345-0458-4450-b5dd-6bc1ef4f8b50",
      "eventName": "CI_STATS",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123456785-LoSt",
      "data": {
        "loInstanceId": "course:12345678_14448475",
        "waitlistCount": 0,
        "enrollmentCount": 10,
        "seatLimit": 30
      }
    }
  ]
}
```

+++

+++COURSE_ENROLLMENT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "12345c1-4576-4ec5-a057-3a6f078cc9d6",
      "eventName": "COURSE_ENROLLMENT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123424713000-040366-10488-0",
      "data": {
        "userId": 12345678,
        "loId": "course:12345678",
        "loInstanceId": "course:12345678_14450088",
        "loType": "course",
        "enrollmentSource": "SELF_ENROLL",
        "dateEnrolled": "2024-11-08T03:49:52.000Z"
      }
    }
  ]
  }
```

+++

+++COURSE_ENROLLMENT_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "1234ec1-4576-4ec5-a057-3a6f078cc9d6",
      "eventName": "COURSE_ENROLLMENT_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123424713000-040366-10488-0",
      "data": {
        "userId": 12345678,
        "loId": "course:12345678",
        "loInstanceId": "course:12345678_14450088",
        "loType": "course",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateEnrolled": "2024-11-08T03:49:52.000Z"
      }
    }
  ]
  }
```

+++

+++COURSE_COMPLETED

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "c2345c-6c98-4ed3-b0b0-ba3da5087c1c",
      "eventName": "COURSE_COMPLETED",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "12345823000-040363-12018-0",
      "data": {
        "userId": 11080928,
        "loId": "course:12345678",
        "loInstanceId": "course:12345678_14448484",
        "loType": "course",
        "enrollmentSource": "SELF_ENROLL",
        "dateCompleted": "2024-11-08T03:49:52.000Z",
        "hasPassed": true
      }
    }
  ]
}
```

+++

+++COURSE_COMPLETED_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "c23458c-6c98-4ed3-b0b0-ba3da5087c1c",
      "eventName": "COURSE_COMPLETED_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123456823000-040363-12018-0",
      "data": {
        "userId": 12345678,
        "loId": "course:12345678",
        "loInstanceId": "course:12345678_14448484",
        "loType": "course",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateCompleted": "2024-11-08T03:49:52.000Z",
        "hasPassed": true
      }
    }
    ]
}
```

+++

+++LEARNING_PATH_ENROLLMENT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "1234791-338f-4c4c-83bc-9f73ea794965",
      "eventName": "LEARNING_PATH_ENROLLMENT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123404248000-040653-71396-0",
      "data": {
        "userId": 12345678,
        "loId": "learningProgram:1234567",
        "loInstanceId": "learningProgram:1234567_109139",
        "loType": "learningProgram",
        "enrollmentSource": "SELF_ENROLL",
        "dateEnrolled": "2024-11-08T03:49:52.000Z"
      }
    }
  ]
  }
```

+++

+++LEARNING_PATH_ENROLLMENT_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "12340791-338f-4c4c-83bc-9f73ea794965",
      "eventName": "LEARNING_PATH_ENROLLMENT_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123404248000-040653-71396-0",
      "data": {
        "userId": 12345678,
        "loId": "learningProgram:1234557",
        "loInstanceId": "learningProgram:1234557_109139",
        "loType": "learningProgram",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateEnrolled": "2024-11-08T03:49:52.000Z"
      }
    }
  ]
  }
```

+++

+++LEARNING_PATH_COMPLETE

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "123404e-d554-4027-944b-086debefdddf",
      "eventName": "LEARNING_PATH_COMPLETED",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1234604391000-040653-314618-0",
      "data": {
        "userId": 12345678,
        "loId": "learningProgram:92348",
        "loInstanceId": "learningProgram:92348_95662",
        "loType": "learningProgram",
        "enrollmentSource": "SELF_ENROLL",
        "dateCompleted": "2024-11-08T03:49:52.000Z",
        "hasPassed": true
      }
    }
  ]
  }
```

+++

+++LEARNING_PATH_COMPLETED_일괄 처리

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "12344e-d554-4027-944b-086debefdddf",
      "eventName": "LEARNING_PATH_COMPLETED_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123404391000-040653-314618-0",
      "data": {
        "userId": 12345678,
        "loId": "learningProgram:92348",
        "loInstanceId": "learningProgram:92348_95662",
        "loType": "learningProgram",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateCompleted": "2024-11-08T03:49:52.000Z",
        "hasPassed": true
      }
    } 
    ]
    }
```

+++

+++CERTIFICATION_ENROLLMENT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "1234e776-148e-4128-80e9-b896a460b655",
      "eventName": "CERTIFICATION_ENROLLMENT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "12344672000-040654-559128-0",
      "data": {
        "userId": 12345678,
        "loId": "certification:123418",
        "loInstanceId": "certification:123418_160299",
        "loType": "certification",
        "enrollmentSource": "SELF_ENROLL",
        "dateEnrolled": "2024-11-08T03:49:52.000Z"
      }
    }
  ]
}
```

+++

+++CERTIFICATION_ENROLLMENT_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "123472ec1-4576-4ec5-a057-3a6f078cc9d6",
      "eventName": "COURSE_ENROLLMENT_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1234524713000-040366-10488-0",
      "data": {
        "userId": 12345678,
        "loId": "course:123456798",
        "loInstanceId": "course:12345678_14450088",
        "loType": "course",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateEnrolled": "2024-11-08T03:49:52.000Z"
      }
    }
  ]
  }
```

+++

+++CERTIFICATION_COMPLETED

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "1234bf8-7521-4bc0-bc51-7f951ff63ea9",
      "eventName": "CERTIFICATION_COMPLETED",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123454768000-040654-756257-0",
      "data": {
        "userId": 123456728,
        "loId": "certification:123418",
        "loInstanceId": "certification:134518_160299",
        "loType": "certification",
        "enrollmentSource": "SELF_ENROLL",
        "dateCompleted": "2024-11-08T03:49:52.000Z"
      }
    }
  ]
  }
```

+++

+++CERTIFICATION_COMPLETED_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "123453bf8-7521-4bc0-bc51-7f951ff63ea9",
      "eventName": "CERTIFICATION_COMPLETED_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1234604768000-040654-756257-0",
      "data": {
        "userId": 12345678,
        "loId": "certification:123418",
        "loInstanceId": "certification:123418_160299",
        "loType": "certification",
        "enrollmentSource": "ADMIN_ENROLL",
        "dateCompleted": "2024-11-08T03:49:52.000Z"
      }
    }
  ]
  }
```

+++

+++LEARNER_PROGRESS

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "d1234d3a4-c3df-44fa-a1cf-7edd6e3d2075",
      "eventName": "LEARNER_PROGRESS",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235604551000-297002-5823-0",
      "data": {
        "loId": "course:7542090",
        "loType": "course",
        "userId": 12380928,
        "loInstanceId": "course:7232090_10423047",
        "dateStarted": "2024-11-08T03:49:52.000Z",
        "progressPercent": 50
      }
}
]
}
```

+++

+++COURSE_UNENROLLMENT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "f3237817-8cb8-40ea-a441-813bec1c7724",
      "eventName": "COURSE_UNENROLLMENT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1345506253000-040298-24078-0",
      "data": {
        "userId": 12311591,
        "loId": "course:12324298",
        "loInstanceId": "course:12324298_14450088",
        "loType": "course",
        "enrollmentSource": "ADMIN_ENROLL",
      }
    }
  ]
}
```

+++

+++COURSE_UNENROLLMENT_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "f2317817-8cb8-40ea-a441-813bec1c7724",
      "eventName": "COURSE_UNENROLLMENT_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "17235506253000-040298-24078-0",
      "data": {
        "userId": 12311591,
        "loId": "course:12324298",
        "loInstanceId": "course:12324298_14450088",
        "loType": "course",
        "enrollmentSource": "SELF_ENROLL"
    }
   }
  ]
}
```

+++

+++학습 경로_등록 취소

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "823df878-1dfd-47ac-9bfe-7d4952e3edd1",
      "eventName": "LEARNING_PATH_UNENROLLMENT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235506667000-040299-28209-0",
      "data": {
        "userId": 12311591,
        "loId": "learning_program:123157",
        "loInstanceId": "learning_program:123157_109139",
        "loType": "learning_program",
        "enrollmentSource": "SELF_ENROLL",
      }
    }
]
}
```

+++

+++LEARNING_PATH_UNENROLLMENT_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "8e23f878-1dfd-47ac-9bfe-7d4952e3edd1",
      "eventName": "LEARNING_PATH_UNENROLLMENT_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235506667000-040299-28209-0",
      "data": {
        "userId": 12311591,
        "loId": "learning_program:123157",
        "loInstanceId": "learning_program:123157_109139",
        "loType": "learning_program",
        "enrollmentSource": "ADMIN_ENROLL"
      }
    }
]
}
```

+++

+++CERTIFICATION_UNENROLLMENT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "7232766b-54d8-472d-b933-7e89d1b75ef8",
      "eventName": "CERTIFICATION_UNENROLLMENT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235507900000-040304-1065-0",
      "data": {
        "userId": 12311591,
        "loId": "certification:123199",
        "loInstanceId": "certification:123199_162078",
        "loType": "certification",
        "enrollmentSource": "SELF_ENROLL"
      }
    }
  ]
}
```

+++

+++CERTIFICATION_UNENROLLMENT_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "7202766b-54d8-472d-b933-7e89d1b75ef8",
      "eventName": "CERTIFICATION_UNENROLLMENT_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1735507900000-040304-1065-0",
      "data": {
        "userId": 12511591,
        "loId": "certification:139199",
        "loInstanceId": "certification:139199_162078",
        "loType": "certification",
        "enrollmentSource": "SELF_ENROLL"
      }
    }
  ]
}
```

+++

+++LEARNING_OBJECT_DRAFT

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "12345da9f-26ec-453c-b56a-cdf18a841948",
      "eventName": "LEARNING_OBJECT_DRAFT",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1234519188000-040344-48604-0",
      "data": {
        "loId": "course:1234091",
        "loType": "course"
      }
    }
  ]
}
```

+++

+++LEARNING_OBJECT_DELETION

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "1234a690-5517-4c09-9cde-d953cdd8582c",
      "eventName": "LEARNING_OBJECT_DELETION",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235605296000-040656-662792-0",
      "data": {
        "loId": "course:12319716",
        "loType": "course"
      }
    }
   ]
}
```

+++

+++LEARNING_OBJECT_MODIFICATION

```
{
  "accountId": 8308,
  "events": [
    {
      "eventId": "223e068-af3e-4dd3-a515-ce19d7234873",
      "eventName": "LEARNING_OBJECT_MODIFICATION",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123350842000-039736-54153-0",
      "data": {
        "loId": "learningProgram:123836",
        "loType": "learningProgram"
      }
    }
   ]
}
```

+++

+++LEARNING_OBJECT_MODIFICATION_BATCH

```
{
  "accountId": 8308,
  "events": [
    {
      "eventId": "1234e068-af3e-4dd3-a515-ce19d7234873",
      "eventName": "LEARNING_OBJECT_MODIFICATION_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235350842000-039736-54153-0",
      "data": {
        "loId": "learningProgram:123836",
        "loType": "learningProgram"
      }
    }
   ]
}
```

+++

+++LEARNING_OBJECT_INSTANCE_MODIFICATION

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "121da98-ab8d-43e9-b671-e79131cd69dc",
      "eventName": "LEARNING_OBJECT_INSTANCE_MODIFICATION",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235603297000-040649-741781-0",
      "data": {
        "loInstanceId": "course:12324298_14453691",
        "loId": "course:12324298",
        "loType": "course"
      }
    }
  ]
}
```

+++

+++LEARNING_OBJECT_INSTANCE_MODIFICATION_BATCH

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "1231da98-ab8d-43e9-b671-e79131cd69dc",
      "eventName": "LEARNING_OBJECT_INSTANCE_MODIFICATION_BATCH",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "123603297000-040649-741781-0",
      "data": {
        "loInstanceId": "course:12324298_14453691",
        "loId": "course:12324298",
        "loType": "course"
      }
    }
  ]
}
```

+++

+++LEARNING_OBJECT_INSTANCE_DELETION

```
{
  "accountId": 1234,
  "events": [
    {
      "eventId": "12d16e90-d73a-457b-83f3-666ba9654edb",
      "eventName": "LEARNING_OBJECT_INSTANCE_DELETION",
      "timestamp": "2024-11-08T03:49:52.000Z",
      "eventInfo": "1235605491000-040657-236307-0",
      "data": {
        "loInstanceId": "course:12319674_14453849",
        "loId": "course:12319674",
        "loType": "course"
      }
    }
  ]
}
```

+++
