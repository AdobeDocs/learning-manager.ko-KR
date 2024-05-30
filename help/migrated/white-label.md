---
jcr-language: en_us
title: Adobe Learning Manager 모바일 앱의 흰색 레이블 지정
description: 흰색 레이블링은 앱 또는 서비스를 자신의 브랜드로 리브랜딩하고 원본 작성자인 것처럼 사용자 정의하는 관행입니다. Adobe Learning Manager에서는 모바일 앱에 흰색 레이블 지정을 적용하여 앱을 다시 브랜딩하고 사용자가 나만의 브랜드로 앱을 사용할 수 있도록 할 수 있습니다.
contentowner: saghosh
exl-id: f37c86e6-d4e3-4095-9e9d-7a5cd0d45e43
source-git-commit: 73d908674e6c32dafa4f9502634c42ec73fc3b6c
workflow-type: tm+mt
source-wordcount: '1205'
ht-degree: 0%

---

# Adobe Learning Manager 모바일 앱의 흰색 레이블 지정

Adobe Learning Manager 모바일 앱은 이제 흰색 레이블 지정을 지원합니다. 즉, 이제 사용자의 브랜딩으로 앱을 출시할 수 있습니다.

## 흰색 레이블이 지정된 앱 실행 준비를 시작하는 방법

고유한 흰색 레이블 앱을 배포하고 관리하려면 다음 단계를 따르십시오.

1. 앱과 앱/Play 스토어의 설명에 모두 사용할 수 있도록 에셋(예: 스플래시 화면 이미지) 및 텍스트를 준비합니다.

1. 다음 기능을 수행할 수 있는 기술 자원 할당:

* 푸시 알림 인증서 파일을 생성하는 중입니다.
* ALM 팀에서 제공하는 앱 바이너리에 서명합니다.
* 게시 프로세스 업로드 및 관리 게시 프로세스를 수행하려면 앱이 모든 게시 지침을 준수하는지 여부를 앱 관리자와 앱/Play Store 팀 사이에 문의해야 합니다. ALM에서 완전 호환 앱 바이너리를 받게 됩니다.

## 개요

흰색 레이블링은 앱 또는 서비스를 자신의 브랜드로 리브랜딩하고 원본 작성자인 것처럼 사용자 정의하는 관행입니다. Adobe Learning Manager에서는 모바일 앱에 흰색 레이블 지정을 적용하여 앱을 다시 브랜딩하고 사용자가 나만의 브랜드로 앱을 사용할 수 있도록 할 수 있습니다.

## 사용자 정의할 수 있는 항목

다음을 사용자 정의할 수 있습니다.

### 필드

<table>

    <tbody>

    <tr>

   <td>

    <p>계정 ID</p></td>

   <td>

    <p>계정의 ID입니다. 흰색 레이블이 지정된 앱은 다른 계정에 속하는 학습자는 액세스할 수 없습니다.</p></td>

  </tr>

  <tr>

   <td>

    <p>추가 계정 ID</p></td>

   <td>

    <p>원하는 경우 여러 계정(하위 도메인)을 추가합니다. 하위 도메인을 공백 없이 쉼표로 구분된 하위 도메인으로 추가합니다. 예를 들어 acc01,acc02,acc03 등이 있습니다.<br> <b>참고:</b> 하위 도메인을 지정할 때 계정 ID를 추가해야 합니다.</br> </p></td>

  </tr>

  <tr>

  <td>

  <p>앱 이름</p></td>

  <td>

  <p>앱에 사용할 이름입니다.</p></td>

  </tr>

  <tr>

  <td>

  <p>앱 짧은 이름</p></td>

  <td>

  <p>앱 이름이 긴 경우 디바이스에 표시되는 짧은 이름을 앱에 지정합니다.</p></td>

  </tr>

   <tr>

  <td>

  <p>내부 앱 이름</p></td>

  <td>

  <p>OS가 앱을 식별하는 데 사용되는 이름입니다. 일반적으로 사용되는 형식은 com.company-name.product-name입니다.</p></td>

  </tr>

  <tr>

  <td>

  <p>내부 앱 이름-iOS</p></td>

  <td>

  <p>사용자가 iOS을 사용하는 경우 앱의 이름을 다르게 지정합니다. iOS과 Android 모두에 동일한 이름을 사용하는 것이 좋습니다.</p></td>

  </tr>

  <tr>

  <td>

  <p>앱 아이콘</p></td>

  <td>

  <p>앱 아이콘(png). 이 아이콘은 앱에 표시됩니다. 이름 형식은 account-id_appIcon.png입니다. 앱 아이콘의 크기는 512 × 512픽셀입니다.</p></td>

  </tr>

  <tr>

  <td>

  <p>앱 시작 화면</p></td>

  <td>

  <p>앱의 시작 화면에 사용자가 앱을 실행할 때 표시되는 이미지(png)를 제공합니다. 이름을 지정할 형식은 account-id_splashIcon.png입니다. 정사각형 기반 스플래시 화면의 크기는 1052 × 1052 픽셀이며 원형 기반 스플래시 화면은 768 x 768 픽셀입니다.</p></td>

  </tr>

  <tr>

  <td>

  <p>클라이언트 ID 및 클라이언트 암호</p></td>

  <td>

  <p>앱을 등록하는 동안 계정의 통합 관리자가 세부 정보를 제공합니다. 통합 책임자는 다음을 사용해야 합니다.<ul><li>학습자:읽기,학습자:역할로 쓰기</li><li>내부 앱 name://redirect 리디렉션 URL</li></ul></p></td>

  </tr>

  <tr>

  <td>

  <p>계정 로고</p></td>

  <td>

  <p>조직의 로고를 호스팅하는 URL입니다. 계정 로고로 cpcontents 링크를 제공합니다. URL은 웹으로 인코딩해야 합니다.</p></td>

  </tr>

  <tr>

  <td>

  <p>앱의 앱 스토어 ID(iOS)</p></td>

  <td>

  <p>강제 업데이트를 구현하는 데 필요한 ID입니다. 앱을 업데이트하려면 학습자가 App Store로 리디렉션되어야 함을 앱이 알아야 합니다.</p></td>

  </tr>

   <tr>

  <td>

  <p>앱의 Google play 스토어 id(Android)</p></td>

  <td>

  <p>강제 업데이트를 구현하는 데 필요한 ID입니다.</p></td>

  </tr>

  <tr>

  <td>

  <p>딥 링크용 호스트 이름</p></td>

  <td>

  <p>딥 링크를 호스팅하려면 learningmanager를 사용합니다. 다른 호스트 이름 URL을 딥 링크로 사용하려면 호스트의 URL을 제공합니다. 예: learningmanager.adobe.com.</p></td>

  </tr>

    </tbody>

</table>

>[!NOTE]
>
>사용자 지정 앱 바이너리에 추가할 수 있도록 CSAM에 데이터를 제공합니다.


#### 사용자 지정 라이브러리를 처리하도록 사이트 연결 업데이트

사용자 정의 도메인 또는 learningmanager\*.adobe.com을 호스트로 사용하는 경우 별도의 조치를 취할 필요가 없습니다. 그러나 URL에 대해 사용자 정의 솔루션 또는 특정 호스트 이름을 사용하는 경우 사이트 연결 파일을 추가합니다.

>[!CAUTION]
>
>파일이 없으면 심도가 작동하지 않습니다. 파일이 있는지 확인합니다.


자세한 내용은 다음 링크를 참조하십시오.

* [Android](https://learningmanager.adobe.com/.well-known/assetlinks.json)
* [iOS](https://learningmanager.adobe.com/.well-known/apple-app-site-association)

## 푸시 알림 생성

Android 및 iOS 앱으로 푸시 알림을 보내려면 두 가지 메커니즘이 필요합니다.

* iOS의 경우 푸시 알림 인증서를 생성합니다.
* Android의 경우 Firebase 프로젝트에서 생성된 서버 키를 제공합니다.

Firebase에서 프로젝트를 설정하려면 아래 지침을 따르십시오.

### iOS의 푸시 알림

iOS 앱 개발에서 푸시 알림 인증서는 Apple에서 발급한 암호화 자격 증명으로, 서버가 Apple의 APN(Push Notification Service)을 통해 iOS 장치로 푸시 알림을 안전하게 보낼 수 있도록 해 줍니다.

인증서는 iOS 장치에 푸시 알림을 보낼 때 서버(또는 공급자)와 Apple APN 간의 보안 통신을 보장합니다.

Android와 iOS은 푸시 알림을 장치에 보내는 서비스로 FCM(Firebase Cloud Messaging)을 사용합니다.

### iOS에서 인증서를 생성하는 방법

다음 절차를 따르십시오.

1. 생성 또는 다운로드 **푸시 알림 인증서** 및 개인 키(.p12). 자세한 내용은 [Apple 개발자 문서](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns).

1. 파일을 다운로드한 후 p12 파일을 설치합니다. 암호를 사용하여 **키체인 액세스**.

1. 다음으로 이동: **내 인증서** 을 입력한 다음 인증서를 내보냅니다. MIME 유형 .cer을 선택해야 합니다.

1. p12 파일 및 cer 파일을 사용할 수 있게 되면 다음 명령을 실행합니다.

```
- openssl pkcs12 -in privatekey.p12 -out myapnappkey.pem -nodes –clcerts

- openssl x509 -in privatekey.cer -inform DER -out myapnsappcert.pem 

- openssl s_client -connect gateway.sandbox.push.apple.com:2195 -cert myapnsappcert.pem -key myapnappkey.pem 
```

서버에 연결할 수 있으면 만든 인증서가 유효합니다. myapnappkey.pem 파일에서 인증서 및 개인 키 값을 복사합니다.

### Android에서 푸시 알림

Firebase에서 프로젝트를 설정하고 CSAM과 서버 키를 공유합니다.

CSM 팀에 연락하여 AWS의 SNS 서비스에 추가된 파일을 가져옵니다. 사용자는 푸시 알림을 위해 SNS 서비스에 등록된 항목을 가져와야 하며, 이 경우 유효성 검사를 위해 위에서 생성한 인증서를 공유해야 합니다.

>[!NOTE]
>
>Android의 경우 사용자는 SNS 서비스에 항목을 추가하기 위해 Android용으로 만든 Firebase 프로젝트에서 서버 키를 제공해야 합니다.


## Firebase에서 프로젝트 만들기

### Android

위 단계에서 만든 것과 동일한 프로젝트를 푸시 알림에 다시 사용합니다.

[프로젝트 추가](https://learn.microsoft.com/en-us/xamarin/android/data-cloud/google-messaging/firebase-cloud-messaging) Firebase에서 ***google-services.json*** 파일입니다.

### iOS

[프로젝트 추가](https://firebase.google.com/docs/ios/setup) Firebase로 이동하여 ***GoogleService-Info.plist*** 파일입니다.

>[!IMPORTANT]
>
>앱 이진 파일 작성에 포함할 파일을 Adobe Learning Manager CSAM 팀으로 보냅니다.


## 서명된 이진 파일 생성

### iOS

```
sh""" xcodebuild -exportArchive -archivePath Runner.xcarchive -exportPath "ipa_path/" -exportOptionsPlist {ExportFile} 

mv ipa_path/*.ipa "${env.AppName}_signed.ipa" """ 
```

>[!NOTE]
>
>서명된 바이너리를 만들려면 XCode 15.2 이상이 필요합니다.


## Android

```
sh""" ~/Library/Android/sdk/build-tools/30.0.3/apksigner sign --ks $storeFile --ks-pass "pass:$store\_password" --ks-key-alias $key\_alias --key-pass "pass:$key\_password" --out app-release-signed.apk -v app-release.apk """
```

>[!NOTE]
>
>서명된 바이너리를 빌드하려면 Android sdk 빌드 도구가 필요합니다.

**다음 단계**

바이너리를 생성한 후 바이너리를 Play 스토어 또는 App Store에 푸시합니다.

## 변경 사항을 적용하는 방법

필요한 에셋 및 파일을 CSM 팀으로 보냅니다. CSM 팀이 다음을 채웁니다. [양식](https://forms.office.com/r/bJRRaRBvSh) 를 필수 변경 사항으로 변경하고 필요한 에셋을 첨부합니다. 그런 다음 팀이 검토 후 변경 사항을 엔지니어링 팀에 알립니다. 그런 다음 엔지니어링 팀은 빌드를 생성하고 CSM 팀과 공유합니다.

CSM 팀이 고객과 빌드를 공유합니다.

## 사용자 정의할 수 없는 항목

* 암호 업데이트 화면
* 계정 생성 화면
