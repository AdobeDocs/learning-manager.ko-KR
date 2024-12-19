---
jcr-language: en_us
title: Adobe Learning Manager 모바일 앱의 흰색 레이블 지정
description: 흰색 레이블링은 앱 또는 서비스를 자신의 브랜드로 리브랜딩하고 원본 작성자인 것처럼 사용자 정의하는 관행입니다. Adobe Learning Manager에서는 모바일 앱에 흰색 레이블 지정을 적용하여 앱을 다시 브랜딩하고 사용자가 나만의 브랜드로 앱을 사용할 수 있도록 할 수 있습니다.
contentowner: saghosh
exl-id: f37c86e6-d4e3-4095-9e9d-7a5cd0d45e43
source-git-commit: c9f2b9f817d4baa04399d58bbc4008d7891e0252
workflow-type: tm+mt
source-wordcount: '1879'
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

    <p>계정 ID</p>

   </td>

   <td>

    <p>계정의 ID입니다. 흰색 레이블이 지정된 앱은 다른 계정에 속하는 학습자는 액세스할 수 없습니다.</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>추가 계정 ID</p>

   </td>

   <td>

    <p>원하는 경우 여러 계정(하위 도메인)을 추가합니다. 하위 도메인을 공백 없이 쉼표로 구분된 하위 도메인으로 추가합니다. 예를 들어 acc01,acc02,acc03 등이 있습니다.<br> <b>참고:</b> 하위 도메인을 지정할 때 계정 ID를 추가해야 합니다.</br> </p>

   </td>

  </tr>

  <tr>

   <td>

    <p>앱 이름</p></td>

   <td>

    <p>앱에 사용할 이름입니다.</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>앱 짧은 이름</p>

   </td>

   <td>

    <p>앱 이름이 긴 경우 디바이스에 표시되는 짧은 이름을 앱에 지정합니다.</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>내부 앱 이름</p></td>

   <td>

    <p>OS가 앱을 식별하는 데 사용되는 이름입니다. 일반적으로 사용되는 형식은 com.company-name.product-name입니다.</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>내부 앱 이름-iOS</p>

   </td>

   <td>

    <p>사용자가 iOS을 사용하는 경우 앱의 이름을 다르게 지정합니다. iOS과 Android 모두에 동일한 이름을 사용하는 것이 좋습니다.</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>앱 아이콘</p>

   </td>

   <td>

    <p>앱 아이콘(png). 이 아이콘은 앱에 표시됩니다. 이름 형식은 account-id_appIcon.png입니다. 앱 아이콘의 크기는 512 × 512픽셀입니다.<div>Apple은 앱 아이콘에서 Alpha 채널을 허용하지 않습니다. 따라서 제출하기 전에 에셋에서 Alpha 채널을 제거해야 합니다.</div></p>

   </td>

  </tr>

  <tr>

   <td>

    <p>앱 시작 화면</p></td>

   <td>

    <p>앱의 시작 화면에 사용자가 앱을 실행할 때 표시되는 이미지(png)를 제공합니다. 이름을 지정할 형식은 account-id_splashIcon.png입니다. 정사각형 기반 스플래시 화면의 크기는 1052 × 1052 픽셀이며 원형 기반 스플래시 화면은 768 x 768 픽셀입니다.</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>클라이언트 ID 및 클라이언트 암호</p>

   </td>

   <td>

    <p>앱을 등록하는 동안 계정의 통합 관리자가 세부 정보를 제공합니다. 통합 책임자는 다음을 사용해야 합니다.<ul><li>학습자:읽기,학습자:역할로 쓰기</li><li>내부 앱 name://redirect 리디렉션 URL</li></ul></p>

   </td>

  </tr>

  <tr>

   <td>

    <p>계정 로고</p>

   </td>

   <td>

    <p>조직의 로고를 호스팅하는 URL입니다. 계정 로고로 cpcontents 링크를 제공합니다. URL은 웹으로 인코딩해야 합니다.</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>앱의 앱 스토어 ID(iOS)</p>

   </td>

   <td>

    <p>강제 업데이트를 구현하는 데 필요한 ID입니다. 앱을 업데이트하려면 학습자가 App Store로 리디렉션되어야 함을 앱이 알아야 합니다.</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>앱의 Google play 스토어 id(Android)</p>

   </td>

   <td>

    <p>강제 업데이트를 구현하는 데 필요한 ID입니다.</p>

   </td>

  </tr>

  <tr>

   <td>

    <p>딥 링크용 호스트 이름</p>

   </td>

   <td>

    <p>딥 링크를 호스팅하려면 learningmanager를 사용합니다. 다른 호스트 이름 URL을 딥 링크로 사용하려면 호스트의 URL을 제공합니다. 예: learningmanager.adobe.com.</p>

   </td>

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

1. **푸시 알림 인증서** 및 개인 키(.p12)를 생성하거나 다운로드합니다. 자세한 내용은 [Apple 개발자 문서](https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/establishing_a_certificate-based_connection_to_apns)를 참조하세요.

1. 파일을 다운로드한 후 p12 파일을 설치합니다. 암호를 사용하여 **키체인 액세스**&#x200B;에 설치합니다.

1. **내 인증서**(으)로 이동하여 인증서를 내보냅니다. MIME 유형 .cer을 선택해야 합니다.

1. p12 파일 및 cer 파일을 사용할 수 있게 되면 다음 명령을 실행합니다.

```
- openssl pkcs12 -in privatekey.p12 -out myapnappkey.pem -nodes –clcerts

- openssl x509 -in privatekey.cer -inform DER -out myapnsappcert.pem 

- openssl s_client -connect gateway.sandbox.push.apple.com:2195 -cert myapnsappcert.pem -key myapnappkey.pem 
```

서버에 연결할 수 있으면 만든 인증서가 유효합니다. myapnappkey.pem 파일에서 인증서 및 개인 키 값을 복사합니다.

### Android에서 푸시 알림

Android의 경우 사용자는 SNS 서비스에 항목을 추가하려면 Firebase 프로젝트에서 services.json 파일을 제공해야 합니다.

Firebase에서 프로젝트를 만들고 services.json 파일을 CSM 팀에 공유합니다. 이 파일은 SNS의 토큰 기반 항목에 필요합니다. 서버 키는 더 이상 사용되지 않습니다. [Firebase에서 프로젝트 만들기](#create-project-in-firebase)를 참조하십시오.

services.json 파일을 다운로드하려면 다음 단계를 따르십시오.

1. **Firebase** 콘솔에 로그인합니다.
1. **프로젝트 설정**(으)로 이동하고 **클라우드 메시징**&#x200B;을 선택합니다.
1. **Firebase 클라우드 메시징 API**&#x200B;를 찾아 **서비스 계정 관리**&#x200B;를 선택합니다.
1. **서비스 계정** 페이지의 왼쪽 패널에서 **서비스 계정**&#x200B;을 선택합니다.
1. 프로젝트 항목을 찾은 다음 작업에서 **세부 정보 관리**&#x200B;를 선택합니다.

   >[!NOTE]
   >
   >   프로젝트 항목 형식은 &lt;-accountname->@appspot.gserviceaccount.com입니다.

1. **키** 탭으로 이동하여 **키 추가**&#x200B;를 선택합니다.
1. 키가 없으면 **새 키 만들기**&#x200B;를 선택하고 키 유형으로 **JSON**&#x200B;을 선택합니다. 그러면 JSON 파일이 생성되고 다운로드됩니다.
1. 이미 키가 있는 경우 **기존 키 업로드**&#x200B;를 선택하고 키를 붙여넣고 업로드합니다. 그러면 JSON 파일이 생성되고 다운로드됩니다.

<!-- Set up a project in Firebase and share the server key with the CSAM.-->

AWS에서 SNS 서비스에 항목을 추가하려면 CSM 팀에 연락하고 JSON 파일을 공유하십시오. 사용자는 푸시 알림을 위해 SNS 서비스에 등록된 항목을 가져와야 하며, 이 경우 유효성 검사를 위해 위에서 생성한 인증서를 공유해야 합니다.

## Firebase에서 프로젝트 만들기 {#create-project-in-firebase}

### Android

위 단계에서 만든 것과 동일한 프로젝트를 푸시 알림에 다시 사용합니다.

Firebase에서 [프로젝트를 추가](https://learn.microsoft.com/en-us/xamarin/android/data-cloud/google-messaging/firebase-cloud-messaging)하고 ***google-services.json*** 파일을 검색합니다.

### iOS

[Firebase에 ](https://firebase.google.com/docs/ios/setup) 프로젝트를 추가하고 ***GoogleService-Info.plist*** 파일을 검색합니다.

>[!IMPORTANT]
>
>앱 이진 파일 작성에 포함할 파일을 Adobe Learning Manager CSAM 팀으로 보냅니다.


## 서명된 이진 파일 생성

### iOS

<!--```
sh""" xcodebuild -exportArchive -archivePath Runner.xcarchive -exportPath "ipa_path/" -exportOptionsPlist {ExportFile} 

mv ipa_path/*.ipa "${env.AppName}_signed.ipa" """ 
```-->

`<root>` 폴더에 **Runner.xcarchive.zip** 파일이 있습니다. 아래 명령을 실행하여 서명된 바이너리를 생성합니다.

1. 다음 명령을 실행하여 아카이브의 압축을 풉니다.

   ```
   unzip Runner.xcarchive.zip
   ```

2. 앱 디렉터리로 이동:

   ```
   cd Runner.xcarchive/Products/Applications/Runner.app
   ```

3. 모바일 프로비저닝 파일 복사:

   ```
   cp <path>/<mobile-provisioningfile>.mobileprovision embedded.mobileprovision
   ```

4. 다음 명령을 실행하여 서명 정보를 프레임워크 라이브러리로 업데이트합니다.

   ```
   codesign -f -s "Distribution Certificate Name" Frameworks/*
   ```

5. `<root>` 폴더(Runner.xcarchive.zip이 있는 위치)로 돌아갑니다.

   ```
   cd <root>
   ```

6. xcodebuild를 사용하여 아카이브 내보내기:

   ```
   xcodebuild -exportArchive -archivePath Runner.xcarchive -exportPath ipa_path/ -exportOptionsPlist <path>/<ExportOptions-file>.plist
   ```

7. ipa_path 폴더에서 .ipa 파일을 찾습니다.
8. .ipa 파일을 `Diawi` 웹 사이트에 업로드합니다.
9. 완전히 업로드되면 **[!UICONTROL 보내기]** 버튼을 선택합니다.
10. 완료 후 QR 코드와 링크를 받게 됩니다.
11. Safari에서 바로 QR 코드나 링크를 엽니다.

디바이스가 프로비저닝 프로파일에 포함되어 있으면 디바이스에서 설치를 진행해야 합니다.

>[!NOTE]
>
>서명된 바이너리를 만들려면 XCode 15.2 이상이 필요합니다.


### Android

**APK 파일**&#x200B;의 경우

```
sh""" <path>/apksigner sign --ks $storeFile --ks-pass env:KS_PASS --ks-key-alias $key_alias --key-pass env:KEY_PASS --out app-release-signed.apk -v app-release.apk """
```

>[!NOTE]
>
>`apksigner` 도구의 경로는 일반적으로 ~/Library/Android/sdk/build-tools/30.0.3/apksigner과 같이 표시됩니다.

**aab 파일**&#x200B;의 경우

>[!NOTE]
>
>서명된 바이너리를 빌드하려면 Android sdk 빌드 도구가 필요합니다.

Play 스토어를 게시하려면 aab 형식의 Android 바이너리가 필요합니다. 따라서 서명되지 않은 .aab 파일이 제공됩니다.

>[!NOTE]
>
>Keystore 파일을 만들 때는 Keystore 암호, 서명 키 별칭 및 서명 키 별칭 암호를 생성해야 합니다.

.aab 파일에 서명하려면 아래 단계를 따르십시오.

다음 명령을 실행합니다.

```
<path>/jarsigner -verbose -sigalg SHA256withRSA -digestalg SHA-256 -keystore <keystore-file> app-release.aab <signingKeyAlias>
```

>[!NOTE]
>
>Java에는 **[!UICONTROL jarsigner]**&#x200B;가 포함되어 있습니다. Java 21을 사용하고 있는지 확인합니다.

메시지가 표시되면 다음 암호를 입력하십시오.

* Keystore 암호
* 키 별칭 서명 암호

제공된 APK를 사용하시면 됩니다 단, aab 파일에서 APK를 생성해야 하는 경우 다음 단계를 따르십시오.

>[!NOTE]
>
>APK를 생성하려면 **[!UICONTROL bundletool]**&#x200B;을(를) 설치해야 합니다.


다음 명령을 실행하여 APK 파일을 만듭니다.

```
java -jar <path>/bundletool-all.jar  build-apks --bundle=app-release.aab --output=my_app.apks --mode=universal
```

파일의 압축을 풀려면 다음 명령을 실행합니다.

```
unzip my_app.apks -d output_dir
```

**[!UICONTROL output_dir]** 폴더에서 APK 파일을 가져옵니다.

**다음 작업**

바이너리를 생성한 후 바이너리를 Play 스토어 또는 App Store에 푸시합니다.

### 검토를 위해 앱을 스토어로 푸시

최종 바이너리를 받은 후 검토를 위해 해당 앱 스토어(iOS 또는 Android)에 업로드할 수 있습니다. 다음 단계에 따라 App Store에 바이너리를 업로드하십시오.

**iOS**

1. App Store 자격 증명으로 Transporter 앱에 로그인합니다.
2. 왼쪽 상단의 **+** 버튼을 선택하고 프로덕션 인증서(.ipa 파일)를 업로드합니다.
3. .ipa 파일이 올바르면 App Store에 앱을 업로드하라는 메시지가 표시됩니다.
4. 앱이 전달되면 App Store에 로그인합니다. 몇 시간 내에 이진이 TestFlight 섹션에 표시됩니다. 앱을 검토하기 전에 TestFlight에서 최종 기밀 테스트를 위해 이 기능을 활성화하고 새 릴리스에 대해 앱을 제출할 때 이 IPA를 바이너리로 사용할 수 있습니다.

**Android**

1. Google Play Store Console을 엽니다.
2. **[!UICONTROL 대시보드]** > **[!UICONTROL 앱 릴리스 보기]** > **[!UICONTROL 릴리스 대시보드]**&#x200B;로 이동한 다음 **[!UICONTROL 새 릴리스 만들기]**&#x200B;를 선택합니다.
3. 생성된 .aab 파일을 앱 번들로 업로드하고 버전 번호 및 새로운 기능 정보와 같은 릴리스 세부 정보를 입력합니다.
4. 변경 사항을 저장하고 검토를 위해 앱을 제출합니다.
5. 앱 배포를 100%로 설정해야 합니다(Google은 기본적으로 20%로 설정함).

#### 앱 게시에 유용한 링크

**Android**

[앱 만들기 및 설정](https://support.google.com/googleplay/android-developer/answer/9859152?hl=en)
[검토할 앱 준비](https://support.google.com/googleplay/android-developer/answer/9859455?sjid=2454409340679630327-AP)

**iOS**

[검토를 위해 제출](https://developer.apple.com/help/app-store-connect/manage-submissions-to-app-review/submit-for-review)

## 변경 사항을 적용하는 방법

필요한 에셋 및 파일을 CSM 팀으로 보냅니다. 그런 다음 CSM 팀은 [양식](https://forms.office.com/r/bJRRaRBvSh)에 필요한 변경 내용을 입력하고 필요한 에셋을 첨부합니다. 그런 다음 팀이 검토 후 변경 사항을 엔지니어링 팀에 알립니다. 그런 다음 엔지니어링 팀은 빌드를 생성하고 CSM 팀과 공유합니다.

CSM 팀이 고객과 빌드를 공유합니다.

## 사용자 정의할 수 없는 항목

* 암호 업데이트 화면
* 계정 생성 화면
