---
description: 사용자 정의된 테마 JSON 파일을 Content Composer로 가져오는 방법과 강의 테마 패널에서 사용할 수 있는 새 사용자 정의 테마로 저장하는 방법을 알아봅니다.
jcr-language: en_us
title: 테마 가져오기
source-git-commit: f8687710f5b73e8b7cf8d56057cac25483f38cdc
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---


# 테마 가져오기

사용자 정의된 JSON 파일을 가져와 Content Composer에서 변경 내용을 새 테마로 적용합니다.

1. 도구 모음에서 **테마**&#x200B;를 선택합니다.

2. **강의 테마** 옵션에서 **가져오기**&#x200B;를 선택합니다.
   ![](../assets/48_course_themes_import_button_updated.png)

3. 컴퓨터에서 사용자 정의된 JSON 파일을 선택합니다.

4. **새로 저장**&#x200B;을 선택하여 새 사용자 지정 테마를 만듭니다.

## 테마 JSON 구조 개요

테마 JSON 파일에는 5개의 기본 영역이 있습니다.

| 섹션 | 컨트롤 |
|----------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 메타데이터(id, 이름, 버전, 설명, 작성자, 소스, isDefault) | 테마 ID 및 표시 정보 |
| foundation.palette | var(—tokenName)을 통해 테마 전체에서 참조된 7개의 핵심 색상 토큰(전경, 배경, 강조, 배경미세하게, 보조, textPrimary, textInverse)입니다. |
| foundation.fonts | 제목 및 본문 글꼴 스택 |
| foundation.spacing 및 foundation.radius | 가로/세로 간격 비율 및 모퉁이 반경 토큰 |
| 요소 | 모든 텍스트 역할(lessonTitle, topicTitle, blockHeading, subject, question, caption, paragraph, buttonLabel) 및 모든 구성 요소(paragraphBlock, imageBlock, videoBlock, imageGrid, 아코디언, 캐러셀, flipCard, 탭, 타임라인, 평가)에 대한 타이포그래피 및 구조적 스타일링 |

대부분의 값은 var(—tokenName)을 사용하여 팔레트 토큰을 참조하므로, 액센트와 같은 단일 토큰을 업데이트하면 이를 참조하는 모든 요소에 걸쳐 변경되는 캐스케이드가 자동으로 생성됩니다. 개별 색상 값을 검색할 필요가 없습니다.

