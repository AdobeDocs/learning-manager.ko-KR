---
description: Claude 또는 ChatGPT Enterprise와 같은 기업 AI 클라이언트에 Adobe Learning Manager MCP 서버를 추가하여 학습자가 연결할 수 있도록 합니다
jcr-language: en_us
title: 기업 AI 클라이언트에 Adobe Learning Manager 추가
exl-id: d893efb7-dc0d-4a3a-88d6-b315340e5daa
source-git-commit: 05691364449234a4782e2de5d4752c7b277f5fd4
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%
---

# 기업 AI 클라이언트에 Adobe Learning Manager 추가

AI 클라이언트에서 관리자 권한이 필요합니다. 먼저 Adobe Learning Manager 관리자로부터 MCP 끝점 URL, 클라이언트 ID 및 보안 키를 얻습니다. 자세한 내용은 **모델 컨텍스트 프로토콜 서버 구성**&#x200B;을(를) 참조하십시오.

## 커넥터 추가

1. 관리자 권한으로 기업 AI 클라이언트에 로그인합니다.
2. 커넥터에 대한 관리자 설정을 엽니다.
3. 모델 컨텍스트 프로토콜을 사용하는 사용자 정의 커넥터를 추가합니다.
4. Adobe Learning Manager MCP 끝점 URL을 입력합니다.
5. Adobe Learning Manager 관리자의 클라이언트 ID와 비밀 키를 입력합니다.
6. 커넥터를 저장합니다.
7. 학습자가 커넥터를 사용할 수 있도록 합니다.

>[!NOTE]
>
>AI 클라이언트 인터페이스는 자주 변경됩니다. 이러한 단계가 클라이언트와 일치하지 않는 경우 AI 클라이언트 공급업체의 원격 커넥터 추가 설명서를 참조하십시오.

## 문제 해결

**학습자가 커넥터를 볼 수 없습니다.** 학습자의 작업 영역 또는 그룹에 대해 커넥터가 활성화되었는지 확인합니다.

**학습자가 연결을 선택하면 인증이 실패합니다.** 클라이언트 ID 및 비밀 키가 Adobe Learning Manager 서버의 **클라이언트 자격 증명** 페이지에 있는 값과 일치하는지 확인하십시오.
