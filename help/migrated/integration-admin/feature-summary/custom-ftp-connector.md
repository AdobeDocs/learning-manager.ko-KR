---
description: Adobe Learning Manager의 사용자 정의 FTP 커넥터
jcr-language: en_us
title: 사용자 정의 FTP 커넥터
contentowner: mmanuel
source-git-commit: 8a5212062c6b172b0e9d4f3faa2e66d26c5c2b56
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---


# Adobe Learning Manager의 사용자 정의 FTP 커넥터

## 소개

Adobe Learning Manager의 사용자 정의 FTP 커넥터를 사용하여 Adobe Learning Manager과 조직의 FTP(SFTP) 서버 간에 안전하고 자동화된 데이터 교환을 할 수 있습니다. 이 통합을 통해 관리자는 외부 시스템에서 사용자 데이터를 가져오고 일정에 따라 학습자 성적 증명서 또는 스킬 데이터를 내보낼 수 있습니다. 이 설정은 데이터 동기화를 간소화하고 수동 작업을 줄이며 타사 HR 또는 보고 시스템과의 원활한 통합을 지원합니다. 구성을 수행하려면 IT 팀과의 협력 및 Adobe CSM(Customer Success Manager)의 지원이 필요합니다.

>[!NOTE]
>
>사용자 정의 FTP 연결을 구성하려면 CSM(고객 성공 관리자)에 문의하십시오. 설정 프로세스에는 IT 팀의 지원이 필요할 수 있으며, IP 주소를 화이트리스트에 추가하고, 필요한 포트를 열고, 필요한 액세스 권한으로 폴더를 만듭니다.

## 지원되는 기능

사용자 정의 FTP 커넥터는 다음 작업을 지원합니다.

### 데이터 가져오기

사용자 가져오기 프로세스는 FTP 서버에서 직원 데이터를 자동으로 가져와 Adobe Learning Manager으로 가져옵니다. 이 기능은 사용자 데이터를 포함하는 CSV 파일을 생성하는 여러 시스템을 통합할 때 유용합니다.

- CSV 파일을 FTP 서버에서 지정된 **가져오기** 폴더에 배치합니다.
- Adobe Learning Manager은 파일을 감지하고 필요한 경우 병합한 다음 정의된 일정에 따라 사용자 데이터를 가져옵니다.

이 프로세스를 자동화하는 방법은 [예약](/help/migrated/integration-admin/feature-summary/custom-ftp-connector.md#scheduling-reports) 섹션을 참조하십시오.

### 속성 매핑

통합 책임자는 CSV 파일의 열을 Adobe Learning Manager의 그룹화 가능한 속성에 매핑할 수 있습니다.

- 매핑은 일회성 설정입니다.
- 이후의 가져오기에서도 동일한 매핑이 사용됩니다.
- 데이터 구조가 변경되면 매핑을 다시 구성할 수 있습니다.

### 데이터 내보내기

Adobe Learning Manager에서 다음을 내보낼 수 있습니다.

- 사용자 스킬
- 학습자 성적 증명서

이러한 보고서 파일은 FTP의 내보내기 폴더에 저장되며 타사 시스템에서 보고, 분석 또는 기타 다운스트림 프로세스에 사용할 수 있습니다.

### 보고서 예약

통합 책임자는 다음 두 가지를 모두 예약할 수 있습니다.

- 사용자 가져오기
- 학습자 성적 증명서 내보내기

스케줄링은 Adobe Learning Manager 환경이 소스 시스템에 최신 상태를 유지하도록 합니다. 필요에 따라 일일 동기화 또는 사용자 정의 간격을 구성할 수 있습니다.

## 사용자 정의 FTP 커넥터 설정

사용자 정의 FTP 커넥터를 구성하려면:

1. 통합 관리자로 Adobe Learning Manager에 로그인합니다.
2. **사용자 지정 FTP** 타일 위로 마우스를 가져간 다음 **연결**&#x200B;을 선택합니다.

   ![](assets/custom-ftp-connector1.png)
   _사용자 지정 FTP 커넥터를 구성하려면 [연결]을 선택하십시오_

### 인증 방법 선택

다음 두 가지 인증 유형 중 하나를 사용하여 사용자 정의 FTP 연결을 구성할 수 있습니다.

#### 기본 인증 계정

1. 다음 세부 사항을 입력합니다.

   - **내 FTP 도메인**
   - **FTP 사용자 이름**
   - **FTP 암호**

   ![](assets/custom-ftp-connector2.png)
   _구성에 대한 FTP 도메인, 사용자 이름 및 암호를 입력하십시오._

2. **연결**&#x200B;을 선택합니다.

#### 인증서 인증

FTP 서버가 SSH 키 인증을 지원하는 경우:

1. **SSH 키 생성**&#x200B;을 선택합니다.

   ![](assets/custom-ftp-connector3.png)
   _SSH 키 생성을 선택하여 키 다운로드_

2. 공개 키가 컴퓨터에 다운로드됩니다.
3. FTP 서버의 승인된 키 목록에 이 키를 추가합니다.
4. 다음 세부 사항을 입력합니다.

   - **내 FTP 도메인**
   - **FTP 사용자 이름**
5. **연결**&#x200B;을 선택합니다.

>[!NOTE]
>
>사용자 지정 FTP 구성에는 **SFTP** 서버만 지원됩니다.

## 연결 후 설정

연결이 설정되면:

- Adobe Learning Manager은 FTP 서버에서 **가져오기** 및 **내보내기**&#x200B;를 위한 폴더를 자동으로 만듭니다.
- 예약 및 매핑 설정에 따라 데이터 가져오기 및 내보내기를 시작할 수 있습니다.
