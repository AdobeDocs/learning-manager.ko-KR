---
jcr-language: en_us
title: 포함된 플레이어 상호 작용 API 설명서
description: 포함된 플레이어에서 이벤트를 수신하고 액션을 트리거하는 다양한 API에 대해 알아보십시오
contentowner: chandrum
exl-id: 4734ecc1-cc8a-40b0-8997-32a31ec661ec
source-git-commit: 3d183dc40e4d1962d25160b74d8cf6cfa26e3171
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 69%

---

# 포함된 플레이어 상호 작용 API 설명서

Adobe Learning Manager는 앱에 통합할 수 있는 라이브러리를 제공합니다. 이 라이브러리는 포함된 플레이어에서 이벤트를 수신하고 동작을 트리거하기 위한 다양한 API를 제공합니다.

제공된 API를 사용하여 플레이어에서 재생, 일시 정지 및 기타 동작을 수행할 수 있습니다.

## 라이브러리 로드

라이브러리는 이 [위치](https://cpcontents.adobe.com/public/publiccdn/playerInteractionLib.min.js)에서 사용할 수 있습니다.

라이브러리를 로드하려면 아래의 단계를 따르십시오.

1. 소비자 응용 프로그램에서 js 파일을 로드합니다.
2. 라이브러리를 로드하면 window.cpPlayerLib가 채워집니다.

>[!NOTE]
>
>prod US를 사용하지 않는 경우 env를 기준으로 cpPlayerLib.env 및 cpPlayerLib.sourceOrigin 매개 변수를 설정합니다.

기본값은 다음과 같습니다.

* window.cpPlayerLib.env = [https://learningmanager.adobe.com/app/player](https://learningmanager.adobe.com/app/player);
* window.cpPlayerLib.sourceOrigin = &quot;[https://cpcontents.adobe.com](https://cpcontents.adobe.com/)&quot;;

### 사용 가능한 메서드

cpPlayerLib 라이브러리는 다음 함수로 구성됩니다.

**startPlayer**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>startPlayer</td>
</tr>
<tr>
<td>설명</td>
<td>앱에서 플레이어를 로드합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>loId : 학습 객체 ID입니다.</li><li>accountId : ALM 계정의 계정 ID입니다.</li><li>userId : 사용자 ID입니다.</li><li>accessToken : 액세스 토큰입니다.</li><li>domRefId: 플레이어를 렌더링해야 하는 div 컨테이너의 ID입니다.</li><li>onModuleLoaded: 이 함수는 아래 세부 정보가 있는 모듈이 로드될 때 호출됩니다.</li><br><li>contentType</li><li>loId</li><li>moduleId</li><li>completed</li><li>currentLanguage</li><li>availableLanguages</li><li>isCCAvailable</li><li>ccEnabled</li></br></td>
</tr>
<tr>
<td>반환</td>
<td>약속을 반환합니다. 이 약속이 해결되면 playerObj가 전달됩니다.</td>
</tr>
<tr>
<td>예외</td>
<td>약속은 예외로 귀착됩니다.</td>
</tr>
<tr>
<td>샘플 코드</td>
<td>cpPlayerLib.startPlayer(loId, accountId, userId, accessToken, domRefId, onModuleLoaded).then((playerObj) =&gt; {//playerObj에는 플레이어와 상호 작용할 API가 있음}) &gt;</td>
</tr>
</tbody>
</table>

**getAllPlays**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>getAllPlayers</td>
</tr>
<tr>
<td>설명</td>
<td>현재 페이지의 모든 플레이어 개체를 반환합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td>없음</td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>cpPlayerLib.getAllPlayers()</td>
</tr>
</tbody>
</table>

**getPlayer**


<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>getPlayer</td>
</tr>
<tr>
<td>설명</td>
<td>지정된 학습 개체 ID의 플레이어 개체를 반환합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>loId : 학습 객체 ID입니다.</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>cpPlayerLib.getPlayer(loId)</td>
</tr>
</tbody>
</table>

**navigateToModule**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>navigateToModule</td>
</tr>
<tr>
<td>설명</td>
<td>다음 모듈로 이동합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>moduleId: 모듈 ID.</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.navigateToModule(moduleID)</td>
</tr>
</tbody>
</table>

**다음**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>next</td>
</tr>
<tr>
<td>설명</td>
<td>다음 모듈로 이동합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>없음</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.next()</td>
</tr>
</tbody>
</table>

**이전**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>previous</td>
</tr>
<tr>
<td>설명</td>
<td>이전 모듈로 이동합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>없음</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.previous()</td>
</tr>
</tbody>
</table>

**toggleTOC**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>toggleTOC</td>
</tr>
<tr>
<td>설명</td>
<td>플레이어에서 목차 패널을 전환합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>없음</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.toggleTOC()</td>
</tr>
</tbody>
</table>

**toggleNotes**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>toggleNotes</td>
</tr>
<tr>
<td>설명</td>
<td>플레이어에서 노트 패널을 전환합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>없음</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.toggleNotes()</td>
</tr>
</tbody>
</table>

**toggleClosedCaption**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>toggleClosedCaption</td>
</tr>
<tr>
<td>설명</td>
<td>플레이어에서 폐쇄 자막 표시를 토글합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>없음</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.toggleClosedCaption()</td>
</tr>
</tbody>
</table>

**언어 변경**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>changeLanguage</td>
</tr>
<tr>
<td>설명</td>
<td>플레이어에서 콘텐츠 언어를 변경합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>language: 지정할 언어 코드입니다.</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.changeLanguage("es")</td>
</tr>
</tbody>
</table>

**closePlayer**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>closePlayer</td>
</tr>
<tr>
<td>설명</td>
<td>플레이어를 닫고 페이지에서 플레이어를 제거합니다. </td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>없음</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.closePlayer()</td>
</tr>
</tbody>
</table>

**재생 일시 중지**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>togglePlayPause</td>
</tr>
<tr>
<td>설명</td>
<td>플레이어에서 콘텐츠 재생 및 일시 중지 간에 전환합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>없음</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.togglePlayPause()</td>
</tr>
</tbody>
</table>

**setVolume**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>setVolume</td>
</tr>
<tr>
<td>설명</td>
<td>플레이어 볼륨을 설정합니다. 값은 0에서 1 사이여야 합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>volume: 볼륨의 값입니다. 유효한 범위는 0-1입니다. </li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.setVolume(0.5)</td>
</tr>
</tbody>
</table>

**setPlayBackSpeed**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>setPlayBackSpeed</td>
</tr>
<tr>
<td>설명</td>
<td>플레이어에서 재생 속도를 설정합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>speed: 지정할 속도 값입니다. 유효한 값은 .25, .5, .75, 1, 1.25, 1.5, 1.75, 2입니다.</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.setPlayBackSpeed(1.25)</td>
</tr>
</tbody>
</table>

**탐색**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>seek</td>
</tr>
<tr>
<td>설명</td>
<td>비디오의 원하는 시간으로 이동합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>time: 이동할 시간입니다. 시간은 초 단위입니다.</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.seek(50)</td>
</tr>
</tbody>
</table>

**앞으로**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>forward</td>
</tr>
<tr>
<td>설명</td>
<td>비디오를 10초 앞으로 이동합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>없음</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.forward()</td>
</tr>
</tbody>
</table>

**뒤로**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>backward</td>
</tr>
<tr>
<td>설명</td>
<td>비디오를 10초 뒤로 이동합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>없음</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.backward()</td>
</tr>
</tbody>
</table>

**navigateToPage**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>navigateToPage</td>
</tr>
<tr>
<td>설명</td>
<td>PPT/PDF에서 지정된 페이지로 이동합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>pageNumber: 이동할 페이지 번호입니다.</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.navigateToPage (5)</td>
</tr>
</tbody>
</table>

**다음 페이지**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>nextPage</td>
</tr>
<tr>
<td>설명</td>
<td>PPT/PDF에서 다음 페이지로 이동합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>없음</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.nextPage()</td>
</tr>
</tbody>
</table>

**previousPage**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>previousPage</td>
</tr>
<tr>
<td>설명</td>
<td>PPT/PDF에서 이전 페이지로 이동합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>없음</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.previousPage()</td>
</tr>
</tbody>
</table>

**확대**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>zoomIn</td>
</tr>
<tr>
<td>설명</td>
<td>PPT/PDF에서 콘텐츠를 확대합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>없음</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.zoomIn()</td>
</tr>
</tbody>
</table>

**축소**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>zoomOut</td>
</tr>
<tr>
<td>설명</td>
<td>PPT/PDF에서 콘텐츠를 축소합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>없음</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.zoomOut()</td>
</tr>
</tbody>
</table>

**다운로드 작업 지원**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>downloadJobAid</td>
</tr>
<tr>
<td>설명</td>
<td>강의에서 작업 지원을 다운로드합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>없음</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.downloadJobAid()</td>
</tr>
</tbody>
</table>

**JobAidPullout**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>toggleJobAidPullout</td>
</tr>
<tr>
<td>설명</td>
<td>작업 지원을 다운로드할 것인지 여부입니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>없음</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.toggleJobAidPullout()</td>
</tr>
</tbody>
</table>

**전체 화면**

<table>
<tbody>
<tr>
<td>메서드 이름</td>
<td>fullScreen</td>
</tr>
<tr>
<td>설명</td>
<td>플레이어를 전체 화면 모드로 설정합니다.</td>
</tr>
<tr>
<td>매개 변수</td>
<td><li>없음</li></td>
</tr>
</tr>
<tr>
<td>샘플 코드</td>
<td>playerObj.fullScreen()</td>
</tr>
</tbody>
</table>

## 이벤트 목록

**onPlayerEvents(callBack)**

콜백 함수를 등록하면 모든 플레이어 이벤트에서 호출됩니다. 이벤트 이름은 다음과 같습니다.

* PLAY(비디오/오디오/CP)
* PAUSE(비디오/오디오/CP)
* TIMEUPDATE(비디오/오디오/CP)
* PAGECHANGE(PPT/PDF)
* NOTEADDED(모든 콘텐츠)
* LAUNCHED(모든 콘텐츠)
* STARTED(모든 콘텐츠)
* COMPLETED(모든 콘텐츠)
* PASSED(모든 콘텐츠)
* FAILED(모든 콘텐츠)

**onStreamingEvents(callBack)**

콜백 함수를 등록하면 사용자 활동을 추적하기 위해 전송되는 모든 플레이어 명령문에 대해 호출됩니다.
