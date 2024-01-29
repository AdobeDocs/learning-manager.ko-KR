---
description: 이 문서에는 데이터와 콘텐츠를 기존 LMS에서 Learning Manager로 마이그레이션하는 동안 발생하는 일반적인 문제를 해결하는 기본적인 문제 해결 팁이 있습니다.
jcr-language: en_us
title: 마이그레이션 문제 해결
contentowner: jayakarr
source-git-commit: 6abc118c6ad7e66e3ded5bd26b9167c3a0b99e4b
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 0%

---



# 마이그레이션 문제 해결

이 문서에는 데이터와 콘텐츠를 기존 LMS에서 Learning Manager로 마이그레이션하는 동안 발생하는 일반적인 문제를 해결하는 기본적인 문제 해결 팁이 있습니다.

## 일반적인 마이그레이션 문제 {#genericmigrationissues}

### FTP 폴더 또는 콘텐츠 폴더에 로그인할 수 없음 {#unabletologintoftpfolderorcontentfolder}

FTP 및 Box 서비스에 계정이 생성되었는지 확인합니다. 마이그레이션 프로젝트를 생성할 때 이 두 가지 서비스를 설정하도록 요청합니다. 서비스를 생성하는 즉시 Exavault 및 Box에서 이메일을 수신하여 암호를 재설정하거나 설정합니다. 암호가 기억나지 않는 경우에는 Exavault 및 Box 웹사이트를 방문하여 암호를 재설정할 수 있습니다.

### 새로 고침 단추를 눌러도 작업이 반영되지 않음 {#jobsarenotreflectedevenafterclickingrefreshbutton}

* CSV 파일이 Exavault FTP의 올바른 폴더에 업로드되었는지 확인합니다. 경로 구조는 다음과 같아야 합니다.

`code Account>Project>Sprint location`

* CSV 파일의 파일 이름이 CSV 사양 이름에 따라 다음과 같은지 확인하십시오.

   * course.csv
   * course_instance.csv
   * course_module.csv
   * enrollment.csv
   * module.csv
   * module_version.csv
   * user_course_grade.csv

### 오류 기록이 있는 작업에 대한 실패가 표시됩니다. {#failuresareshownforjobswitherrorrecords}

1. 을 클릭하여 오류 로그를 다운로드합니다. **오류 기록 다운로드** 링크
1. 보고된 오류를 기반으로 원본 CSV를 수정한 다음
1. 수정된 CSV로 스프린트를 다시 실행합니다.

전체 기록 수보다 변경 사항의 개수가 적으면 새로운 스프린트에서 수정된 CSV를 실행하는 것이 좋습니다.

### 스프린트 마이그레이션을 중지한 후에도 Learning Manager에 로그인할 수 없음 {#unabletologintocaptivateprimeapplicationevenafterstoppingthesprintmigration}

스프린트 실행이 중지되거나 완료되면 계정 잠금 해제에 10~15분이 소요될 수 있습니다. 15분 후에 응용 프로그램에 액세스합니다.

### 일부 마이그레이션 작업은 &#39;중지&#39;가 트리거된 후에도 &#39;진행 중&#39; 상태로 표시됩니다. {#someofthemigrationjobsdisplayinprogressstatusevenafterstopistriggered}

모든 작업이 &#39;진행 중&#39; 상태가 되면 실행 중지에 10~15분이 소요될 수 있습니다. 10분 후에 상태를 다시 확인하십시오.

### 단추가 비활성화되어 스프린트를 생성할 수 없음 {#unabletocreateasprintasthebuttonisdisabled}

스프린트를 만들기 전에 현재 스프린트가 완료로 표시되어 있는지 확인합니다. 다음을 수행합니다. **[!UICONTROL 스프린트 완료로 표시]** 페이지 상단에서 스프린트 마이그레이션을 완료합니다.

### 단추가 비활성화되어 마이그레이션 프로젝트를 완료로 표시할 수 없음 {#unabletomarkamigrationprojectascompleteasthebuttonisdisabled}

마이그레이션 프로젝트 완료를 표시하기 전에 현재 스프린트가 완료로 표시되어 있는지 확인합니다. 다음을 수행합니다. **[!UICONTROL 스프린트 완료로 표시]** 페이지 상단에서 스프린트 마이그레이션을 완료합니다.

## CSV 문제 {#csvissues}

### module_version.csv 파일 마이그레이션에 실패하여 콘텐츠가 아직 마이그레이션되지 않음 {#moduleversioncsvfilemigrationisfailingandcontentisnotmigratedyet}

콘텐츠 폴더(지정된 마이그레이션 프로젝트의 Box 계정, 스프린트 경로)에서 콘텐츠를 사용할 수 있는지 확인합니다. 또한 옵션을 선택했는지 확인하십시오 **예** 에 대해 **이 스프린트의 콘텐츠를 마이그레이션하시겠습니까?** 라는 질문에 예 옵션을 선택했는지 확인합니다.

선택하지 않은 경우 **예**&#x200B;그런 다음 이 스프린트를 계속 진행하면 해당 스프린트를 완료할 때까지 기다려야 합니다. 다른 스프린트를 생성한 다음 을 클릭합니다 **[!UICONTROL 예]**.

### &#39;유효한 Learning Manager ID가 아닙니다&#39;라는 오류 메시지와 함께 enrollment.csv 또는 user_course_grade.csv 기록이 실패함 {#enrollmentcsvorusercoursegradecsvrecordsfailwithanerrormessagenotavalidprimeid}

userId, assignedByUserID 필드의 일부로 제공된 전자 메일 ID가 유효한 Learning Manager 사용자에게 속하는지 확인합니다. 그렇지 않다면 사용자를 추가하고 다음으로 새로운 스프린트를 생성합니다. **사용자 동기화** 옵션을 선택했습니다. 사용자가 조직에 포함되어 있지 않은 경우 사용자 추가 CSV 사양을 사용하여 사용자를 Learning Manager에서 삭제된 사용자로 추가합니다. 삭제된 사용자를 추가하기 위한 샘플 CSV 사양은 아래를 참조하십시오.

[Users.csv](assets/users.zip) 자세한 내용은 **CSV 사양 및 샘플 CSV** 섹션 [마이그레이션 설명서](../integration-admin/feature-summary/migration-manual.md) 전체 CSV 사양 및 샘플 CSV 파일을 다운로드합니다.

### 강의가 비어 있음으로 표시되거나 마이그레이션된 강의에 잘못된 모듈이 재생됨 {#coursesappearblankorincorrectmodulesplayforamigratedcourse}

다음을 확인합니다. **모듈 순서** 강의의 키 값은 다음으로 시작합니다. **0** 연속되는 순서입니다. courseModuleType 순서는 PRETEST, TESTOUT, CONTENT여야 합니다.

또한 활동, 강의실 및 VC의 두 가지 버전이 기존 강의와 연결되어 있지 않은지 확인합니다.

### &#39;모듈이 이미 기존 강의에 연결되어 있습니다&#39;라는 메시지 수신 {#receivingamessageasmoduleisalreadylinkedwithanexistingcourse}

Learning Manager에서는 활동/VC/강의실 모듈을 두 개 이상의 강의에 연결할 수 없습니다. 모듈이 다른 강의에 연결되어 있지 않은지 확인합니다.

### 강의가 다른 모듈 버전과 연결되어 있더라도 모든 강의는 최신 버전의 활동/VC/강의실 모듈을 표시합니다 {#allthecoursesshowthelatestversionofactivityvcclassroommoduleseventhoughthecoursesarelinkedwithdifferentmoduleversions}

활동, 강의실, 가상 강의실 모듈 버전 관리는 Learning Manager에서 지원되지 않습니다. moduleVersion.csv 파일을 통해 버전을 제공하면 새 버전을 생성하는 대신 기존 파일을 업데이트합니다.

### 마이그레이션된 활동/VC/강의실 모듈에 원하는 지속 기간이 표시되지 않음 {#desireddurationdoesnotappearforamigratedactivityvcclassroommodule}

원하는 지속 기간은 활동/VC/강의실 모듈에 유효한 항목이 아닙니다.

### Learning Manager에서 하이퍼링크 URL이 열리지 않음 {#hyperlinkurldoesntopenupincaptivateprime}

제공된 링크가 &#39;http://&#39; 또는 &#39;https://&#39;으로 고정되어 있는지 확인합니다.

### &#39;파일을 찾을 수 없습니다&#39; 오류와 함께 moduleVersion 마이그레이션 실패 {#moduleversionmigrationfailswithfilenotfounderrors}

참조 파일이 콘텐츠 폴더에 있고 성공적으로 마이그레이션되었는지 확인합니다.

### &#39;모듈: x 및 moduleVersion: y에 내부 오류가 발생했습니다&#39;라는 오류 메시지와 함께 moduleVersion 마이그레이션 실패 {#moduleversionmigrationfailswithanerrormessageasaninternalerrorhasoccurredformodulexandmoduleversiony}

스프린트를 다시 실행하여 문제를 해결합니다.
