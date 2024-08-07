---
jcr-language: en_us
title: Adobe Learning Manager에서 강의를 완료했으나 모듈이 미완료로 표시됨
description: 학습자가 Adobe Learning Manager에서 강의를 완료한 후에도 모듈이 미완료로 표시됩니다.
contentowner: nluke
exl-id: c0f14f2e-733a-4b4f-a2c2-4c0b33a15fa1
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 53%

---

# Adobe Learning Manager에서 강의를 완료했으나 모듈이 미완료로 표시됨

## 문제

학습자가 Adobe Learning Manager에서 강의를 완료한 후에도 모듈이 미완료로 표시됩니다.

## 원인

SCORM 2004의 경우 성공 및 완료 조건을 지정하고 각각에 대한 명령문을 별도로 전송합니다.

**완료 조건**&#x200B;이 슬라이드 보기 100%이고, **성공 조건**&#x200B;이 &quot;퀴즈 합격&quot;으로 설정된 콘텐츠를 예로 들어보겠습니다.

학습자가 강의는 완료했으나 퀴즈에 불합격합니다. 이 경우 진행률은 100%지만 학습자가 **성공 조건**&#x200B;을 충족하지 못하여 모듈이 미완료로 표시됩니다.

## 해결 방법

이 문제는 프로젝트에 대해 설정된 **환경 설정**&#x200B;과 관련이 있습니다. 작성자는 강의 완료 및 성공을 위해 설정된 조건을 확인해야 합니다.

변경이 필요한 경우, 작성자는 Adobe Captivate Classic과 같은 콘텐츠 제작 도구를 사용하여 변경할 수 있습니다. 그런 다음 작성자는 해당 변경에 따라 모듈을 업데이트할 수 있습니다.

![](assets/scorm.png)

*Captivate 클래식 보고 환경 설정 보기*
