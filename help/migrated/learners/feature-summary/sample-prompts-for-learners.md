---
description: 학습자가 Claude 또는 ChatGPT Enterprise에서 강의 검색, 등록 확인 및 학습 경로 빌드를 요청할 수 있는 샘플 프롬프트를 찾습니다
jcr-language: en_us
title: Adobe Learning Manager 학습자를 위한 샘플 프롬프트
exl-id: e5d64ac4-03e9-49bc-95d0-bb074d55987f
source-git-commit: 89aa1b5ab02eed8a61507ab162fcbbd384e6c5fc
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 2%
---

# Adobe Learning Manager 학습자를 위한 샘플 프롬프트

Claude 또는 ChatGPT Enterprise에서 이러한 프롬프트를 사용하여 강의를 검색하고, 등록을 확인하고, 학습 경로를 빌드할 수 있습니다.

먼저 AI 클라이언트를 연결하십시오. [AI 클라이언트를 Adobe Learning Manager에 연결](/help/migrated/learners/feature-summary/connect-ai-client-to-alm-learner.md)하는 방법에 대해 자세히 알아보십시오. 각 프롬프트는 [학습자 도구 참조](/help/migrated/learners/feature-summary/learner-tools-reference.md)의 도구에 매핑됩니다.

>[!TIP]
>
>주제, 강의 상태 또는 마감일 등 필요한 항목의 이름을 지정합니다. 특정 요청은 AI 클라이언트가 올바른 도구를 선택하는 데 도움이 됩니다.

## 등록

| **프롬프트** | **도구** |
|------------------------------------------|------------------------------|
| 어떤 강의에 등록되어 있습니까? | list_my_learning_enrollments |
| 내 강의 중 만료 예정 강의는 무엇입니까? | list_my_learning_enrollments |

## 검색

| **프롬프트** | **도구** |
|-----------------------------------------|-----------------------|
| 어떤 리더십 과정을 이용할 수 있습니까? | search_learning_item |
| 사용할 수 있는 보안 교육을 표시합니다. | search_learning_item |

## 지식

| **프롬프트** | **도구** |
|----|----|
| FedRAMP에서 공급망 리스크 관리는 무엇을 의미합니까? | answer_learning_content_question |
| 규정 준수 과정의 요구 사항을 설명합니다. | answer_learning_content_question |

## 학습 경로

| **프롬프트** | **도구** |
|----|----|
| 프로젝트 관리 기술을 향상시키기 위한 강의 집합을 찾을 수 있도록 도와주십시오. | personalized_learning_path |
| 이 학습 경로를 저장합니다. | personalized_learning_path |
