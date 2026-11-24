---
description: 학습자가 Adobe Learning Manager 모델 컨텍스트 프로토콜 서버로 수행할 수 있는 작업과 각 기능을 지원하는 도구를 살펴보십시오.
jcr-language: en_us
title: 모델 컨텍스트 프로토콜 서버용 학습자 도구
exl-id: 4509b984-d0ba-4b7e-a0bb-803aa235fd1e
source-git-commit: 89aa1b5ab02eed8a61507ab162fcbbd384e6c5fc
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%
---

# 모델 컨텍스트 프로토콜 서버용 학습자 도구

## 개요

학습자가 연결되면 모든 기능이 로그인 학습자로 실행됩니다. 요청은 학습자가 Adobe Learning Manager에서 액세스할 수 있는 항목만 반환합니다. [AI 클라이언트 연결](/help/migrated/learners/feature-summary/connect-ai-client-to-alm-learner.md)에 대해 자세히 알아보세요.

## 학습자 기능

| **기능** | **학습자가 할 수 있는 작업** | **요청 예시** |
|----|----|----|
| 학습 콘텐츠 검색 | 강의, 인증 및 학습 경로 찾기 | 어떤 리더십 과정을 이용할 수 있습니까? |
| 등록 보기 | 등록 및 기한 학습 확인 | 내 강의 중 만료 예정 강의는 무엇입니까? |
| 학습 관련 질문 | 학습 콘텐츠에서 답변 받기 | FedRAMP에서 공급망 리스크 관리는 무엇을 의미합니까? |
| 학습 경로 생성 | 개인화된 학습 경로 생성 | 프로젝트 관리 기술을 향상하는 강의를 찾도록 도와주십시오. |
| 학습 경로 저장 | 생성된 학습 경로 저장 | 이 학습 경로를 저장합니다. |

## 지원되는 MCP 도구

Adobe Learning Manager MCP 서버는 다음과 같은 학습자 도구를 노출합니다.

| **도구 이름** | **설명** |
|----|----|
| search_learning_item | 카탈로그에서 강의, 학습 경로, 인증, 작업 지원, 배지, 스킬, 카탈로그 및 태그를 검색합니다. 학습자 상태, 스킬, 태그, 카탈로그, 전달 형식, 가격 및 언어별로 필터링합니다. 주제 질문의 경우 answer_learning_content_question을 사용합니다. 예: &quot;초보자 파이썬 코스&quot; |
| list_my_learning_enrollments | 학습자의 등록, 진행 중 및 완료한 과정, 학습 경로, 인증, 작업 지원을 상태, 진행 상황 및 기한과 함께 나열합니다. 학습 객체 유형 또는 완료 상태별로 필터링합니다. 가장 최근 등록을 먼저 확인한 결과가 표시됩니다. 예: &quot;예정된 날짜가 얼마 남지 않았습니까?&quot; |
| get_learning_object | ID에 따라 강의, 학습 경로, 인증 또는 작업 지원에 대한 전체 세부 정보를 얻을 수 있습니다(선택 사항). 인스턴스, 스킬 및 하위 학습 개체도 함께 제공됩니다. search_learning_items 또는 list_my_learning_enrollments에서 ID를 가져옵니다. |
| get_my_learning_profile | 계정 및 관리자 세부 정보를 포함하여 학습자의 프로필을 가져옵니다. 등록 및 진행률을 보려면 list_my_learning_enrollments를 사용합니다. |
| answer_learning_content_question | 학습 내용에 대한 질문에 답하고, 학습 자료를 근거로 하며, 원천 학습 대상을 인용한다. 하나의 학습 객체를 요약하거나, 적용 범위, 깊이, 사전 요구 사항 및 대상자에 대해 두 가지를 나란히 비교합니다. 콘텐츠를 찾거나 나열하려면 search_learning_items 또는 list_my_learning_enrollments를 사용합니다. 예: &quot;내 네트워킹 과정에서 다루는 TCP와 UDP를 설명합니다.&quot; |
| personalized_learning_path | 학습자의 목표, 주제 및 요구 사항과 일치하는 강의를 추천합니다. 승인된 경로를 학습자 계정에 저장합니다. 저장된 경로를 나열하거나 ID를 사용하여 한 경로의 세부 정보와 강의를 가져옵니다. |

>[!IMPORTANT]
>
>도구 이름은 참조용으로 표시되며 클라이언트 구현에 따라 다를 수 있습니다.
