---
description: ALM의 API 변경 사항
jcr-language: en_us
title: 2026년 5월 패치 릴리스의 API 변경 사항
source-git-commit: 24f54599749bce60916a57634144b0ca7f6a6d10
workflow-type: tm+mt
source-wordcount: '113'
ht-degree: 0%

---


# 2026년 5월 패치 릴리스의 API 변경 사항

## GET /learningObjects API 개선 사항

이제 GET 관계가 포함될 때 인스턴스 /learningObjects API에 learningObjectInstance 리소스의 새 startDate 속성이 포함됩니다.

**끝점**
GET /learningObjects/{id}?include=instances

**변경**
새 필드 startDate가 다음 아래에 추가되었습니다.
included[].attributes.startDate

**설명**
startDate는 학습 객체 인스턴스의 예약된 시작 날짜 및 시간을 나타냅니다.

**예**
https://learningmanagerstage1.adobe.com/primeapi/v2/learningObjects/course:13209797?include=instances
샘플 응답(잘림)

```
{
  "id": "course:13209797_16226533",
  "type": "learningObjectInstance",
  "attributes": {
    "dateCreated": "2026-05-20T04:35:46.000Z",
    "isAET": false,
    "isDefault": true,
    "isFlexible": false,
    "startDate": "2026-10-06T18:29:59.000Z",
    "state": "Active",
    "timeZoneCode": "IST"
  }
}
```

**노트**

* 해당 학습 객체 인스턴스에 대해서만 필드가 반환됩니다.
* 이 값은 ISO 8601 UTC 날짜-시간 형식으로 반환됩니다.
* 기존 통합은 이전 버전과 호환되는 상태로 유지됩니다.
