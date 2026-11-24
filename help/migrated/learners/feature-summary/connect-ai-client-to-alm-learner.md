---
description: AI 클라이언트가 Adobe Learning Manager에 한 번 액세스하도록 인증하면 과정, 등록 및 학습 경로에 대해 자연어로 질문할 수 있습니다.
jcr-language: en_us
title: AI 클라이언트를 Adobe Learning Manager에 연결
exl-id: dfb3d08d-405d-468c-9126-71a345815d5c
source-git-commit: 89aa1b5ab02eed8a61507ab162fcbbd384e6c5fc
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%
---

# AI 클라이언트를 Adobe Learning Manager에 연결

## 개요

통합 책임자는 먼저 커넥터를 구성해야 합니다. Adobe Learning Manager 커넥터가 표시되지 않으면 관리자에게 문의하십시오. **커넥터는 Adobe Learning Manager Ultimate 계층 계정에서만 사용할 수 있습니다**. 관리자는 [기업 AI 클라이언트에 Adobe Learning Manager 추가](/help/migrated/administrators/feature-summary/add-alm-to-ai-client.md)를 볼 수 있습니다.

1. Claude 또는 ChatGPT Enterprise와 같은 조직의 AI 클라이언트를 엽니다.
2. 커넥터 목록에서 Adobe Learning Manager 커넥터를 찾습니다.
3. **연결**&#x200B;을 선택합니다.
4. 연결을 인증하고 메시지가 표시되면 Adobe Learning Manager 계정 세부 정보를 제공합니다.
5. 학습에 대해 질문해 보십시오. [학습자를 위한 샘플 프롬프트](/help/migrated/learners/feature-summary/sample-prompts-for-learners.md)에 대해 자세히 알아보세요.

>[!NOTE]
>
>한 번 인증하면 됩니다. 요청은 자체 권한으로 실행되므로 Adobe Learning Manager에서 액세스할 수 있는 항목만 표시됩니다.

## 문제 해결

**커넥터를 찾을 수 없습니다.**
관리자에게 커넥터를 활성화하도록 요청하십시오.

**AI 클라이언트가 이전 질문을 기억하지 못합니다**
서버는 각 요청을 새 요청으로 처리합니다. 대화가 계속되는지 여부는 AI 클라이언트에 따라 달라집니다. 다음 질문에서 관련 세부 사항을 다시 진술하십시오.

**AI 클라이언트가 Adobe Learning Manager 커넥터를 호출하지 않습니다.**
등록 또는 강의 주제 등 질문에서 원하는 항목의 이름을 지정합니다.
