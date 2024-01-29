---
jcr-language: en_us
title: Learning Manager의 xAPI
description: Experience API(xAPI)는 모든 유형의 학습 경험을 기록 및 추적하는 방식으로 학습 콘텐츠와 학습 시스템이 서로 통신할 수 있도록 하는 e-러닝 소프트웨어 사양입니다.
source-git-commit: 0fabd369e70e15ba22fead0177a24aafd851d88d
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 0%

---



# Learning Manager의 xAPI

## xAPI란? {#whatisxapi}

Experience API(xAPI)는 모든 유형의 학습 경험을 기록 및 추적하는 방식으로 학습 콘텐츠와 학습 시스템이 서로 통신할 수 있도록 하는 e-러닝 소프트웨어 사양입니다. 학습 경험은 학습 기록 저장소(LRS)에 기록됩니다. LRS는 기존의 LMS(교육 관리 시스템) 내에 또는 그 자체로 존재할 수 있습니다.

xAPI에 대한 자세한 내용은 다음을 참조하십시오.  [https://github.com/adlnet/xAPI-Spec](https://github.com/adlnet/xAPI-Spec).

## Learning Manager는 xAPI를 어떻게 지원합니까? {#howdoescaptivateprimesupportxapi}

Learning Manager에는 내장된 학습 기록 저장소가 있습니다. 이 LRS에는 Learning Manager 내에 호스트된 콘텐츠에서 xAPI 명령문을 수락할 수 있는 전체 기능이 있습니다. 서드파티가 생성하는 xAPI 명령문도 허용합니다. 이러한 xAPI 명령문은 Learning Manager 내에 저장되며 Learning Manager 외부로 내보내 타사 데이터 웨어하우징 시스템으로 시각화할 수 있습니다.

## xAPI는 언제 사용합니까? {#whendoyouusexapi}

여러 시스템에 걸쳐 있는 최종 사용자의 학습 경험을 캡처해야 하는 경우가 늘어나고 있습니다.  교육 콘텐츠와 함께 학습자의 정확한 참여를 추적할 필요성도 존재한다. 시작, 진행 중 및 완료(SCORM에서 캡처한 유일한 속성)를 넘어갑니다.

## Learning Manager에서 xAPI 사용 {#usingxapiinprime}

## 애플리케이션 설정 {#setupyourapplication}

1. 통합 책임자로 로그인합니다. 선택 **[!UICONTROL 응용 프로그램]** > **[!UICONTROL 등록]**.

   ![](assets/appregistration.png)

1. 새 응용 프로그램을 등록합니다.

   ![](assets/appregistration.png)

1. 응용 프로그램의 범위를 정의합니다.

   * If **[!UICONTROL 관리자 역할 xAPI 읽기 및 쓰기 액세스]** 이 옵션을 활성화하면 관리자가 xAPI 명령문과 문서를 게시하고 가져올 수 있습니다.
   * If **[!UICONTROL 학습자 역할 xAPI 읽기 및 쓰기 액세스]** 이 옵션을 활성화하면 관리자가 xAPI 명령문과 문서를 게시하고 가져올 수 있습니다.

1. 변경 사항을 저장합니다. 개발자 ID와 시크릿을 받습니다.

**끝점**:

xAPI Swagger 문서를 보려면 아래 링크를 클릭하십시오.

[https://learningmanagereu.adobe.com/docs/primeapi/xapi/](https://learningmanagereu.adobe.com/docs/primeapi/xapi/)

참고: Learning Manager에서 지원되는 xAPI 버전은 1.0.3입니다.

## API 인증 {#apiauthentication}

Learning Manager xAPI는 클라이언트 응용 프로그램 인증 및 승인에 OAuth 2.0 프레임워크를 사용합니다. 응용 프로그램을 등록하면 clientId 및 clientSecret을 가져올 수 있습니다. 브라우저에서는 SSO, Adobe ID 등 사전 구성된 계정을 이용하여 Learning Manager 사용자를 인증하는 Get URL이 사용됩니다.

```
GET https://learningmanager.adobe.com/oauth/o/authorize?client_id=<Enter your clientId>&redirect_uri=<Enter a url to redirect to>&state=<Any String data>&scope=<admin:xapi or learner:xapi>&response_type=CODE.
```

## Learning Manager LO로 xAPI 명세서 추적 {#trackingxapistatementsasprimelo}

이제 작성자는 강의를 만들면서 xAPI 모듈을 선택하여 Learning Manager 외부의 사용자 경험을 모니터링할 수 있습니다. 예를 들어 이 기능을 사용하여 강의 소비에 사용되는 서드파티 플랫폼의 사용자 활동을 평가할 수 있습니다.

1. 이미지를 만드는 동안 **[!UICONTROL 활동 모듈]**, **[!UICONTROL 유형]**option, 팝업 메뉴를 사용하여  **[!UICONTROL xAPI 기반 모듈.]**

   ![](assets/xapimodulecreation.png)

1. IRI를 제공해야 합니다. 제공되지 않은 경우 Learning Manager에서 자동으로 생성합니다.

   활동에 대한 IRI는 계정 전체에서 고유합니다. 즉, Learning Manager의 두 모듈은 동일한 IRI를 가질 수 없습니다. 다음과 같은 경우 새 IRI가 생성됩니다.

   * xAPI 모듈이 있는 강의가 계정 간에 공유되는 경우.
   * xAPI 모듈이 있는 인증이 되풀이되는 경우



   언급된 IRI가 포함된 모든 xAPI 명령문은 위의 모듈에서 추적되며 Learning Manager 보고서에 반영됩니다.

1. 자동 생성된 IRI를 복사하려면 활동 모듈 페이지를 다시 방문하십시오.
1. 모듈을 게시합니다.

**참고 사항:**

* Learning Manager는 현재 mbox만 식별자로 지원합니다. mboz_sha1, openid, 계정을 포함한 다른 식별자는 지원되지 않습니다.

* stateId 및 profileId는 Learning Manager와 함께 사용되는 UUID입니다.
* PUT 요청은 xAPI 에이전트/프로필, 활동/프로필 및 활동/상태에 대한 문서를 덮어쓰지 않습니다.
* 알 수 없는 그룹은 Actor에서 지원되지 않습니다.
* &quot;related_activities&quot; 매개 변수는 GET 문에서 지원되지 않습니다.
* &#39;format=ids&#39; 및 &#39;format=canonical&#39; 매개 변수는 GET 문에서 지원되지 않습니다.
* xAPI 명령문을 무효화해도 명령문이 게시될 때 Learning Manager에서 발생한 작업은 실행 취소되지 않습니다.

## 보고서 생성 {#generatereports}

xAPI 보고서는 excel 보고서로 생성할 수 있습니다. 책임자가 **[!UICONTROL 보고서]** > **[!UICONTROL Excel 보고서]** > **[!UICONTROL xAPI 활동 보고서]**.

다운로드된 보고서는 학습자와 책임자가 어떤 명령문에든 게시한 모든 정보를 불러옵니다.

타사 통합을 위해 FTP 및 Box 커넥터를 사용하여 동일한 보고서를 생성/예약할 수 있습니다. 다음 단계를 따르십시오.

통합 책임자로 로그인 > FTP/Box 커넥터 열기 > 왼쪽 창에서 xAPI 활동 보고서 선택 > 보고서 예약/생성을 선택합니다.

![](assets/xapischedule.png)

* xAPI 명령문에서 최대 점수 없이 원시 점수만 전송되면, LT에 퀴즈 점수가 표시되지 않습니다.

* Learning Manager에서 백분율 점수를 얻기 위해 배율이 조정된 점수가 xAPI를 통해 전송됩니다.

## 샘플 보고서 {#samplereport}

[샘플 xAPI 보고서](assets/xapireport8842560559890766717csv.zip)
