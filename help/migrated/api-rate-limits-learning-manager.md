---
jcr-language: en_us
title: Learning Manager의 API 속도 제한
contentowner: saghosh
preview: true
source-git-commit: 544c695a77c21dd9162b9b943b6119d27aa373dc
workflow-type: tm+mt
source-wordcount: '1757'
ht-degree: 51%

---



# Learning Manager의 API 속도 제한

## 속도 제한 소개 {#introductiontoratelimiting}

Adobe Learning Manager는 고객이 Learning Manager와 통합되는 응용 프로그램을 구축하거나 사용자 정의 사용자 경험 및 비즈니스에 도움이 되는 워크플로우에 대한 확장 프로그램을 구축할 수 있도록 도와주는 풍부한 REST API 제품군을 제공합니다.

API가 호출될 때마다 Learning Manager 서버에 활용되는 공유 컴퓨팅 리소스가 있으므로 응용 프로그램이 잘 작동하고 플랫폼의 성능 및 가용성 특성을 손상시키지 않도록 주의하고 주의해야 합니다. 이는 API 클라이언트의 호출 방식(빈도 및 속도)에 대한 제한을 도입하여 수행됩니다.

예를 들어, 응용 프로그램에서 해당 계정의 모든 사용자를 가져오려고 할 수 있으며 여러 페이지로 구분된 API를 빠른 속도로 호출할 수 있습니다. 실수로 개발자는 이 문제를 서버에 엄청난 부하를 초래하고 애플리케이션이 느려지게 만들며 의도하거나 필요한 것보다 더 많은 리소스를 소비하여 플랫폼을 위태롭게 만들 수도 있습니다.

이 문제를 해결하기 위해 특정 계정의 특정 클라이언트 애플리케이션에서 단일 사용자가 만들 수 있는 API 호출의 수에 대한 요금 제한을 도입하고 있습니다. 이를 RPM으로 축약된 분당 요청 수로 측정합니다. 예를 들어 GET API 호출의 한도를 600RPM이라고 할 때, 이는 단순히 한 사용자가 1분에 최대 600개의 호출을 초과할 수 없으며, 사용자가 해당 한도를 초과하면 사용자가 요금 제한을 받게 됩니다. 요청은 밀리초 단위로 추적되므로 이 제한은 100밀리초(밀리초)마다 1개의 요청에 해당합니다. 사용자가 지정한 속도(이 경우 600RPM)를 초과하여 요청할 수 있는 수를 정의하는 속도 제한과 함께 정의되는 버스트(Burst)라는 매개변수가 하나 더 있습니다. 예를 들어, Burst 매개 변수가 10인 경우, 대기열에 최대 10개의 슬롯이 할당되고 요청이 &quot;너무 빨리&quot;(이 경우 100ms 보다 빠름)에 도달하면 대기열에 사용 가능한 슬롯이 있는 경우 즉시 처리됩니다. 그런 다음 슬롯은 &quot;촬영&quot;된 것으로 표시되며 해당 시간이 경과할 때까지(이 경우 100ms 후) 다른 요청에 의해 사용할 수 있도록 해제되지 않습니다. 실제 트래픽은 일반적으로 버스트(burst)를 사용하므로 버스트(Burst) 매개변수가 도움이 됩니다. Learning Manager 플랫폼의 경우 특정 API 버전(예: V2), 역할(학습자/관리자) 및 동사(GET/PUT/POST/DELETE/PATCH)에 대한 제한을 정의합니다. 예제에서 위에 서술하면 우리는 금리 제한이 (600, 10)이라고 말할 것이다.

Learning Manager의 공개 API에 대한 등급 제한은 항상 있었지만, 지금까지 매우 높은 RPM을 허용하는 데는 자유로웠습니다. 그러나 즐겨 사용하는 학습 플랫폼의 성장으로 API 사용량이 급격히 증가함에 따라 모든 고객의 이익과 플랫폼의 더 나은 관리를 위해 이러한 제한 요율을 명시적으로 문서화하기로 결정했습니다. 이와 관련하여 API를 업그레이드하여 새 API 응답(HTTP 상태 코드 429)을 반환하기 시작했습니다. 이 응답은 지금까지 표시되지 않았습니다. 이 응답은 속도 제한이 위반될 때 API 클라이언트에 제공됩니다. 클라이언트 응용 프로그램은 이제 해당 응용 프로그램의 논리에 맞게 이 응답 코드를 처리해야 합니다. 이 문서는 주로 개발자가 이러한 응답을 볼 때 코드에 올바른 논리를 통합하는 데 필요한 정보를 제공하는 데 있습니다.

## 강제 적용 환율 제한을 확인하는 방법은 무엇입니까? {#howtoconfirmtheenforcedratelimits}

각 요청에 대해 응답 헤더에는 다음과 같은 정보가 포함됩니다.

```
x-rate-limit: 600r/m 
x-burst: 10
```

* x-rate-limit 는 분당 요청 수로 기본 요청 속도 임계값을 지정합니다.
* x-burst는 기본 요청 속도를 초과하는 요청을 즉시 처리할 수 있도록 허용하는 횟수를 지정합니다.

## 요금 제한으로 인한 오류를 포착하는 방법은 무엇입니까? {#howtocatcherrorscausedbyratelimits}

각 요청에 대해 요금 한도에 부딪혔는지 확인할 수 있습니다. 응답 코드 429, &quot;{&quot;message&quot;:&quot;429 Too many requests&quot;}&quot;이(가) 수신되면 속도 제한에 도달했습니다.

스크립트에 429개의 응답을 포착하는 코드를 포함하는 것이 좋습니다. 스크립트에서 &quot;너무 많은 요청&quot; 오류를 무시하고 요청을 계속 시도하면 null 오류가 발생할 수 있습니다. 그 시점에서 오류 정보는 문제를 진단하는 데 유용하지 않을 것이다.

예를 들어, 비율 제한에 부딪히는 curl 요청은 다음과 같은 응답을 반환할 수 있습니다.

```
< HTTP/2 429 
< date: Wed, 04 Nov 2020 06:53:04 GMT 
< content-type: application/json; charset=utf-8 
< server: openresty 
< x-rate-limit: 60r/m 
< x-burst: 10 
< retry-after: 10.752 
< access-control-allow-credentials: true 
< access-control-allow-methods: GET, POST, OPTIONS, PUT, HEAD, DELETE, PATCH 
< access-control-allow-headers: X-acap-all-roles, X-acap-account,X-acap-user,X-acap-caller-role,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type, x-experience-api-version, Authorization, X-CSRF-TOKEN, X-HTTP-Method-Override 
< strict-transport-security: max-age=31536000; includeSubDomains 
< x-frame-options: SAMEORIGIN 
< x-xss-protection: 1 
< x-content-type-options: nosniff 
< x-request-id: gwBBFC9741-58A5-43B1-B1FE-7D14275961E7 
< strict-transport-security: max-age=31536000; includeSubDomains
```

응답에는 다음 키에 대한 정보가 포함되어 있습니다.

```
status: 429 
retry-after: 10.752
```

상태 코드 429는 &quot;요청이 너무 많음&quot;을 의미하며 현재 요청이 처리되지 않았습니다. retry-after 헤더는 API 호출을 10.752초 후에 다시 시도할 수 있도록 지정합니다. 다시 시도할 수 있는 충분한 시간이 경과할 때까지 코드에서 추가 API 요청을 중단해야 합니다.

다음 의사 코드는 비율 제한 오류를 catch하는 간단한 방법을 보여 줍니다.

```
response = request.get(url) 
if response.status equals 429: 
    alert('Rate limited. Waiting to retry…') 
    wait(response.retry-after) 
    retry(url)
```

실제로 사용자가 429 상태 코드를 쉽게 처리할 수 있도록 Learning Manager 더미 API도 만들었습니다.

```
curl -X GET --header 'Accept: application/json' --header 'Authorization: oauth < 
<token>
  >' 'https://learningmanager.adobe.com/learningmanagerapi/v2/dummy 
</token>
```

이 더미 API의 제한 사항:

```
x-rate-limit: 5r/m 
x-burst: 2
```

더미 API의 제한은 의도적으로 낮아서 속도 제한을 매우 빠르게 충돌한 다음 속도 제한 오류를 포착하고 처리할 코드 개발에 더 집중할 수 있습니다.

## 더미 API 테스트 {#testingthedummyapi}

속도 제한이 작동하는 방식을 확인할 수 있는 끝점을 제공했습니다. 이를 위해 학습자 읽기 범위가 있는 GET /더미라는 특별한 엔드포인트를 만들었습니다. 이 API는 버스트 제한 = 2와 함께 분당 5개의 요청이라는 매우 엄격한 비율 제한에 대해 의도적으로 구성되었습니다.

5 RPM 이하 및 5 RPM 이상의 속도로 이 끝점을 눌러 쉽게 테스트할 수 있습니다. HTTPS 상태 코드 429를 처리하고 응답 헤더의 정보를 기반으로 하는 코드를 작성합니다.

이 샘플 JavaScript 코드를 사용하면 이러한 내용을 쉽게 확인할 수 있습니다. 이 항목 클릭 [바이올린](https://jsfiddle.net/ACAPJS/9yv8zcmL/) 작동 중인 코드를 확인합니다.

이 응용 프로그램을 사용하려면 계정에 대한 학습자 역할 응용 프로그램 토큰을 제공해야 합니다. 다음을 참조하십시오. [응용 프로그램 개발자 설명서](https://captivateLearning Manager.adobe.com/docs/Learning Managerapi/v2/) API 토큰에 대한 정보를 확인하고 Learning Manager 통합 책임자 응용 프로그램의 개발자 리소스 섹션에서 토큰 도우미를 사용하여 토큰을 생성할 수 있습니다.

이 응용 프로그램은 한 번에 10개의 더미 API를 루프에서 호출합니다. 더미 API의 속도 제한이 (5, 2)이므로 Learning Manager에서 받은 첫 5+2 호출이 성공하면 속도 제한이 위반되고 성공 응답이 표시됩니다.

그러나 이 응용 프로그램이 429 상태 코드를 찾고 이에 대한 응답으로 처리하는 방법에 유념하십시오. 이 애플리케이션이 이러한 응답을 받으면, API 응답의 세부 정보가 출력되고, 제안된 시간을 기다린 후 실패한 시도를 재시도합니다.

## 속도 제한을 처리하는 모범 사례 {#bestpracticestohandleratelimiting}

많은 경우, 계정의 데이터는 자주 변경되지 않습니다. 예를 들어, 계정 강의는 자주 변경되지 않을 수 있습니다. 매번 모든 데이터를 가져오려고 하는 대신 특정 데이터가 필요할 때 가져올 수 있는지 확인하고 캐시 메커니즘을 사용하십시오. 이런 식으로, 당신의 응용 프로그램이 정말로 많은 통화를 할 필요가 있을 때, 당신은 그러한 중요한 통화를 하기 위해 귀하의 요금 제한 내에 충분한 할당량을 가질 것입니다.

일부 데이터는 더 자주 변경될 수 있으며 더 자주 가져와야 할 수도 있습니다. 응용 프로그램이 사용자의 작업 과정과 관련이 없을 수 있으므로 약간 오래된 데이터(N분 전에 가져온 캐시에 있을 수 있음)를 보유할 여유가 있는지 자문하십시오. 서버에서 새 데이터를 가져와야 하더라도 필요한 모든 데이터를 가져오는 대신 특정 데이터만 가져오는 것이 현명한 방법입니다.

API가 한 번의 호출로 정확히 원하는 것을 제공할 만큼 유연하지 않을 수 있기 때문에 많은 데이터를 얻을 수 밖에 없는 경우도 있습니다. API에서 호출 수를 최소화하는 데 사용할 수 있는 필터 및 정렬 기준을 제공하는지 확인하고 계정의 많은 사용자가 동일한 데이터를 필요로 할 수 있으므로 캐싱을 고려해야 합니다.

GUI를 사용하는 대화형 응용 프로그램의 컨텍스트에서 너무 많은 데이터가 수신되면 응용 프로그램이 너무 많은 작업을 수행하려고 할 수 있으며 응용 프로그램의 사용자 환경에 영향을 주는 많은 정보/기능으로 사용자를 압도할 수 있습니다.

비대화형 응용 프로그램(일상 작업)을 구축할 때 많은 데이터를 대량으로 가져와야 할 수 있습니다. 이러한 경우 주로 CSV 형식으로 대량 데이터를 반환하도록 설계된 작업 API를 사용하는 것이 좋습니다. 작업 API에는 하루에 N번 호출할 수 있는 할당량 제한이 있습니다.

Learning Manager는 JSONAPI 사양을 구현했으므로 일부 데이터를 테스트용 로드할 수 있는 API가 있습니다. 이렇게 하면 추가 API 호출을 절약할 수 있지만 데이터를 너무 열심히 가져오는 것과 이러한 작업을 구분해야 합니다. 테스트용 로드 데이터는 경우에 따라 크기가 매우 클 수 있으므로 API 페이지 구분 호출에서는 최대 페이지 크기를 10으로 제한하지만, 포함하지 않는 API 호출의 경우 최대 100의 페이지 크기를 지정할 수 있습니다

결국 짧은 시간 안에 API 요청을 많이 하면 요청에 대한 API 비율 한도가 부딪히게 된다. 한도에 도달하면 Learning Manager에서는 특정 시간이 경과할 때까지 더 이상 요청 처리를 중지합니다.

요금 제한은 이 문서의 마지막 섹션에 설명되어 있습니다. 당신이 한계를 숙지하는 것이 좋습니다.

## V2 API 엔드포인트에 대한 속도 제한 {#ratelimitsforv2apiendpoints}

다음 표에서는 다양한 V2 끝점에 대한 제한을 제공합니다. 현재는 고객에게 요금 제한이 적용되지 않지만 DD/MM/YYYY부터 이러한 제한이 적용됩니다. 따라서 고객은 기존 애플리케이션의 코드를 검토하여 이러한 속도 제한을 인식하고 HTTP 상태 코드 429로 API 응답을 처리하는 방법을 확인하는 것이 중요합니다.

<table> 
 <tbody>
  <tr> 
   <td><p><b>작업</b></p></td> 
   <td><p><b>관리자 API</b></p></td> 
   <td><p><b>학습자 API</b></p></td> 
  </tr> 
  <tr> 
   <td><p>DELETE</p></td> 
   <td><p>(25, 10) <br></p></td> 
   <td><p>(20, 10)<br></p></td> 
  </tr> 
  <tr> 
   <td><p>패치</p></td> 
   <td><p>(60, 20)</p></td> 
   <td><p>(15, 5) <br></p></td> 
  </tr> 
  <tr> 
   <td><p>POST</p></td> 
   <td><p>(30, 10)<br></p></td> 
   <td><p>(30, 10)<br></p></td> 
  </tr> 
  <tr> 
   <td><p>PUT</p></td> 
   <td><p>(20, 10)<br></p></td> 
   <td><p>(20, 10)<br></p></td> 
  </tr> 
  <tr> 
   <td><p>GET</p></td> 
   <td><p>(100, 100)<br></p></td> 
   <td><p>(100, 30)<br></p></td> 
  </tr> 
 </tbody>
</table>

