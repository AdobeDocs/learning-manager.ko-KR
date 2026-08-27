---
description: 설정, 구성 및 이벤트 처리를 포함하여 iframe을 사용하여 앱에 학습자 도우미를 포함하는 방법에 대해 알아봅니다
jcr-language: en_us
title: iFrame을 포함하여 학습자 도우미 통합
source-git-commit: 1549a4592b7a930631dcff6b2e75ec3a3d4f5592
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 1%

---


# iframe을 사용한 학습자 도우미 포함

## 개요

Adobe Learning Manager(ALM) 사용자는 자신의 학습자 관련 응용 프로그램(예: 사용자 정의 포털, LMS 프런트 엔드, 학습 허브 등)에 **학습자 도우미**&#x200B;를 직접 포함할 수 있습니다 표준 HTML `<iframe>` 사용.

iFrame을 통해 포함되면 학습자 도우미는 다음을 포함한 모든 학습자 도우미 기능에 대한 액세스를 제공합니다.

* 오케스트레이터
* 응답 에이전트
* 지식 에이전트
* 학습 경로 에이전트

>[!IMPORTANT]
>
>iFrame을 포함하면 응용 프로그램에서 학습자 도우미의 기본 상담사에 완전히 액세스할 수 있습니다. 그러나 귀하의 응용 프로그램(&quot;상위 앱&quot;)은 도우미가 발생시키는 모든 이벤트를 처리합니다. 예를 들어, 학습자가 길잡이의 응답 내에 있는 인용 또는 강의 링크를 클릭하면 길잡이가 이벤트를 발생시키고 부모 응용 프로그램이 해당 이벤트를 처리하고 실제 탐색을 수행해야 합니다. 학습자 도우미가 응용 프로그램을 대신하여 탐색하지 않습니다.

## 사전 요구 사항

시작하기 전에 다음 사항이 있는지 확인하십시오.

* 학습자 도우미가 활성화된 ALM 테넌트 관리자 설정 페이지에서 필요한 카탈로그를 구성합니다.
* 학습자(또는 책임자) 세션 인증을 위한 유효한 accessToken입니다. 액세스 토큰을 생성하려면 [OAuth 2.0을 사용한 인증](https://experienceleague.adobe.com/ko/docs/learning-manager/using/integration/developer-manual#authentication-using-oauth-20) 페이지의 지침을 따르십시오. 이 페이지에는 인증에 필요한 단계와 계속하는 데 필요한 액세스 토큰을 생성하는 단계가 포함되어 있습니다.
* 응용 프로그램에 `<iframe>`을(를) 포함하고 브라우저의 postMessage API를 통해 응용 프로그램과 통신하는 기능입니다.
* 응용 프로그램은 포함된 iFrame의 메시지를 수신하고 응답해야 하므로 상위 응용 프로그램의 프런트 엔드 코드 소유권입니다.

## Learning Assistant 구성 매개변수

| 매개 변수 이름 | 값 | 설명 |
|---|---|---|
| hostName | learningmanager.adobe.com | 응용 프로그램의 호스트 도메인을 지정합니다. |
| accessToken | token123(실제 액세스 토큰) | 사용자 세션을 인증하고 권한을 부여하는 데 사용되는 토큰입니다. |

## iFrame 초기화

포함된 iFrame 구성 핸드셰이크를 사용하여 postMessage API로 구성을 학습자 도우미에 전달합니다.

1. 상위 응용 프로그램은 학습 도우미를 `<iframe>`(으)로 포함합니다.
2. URL 기반 구성이 발견되지 않으면 Learning Assistant는 ALM_CHAT_REQUEST_CONFIG 이벤트를 상위 응용 프로그램으로 보냅니다.
3. 상위 응용 프로그램은 구성 페이로드를 포함하는 ALM_CHAT_CONFIG 이벤트로 응답합니다. 예:

   ```json
   {
     "hostName": "learningmanager.adobe.com",
     "accessToken": "token123",
     "openByDefault": false,
     "isAdmin": false
   }
   ```

4. 초기화에 성공하면 학습자 도우미가 렌더링하여 사용할 준비가 됩니다.

## iFrame 이벤트 요약

학습자 도우미와 상위 응용 프로그램은 양방향 postMessage 이벤트를 통해 통신합니다.

### 나가는 이벤트(학습자 도우미 iFrame에서 상위 앱으로)

| 이벤트 이름 | 설명 | 전달된 매개 변수 |
|---|---|---|
| ALM_CHAT_OPENED | 채팅이 열리면 발생합니다. | -- |
| ALM_CHAT_CLOSED | 채팅이 닫히면 발생합니다. | -- |
| ALM_CHAT_LO_REDIRECT | 개인화된 학습 경로 개요 페이지로 이동합니다. | loId, loType, instanceId |
| ALM_CHAT_URL_REDIRECT | 채팅 메시지에서 외부 링크를 클릭하면 발생합니다. | url |
| ALM_CHAT_REQUEST_CONFIG | 상위 응용 프로그램에서 구성을 요청합니다. | -- |
| ALM_CHAT_WAITING_FOR_REPLY | 도우미가 요청을 처리하고 있거나 응답을 기다리고 있음을 나타냅니다. | isWaitingForReply |
| ALM_CHAT_PERSONALIZED_PATH_CREATED | 학습 경로가 저장되면 트리거됩니다. | -- |

### 수신 이벤트(학습자 길잡이 상위 앱)

| 이벤트 이름 | 설명 | 페이로드 |
|---|---|---|
| ALM_CHAT_CONFIG | 도우미를 초기화하는 데 필요한 구성 페이로드를 보냅니다. | 구성 객체 |
| ALM_CHAT_OPEN | 학습자 도우미를 엽니다. | 없음 |
| ALM_CHAT_CLOSE | 학습자 도우미를 닫습니다. | 없음 |
| ASK_AI_ASSISTANT_QUERY | 채팅 창을 열고 도우미에게 쿼리를 제출합니다. | { query: &quot;Question text&quot; } |

## 상위 응용 프로그램의 이벤트 처리 요구 사항

iFrame을 통해 학습자 도우미를 포함한다고 해서 완전히 자가 포함 위젯이 되는 것은 아닙니다. 부모 응용 프로그램은 적극적으로 나가는 이벤트를 듣고 적절한 조치를 취해야 합니다. 최소한 응용 프로그램은 다음 작업을 수행해야 합니다.

* ALM_CHAT_REQUEST_CONFIG를 듣고 ALM_CHAT_CONFIG로 응답하여 도우미가 초기화할 수 있도록 합니다.
* ALM_CHAT_LO_REDIRECT 처리: 학습자가 도우미의 답변에서 인용 또는 소스를 클릭하면 애플리케이션이 loId, loType 및 instanceId를 수신하며 학습자를 올바른 과정 또는 학습 개체로 탐색합니다.
* ALM_CHAT_URL_REDIRECT 처리: 학습자가 채팅 메시지에서 외부 링크를 클릭하면 애플리케이션이 URL을 수신하고 URL을 열거나 탐색합니다(예: 새 탭).
* 필요에 따라 ALM_CHAT_OPENED / ALM_CHAT_CLOSED / ALM_CHAT_WAITING_FOR_REPLY를 추적하여 자신의 UI에 도우미의 상태를 반영합니다(예: isWaitingForReply가 true인 동안 로드 표시기를 표시).
* 선택적으로 ALM_CHAT_OPEN / ALM_CHAT_CLOSE / ASK_AI_ASSISTANT_QUERY를 사용하여 도우미를 프로그래밍 방식으로 제어합니다. 예를 들어, 길잡이를 열고 응용 프로그램의 다른 곳에서 **도움말** 단추의 쿼리를 미리 채울 수 있습니다.

## 도움이 필요하십니까?

Adobe 고객 성공 관리자에게 연락하여 기술 워크스루를 설정합니다.
