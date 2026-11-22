---
description: 학습자가 Claude, ChatGPT Enterprise 및 사용자 정의 상담사 내에서 강의를 찾고, 진행 상황을 추적하고, Adobe Learning Manager 콘텐츠에서 답변을 받을 수 있도록 합니다.
jcr-language: en_us
title: Adobe Learning Manager 모델 컨텍스트 프로토콜 서버
exl-id: 8d0a25a6-1301-4f68-8db7-e3b1d3ff6537
source-git-commit: f6dc1e97076edf812862b80a6ed5931989c660da
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 0%
---

# Adobe Learning Manager 모델 컨텍스트 프로토콜 서버

## 개요

모델 컨텍스트 프로토콜(MCP)은 AI 클라이언트가 도구에 연결하는 표준 방법입니다. Adobe Learning Manager MCP 서버는 학습자가 이미 작업한 곳에 학습을 가져옵니다. 이는 Adobe Learning Manager 학습자 도구를 사용자 정의 엔터프라이즈 상담사, Claude 또는 ChatGPT와 같이 MCP를 지원하는 모든 AI 클라이언트에 공개합니다. 그러면 학습자는 콘텐트가 Adobe Learning Manager에 머무르는 동안 동일한 클라이언트 내에서 교육 및 진행률에 액세스할 수 있습니다.

## 학습자 기능

학습자는 이미 사용하고 있는 AI 클라이언트에서 자연어로 작업합니다. 클라이언트는 각 요청을 해석하고 적절한 Adobe Learning Manager 학습자 도구를 호출한 다음 학습자가 액세스할 수 있는 내용에 따라 응답을 반환합니다. 학습자는 다음을 수행할 수 있습니다.

* 사용할 수 있는 강의, 인증 및 학습 경로를 찾아보십시오.
* 곧 만료될 학습 내용을 포함하여 등록, 진행 상황 및 기한을 추적합니다.
* 학습 콘텐츠에 대한 답변 기반을 확보하세요.
* 목표에서 개인화된 학습 경로를 생성하고 저장합니다.
전체 목록을 보려면 **학습자 도구 참조**&#x200B;를 확인하세요.

AI 클라이언트는 MCP 서버를 호출하여 각 요청을 일치하는 학습자 도구로 라우팅합니다.

전체 목록을 보려면 **학습자 도구 참조**&#x200B;를 확인하세요.

## 고객 및 파트너 교육

고객 및 파트너 교육은 MCP 서버의 주요 사용입니다. 자체 기업 AI 에이전트를 구축하는 조직은 해당 에이전트를 Adobe Learning Manager 학습자 도구에 연결할 수 있습니다. 그런 다음 고객과 파트너는 별도의 학습 도우미로 이동하지 않고도 이미 사용하는 도우미에서 학습합니다.

예를 들어 Acme Inc.는 자체 엔터프라이즈 AI 어시스턴트를 구축합니다. Acme Inc. 파트너가 Tech Corp의 환경을 방문하여 Tech Corp 제품에 대해 알아봅니다. Acme의 도우미는 MCP 서버를 통해 Adobe Learning Manager 계정에 연결하고 학습 관련 응답을 반환하므로 파트너가 Acme 경험을 떠나지 않습니다.

이 접근 방식을 통해 조직은 다음을 수행할 수 있습니다.

* 파트너의 기존 AI 경험에서 학습을 제공하세요.
* 맞춤형 기업 상담사가 Adobe Learning Manager 학습자 도구를 사용하도록 합니다.
* 학습을 나만의 워크플로우로 빌드하세요.
* 학습을 엔터프라이즈 AI 에코시스템과 통합합니다.

## 직원 교육

클로드와 같은 AI 클라이언트를 이미 사용하는 직원은 학습 정보를 현지에서 얻을 수 있다. 예를 들어 직원은 Adobe Learning Manager으로 전환하지 않고도 할당된 학습을 확인하고, 등록을 검토하고, 주제의 강의를 찾거나 학습 경로를 요청할 수 있습니다. 샘플 요청은 [학습자용 샘플 프롬프트](https://word-edit.officeapps.live.com/docs/sample-prompts-adobe-learning-manager-learners)를 참조하십시오.

이 접근 방식을 통해 직원은 다음을 수행할 수 있습니다.

* 이미 사용하고 있는 도구에 머무르십시오.
* 어디에서나 학습에 임할 수 있습니다.
* MCP를 지원하는 모든 AI 클라이언트를 Adobe Learning Manager의 진입점으로 사용합니다.
* 컨텍스트를 변경하지 않고 학습 정보를 얻을 수 있습니다.

## 두 대상 그룹을 위한 서버 1대

고객 및 파트너 교육과 직원 교육은 동일한 학습자 도구와 동일한 서버를 사용합니다. 관객만이 변화합니다. 학습자의 성향에 맞는 접근 방식을 선택합니다.

| **대상자** | **예** | **학습자가 작업하는 위치** |
|----|----|----|
| 외부 | 고객 및 파트너 | 귀사의 자체 엔터프라이즈 AI 에이전트 |
| 내부 | 직원 | Claude 또는 ChatGPT Enterprise와 같은 기업 AI 클라이언트 |

## 역할 설정

셋업은 세 가지 역할로 분할됩니다.

* **관리자:** Adobe Learning Manager에서 MCP 클라이언트 응용 프로그램을 만들고 관리합니다. [MCP 서버 구성](https://word-edit.officeapps.live.com/docs/configure-model-context-protocol-server-adobe-learning-manager)을 참조하세요.
* **AI 클라이언트 관리자:** Claude 또는 ChatGPT Enterprise와 같은 조직의 엔터프라이즈 AI 클라이언트에 서버를 추가합니다.
* **학습자:** AI 클라이언트에서 **연결**&#x200B;을 선택하고, 연결을 인증하고, Adobe Learning Manager 계정 세부 정보를 제공합니다.

## 학습자 요청 보안

각 학습자는 연결을 인증하고 Adobe Learning Manager 계정 세부 정보를 제공합니다. 요청은 해당 학습자로 실행되므로 AI 클라이언트는 학습자가 Adobe Learning Manager에서 액세스할 수 있는 정보만 반환합니다. 서버에서는 학습자에게 추가 액세스 권한이 부여되지 않습니다.

## 이 업데이트의 MCP 제한 사항

* 도구 가용성은 AI 클라이언트가 지원하는 기능에 따라 달라집니다.
* 각 요청은 새 요청으로 처리됩니다. 멀티턴 대화는 AI 클라이언트가 대화 컨텍스트를 유지하는 경우에만 작동합니다.
