---
description: Adobe Learning Manager의 getAbstract 커넥터
jcr-language: en_us
title: getAbstract 커넥터
contentowner: mmanuel
source-git-commit: 8a5212062c6b172b0e9d4f3faa2e66d26c5c2b56
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 1%

---


# Adobe Learning Manager용 getAbstract 커넥터

## 소개

**getAbstract 커넥터**&#x200B;는 [getAbstract.com](https://www.getabstract.com/)의 기업 고객을 위해 설계되었습니다. 이를 통해 학습자는 Adobe Learning Manager을 통해 직접 getAbstract 콘텐츠를 찾고 소비할 수 있습니다. 또한 책임자는 커넥터를 사용하여 사용자 참여 데이터를 가져오고 학습자 완료 기록을 자동으로 추적할 수 있습니다.

Adobe Learning Manager은 학습자에게 리더쉽과 소프트 스킬에 중점을 둔 지속적인 자기 주도적 학습 기회를 제공하고자 합니다. 관리자는 내부적으로 모든 콘텐츠를 개발하는 대신 getAbstract 커넥터를 사용하여 조직의 getAbstract 계정을 Adobe Learning Manager에 연결합니다.

- getAbstract 콘텐츠를 자동으로 Adobe Learning Manager으로 가져옵니다.
- 학습자의 강의 및 학습 경로 사용량을 추적합니다.

이 문서에서는 Adobe Learning Manager에서 getAbstract 커넥터를 구성하고 관리하는 단계에 대해 설명합니다.

## 사전 요구 사항

- 커넥터를 구성하기 전에 계정에 대해 **마이그레이션** 기능이 활성화되어 있는지 확인하십시오.
- getAbstract 계정 담당자로부터 **클라이언트 ID** 및 **클라이언트 암호**&#x200B;을(를) 얻습니다. 이러한 자격 증명은 강의 메타데이터 및 사용자 소비 데이터를 검색하는 데 필요합니다.

## getAbstract 커넥터 구성

getAbstract 커넥터를 통해 Adobe Learning Manager 관리자는 getAbstract에서 선별된 고품질 콘텐츠를 통합하여 학습 경험을 향상시킬 수 있습니다.

getAbstract 커넥터를 구성하려면:

1. 통합 책임자로 로그인합니다.
2. 홈 페이지에서 **getAbstract**&#x200B;을(를) 선택합니다.
3. **커넥터** 타일의 다음 옵션 중에서 선택합니다.

   - **시작**: 커넥터의 개요입니다.
   - **연결**: 새 연결을 만듭니다.
   - **연결 관리**: 기존 연결을 보거나 수정합니다.

   ![](assets/getabstract-connector1.png)
   _getAbstract 타일은 구성에 대한 세 가지 옵션을 표시합니다_

## 새 연결 만들기

새 연결을 생성하려면 다음을 수행하십시오.

1. **연결**&#x200B;을 선택합니다.

   ![](assets/getabstract-connector2.png)
   _새 연결을 만들려면 getAbstract 타일에서 연결 선택_

2. **연결 이름**&#x200B;을 입력하십시오.
3. **클라이언트 ID** 및 **클라이언트 암호**&#x200B;을 입력하십시오.

   ![](assets/getabstract-connector3.png)
   _getAbstract 연결 페이지에서 연결, 클라이언트 ID 및 클라이언트 암호를 입력하십시오._

4. **저장**&#x200B;을 선택하여 연결을 만듭니다.

## getAbstract 커넥터 관리

데이터를 가져오기 전에 커넥터를 구성하고 동기화 일정을 설정해야 합니다. 커넥터가 구성되면 사용 데이터를 자동으로 가져와 학습자 진행률을 모니터링하고 학습 계획 및 보고서에 getAbstract 콘텐츠를 포함할 수 있습니다.

### 연결 활성화

연결을 사용하려면 다음을 수행하십시오.

1. **getAbstract** 타일에서 **연결 관리**&#x200B;를 선택합니다.

   ![](assets/getabstract-connector4.png)
   _데이터 가져오기를 구성하고 예약하기 위한 연결 관리_

2. 연결을 선택합니다.
3. 왼쪽 탐색 창에서 **구성**&#x200B;을 선택합니다.
4. **연결 사용**&#x200B;을 선택한 다음 **저장**&#x200B;을 선택하십시오.

   ![](assets/getabstract-connector5.png)
   _getAbstract에서 Adobe Learning Manager으로 데이터를 가져오려면 연결 사용_

### 연결 편집

연결을 편집하려면 다음을 수행합니다.

1. **getAbstract** 타일에서 **연결 관리**&#x200B;를 선택합니다.
2. 연결을 선택합니다.
3. 왼쪽 탐색 창에서 **구성**&#x200B;을 선택합니다.
4. **편집**&#x200B;을 선택하여 **클라이언트 ID** 및 **클라이언트 암호**&#x200B;를 업데이트합니다.

   ![](assets/getabstract-connector6.png)
   _클라이언트 ID 및 클라이언트 암호를 포함한 자격 증명 편집_

5. **저장**&#x200B;을 선택합니다.

### 동기화 예약

동기화를 예약하려면 다음을 수행합니다.

1. **getAbstract** 타일에서 **연결 관리**&#x200B;를 선택합니다.
2. 연결을 선택합니다.
3. 왼쪽 탐색 창에서 **구성**&#x200B;을 선택합니다.
4. **예약 동기화** 섹션에서 **예약 사용**&#x200B;을 선택합니다.

   ![](assets/getabstract-connector7.png)
   _getAbstract에서 Adobe Learning Manager으로 데이터 가져오기 예약_

5. 시작 날짜 및 시간을 UTC로 선택합니다.
6. 동기화를 반복해야 하는 일 수를 입력합니다.
7. **저장**&#x200B;을 선택합니다.

동기화 설정이 저장됩니다. 커넥터는 일정대로 실행되며 getAbstract에서 Adobe Learning Manager으로 데이터를 가져옵니다.

## 온디맨드 동기화 실행

**온디맨드 동기화** 옵션을 사용하면 getAbstract에서 Adobe Learning Manager으로 데이터를 수동으로 가져올 수 있습니다. 이 기능은 다음 예약된 동기화를 기다리지 않고 즉시 학습자 활동 데이터를 업데이트하려는 경우 유용합니다.

온디맨드 데이터 임포트를 실행하려면

1. **getAbstract** 타일에서 **연결 관리**&#x200B;를 선택합니다.
2. 연결을 선택합니다.
3. 왼쪽 창에서 **온디맨드 실행**&#x200B;을 선택합니다.
4. **시작 날짜**&#x200B;를 선택합니다.

   ![](assets/getabstract-connector8.png)
   _getAbstract에서 Adobe Learning Manager으로 즉각적인 데이터 가져오기를 위한 온디맨드 요청 실행_

5. 다음 옵션 중 하나를 선택합니다.

   - **실행 중 Adobe Learning Manager에 대한 액세스를 사용하지 않도록 설정**: 동기화로 인해 다운타임이 발생할 수 있는 경우 권장됩니다.
   - **실행 중 Adobe Learning Manager에 대한 액세스를 사용합니다**: 서비스 중단을 방지하려면 이 옵션을 사용하는 것이 좋습니다.
6. 시작 날짜부터 현재까지의 모든 데이터를 가져오려면 **실행**&#x200B;을 선택하십시오.

### 실행 기록 보기

**실행 상태** 페이지에 모든 동기화 실행이 순서대로 나열됩니다. 실행에 오류가 있으면 경고 아이콘이 나타납니다. 오류 로그를 확인하고 CSV 파일을 수정한 다음 필요한 경우 최신 동기화를 다시 실행할 수 있습니다.

실행 기록을 보려면 다음을 수행합니다.

1. 왼쪽 창에서 **실행 상태**&#x200B;를 선택합니다.
2. 다음 열을 볼 수 있습니다.
   - **실행**
   - **시작 날짜**
   - **기간**
   - **유형**(예약 또는 주문형)
   - **상태**(진행 중 또는 완료)

   ![](assets/getabstract-connector9.png)
   _온디맨드 및 예약된 가져오기의 실행 상태 보기_

>[!NOTE]
>
>연결을 삭제하고 다시 생성해도 이전 실행에 대한 실행 기록이 계속 표시됩니다. 최신 동기화만 다시 실행할 수 있습니다.

### 성공적인 동기화를 위한 요구 사항

동기화가 올바르게 작동하도록 하려면 다음을 수행하십시오.

- 지정된 동기화 날짜에 대해 올바른 사용자 피드 파일이 getAbstract FTP 폴더에 있어야 합니다.
- 파일은 이름 지정 형식을 따라야 합니다.
   - report_export_yyyy_MM_dd_HHmmss.xlsx 또는
   - report_export_yyyy_MM_dd.xlsx

[샘플 getAbstract 사용자 피드 파일](https://experienceleague.adobe.com/docs/learning-manager/assets/report-export-20170401175342.xlsx?lang=en)을 다운로드하여 형식을 파악하세요.
