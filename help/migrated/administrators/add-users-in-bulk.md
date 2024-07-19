---
jcr-language: en_us
title: 사용자 일괄 추가
description: 한 번에 여러 사용자를 추가하는 방법을 알아봅니다.
contentowner: saghosh
exl-id: c3309ce5-8764-452e-82d5-5637c23c661b
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 25%

---

# 사용자 일괄 추가

이 교육에서는 CSV를 통해 사용자를 일괄 추가하는 방법을 알아봅니다.

[![단추](feature-summary/assets/launch-training-button.png)](https://learningmanager.adobe.com/app/learner?accountId=98632&amp;sdid=51TC8QS1&amp;mv=display&amp;mv2=display#/course/7555555)

교육을 시작할 수 없는 경우 <almacademy@adobe.com>에 작성하세요.

## 여러 사용자를 추가하는 방법

아래 단계에 따라 한 번에 여러 사용자를 추가할 수 있습니다.

1. 관리자 로그인의 왼쪽 창에서 **[!UICONTROL 사용자]**&#x200B;를 클릭한 다음 **[!UICONTROL 추가]** > **[!UICONTROL csv 업로드]**&#x200B;를 클릭합니다. 팝업 대화 상자가 나타납니다.

1. .CSV 파일을 사용하여 여러 사용자를 추가할 수 있습니다. **[!UICONTROL 가져오기]**&#x200B;를 클릭하고 컴퓨터에서 .csv 파일을 선택하거나 엽니다.

1. 파일을 가져오고 난 다음, 처음 .csv 파일을 업로드할 때 .csv 파일의 콘텐트를 응용 프로그램 레이블과 매핑합니다.

   이후 업로드하는 모든 파일에는 이전 레이블 설정이 적용됩니다. 데이터 매핑을 완료한 후 **[!UICONTROL 저장]**&#x200B;을 클릭하고 **[!UICONTROL 추가]**&#x200B;를 클릭하여 매핑한 .csv 파일을 업로드합니다.

1. 데이터 매핑을 완료한 후 **[!UICONTROL 저장]**&#x200B;을 클릭하고 **[!UICONTROL 추가]**&#x200B;를 클릭하여 매핑한 .csv 파일을 업로드합니다.

## 필수 필드로 CSV 업로드 {#csvuploadwithmandatoryfields}

CSV에 사용자의 프로필과 관리자의 이메일 ID를 추가할 필요는 없습니다. 사용자 이름 및 사용자의 이메일 ID 만 필수 필드입니다.

이 경우 기본적으로 회사의 관리자는 사용자의 관리자로 간주됩니다. 기본적으로 직원은 사용자의 프로필로 간주됩니다.

**샘플 CSV**

필수 필드가 있는 Learning Manager 샘플 CSV를 아래에서 사용할 수 있습니다.
[Sample-CSV-name-email.zip](assets/sample-csv-name-email.zip)

## 모든 필드로 CSV 업로드 {#csvuploadwithallthefields}

직원에 대한 관리자의 이메일 ID를 포함하기 전에 관리자가 CSV에 직원으로 먼저 추가되었는지 확인하십시오. 예를 들어 아래 스냅샷에서 직원 이름인 Howard Walters를 참조하십시오.

![](assets/csv-example.png)

*업로드를 위한 CSV 템플릿*

또한 조직 책임자는 자신을 사원으로 추가하고 관리자의 이메일 ID를 루트로 언급할 수 있습니다.

**샘플 CSV**

모든 필드가 있는 Learning Manager 샘플 CSV를 아래에서 사용할 수 있습니다.
[learning-manager-sample-csv.zip](assets/learning-manager-sample-csv.zip).

자세한 내용은 [CSV 업로드 사용](/help/migrated/administrators/feature-summary/add-users-user-groups.md) 기능 도움말 콘텐츠를 참조하십시오.
