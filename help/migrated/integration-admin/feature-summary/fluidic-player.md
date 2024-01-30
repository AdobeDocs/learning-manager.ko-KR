---
description: 이 문서를 읽고 사용자 정의 응용 프로그램에서 Fluidic Player를 포함하는 방법에 관해 알아보십시오.
jcr-language: en_us
title: 포함 가능한 Fluidic Player
contentowner: dvenkate
preview: true
source-git-commit: fba5e5ddc1964b485be473bf356806f234688cf4
workflow-type: tm+mt
source-wordcount: '1626'
ht-degree: 25%

---



# 포함 가능한 Fluidic Player

이 문서를 읽고 사용자 정의 응용 프로그램에서 Fluidic Player를 포함하는 방법에 관해 알아보십시오.

이제 기업은 Learning Manager 외부의 학습자에게 사용자 정의 환경을 제공할 수 있습니다. 공개 API를 사용하면 학습 객체, 학습자 등록 및 학습 진행률과 관련된 모든 정보를 가져와 웹 사이트에 표시할 수 있습니다. 더욱더 중요한 것은 귀하의 웹사이트에 Learning Manager의 Fluidic Player를 포함하여 학습자가 웹사이트에서 바로 콘텐트를 수료할 수 있다는 것입니다. Fluidic Player는 Learning Manager에서 지원하는 모든 콘텐트를 재생하게 해줍니다. 자체 웹 사이트에 포함하면 Learning Manager 내에서 사용할 때와 똑같은 기능을 제공합니다.

**모든 eLearning 콘텐츠 재생[](../../learners/feature-summary/fluidic-player.md#main-pars_text_779047019)**

Fluidic Player는 플러그인이나 다운로드 없이 일관적이고 직관적인 방식으로 모든 형식의 e러닝 콘텐트를 가상으로 재생합니다. 학습자는 콘텐트 파일 형식에 관계 없이 콘텐트를 실행하고 재생할 수 있습니다.

**노트 및 책갈피**

파일 형식에 관계 없이 모든 콘텐트에 노트와 책갈피를 사용할 수 있습니다. 긴 파일 또는 비디오에서 특정 항목을 선택하려면 필요에 맞는 정보를 찾은 지점에 책갈피를 추가할 수 있습니다. 메모와 책갈피는 검색하거나 전자 메일로 보낼 수 있습니다. 노트나 책갈피를 클릭하면 Fluidic Player 내 비디오의 지점 또는 문서의 페이지에 정확하게 도착합니다.

Fluidic Player에 대한 자세한 내용은 다음을 참조하십시오 [Fluidic Player](../../learners/feature-summary/fluidic-player.md).

다음은 포함 가능한 Fluidic Player를 사용할 수 있는 위치의 몇 가지 예입니다.

* Fluidic Player를 웹 사이트** 포함하여 직원** 등록한 강의를 목록화하고 같은 페이지에서 교육을 실행하는 링크를 제공할 수도 있습니다. 이는 학습자가 인트라넷 웹 사이트에서 교육을 수료할 수 있음을 의미합니다.

* 교육업에 종사하시는 경우, 귀하의 고객이 강의를 구매하는 웹사이트를 갖고 계실 것입니다. 고객이 웹 사이트 내에서 구매한 콘텐츠를 수료하도록 웹사이트에 포함 가능한 플레이어를 통합할 수 있습니다.

## 웹사이트에 Fluidic Player를 포함하는 단계 {#stepstoembedfluidicplayerinyourwebsite}

귀하의 웹사이트에 Fluidic Player를 포함하는 사용자 정의 응용 프로그램 제작은 3개의 기본 단계로 이루어집니다.

1. Learning Manager의 통합 책임자 앱에서 응용 프로그램을 생성합니다.
1. 액세스 토큰을 회수합니다.
1. 액세스 토큰으로 공용 API를 사용하여 Learning Manager에서 리소스를 회수합니다.

### 1. 통합 책임자로 응용 프로그램 생성 {#1createanapplicationinintegrationadmin}

이 단계는 새로 고침 토큰 및 액세스 토큰을 회수하는 데 사용되는 응용 프로그램/클라이언트 ID 및 응용 프로그램/클라이언트 시크릿을 생성하는 데 필요합니다. 응용 프로그램 만들기에 대한 자세한 내용은 다음을 참조하십시오  [애플리케이션 개발 프로세스](developer-manual.md#main-pars_header_994876235)

1. **[!UICONTROL &#39;통합 책임자&#39;]** 앱으로 이동한 다음 **[!UICONTROL &#39;응용 프로그램&#39;]**&#x200B;을 엽니다.

1. 페이지의 오른쪽 상단 모서리에 있는 **[!UICONTROL &#39;등록&#39;]**&#x200B;을 선택합니다.
1. **[!UICONTROL 새로운 응용 프로그램 등록]** 창이 열립니다. 필수 필드를 채웁니다.
1. 사용자 정의 응용 프로그램을 여러 계정에 공유해야 하는 경우 다음을 선택합니다. **[!UICONTROL 아니요]** 옵션 필드에서  **[!UICONTROL 이 계정에만 해당합니까?]**
1. 응용 프로그램을 저장하고 응용 프로그램 ID와 시크릿을 생성하려면 **[!UICONTROL &#39;저장&#39;]**&#x200B;을 클릭합니다.

### 2. 액세스 토큰 회수 {#2retrievingaccesstoken}

Learning Manager는 OAUTH2.0을 사용하므로 공개 API를 사용하여 리소스를 회수하려면 액세스 토큰이 필요합니다. 새로 고침 토큰, 클라이언트 ID 또는 클라이언트 시크릿을 사용하여 액세스 토큰을 불러올 수 있습니다.

**2.1 새로 고침 토큰**

* OAuth 코드 회수

새로 고침 토큰을 회수하려면 OAuth 코드가 필요합니다. 아래 url을 사용하여 로그인한 경우 Learning Manager는 OAuth 코드를 통해 사용자를 리디렉션 URL로 리디렉션합니다(OAuth 코드 추출 예시는 샘플 응용 프로그램의 &quot;oauthredirect.html&quot;에서 확인할 수 있습니다).

```
code https://learningmanager.adobe.com/oauth/o/authorize  
client_id= <application_id>  
&redirect_uri=<redirect_uri>  
&state=<dummy_data>  
&scope=learner:read,learner:write  
&response_type=CODE  
&account=<account_id>  
&email=<email_id>
```

여기, **[!UICONTROL 클라이언트 id]** 은 1단계에서 얻은 응용 프로그램 id입니다.
**[!UICONTROL redirect_url]** 는 1단계의 redirect_url 세트입니다.
**[!UICONTROL 상태]** 는 OAuth 코드를 획득하기 위해 리디렉션 URL을 필터링해야 하는 더미 데이터입니다. Scope는 1단계의 학습자 범위입니다.
**[!UICONTROL response_typ]**e는 항상 &quot;CODE&quot;입니다.\
**[!UICONTROL 계정]**는 선택적 필드입니다.\
**[!UICONTROL email]** 은(는) 선택적 필드입니다\
&#42; 계정 ID와 이메일이 모두 제공된 경우 위의 URL을 통해 사용자는 동일한 계정에 로그인할 수 있습니다. 이 끝점 예제는 샘플 응용 프로그램의 &quot;index.html&quot; 파일에 나와 있습니다.

* 새로 고침 토큰 회수

OAuth 코드를 받으면 아래 끝점에서 받은 OAuth 코드, 클라이언트 ID 및 클라이언트 암호를 사용하여 새로 고침 토큰을 검색할 수 있습니다.

**https://learningmanager.adobe.com/oauth/token**

POST 요청에 대한 응답으로 다음과 같은 내용을 받게 됩니다.

i. refresh_token\
나... access_token\
iii. user_id\
iv. expires_in\
v. user_role\
vi. account_id

**2.2 새로 고침 토큰에서 액세스 토큰 회수**

액세스 토큰을 회수하려면 다음 URL 게시물 본문으로 refresh_token, client_id, client_secret을 사용하여 다른 요청을 전송합니다.

**https://learningmanager.adobe.com/oauth/token/refresh**

POST 요청에 대한 응답으로 다음과 같은 내용을 받게 됩니다.\
i. refresh_token\
나... access_token\
iii. user_id\
iv. expires_in\
v. user_role\
vi. account_id

### 3. 공용 API를 사용하여 리소스 회수 {#3retrieveresourcesusingpublicapi}

세 번째 단계는 액세스 토큰으로 공용 api 를 사용하여 Learning Manager에서 리소스를 회수합니다.  액세스 토큰은 공개 api 호출을 수행하는 데 필요하며 샘플 응용 프로그램에서 예시된 것처럼 헤더에 추가되어야 합니다.

## 포함 가능한 플레이어 {#embeddableplayer}

타사 응용 프로그램에서 포함 가능한 플레이어를 사용하여 학습 객체의 콘텐트를 재생할 수 있습니다.

**포함 가능한 플레이어로 강의 열기**

1. 포함 가능한 URL 생성

   포함 가능한 플레이어를 사용하여 강의를 열려면 아래와 같이 포함 가능한 URL을 생성해야 합니다.

   `https://learningmanager.adobe.com/app/player?lo_id=<v2-api course id>&access_token=<access_token>`

   여기서 lo_id는 V2 API 강의 ID 형식을 준수해야 합니다.

   예: `https://learningmanager.adobe.com/app/player?lo_id=course:123456&access_token=45b269b75ac65d6696d53617f512450f`

   인증, 학습 프로그램, 작업 지원은 포함 가능한 플레이어에서 재생할 수도 있습니다.

   예: `https://learningmanager.adobe.com/app/player?lo_id=certification:12345&access_token=c1a4847dfbf4007826a027d481b93c1e`

   `https://learningmanager.adobe.com/app/player?lo_id=learningProgram:12345&access_token=c1a4847dfbf4007826a027d481b93c1e`

   `https://learningmanager.adobe.com/app/player?lo_id=jobAid:1234&access_token=c1a4847dfbf4007826a027d481b93c1e`

1. iframe의 &quot;src&quot; 특성에서 이 URL을 설정합니다.

**포함 가능한 플레이어 닫기**

```
code window.addEventListener("message", function closePlayer(){  
   if(event.data === "status:close"){  
     //handle closing event  
   }  
});
```

## 샘플 응용 프로그램 자습서 {#sampleapplicationtutorial}

첨부된 pdf 문서에는 샘플 응용 프로그램 자습서가 포함되어 있습니다.
[Fluidic Player를 포함하는 샘플 튜토리얼 및 튜토리얼 소스](assets/sample-applicationtutorial.zip) 대체 콘텐츠

관리자인 경우 Fluidic Player 내에서 학습자에게 대체 콘텐츠를 제공할 수 있는 방식으로 강의 자료를 설정할 수 있습니다. 예를 들어, 여러 지역에 걸쳐 여러 언어를 사용하려는 학습자가 있는 경우 동일한 콘텐츠를 여러 언어로 만들 수 있습니다. Fluidic Player는 설정된 언어를 학습자에게 제공하지만 학습자는 플레이어 내에서 바로 대체 언어로 전환할 수도 있습니다.

비디오 관련 컨트롤

Learning Manager Fluidic Player에서 사용하는 스트리밍 기술은 비디오 시작이 지연되지 않고 모든 장치의 디스크 공간에 대한 요구 사항 없이 비디오 재생 환경을 학습자에게 제공합니다. Fluidic Player는 또한 재생 속도(1x, 1.5X) 및 건너뛰기 +-10초 와 같은 스마트 컨트롤을 제공하여 학습자가 학습 속도에 맞는 데 필요한 정확한 제어 수준을 제공하도록 설계되었습니다.

이 작업은 IT 팀 직원이나 외부 컨설턴트가 직접 수행해야 하는 작업입니다. 외부 컨설턴트는 해당 사이트에 호스팅된 애플리케이션을 만듭니다.

1. 가져와야 하는 정확한 학습 개체를 가리키는 매개 변수가 있는 Learning Manager 내장 플레이어 URL을 수정합니다.

   URL:  [https://learningmanager.adobe.com/app/player](https://cpcontents.adobe.com/public/embedplayer/index22fa615ec2baa034a22090c8cd4289fa.html)

1. 다음 매개 변수 중 하나를 사용하여 강의를 실행하십시오.

   * course_id : 실행할 강의 ID입니다.
   * learning_program_id : 실행할 학습 프로그램의 ID입니다.
   * certification_id : 실행할 인증의 ID입니다.
   * lo_id : 재생할 학습 개체의 ID( 강의/학습 프로그램/인증/작업 지원)


1. 액세스 토큰을 필수 매개 변수로 사용합니다.

   * access_token : 보안 매개 변수입니다. 공개 API oauth 액세스 토큰을 사용합니다.

   통합 책임자에 포함 가능한 Fluidic Player를 설정하여 토큰을 가져올 수 있습니다. 액세스 토큰으로 사용할 수 있는 인증 토큰을 받을 수 있습니다.

   생성된 URL의 예: https://learningmanager.adobe.com/app/player?lo_id=&quot;+lo_id+&quot;&amp;access_token=&quot;+accToken

   여기서 lo_id 는 강의, 학습 프로그램, 인증 및 작업 지원 의 ID입니다.

   lo_id - course:21324, learningProgram:2143, certification:23432, jobAid:237 예

1. Learning Manager API를 호출하여 위에 언급된 매개 변수를 검색합니다.

   이러한 API 호출은 IT 팀/컨설턴트가 사이트에서 작성하고 호스팅하는 애플리케이션에 의해 이루어집니다.

   API 사용에 대한 자세한 내용은 여기에서 확인할 수 있습니다.

   Learning Manager V1 API - [https://learningmanager.adobe.com/docs/primeapi/v1/](https://learningmanager.adobe.com/docs/primeapi/v1/)



   Learning Manager V2 API - [https://learningmanager.adobe.com/docs/primeapi/v2/](https://learningmanager.adobe.com/docs/primeapi/v2/)

   객체의 ID는 V1 및 V2 API와 다릅니다. 포함 가능한 플레이어에는 v2 형식의 ID가 필요합니다. V2의 ID 매핑 API를 사용하여 V1 ID에서 V2 ID로 변환합니다.

   URL을 구성한 후 응용 프로그램에서 URL을 학습자에게 표시하는 데 사용하는 한 가지 방법은 iFrame 내에 배치하는 것입니다. 이 링크를 클릭하면 컨텍스트에서 특정 강의와 함께 Fluidic Player가 실행됩니다.

   ![](assets/salesforce-player.png)

   진행 상황 및 완료 보고서를 확인하려면 Learning Manager에 로그인하십시오.

   학습자가 플레이어를 닫으면 Fluidic Player에서 html5 postMessage를 사용하여 상위 요소에 &quot;닫기&quot; 메시지를 보냅니다. 로드 컨트롤러가 이 메시지를 처리하고 계속해야 합니다.

가져와야 하는 정확한 학습 개체를 가리키는 매개 변수가 있는 Learning Manager 내장 플레이어 URL을 수정합니다.

URL:  [https://learningmanager.adobe.com/app/player](https://learningmanager.adobe.com/app/player)

다음 매개 변수 중 하나를 사용하여 강의를 실행할 수 있습니다.

* course_id : 실행할 강의 ID입니다.
* learning_program_id : 실행할 학습 프로그램의 ID입니다.
* certification_id : 실행할 인증의 ID입니다.
* lo_id : 재생할 학습 개체의 ID( 강의/학습 프로그램/인증/작업 지원)

필수 매개 변수:

* access_token : 보안 매개 변수입니다. 공개 API oauth 액세스 토큰을 사용합니다.

Learning Manager API를 호출하여 위에 언급된 매개 변수를 검색합니다. 이러한 API 호출은 IT 팀/컨설턴트가 사이트에서 작성하고 호스팅하는 애플리케이션에 의해 이루어집니다.

API 사용에 대한 자세한 내용은 여기에서 확인할 수 있습니다.

Learning Manager V1 API - [https://learningmanager.adobe.com/docs/primeapi/v1/](https://learningmanager.adobe.com/docs/primeapi/v1/)



Learning Manager V2 API -  [https://learningmanager.adobe.com/docs/primeapi/v2/](https://learningmanager.adobe.com/docs/primeapi/v2/)


