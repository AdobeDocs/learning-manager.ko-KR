---
jcr-language: en_us
title: 수강생을 확인할 수 없음
description: 강의의 학습자 탭에는 Adobe Learning Manager에 등록된 학습자가 표시되지 않습니다. 그러나 보고서를 생성하면 보고서에서 등록된 학습자를 확인할 수 있습니다.
contentowner: saghosh
exl-id: 2ea54347-fa6b-493e-b73c-d350efb2aaaf
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 58%

---

# 수강생을 확인할 수 없음

## 문제

강의에 등록된 학습자를 확인할 수 없습니다.

## 설명

강의의 학습자 탭에는 등록된 학습자가 표시되지 않습니다. 그러나 보고서를 생성하면 보고서에서 등록된 학습자를 확인할 수 있습니다.

![](assets/no-learners.png)

*학습자가 표시되지 않음*

## 원인

상위 학습 개체(학습 프로그램 또는 인증)를 통해 등록된 학습자는 상위 학습 개체의 학습자 탭에 표시됩니다. 강의의 학습자 탭에서는 학습자를 검색할 수 없습니다.

**학습자가 어떤 상위 학습 개체에 등록되어 있는지 확인하는 방법**

이 정보는 학습자 성적 증명서에서 확인할 수 있습니다. 성적 증명서를 생성하려면 아래 단계를 따르십시오.

1. 관리자로 로그인합니다.
1. **[!UICONTROL 보고서]** > **[!UICONTROL 사용자 지정 보고서]** > **[!UICONTROL Excel 보고서]** > **[!UICONTROL 학습자 성적 증명서]**&#x200B;를 클릭합니다.

1. **[!UICONTROL 학습자]**&#x200B;의 이름을 입력하고 **[!UICONTROL 날짜]** 범위를 지정하십시오.
1. **[!UICONTROL 고급 옵션]** 섹션을 펼친 후 **[!UICONTROL 모듈 레벨 정보 활성화]** 옵션을 선택합니다.
1. **[!UICONTROL 생성]**&#x200B;을 클릭합니다.

   학습자 성적 증명서에서 학습자가 등록된 상위 학습 개체를 확인할 수 있습니다.
