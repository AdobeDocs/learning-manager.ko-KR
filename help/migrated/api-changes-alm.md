---
description: ALM의 API 변경 사항
jcr-language: en_us
title: 4월 릴리스의 API 변경 사항
source-git-commit: 3b35c16d74c83329cee24ee9ad007a53ccbd8cf3
workflow-type: tm+mt
source-wordcount: '4093'
ht-degree: 0%

---


# 2026년 4월 릴리스의 API 변경 사항

Adobe Learning Manager의 2026년 4월 릴리스에는 대체 및 대응 항목과 관련하여 공개 API가 중점적으로 개선되고, 콘텐츠의 시간 창을 통한 액세스, 콘텐츠 중심의 퀴즈 시도, 로그인하지 않은 경험, 작업 지원 처리가 도입되었습니다. 변경 사항은 보다 정밀한 통합을 가능케 하면서 대부분 이전 버전과 호환되도록 설계되었습니다.

## 학습 경로에 대한 적응형 학습

이 릴리스에는 적응형 학습 경로에 대한 전체 공개 API 지원이 추가되었습니다. 이제 학습 경로(LP)는 서로 다른 학습자 그룹에 표시되는 섹션 및 하위 학습 개체(하위 LO)를 제어하는 적응형 규칙을 정의할 수 있으며, 공개 API는 이러한 동작을 반영합니다.

다음 엔드포인트가 영향을 받습니다.

- GET /primeapi/v2/learningObjects?filter.loTypes=learningPath
- GET /primeapi/v2/learningObjects/{loId}

새로운 부울 속성인 attributes.isAdaptive 는 학습 프로그램이 적응 규칙을 사용함을 나타냅니다. 이 플래그가 true이면 sections 속성이 적응적으로 해석됩니다.

학습자 통화의 경우 현재 학습자에게 표시되는 섹션만 반환됩니다. 각 섹션에는 학습 개체 ID(loId) 목록, 필수 플래그 및 해당 학습자의 적응 구성에 따라 계산된 필수 LOCount과 sectionId가 포함됩니다. 이제 relationships.subLOs 관계도 필터링되어 해당 학습자에게 표시되는 하위 학습 객체만 포함됩니다.

관리자 호출의 경우 섹션에서 adaptiveConfig 배열을 추가로 표시할 수 있습니다. 이는 userGroupId, userGroupName 및 해당 그룹에 섹션이 필수인지 여부를 포함하여 사용자 그룹별 적응 규칙에 대해 설명합니다. 관리자 접근 도구는 이를 사용하여 적응 규칙을 시각화하고 관리할 수 있습니다.

학습 프로그램 완료 재설정

이 릴리스에서는 적응형 학습 프로그램을 포함하여 학습 개체를 __새로 고침(재설정) 완료__&#x200B;하는 API가 도입되었습니다. 재교육, 정기적인 규정 준수 새로 고침 또는 프로그램 재시작과 같은 시나리오를 지원합니다.

새 끝점을 사용할 수 있습니다.

```
POST /primeapi/v2/learningObjects/{loId}/instances/{loInstanceId}/refreshCompletion
```

이 작업에는 적절한 쓰기 권한이 필요하며 지정된 사용자 컨텍스트에서 지정된 학습 개체 인스턴스의 완료 상태가 재설정됩니다. 책임자 자동화나 학습자 도구에 맞게 범위가 지정된 도구를 사용하기 위한 것입니다.

이 기능의 대량 버전은 작업 API를 통해 계획되었습니다. 요청 모양은 이메일, 사용자 ID 또는 사용자 그룹 ID를 기준으로 사용자를 대상으로 합니다. 예를 들면 다음과 같습니다.

```
{  
  "emails": ["[user1@example.com](mailto:user1@example.com)", "[user2@example.com](mailto:user2@example.com)"],  
  "userIds": ["12345", "67890"],  
  "userGroupIds": ["ug1", "ug2"]  
}  
```

통합에서는 각 프로그램 또는 과정에서 학습자를 다시 시작해야 할 때 이 API를 사용해야 합니다. 클라이언트는 오류 응답을 적절하게 처리해야 합니다. 즉, 재설정이 적용되지 않는 경우(예: 완료가 없거나 지원되지 않는 학습 객체 유형이 있는 경우) API에서 새로 고침 요청을 거부할 수 있습니다.

## 해당 항목 및 대체 완료

여러 학습 객체가 동일한 요구 사항을 충족할 수 있는 구현을 지원하기 위해 이 릴리스에서는 등가 및 대체 기능을 공개 API로 도입했습니다.

이제 학습 개체 끝점에 다음 정보가 포함됩니다.

```
- GET /primeapi/v2/learningObjects
- GET /primeapi/v2/learningObjects/{loId}
```

새로운 부울 속성 속성 속성 속성.isAlternateComplete는 지정된 학습 개체에 대한 학습자의 완료 결과가 개체 자체가 아닌 대체 학습 개체 또는 동등한 학습 개체의 결과인지 나타냅니다. 이 값이 true이면 relationships.alternateCompletions 관계에는 대체 역할을 하는 학습 객체가 나열됩니다. 이를 통해 다운스트림 보고 및 대시보드는 직접 완료와 대체 완료를 구분하고 요구 사항을 충족한 대안을 표시할 수 있습니다.

또한 관련 학습 객체 보기를 사용하면 학습 객체를 만족시킬 수 있는 잠재적 대안을 검색할 수 있습니다. 이 문제는 다음을 통해 노출됩니다.

```
GET /primeapi/v2/learningObjects/{loId}/relatedLOs?type=sourceAlternateLOs&limit={n}
```

응답은 대체자로 사용할 수 있는 학습 객체를 반환하며 현재 제한과 관계없이 이러한 대체자의 총 수를 나타내는 meta.count 필드를 포함합니다. 통합에서는 이를 사용하여 권장 등가물을 제시하거나 대체 매핑의 관리 뷰를 작성할 수 있습니다.

## 보고 및 분석 사용 사례

보고서 또는 분석을 생성하는 사용자는 논리를 업데이트하여 isAlternateComplete 및 alternateCompletions를 보고 워크플로우에 추가해야 합니다.

완료 데이터(예: LT 내보내기, 사용자 지정 데이터 웨어하우스 피드 또는 BI 대시보드)를 사용하는 보고 통합은 논리를 확장하여 두 특성을 모두 읽고 유지해야 합니다.isAlternateComplete 및 관계.alternateLO API에서 완료:

- isAlternateComplete가 ==는 경우:\
  오늘처럼 레코드를 LO의 __직접 완료__&#x200B;로 취급합니다.
- isAlternateComplete가 == 경우:
   - 레코드를 보고서의 __대체 완료__(예: &quot;완료 방법&quot; 열에 DIRECT와 ALTERNATE 값을 함께 포함)로 플래그 지정합니다.
   - relationships.alternateCompletions.data[*].id를 사용하여 이 완료 권한을 부여한 __소스 LO__&#x200B;을(를) 캡처합니다(예: &quot;강의 B는 대체 강의 A를 통해 완료&quot;).

일반적인 사용 사례:

- _준수 보고서_ - 승인된 해당 강의를 통해 준수 과정이 완료되었음을 표시하고 요구 사항을 이행한 원본 과정을 나열합니다.
- _프로그램 진행률 대시보드_ - 보다 정확한 진행률과 수정 보기를 위해 _직접_ 경로를 완료한 학습자와 대안을 통해 해당 경로를 충족한 학습자를 구분합니다.
- _감사 추적_ - isAlternateComplete=true로 표시된 모든 LO에 대해 감사자는 해당 완료를 부여하는 데 사용된 대체 교육을 정확하게 확인할 수 있습니다.

이 두 필드를 통합하지 않으면 다운스트림 보고서는 대체 완료를 일반 완료로 취급하며 학습자가 직접 수강하지 않은 교육을 완료한 것으로 표시할 수 있는 경우 _설명할 수 없는 경우_ *이유*&#x200B;를 설명할 수 없습니다.

## 학습자 및 책임자 LO API 동작

다중 언어 작업 지원 구조는 학습자 및 책임자 LO API에서 모두 동일합니다. 학습자 범위는 학습자에게 표시되는 작업 지원만 반환하지만 표시되는 각 작업 지원에 대해 여러 리소스 엔터티(로케일당 하나) 및 다중 로케일의 지역화된 Metadata를 통해 구성된 모든 로케일이 표시됩니다. 관리 범위는 관리자가 관리할 수 있는 모든 작업 지원을 동일한 LO 모델 및 로케일별 리소스 ID로 반환합니다. 학습자 범위가 있는 클라이언트는 속성이 학습자의 콘텐츠 언어와 가장 잘 맞는 리소스를 선택해야 하며, 관리 도구는 보고 및 관리를 위해 모든 로케일을 열거할 수 있습니다.

## 주석 달기 기능이 있는 체크리스트

검토자가 체크리스트 기반 활동에 대한 구조화된 피드백을 공유할 수 있는 워크플로우를 지원하기 위해 이 릴리스에서는 학습 개체 리소스 API를 통해 *체크리스트 주석* 및 검토자 가시성 컨트롤이 표시됩니다.

체크리스트 관련 메타데이터는 과정 또는 기타 학습 개체 내의 체크리스트 리소스를 나타내는 learningObjectResource 엔터티(JApiLOResource, &quot;type&quot;: &quot;learningObjectResource&quot;)에 표시됩니다.

이 정보는 다음을 통해 제공됩니다.

```
GET /primeapi/v2/learningObjects/{loId}?include=instances.loResources
```

학습 객체 인스턴스에 체크리스트 유형 리소스가 포함되어 있는 경우 포함된 배열의 해당 learningObjectResource 항목은 속성 아래에 주석 및 검토자 가시성 속성이 표시되고 관계 아래에 검토자 ID가 표시됩니다.

### 새 체크리스트 주석 속성

체크리스트 리소스의 경우 learningObjectResource에 다음 속성이 있을 수 있습니다.

- attributes.checklistComment\
  검토자가 학습자에게 남긴 자유 텍스트 댓글입니다. 예시는 다음과 같습니다.\
  &quot;checklistComment&quot;: &quot;탁월한 성능! 모든 안전 프로토콜이 올바르게 준수되었습니다.&quot;\
  이 특성은 _인 경우에만_&#x200B;채워집니다.
   - showChecklistComment는 true이고,
   - 체크리스트 구성에서 enable_reviewer_remarks를 사용하도록 설정했습니다.
- attributes.showChecklistComment\
  학습자에게 검토자 의견을 표시할지 여부를 나타내는 부울 플래그:\
  &quot;showChecklistComment&quot;: true\
  이 특성은 체크리스트 구성에서 _enable_ reviewer_remarks가 활성화된 경우에만 _존재합니다.\
  클라이언트는 이 플래그를 사용하여 학습자 경험에서 checklistComment를 렌더링할지 여부를 결정해야 합니다.
- attributes.showReviewerNameToLearner\
  학습자가 검토자의 ID를 표시해야 하는지 여부를 제어하는 부울 플래그:\
  &quot;showReviewerNameToLearner&quot;: true\
  true인 경우 클라이언트는 checklistReviewedBy 관계(아래 참조)를 사용하여 검토자의 이름을 확인하고 표시할 수 있습니다(예: 사용자 조회 API 사용).

더 풍부한 체크리스트 UI 및 보고를 지원하기 위해 동일한 learningObjectResource에서도 checklistEvaluationStatus, isChecklistMandatory, resourceSubType: &quot;체크리스트&quot; 및 submissionDate와 같은 다른 체크리스트별 컨텍스트를 사용할 수 있습니다.

### 검토자 ID 관계

검토자 이름이 표시될 경우 learningObjectResource에는 검토자 사용자를 가리키는 관계가 포함됩니다.

```
"relationships": {
  "checklistReviewedBy": {
    "data": {
      "id": "user_id",
      "type": "user"
    }
  }
}
```

이 관계는 _인 경우에만_&#x200B;채워집니다.

- showReviewerNameToLearner는 true이고,
- checklistReviewedBy는 null이 아닙니다(예: 체크리스트가 검토됨).

클라이언트 애플리케이션은 다음 작업을 수행해야 합니다.

1. attribute.showReviewerNameToLearner를 확인합니다.
2. true 및 relationships.checklistReviewedBy.data가 있는 경우 해당 사용자 API를 호출하여 &quot;id&quot;: &quot;user_id&quot;를 표시 이름으로 확인합니다.
3. 체크리스트 주석 또는 상태 옆의 검토자 이름을 적절하게 렌더링합니다.

### 체크리스트 리소스 및 주석 액세스

지정된 학습 객체에 대한 체크리스트 리소스와 주석을 검색하려면 다음과 같이 해야 합니다.

- 통화

```
GET /primeapi/v2/learningObjects/{loId}?include=instances.loResources
```

- 이에 대한 응답으로:
   - 기본 learningObject의 relationships.instances를 사용하여 포함된 관련 learningObjectInstance 항목을 찾습니다.
   - 각 learningObjectInstance에서 relationships.loResources에 따라 learningObjectResource 항목을 찾습니다.
   - 다음 위치에서 learningObjectResource 항목을 필터링합니다.
      - attribute.resourceSubType == &quot;CHECKLIST&quot;(체크리스트 리소스의 경우),
      - 선택 사항으로 attributes.showChecklistComment== true이면 학습자가 볼 수 있는 주석이 있는 체크리스트를 찾습니다.

- 각 체크리스트 learningObjectResource에 대한 다음 리소스를 사용합니다.
   - attributes.checklistComment(present 및 showChecklistComment가 true인 경우)
   - attributes.checklistEvaluationStatus(예: &quot;PASSED&quot;)
   - attributes.showReviewerNameToLearner
   - relationships.checklistReviewed검토자를 식별하기 위한 (있는 경우).

이 패턴을 통해 헤드리스 또는 사용자 정의 클라이언트는 Prime API에서 직접 상태, 필수/선택적 플래그 및 검토자 피드백을 포함한 포괄적인 체크리스트 경험을 렌더링할 수 있습니다.

### 보고 및 UX 고려 사항

- _보고 및 분석_
체크리스트에서 학습자 성과를 추적하는 통합에는 다음이 포함될 수 있습니다.
   - 검사 목록합격/불합격 또는 기타 상태 표시기에 대한 평가상태입니다.
   - isChecklist필수 활동과 선택적 체크리스트 활동을 구분하려면 필수입니다.
   - 피드백 검사 감사를 위해 체크리스트주석 및 showChecklist주석이 있는지 여부
- _학습자 경험_
UI 구현은 다음과 같습니다.
   - 비고를 표시하기 전에 showChecklistComment를 존중합니다.
   - showReviewerNameToLearner 및 checklistReviewedBy를 사용하여 검토자의 이름을 표시할지 또는 검토를 익명으로 유지할지 결정합니다.
   - 댓글이 비활성화되거나 표시되지 않고 평가 상태 및 제출 정보가 표시되는 경우 우아하게 뒤로 넘어갑니다.

## 작업 지원에 대한 다국어 지원

작업 지원이 학습자와 관리자 모두에게 다국어로 전달되어야 하는 구현을 지원하기 위해 이 릴리스에서는 작업 지원 처리가 하드 코딩된 단일 en-US 리소스 대신 *로케일당 하나의 리소스*&#x200B;를 반환하도록 확장되었습니다.

다중 언어 작업 지원은 기존 계층 구조를 계속 사용합니다.

_학습 개체_(lo) → _learningObjectResource_(loResource) → _리소스_

API 계약을 변경할 필요가 없습니다. 지역화된 모든 작업 지원은 로케일별로 별도의 리소스 엔티티와 learningObject/learningObjectResource 수준의 지역화된 공유 메타데이터를 통해 자연스럽게 이 구조에 맞춰집니다.

작업 지원 데이터는 다음을 통해 노출됩니다.

```
GET /primeapi/v2/learningObjects/jobAid:{jobAidId}?include=instances.loResources.resources
```

작업 지원에 여러 언어 변형이 있는 경우 포함된 배열에는 여러 &quot;type&quot;: &quot;resource&quot; 항목이 포함되며 각 로케일에 대해 하나씩(예: en-US, fr-FR, es-ES), 모두 단일 learningObjectResource에서 연결됩니다.

### 다국어 작업 지원 구조

다중 언어 작업 지원 사용:

- _learningObject(유형: learningObject)_
   - 클라이언트가 적절한 언어로 작업 지원 제목/설명을 표시할 수 있도록 여러 항목(예: en-US, fr-FR)이 있는 localizedMetadata를 포함합니다.
- _learningObjectInstance(유형: learningObjectInstance)_
   - relationships.loResources를 통해 하나 이상의 learningObjectResource 항목을 참조합니다.
- _learningObjectResource(유형: learningObjectResource)_
   - 공통 구성(컨텐츠 유형, 버전 등) 보유 다중 로케일의 localizedMetadata를 사용할 수 있습니다.
   - relationships.resources를 통해 하나 이상의 리소스 엔터티에 연결합니다.
- _리소스(유형: 리소스)_
   - *로케일당 1개*, 각 로케일은 고유 ID, 로케일, 이름 및 URL(location / downloadUrl)을 가집니다.

다국어 작업 지원의 경우 일반적인 패턴은 다음과 같습니다.

- en-US 및 fr-FR에 대한 localizedMetadata가 있는 learningObjectResource
- relationships.resources.data 가리키기:
   - 리소스(로케일 포함): &quot;en-US&quot;
   - 로케일이 &quot;fr-FR&quot;인 리소스

클라이언트는 학습자의 로케일을 resource.attributes.locale 필드에 일치시켜 적절한 리소스를 선택할 수 있습니다.

### 작업 지원에 대한 새 리소스 ID 형식

작업 지원 리소스의 지역화된 여러 변형을 올바르게 구별하기 위해 _리소스 ID 형식이 변경되었습니다_.

_이전(레거시) 리소스 ID 형식_

이전에는 작업 지원 리소스에서 다음과 같은 불투명 ID 형식을 사용했습니다.

작업 지원:131032_-1_-1_2_resource

이 형식은 로케일을 인코딩하지 않았으며, API는 사실상 단일 리소스(일반적으로 en-US)만 노출합니다.

_새 리소스 ID 형식(다중 언어 인식)_

새로운 형식은 다음과 같습니다.

```
jobAid:<jobAidId>_<version>_<localeCode>
```

예:

- 작업 지원:131032_2_en-US
- 작업 지원:131032_2_fr_FR
- 작업 지원:131032_2_es_ES

시각 장애:

```
jobAid:131032_2_fr_FR

        │      │ │ │

        │      │ │ └──► Locale Code (fr_FR, en_US, es_ES, etc.)

        │      │ └────► Version (2)

        │      └──────► JobAid ID (131032)

        └─────────────► Resource Type Prefix ("jobAid:")
```

이 구조를 통해 클라이언트는 다음을 수행할 수 있습니다.

- 리소스가 속한 작업 지원 및 버전을 빠르게 식별합니다.
- 필요한 경우 리소스 ID에서 로케일을 직접 추론합니다.

### 이전 버전과의 호환성: 

```/resources/{resourceId}```

레거시 리소스 끝점은 계속 사용할 수 있습니다.

```GET /primeapi/v2/resources/{resourceId}

```

이제 이전 ID 형식과 새 ID 형식이 모두 _이전 버전과 호환_&#x200B;됩니다.

- _이전 ID 형식_(예: 작업 지원:131032_-1_-1_2_resource)
   - 계속 작동합니다.
   - 해당 레거시 식별자(일반적으로 원래 en-US 리소스)와 연결된 _처음 만든 리소스_&#x200B;를 반환합니다.
- _새 ID 형식_(예: 작업 지원:131032_2_fr_FR)
   - 해당 ID에 해당하는 _정확한 로캘별 리소스_&#x200B;를 반환합니다.
   - 이를 통해 지역화된 작업 지원 변형의 정밀한 검색 및 조작이 가능합니다.

현재 이전 리소스 ID를 저장하거나 참조하는 통합은 변경 없이 계속 작동할 수 있지만, 최신 구현은 로케일별 작업에 대한 새 ID 형식을 채택하는 것이 좋습니다.

### 통합 및 UX 고려 사항

- _학습자/관리자 UI_
   - learningObject.localizedMetadata 및 learningObjectResource.localizedMetadata를 사용하여 제목과 설명을 해당 언어로 표시합니다.
   - resource.attributes.locale 을 사용하여 학습자 로케일에 맞는 URL (location / downloadUrl) 을 선택합니다.
   - 학습자의 정확한 로케일을 사용할 수 없는 경우 대체 동작(예: en-US로 대체)을 구현합니다.
- _API 및 저장소_
   - 새 통합의 경우 _새로운 형식의 리소스 ID_(```jobAid:<jobAidId>_<version>_<localeCode>```)를 저장하여 모호하지 않은 로케일 특정 검색을 사용하도록 설정하십시오.
   - 레거시 ID는 /resources/{resourceId}와 함께 사용할 수 있지만 로케일을 구분하지 않습니다.

## 시작 모듈에 대한 시간 슬롯 제약 조건

일부 학습 경험은 정의된 기간 내에서만 사용할 수 있어야 합니다. 이 릴리스에는 학습 객체 리소스에 대한 시간 슬롯 정보가 표시되고 학습자가 현재 시간에 리소스를 시작할 수 있는지 여부를 확인하는 유효성 검사 끝점이 도입됩니다.

타임 슬롯 메타데이터는 끝점을 통해 사용할 수 있습니다.

```GET /primeapi/v2/learningObjects/{loId}?include=instances.loResources```

이제 학습 객체 리소스 수준에서 startTime 및 endTime 값을 UTC로 하는 timeSlot 객체가 속성에 있을 수 있습니다. 리소스를 시작할 수 있는 창을 지정합니다.

통합을 통해 모듈을 시작하기 전에 새 유효성 검사 끝점을 호출할 수 있습니다.

```GET /primeapi/v2/learningObjects/{loId}/instances/{loInstanceId}/loResources/{loResourceId}/canStart```

학습자 읽기 시나리오를 위한 이 엔드포인트는 구성된 타임 슬롯, 제공 유형 및 기타 백엔드 규칙을 고려하여 학습자가 현재 리소스를 시작할 수 있는지 여부를 반환합니다.

사용자 정의 플레이어와 클라이언트 응용 프로그램은 canStart를 사용하여 시간 기반 액세스를 적용하고, timeSlot 메타데이터를 사용하여 컨텐츠가 사용 가능해지거나 만료되는 시점에 대한 명확한 메시지를 표시해야 합니다. canStart의 부정적인 응답을 명확하게 처리하여 학습자가 컨텐츠를 아직 시작할 수 없거나 더 이상 시작할 수 없는 이유를 알려주어야 합니다.

## 다중 시도 컨텐츠 중심 퀴즈

일부 콘텐츠 패키지는 Adobe Learning Manager에만 의존하지 않고 자체 시도 추적을 구현합니다. 이 릴리스에는 시도가 콘텐츠 자체에 의해 주도되는 시기를 나타내는 플래그가 도입됩니다.

까지:

```GET /primeapi/v2/learningObjects/{loId}?include=instances.loResources```

이제 학습 객체 리소스가 부울 속성 hasContentDrivenAttemptTracking을 표시할 수 있습니다. 이 경우 퀴즈 또는 모듈은 내부적으로(예: SCORM 또는 xAPI 논리를 통해) 시도를 관리하며 플랫폼의 표준 시도 카운터가 학습자의 경험을 완전히 반영하지 못할 수 있습니다.

시도 횟수를 표시하거나 재시도 동작을 제어하는 통합은 이 플래그를 확인해야 합니다. 이 기능이 활성화되면 플랫폼 메타데이터만으로 시도 제한을 추론해서는 안 되며 xAPI 명령문 등을 통한 컨텐츠 측 보고 또는 비즈니스별 규칙에 의존하도록 준비해야 합니다.

## 작업 지원 리소스 ID 형식의 동작 변경

이 릴리스에서는 작업 지원 리소스 ID 형식의 중요한 __동작 변경__&#x200B;을 소개합니다. 새 엔드포인트는 포함되지 않지만 이러한 ID를 저장하거나 구문 분석하는 시스템에는 직접적인 영향을 미칩니다.

이전에는 작업 지원 리소스 ID가 다음과 같은 형식을 사용했습니다.

```jobAid:<jobAidId>_-1_-1_2_resource```

2026년 4월 릴리스에서는 이 기능이 단순화되고 더 명확한 형식으로 대체되었습니다.

```jobAid:<jobAidId>_<version>_<localeCode>```

예:

작업 지원:131032_2_fr_FR

구성 요소는 다음과 같습니다.

- ```<jobAidId>```: 숫자 작업 지원 ID(예: 131032),
- ```<version>```: 작업 지원의 버전 번호(예: 2),
- ```<localeCode>```: 로케일 코드(예: en_US, fr_FR, es_ES).

작업 지원 리소스 ID에서 리소스를 인덱싱하거나 지속되는 모든 통합은 새 형식을 인식하도록 해당 구문 분석 및 저장소 논리를 업데이트해야 합니다. 식별자 자체가 변경되므로 2026년 4월 릴리스로 업그레이드한 후 작업 지원 리소스 ID로 입력된 로컬 인덱스를 다시 작성하는 것이 좋습니다.

## 마이그레이션을 통해 강의 배너 이미지 설정

이제 표준 마이그레이션 작업 과정의 일부로 Adobe Learning Manager에서 강의 배너 이미지를 설정하거나 업데이트할 수 있습니다. 이렇게 하면 수동으로 편집하지 않고도 강의 페이지를 시각적으로 일관성 있게 유지하면서 큰 카탈로그를 실행하거나 정리할 수 있습니다

### 배너 이미지 정의 위치

배너 이미지는 다음과 같은 과정 메타데이터를 제공하는 데 이미 사용하는 _course.csv_ 마이그레이션 파일에 구성됩니다.

- ID
- courseName
- courseCreationDate
- 상태
- 작성자
- thumbnailUrl

향상된 기능을 통해 course.csv 사양에는 강의 배너 이미지에 대한 추가 _선택 열_&#x200B;이 포함됩니다. 정확한 헤더 이름은 Learning Manager 계정에서 다운로드하는 CSV 사양에 정의됩니다(예: bannerUrl 또는 bannerImageUrl로 표시될 수 있음).

배너 열:

- _강의 배너_&#x200B;로 사용할 이미지 파일을 가리킵니다.
- 구성된 컨텐츠 저장소(Box/FTP)에서 사용할 수 있는 이미지를 사용하여 thumbnailUrl과 동일한 방식으로 작동합니다.

### 마이그레이션을 위한 배너 이미지 준비

1. 배너 이미지 업로드: 배너 이미지 파일을 기존 디렉터리 구조를 따라 다른 마이그레이션 에셋에 사용하는 것과 동일한 Box 또는 FTP 위치에 배치합니다.
2. 파일 형식 확인:
시스템 요구 사항에 설명된 대로 지원되는 이미지 형식(예: png, jpg, jpeg, gif) 중 하나를 사용합니다.
   1. [*시스템 요구 사항*](/help/migrated/system-requirements.md)
3. course.csv 업데이트: 새 배너 열에서 배너 이미지의 상대 경로 또는 식별자를 참조하십시오. 개념적 예:

```
id,courseName,courseCreationDate,state,author,thumbnailUrl,bannerUrl  
12345,DEMO1,2018-05-05T08:56:21.000Z,Published,Sudheer,pic1.png,banners/banner1.png  
45678,DEMO2,2018-05-05T08:56:21.000Z,Published,Sudheer,pic2.png,banners/banner2.png  
```

### 마이그레이션 실행 중 배너 적용

course.csv가 업데이트되면 플로우가 다른 마이그레이션과 동일합니다.

1. _CSV 업로드_
마이그레이션하도록 구성된 Box/FTP 폴더에 업데이트된 course.csv(및 기타 관련 파일)를 업로드하십시오. 파일 이름은 csv_specifications.zip에 지정된 이름과 정확히 일치해야 합니다(대/소문자를 구분함).
2. _스프린트 실행 시작_
Adobe Learning Manager에서 통합 책임자는 course.csv를 포함하는 마이그레이션 _스프린트 실행_&#x200B;을 시작합니다.\
   마이그레이션 엔진은 배너 열을 읽고 각 과정에 배너 이미지를 적용합니다.
3. _결과 및 오류 로그 검토_
스프린트 후:
   1. _작성자_ 및 _학습자_ 앱에서 배너를 확인합니다.
   2. 잘못된 파일 경로나 지원되지 않는 형식 등으로 인해 일부 행이 실패할 경우, 마이그레이션 실행에서 오류 CSV를 다운로드하고 데이터를 수정합니다.

### 새 강의와 기존 강의 비교

배너 필드는 다음 두 가지 시나리오에서 작동합니다.

- _마이그레이션을 통해 생성된 새 과정_
course.csv에서 처음으로 강의가 생성되고 배너 열이 채워지면 해당 배너가 즉시 설정됩니다.
- _기존 강의(개선/수정)_
동일한 과정 ID와 새 배너 값을 사용하여 마이그레이션을 다시 실행하는 경우:
   - Learning Manager가 기존 과정을 찾습니다.
   - 배너 이미지가 CSV에 지정된 새 이미지로 _업데이트_&#x200B;되었습니다.

실제 열 이름 및 경로는 _다운로드된 CSV 사양_ 및 콘텐츠 리포지토리 레이아웃과 일치해야 합니다.

## LearningProgramCourse에서 순서 열 제거

이제 Adobe Learning Manager은 마이그레이션 중 _학습 경로(학습 프로그램)_&#x200B;의 과정 순서 지정을 위한 간소화된 모델을 지원합니다. 이 변경의 일부로 learning _program_ course.csv 마이그레이션 파일에서 _순서 열이 제거_됩니다.

이전에는 learning_program_course.csv 파일에 다음 작업에 사용된 열(주문 또는 이와 유사한 것이라고도 함)이 포함되었습니다.

- 해당 열의 숫자 값을 기반으로 학습 프로그램 내에서 각 강의의 _위치_&#x200B;를 명시적으로 설정합니다.
- 특히 강의를 삽입하거나 순서를 변경할 때 이 숫자 시퀀스를 수동으로 유지하려면 관리자 또는 스크립트가 필요합니다.

이제 Adobe Learning Manager에서는 learning_program_course.csv의 주문 열을 사용하여 강의 주문을 결정하지 않습니다. 대신 마이그레이션 CSV는 숫자로 정렬되는 방식보다 _어떤 과정이 학습 프로그램에 속하는지_&#x200B;에 초점을 맞춥니다.

## 마이그레이션 CSV에 미치는 영향

### learning_program_course.csv

레거시 주문 열을 제거되거나 무시된 것으로 간주해야 합니다.

- 마이그레이션 중 학습 프로그램에서 강의 순서를 제어하려면 순서를 따르지 마십시오.
- 이전 템플릿의 주문 열이 여전히 있는 경우:
   - Learning Manager는 주문 시 이를 무시합니다.
   - 시간이 경과함에 따라 CSV에서 안전하게 파일을 제거하여 마이그레이션 파일을 간소화할 수 있습니다.
- 필수 매핑의 핵심은 다음과 같습니다.
   - 학습 프로그램 ID ↔ 강의 ID(및 ID, learningProgramId, courseId 및 날짜와 같이 아직 문서화된 기타 열)

항상 Learning Manager 계정의 최신 [_CSV 사양_](https://experienceleague.adobe.com/ko/docs/learning-manager/using/integration/migration-manual)을 참조하여(csv_specifications.zip을 통해) 현재 헤더 세트 및 요구 사항을 확인하십시오.

## 강의 인스턴스의 시간대 코드

이번 릴리스부터는 강의 인스턴스 모델(learningObjectInstance)에 새로운 속성이 표시됩니다.

timeZoneCode — 강의 인스턴스를 계정에 구성된 시간대 중 하나에 명시적으로 연결하는 문자열 필드입니다.

이를 통해 클라이언트는 다음을 수행할 수 있습니다.

- 일관된 API 기반 방식으로 강의 인스턴스의 시간대를 해결합니다.
- 사용자의 시간대에 관계없이 해당 인스턴스에 대해 모든 인스턴스 레벨 날짜/시간을 올바르게 해석하고 표시합니다.

### timeZoneCode 가 표시되는 위치

이 필드는 learningObjectInstance 모델의 특성에 추가됩니다.
강의 인스턴스만 해당.

예:

```
{
  "id": "course:1262748_1359228",
  "type": "learningObjectInstance",
  "attributes": {
    "dateCreated": "2019-08-06T13:50:39.000Z",
    "isAET": false,
    "isDefault": true,
    "timeZoneCode": "356",
    "isFlexible": false,
    "state": "Active",
    "localizedMetadata": [
      {
        "locale": "en-US",
        "name": "Default instance"
      }
    ]
  }
}
```

### timeZoneCode 해결 방법

숫자 timeZoneCode는 계정의 시간대 카탈로그에 대한 조회 키이며 계정 API를 통해 표시됩니다.

```http
GET /primeapi/v2/account
Authorization: Bearer <access_token>
```

응답 내의 시간대는 다음과 같습니다.

```
"data": {
  "attributes": {
    "timeZones": [
      {
        "name": "Etc/GMT+12",
        "timeZoneCode": "356",
        "utcOffset": -720,
        "utcOffsetCode": "UTC-12:00(Etc/GMT+12)",
        "zoneId": "Etc/GMT+12"
      },
      "..."
    ]
  }
}
```

### 권장 클라이언트 흐름:

1. 테넌트에 대해 GET /account, cache attributes.timeZones를 한 번 호출합니다.
2. 각 강의 인스턴스에 대해:
   - attributes.timeZoneCode를 읽습니다.
   - timeZoneCode가 일치하는 timeZones에서 해당 항목을 찾습니다.
   - 표시 및 예약 논리에 해당 항목의 zoneId, utcOffset 및 utcOffsetCode를 사용합니다.

## 사용자 그룹 멤버십을 위한 비동기 공용 API

### 소개

Adobe Learning Manager은 UG(사용자 그룹) 멤버십을 관리하기 위해 두 개의 _관리자 비동기 API_&#x200B;를 노출합니다.

- POST /async/userGroups/{userGroupId}/users - 사용자를 UG에 비동기적으로 추가
- DELETE /async/userGroups/{userGroupId}/users - UG에서 비동기적으로 사용자 제거

이러한 API는 동일한 요청에서 멤버십을 업데이트하는 대신 일괄 처리를 수락하고 _이벤트 ID_&#x200B;을 반환합니다. 실제 결과는 나중에 Webhook을 통해 전달됩니다.

다음의 경우 사용하십시오.

- 대규모 그룹 또는 빈번한 일괄 업데이트를 관리하고 있습니다.
- 지연 시간은 신뢰성 및 처리량보다 덜 중요합니다.
- UI 클릭 대신 통합(HR, CRM, LXP)을 구축하고 있습니다.

소규모 대화형 관리자 작업의 경우 동기 `/userGroups/{id}/users` API를 계속 사용할 수 있습니다.

### 인증 및 기본 URL

이러한 API는 표준 __v2 관리 API__ 표면의 일부입니다.

- [기본 URL(prod)](https://learningmanager.adobe.com/docs/primeapi/v2/)
- 인증: `admin:write` 범위의 OAuth 2.0 액세스 토큰
- 필수 헤더:
   - 인증: Bearer &lt;access_token>
   - Content-Type: application/json
   - 수락: application/json

일반적인 관리자 API 동작 및 범위는 다음을 참조하십시오.

- [개발자 설명서](/help/migrated/integration-admin/feature-summary/developer-manual.md)
- [API 참조 안내서](https://learningmanager.adobe.com/docs/primeapi/v2/)

### 요청 형식

__추가__&#x200B;와 __제거__ 모두 정확히 동일한 본문 모양을 사용합니다.

#### 본문

```
{
  "metadata": {
    "event_id": "my-optional-correlation-id",
    "sourceSystem": "HRIS",
    "batchId": "hr_2026_03_30_0001"
  },
  "data": [
    { "type": "user", "id": "11101219" },
    { "type": "user", "id": "11101220" }
  ]
}
```

#### 데이터(필수)

data는 이 배치에 대한 사용자 리소스 식별자 목록입니다.

- `type`은(는) &quot;user&quot;여야 합니다.
- `id`은(는) ALM의 _숫자 사용자 ID_&#x200B;입니다(전자 메일이 아님, UUID 아님).

#### 제약 조건

- `data`이(가) 있어야 하며 비어 있지 않아야 합니다.
- 최소 한 명의 사용자가 필요합니다.
- 최대 페이로드 크기는 요청당 20명의 사용자입니다.
- 모든 ID는 숫자여야 하며 유효한 사용자를 참조해야 합니다.

이러한 조건 중 하나라도 실패하면 API에서 오류를 반환하고 대기열에 아무것도 없습니다.

#### metadata (선택 사항)

`metadata`은(는) Webhook에서 다시 반복할 추가 상관 관계 데이터입니다.

일반적인 사용:

- `event_id` - 생성한 상관 관계 ID입니다.
- `sourceSystem` - 업스트림 시스템의 이름입니다.
- `batchId` - 일괄 처리 또는 작업 식별자입니다.

서비스는 이 개체를 Webhook 응답에서 변경되지 않은 상태로 반환하므로 콜백을 내부 작업에 일치시킬 수 있습니다.

제한:

- 선택 사항입니다. 완전히 생략할 수 있습니다.
- 모든 키와 값의 조합 길이는 1000자를 초과할 수 없습니다.

### 응답 형식

두 엔드포인트 모두 이벤트 ID로 동기적으로 응답합니다.

```
{ "event_id": "cd2972c8-cb15-47a0-a23f-e4a16cb720f5" }
```

동작:

- `metadata.event_id`이(가) 전달되면 해당 값이 사용됩니다.
- 그렇지 않으면 서비스는 UUID를 생성합니다.

항상 다음 작업을 수행해야 합니다.

- 이 `event_id`을(를) 일괄 처리의 기본 식별자로 저장합니다.
- Webhook 콜백에서 동일한 값을 받게 됩니다.

자세한 내용은 [사용자 그룹 구성원 추가 및 제거에 대한 Webhook](/help/migrated/integration-admin/feature-summary/webhooks.md#webhooks-for-adding-and-removing-user-group-membership)을(를) 참조하십시오.

## 자주 묻는 질문

_2026년 4월 릴리스는 적응형 학습 프로그램에 대한 learningObjects API를 어떻게 변경합니까?_

이 릴리스에서는 학습 프로그램에 isAdaptive 플래그를 추가하고 섹션과 하위 LO가 학습자를 인식하도록 합니다. 적응형 프로그램에서 학습자는 적응형 규칙을 기반으로 표시되는 섹션 및 하위 학습 개체만 볼 수 있으며, 관리자는 사용자 그룹의 기본 적응형 구성을 볼 수 있습니다.

_모든 섹션 및 하위 LO가 항상 반환된다고 가정할 경우 통합을 업데이트해야 합니까?_

예. 적응형 학습 프로그램의 경우 API는 이제 현재 학습자에게 표시되는 섹션 및 하위 LO만 반환합니다. 클라이언트 코드에서는 응답을 전체 목록을 가정하지 않고 신뢰할 수 있는 필터링된 보기로 취급해야 합니다.

_강의 또는 학습 프로그램의 학습자 완료를 프로그래밍 방식으로 재설정하려면 어떻게 해야 합니까?_

새 끝점 사용:

```POST /primeapi/v2/learningObjects/{loId}/instances/{loInstanceId}/refreshCompletion```
권한 및 상태에서 허용할 경우 대상 인스턴스에 대한 완료가 재설정됩니다.

_학습자가 대체 또는 동등한 학습 개체를 통해 무언가를 완료했는지 확인하는 방법은 무엇입니까?_

학습 개체에서 isAlternateComplete 속성을 확인합니다. AlternateCompletions 관계는 학습자가 완료했을 때 대체 역할을 한 학습 개체를 나열합니다.

_특정 학습 개체를 만족시킬 수 있는 모든 대안을 찾으려면 어떻게 하나요?_

다음 엔드포인트를 사용합니다.

```GET /primeapi/v2/learningObjects/{loId}/relatedLOs?type=sourceAlternateLOs&limit={n}```

그리고 데이터 배열(대체 항목) 및 meta.count(대체 항목의 총 수)를 사용합니다.

_현재 학습자가 모듈을 시작할 수 있는지 어떻게 알 수 있습니까?_

먼저 다음 위치에서 자원의 timeSlot을 가져옵니다.

```GET /primeapi/v2/learningObjects/{loId}?include=instances.loResources```
그런 다음 다음을 사용합니다.

```GET /primeapi/v2/learningObjects/{loId}/instances/{loInstanceId}/loResources/{loResourceId}/canStart```

_리소스에 대한 hasContentDrivenAttemptTracking은 무엇을 의미합니까?_

시도 추적은 플랫폼 카운터가 아닌 콘텐츠 자체(예: SCORM/xAPI 로직)에 의해 제어됨을 나타냅니다. 사실이라면, UX 및 보고용 플랫폼 시도 횟수나 제한에만 의존하지 마십시오.

_로그인하지 않은 사용자(공용 환경)에게 적합한 메뉴를 가져오려면 어떻게 해야 합니까?_

사용:

```GET /primeapi/v2/templates/menus?include=pages,subMenus.pages&isNonLoggedIn=true```

이렇게 하면 Experience Builder 또는 기타 헤드리스 사이트에 적합한 익명 사용자에 대해 필터링된 메뉴 및 페이지 구조가 반환됩니다.

_effectiveModifiedDate를 사용한 작업 지원 필터링에서 변경된 사항은 무엇입니까?_

filter.effectiveModifiedDate를 filter.loTypes=jobAid와 결합하는 요청은 이제 지정된 날짜 창 내에서 작업 지원만 올바르게 반환합니다.

_작업 지원 리소스 ID 형식이 변경된 내용과 이를 어떻게 처리해야 합니까?_

ID 형식이 다음과 같은 값에서 변경되었습니다.

```jobAid:<jobAidId>_-1_-1_2_resource```

받는 사람:

```jobAid:<jobAidId>_<version>_<localeCode>```

(예: 작업 지원:131032_2_fr_FR). 작업 지원 리소스 ID를 저장하거나 구문 분석하는 모든 시스템은 업데이트해야 하며 2026년 4월 릴리스로 업그레이드한 후 이러한 ID로 입력된 로컬 인덱스를 다시 작성해야 합니다.
