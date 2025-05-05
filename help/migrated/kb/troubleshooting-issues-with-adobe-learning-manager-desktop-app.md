---
description: 이 문서에는 Adobe Learning Manager 데스크탑 응용 프로그램을 설치하고 사용하는 동안 발생하는 일반적인 문제를 해결하기 위한 기본적인 문제 해결 팁이 있습니다.
jcr-language: en_us
title: Adobe Learning Manager 데스크탑 앱 관련 문제 해결
contentowner: kuppan
exl-id: 68d40a52-e048-43af-a7aa-917b569b583d
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '1447'
ht-degree: 53%

---

# Adobe Learning Manager 데스크탑 앱 관련 문제 해결

이 문서에는 Adobe Learning Manager 데스크탑 응용 프로그램을 설치하고 사용하는 동안 발생하는 일반적인 문제를 해결하기 위한 기본적인 문제 해결 팁이 있습니다.

## 다음 작업을 수행할 수 없습니다. {#iamunabletodothefollowing}

+++Adobe Learning Manager 데스크탑 애플리케이션을 다운로드할 수 없습니다

1. 인터넷 연결 및 방화벽 설정을 확인합니다.
1. [소셜 학습]에서 **[!UICONTROL 새 게시물]**&#x200B;을 클릭하여 게시물을 작성합니다. 게시판이 없다면 먼저 게시판을 만드십시오.
1. 스크린샷, 오디오 레코딩, 비디오 레코딩, Learning Manager 갤러리와 같은 콘텐츠를 만들 수 있도록 표시되는 다음 게시물 단추 옵션 중 하나를 클릭합니다. 데스크탑용 Adobe Learning Manager 데스크탑 응용 프로그램을 다운로드할 수 있는 Adobe Learning Manager 데스크탑 응용 프로그램 페이지가 표시됩니다.
1. 책임자에 의해 [소셜 학습]이 활성화되어 있는 유효한 Adobe Learning Manager 계정이 필요합니다. 책임자가 웹 브라우저를 통해 다운로드를 비활성화했을 수도 있습니다. Adobe Learning Manager 데스크탑 앱 다운로드에 대한 자세한 내용은 Adobe Learning Manager 책임자에게 문의하십시오.

+++

+++Adobe Learning Manager 데스크탑 애플리케이션을 설치할 수 없습니다.

1. 시스템이 최소 시스템 요구 사항을 충족하는지 확인합니다. [데스크탑용 Adobe Learning Manager 앱 시스템 요구 사항](../learners/adobe-learning-manager-app-for-desktop/adobe-learning-manager-desktop-app-system-requirements.md)을 참조하십시오.
1. Adobe Learning Manager 데스크탑 응용 프로그램의 이전 설치를 모두 정리합니다. 자세한 내용은 [이전 설치를 정리하는 방법](#howtocleanuppreviousinstallationsofadobelearningmanagerdesktopapp)을 참조하세요.
1. 설치 프로세스 중 오류가 발생한 경우 [응용 프로그램 로그를 찾는 방법](#howtofindapplicationlogs)을 참조하십시오. 도움이 필요하면 Adobe Learning Manager 데스크탑 응용 프로그램 책임자에게 문의하십시오.

+++

+++Adobe Learning Manager 데스크탑 응용 프로그램을 시작할 수 없습니다.

1. Adobe Learning Manager 데스크탑 응용 프로그램이 다운로드 및 설치되어 있는지 확인합니다.
1. [소셜 학습]에서 **[!UICONTROL 새 게시물]**&#x200B;을 클릭합니다(게시판이 없으면 게시판을 만듭니다). 게시물 단추 옵션(스크린샷 생성, 오디오 레코딩, 비디오 레코딩, Adobe Learning Manager 갤러리) 중 하나를 클릭합니다. Adobe Learning Manager 데스크탑 응용 프로그램을 실행할 수 있는 페이지가 표시됩니다.
1. 앱이 실행되지 않는 경우 Windows의 시작 메뉴 또는 Mac OS X의 Launchpad에서도 실행할 수 있습니다.

+++

+++Adobe Learning Manager 데스크탑 응용 프로그램에서 내 계정에 로그인할 수 없습니다.

1. 인터넷에 연결되어 있고 방화벽 설정이 Adobe Learning Manager 데스크탑 응용 프로그램을 차단하지 않는지 확인합니다.
1. [소셜 학습]이 활성화된 유효한 Adobe Learning Manager 학습자 계정이 있는지 확인합니다.
1. 여전히 로그인할 수 없는 경우 Adobe Learning Manager 데스크탑 응용 프로그램을 종료했다가 다시 실행한 다음 다시 시도해 봅니다.
1. 도움이 필요하면 Adobe Learning Manager 관리자에게 문의하십시오.

+++

+++Adobe Learning Manager 데스크탑 응용 프로그램에 나열된 내 웹캠/마이크가 표시되지 않습니다.

1. 웹캠/마이크가 시스템에 제대로 연결되어 있고 제대로 작동하는지 확인합니다.
1. 웹캠/마이크용 최신 드라이버가 설치되어 있는지 확인합니다. 일부 장치의 경우 전용 드라이버가 없으면 제대로 작동하지 않습니다.
1. 응용 프로그램 환경 설정을 재설정한 다음, Adobe Learning Manager 데스크탑 응용 프로그램을 다시 실행하고 다시 시도합니다. 자세한 내용은 [응용 프로그램 환경 설정 재설정 방법](#howtoresetapplicationpreferences)을 참조하십시오.
1. Mac OS X Mojave 10.14에 있는 경우 Adobe Learning Manager 데스크탑 응용 프로그램에 권한을 부여하여 웹캠/마이크에 액세스합니다. 자세한 내용은 [OSX Mojave에서 웹캠/마이크 권한을 설정하는 방법](#howtosetwebcammicrophonepermissionsonMacOSXMojave)을 참조하십시오.

+++

+++Adobe Learning Manager 데스크탑 애플리케이션에서 게시물을 게시할 수 없습니다.

1. Adobe Learning Manager 관리자에 의해 [소셜 학습]이 활성화된 유효한 Adobe Learning Manager 학습자 계정이 있는지 확인합니다.
1. 응용 프로그램 환경 설정을 재설정한 다음, Adobe Learning Manager 데스크탑 응용 프로그램을 다시 실행하고 다시 시도합니다. 자세한 내용은 [응용 프로그램 환경 설정 재설정 방법](#howtoresetapplicationpreferences)을 참조하세요.
1. 게시 중 오류가 발생하면 고급 로깅을 사용하십시오. 자세한 내용은 [고급 로깅을 사용하는 방법](#howtoenableadvancedlogging)을 참조하고, Adobe Learning Manager 데스크탑 응용 프로그램을 다시 시작한 후 오류를 초래하는 위의 단계를 다시 실행하십시오. 도움이 필요하면 최신 응용 프로그램 로그를 Adobe Learning Manager 관리자에게 보내십시오. 자세한 내용은 [응용 프로그램 로그를 찾는 방법](#howtofindapplicationlogs)을 참조하십시오.

+++

+++이전 프로젝트를 보거나 열 수 없습니다.

1. Adobe Learning Manager 계정으로 생성된 프로젝트는 프로젝트가 생성된 것과 동일한 컴퓨터에서만 볼 수 있습니다.
1. 응용 프로그램 환경 설정을 재설정한 다음, Adobe Learning Manager 데스크탑 응용 프로그램을 다시 실행하고 다시 시도합니다. 도움이 필요하면 [응용 프로그램 환경 설정을 재설정하는 방법](#howtoresetapplicationpreferences)을 참조하십시오.
1. 프로젝트를 여는 동안 오류가 발생하면 고급 로깅을 사용하십시오. 자세한 내용은 [고급 로깅을 사용하는 방법](#howtoenableadvancedlogging)을 참조하세요. Adobe Learning Manager 데스크탑 응용 프로그램을 다시 시작하고 오류를 초래하는 단계를 다시 실행하십시오. 도움이 필요하면 최신 응용 프로그램 로그를 Adobe Learning Manager 관리자에게 보내십시오. 자세한 내용은 [응용 프로그램 로그를 찾는 방법](#howtofindapplicationlogs)을 참조하십시오.

+++

## 응용 프로그램 환경 설정을 재설정하는 방법 {#howtoresetapplicationpreferences}

### Windows {#windows}

1. [실행] 대화 상자를 열려면 **Windows + R** 키를 누릅니다.
1. `**%APPDATA%\\..\\Local\\Adobe\\Learning Manager 1.0**`을(를) 입력하고 Enter 키를 누릅니다.
1. **preferences.json** 및 **preferences.xml**&#x200B;이라는 파일을 삭제합니다.

### Mac {#macosx}

1. 파인더를 엽니다.
1. **이동** 폴더 대화 상자를 열려면 **Cmd + Shift + G** 키를 누릅니다.
1. `**~/Library/Application Support/Adobe/Learning Manager 1.0**`을(를) 입력하고 Enter 키를 누릅니다.
1. **preferences.json** 및 **preferences.xml**&#x200B;이라는 파일을 삭제합니다.

## 응용 프로그램 로그를 찾는 방법? {#howtofindapplicationlogs}

### Windows {#application-logs}

1. [실행] 대화 상자를 열려면 **Windows + R** 키를 누릅니다.
1. `**%TEMP%\\elthor**`을(를) 입력하고 Enter 키를 누릅니다.
1. **수정한 날짜**&#x200B;를 기준으로 폴더를 정렬하고 가장 최근 폴더를 엽니다. 이 폴더에는 최신 응용 프로그램 로그가 포함되어 있습니다.

### Mac {#MacOSX-1}

1. **파인더**&#x200B;를 엽니다.
1. **폴더로 이동** 대화 상자를 열려면 **Cmd + Shift + G** 키를 누릅니다.
1. &quot;**/var/folders**&quot;(따옴표 제외)을 입력하고 Enter 키를 누릅니다.
1. 검색 창에서 &quot;**elthor**&quot;을(를) 검색하고 폴더를 엽니다.
1. **수정한 날짜**&#x200B;를 기준으로 폴더를 정렬하고 가장 최근 폴더를 엽니다. 이 폴더에는 최신 응용 프로그램 로그가 포함되어 있습니다.

## 고급 로깅을 사용하는 방법 {#howtoenableadvancedlogging}

### Windows {#Windows-1}

1. [실행] 대화 상자를 열려면 **Windows 키 + R**&#x200B;을(를) 누릅니다.**&#x200B;**
1. &quot;**%APPDATA%\\..\\Local\\Adobe\\Learning Manager 1.0**&quot;(따옴표 제외)을 입력하고 Enter 키를 누릅니다.**&#x200B;**
1. **preferences.json** 파일을 백업한 다음, 텍스트 편집기에서 엽니다.**&#x200B;**
1. **debugMode** 키를 검색하고 이 키의 값 속성을 &quot;**true**&quot;(따옴표 제외)로 변경합니다.

### Mac {#MacOSX-2}

1. 파인더를 엽니다.
1. **폴더로 이동** 대화 상자를 열려면 **Cmd + Shift + G**&#x200B;를 누릅니다.
1. Adobe &quot;**~/Library/Application Support/Library/Learning Manager 1.0**&quot;(따옴표 제외)을 입력하고 Enter 키를 누릅니다.
1. **preferences.json** 파일을 백업한 다음, 텍스트 편집기에서 엽니다.
1. **debugMode** 키를 검색하고 이 키의 값 속성을 &quot;**true**&quot;(따옴표 제외)로 변경합니다.

## Mac OS X Mojave에서 웹캠/마이크 권한을 설정하는 방법은 무엇입니까? {#howtosetwebcammicrophonepermissionsonmacosxmojave}

1. Dock에서 **[!UICONTROL 시스템 환경 설정]** 아이콘을 클릭합니다.
1. **[!UICONTROL 보안 및 개인 정보]** > **[!UICONTROL 개인 정보].**&#x200B;를 클릭합니다.
1. **[!UICONTROL 웹캠 및 마이크 옵션]**&#x200B;을 클릭하고 Adobe Learning Manager 확인란이 선택되어 있는지 확인합니다. Adobe Learning Manager가 나열되지 않으면 먼저 Adobe Learning Manager 데스크탑 응용 프로그램을 설치하여 실행합니다.

## 데스크탑 업데이트 캐시용으로 Adobe Learning Manager를 정리하는 방법은 무엇입니까? {#howtocleanupadobecaptivateprimefordesktopupdatescache}

### Windows {#clean-previous-installation}

1. [실행] 대화 상자를 열려면 **Windows 키 + R**&#x200B;을(를) 누릅니다.
1. `**%APPDATA%\\..\\Local\\Adobe\\Learning Manager 1.0**`을(를) 입력하고 Enter 키를 누릅니다.
1. **updates**&#x200B;라는 폴더를 삭제합니다.

### Mac {#MacOSX-3}

1. 파인더를 엽니다.
1. **폴더로 이동** 대화 상자를 열려면 **Cmd + Shift + G**&#x200B;를 누릅니다.
1. `**~/Library/Application Support/Adobe/Learning Manager 1.0**`을(를) 입력하고 Enter 키를 누릅니다.
1. **updates**&#x200B;라는 폴더를 삭제합니다.

## 데스크탑 임시 폴더용으로 Adobe Learning Manager를 정리하는 방법은 무엇입니까? {#howtocleanupadobecaptivateprimefordesktoptempfolder}

### Windows {#clean-previous-installation-1}

1. [실행] 대화 상자를 열려면 **Windows 키 + R**&#x200B;을(를) 누릅니다.
1. &quot;**%TEMP%**&quot;(따옴표 제외)을 입력하고 Enter 키를 누릅니다.
1. 이름이 &quot;**elthor**&quot;인 폴더를 삭제합니다.

### Mac {#MacOSX-4}

1. 파인더를 엽니다.
1. **폴더로 이동** 대화 상자를 열려면 **Cmd + Shift + G** 키를 누릅니다.
1. &quot;**/var/folders**&quot;(따옴표 제외)을 입력하고 Enter 키를 누릅니다.
1. 검색 창에서 &quot;**elthor**&quot;을(를) 검색합니다.
1. 이름이 &quot;**elthor**&quot;인 폴더를 삭제합니다.

## 데스크탑 프로젝트용으로 Adobe Learning Manager를 찾는 방법은 무엇입니까? {#howtolocateadobecaptivateprimefordesktopprojects}

### Windows {#Windows-2}

1. [실행] 대화 상자를 열려면 **Windows 키 + R**&#x200B;을(를) 누릅니다.
1. &quot;**~/Documents/My Adobe Learning Manager Projects**&quot;(따옴표 제외)을 입력하고 Enter 키를 누릅니다.
1. 사용자 또는 Adobe Learning Manager 책임자가 기본 프로젝트 폴더 위치를 변경했을 수 있습니다. 프로젝트를 찾고 정리하는 데 도움이 필요하면 관리자에게 문의하십시오.

### Mac {#MacOSX-5}

1. 파인더를 엽니다.
1. **폴더로 이동** 대화 상자를 열려면 **Cmd + Shift + G** 키를 누릅니다.
1. &quot;**~/Documents/My Adobe Learning Manager Projects**&quot;(따옴표 제외)을 입력하고 Enter 키를 누릅니다.

   사용자 또는 Adobe Learning Manager 책임자가 기본 프로젝트 폴더 위치를 변경했을 수 있습니다. 프로젝트를 찾고 정리하는 데 도움이 필요하면 책임자에게 문의하십시오.

## Adobe Learning Manager 데스크탑 앱의 이전 설치를 정리하는 방법은 무엇입니까? {#howtocleanuppreviousinstallationsofadobelearningmanagerdesktopapp}

### Windows {#Windows-3}

1. **실행 대화 상자를 열려면 Windows 키 + R**&#x200B;을 **누르세요**.
1. regedit 를 입력하고 &quot;**HKEY_LOCAL_MACHINE \\SOFTWARE\\Classes\\Installer\\**&quot;(따옴표 제외) 또는 &quot;**HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Installer\\UserData\\S-1-5-18\\Products\\**&quot;(따옴표 제외)을(를) 검색한 다음 Enter 키를 누릅니다.
1. Adobe Learning Manager라는 폴더를 찾아 이전 설치를 찾습니다. 레지스트리 항목을 삭제합니다.  F3 키를 누르면 키를 찾을 수 있다.

### Mac {#MacOSX-6}

경로 &quot;**/Applications/Adobe Learning Manager Adobe/Users/Shared/User/Learning Manager Assets/1.0**&quot;의 파일을 휴지통으로 이동한 다음 휴지통을 비웁니다.
