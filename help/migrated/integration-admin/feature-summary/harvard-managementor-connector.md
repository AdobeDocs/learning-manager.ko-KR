---
description: Harvard ManageMentor를 Adobe Learning Manager과 통합하는 방법 알아보기
jcr-language: en_us
title: Harvard ManageMentor 커넥터
contentowner: mmanuel
source-git-commit: 8a5212062c6b172b0e9d4f3faa2e66d26c5c2b56
workflow-type: tm+mt
source-wordcount: '737'
ht-degree: 0%

---


# Adobe Learning Manager의 Harvard ManageMentor 커넥터

## 소개

**Harvard ManageMentor 커넥터**&#x200B;는 Harvard ManageMentor를 사용하는 기업 고객을 위해 설계되었습니다. 학습자가 Adobe Learning Manager에서 직접 Harvard ManageMentor 과정을 발견하고 액세스할 수 있습니다. 연결되면 시스템은 학습자 진행률 데이터를 정기적으로 가져오고 가져온 메타데이터를 기반으로 Adobe Learning Manager에서 강의를 생성할 수 있습니다.

이 문서에서는 Adobe Learning Manager에서 Harvard ManageMentor 커넥터를 구성하고 사용하는 방법에 대해 설명합니다.

이번 통합을 통해 통합 책임자는 새로운 교육 콘텐츠를 처음부터 만들지 않고도 회사의 Harvard ManageMentor 계정을 Adobe Learning Manager에 연결하여 과정을 자동으로 가져오고 학습자 진행률을 추적할 수 있습니다.

## 선행 작업

커넥터를 구성하기 전에 계정에 대해 **마이그레이션** 기능이 활성화되어 있는지 확인하십시오.

## 커넥터 설정

Harvard ManageMentor 커넥터를 사용하여 Harvard ManageMentor의 과정을 Adobe Learning Manager으로 가져올 수 있습니다. 계정을 연결한 후 강의 세부 정보를 가져오고 학습자의 진행률을 추적할 수 있습니다.

커넥터를 설정하려면:

1. 통합 책임자로 로그인합니다.
2. 홈페이지에서 **Harvard ManageMentor**&#x200B;를 선택합니다.
3. 커넥터 타일에서 다음 옵션 중 하나를 선택합니다.
   - **시작**
   - **연결**
   - **연결 관리**

   ![](assets/harvard-managementor-connector1.png)
   _Harvard ManageMentor 타일에는 구성에 대한 세 가지 옵션이 표시됩니다._

## 새 연결 만들기

새 연결을 생성하려면 다음을 수행하십시오.

1. **Harvard ManageMentor** 타일에서 **연결**&#x200B;을(를) 선택합니다.

   ![](assets/harvard-managementor-connector2.png)
   _연결을 선택하여 새 Harvard ManageMentor 연결을 만듭니다_

2. **연결 이름** 필드에 연결을 입력하십시오.
3. **연결**&#x200B;을 선택하여 연결을 만듭니다.

   ![](assets/harvard-managementor-connector3.png)
   _연결 이름 필드에 이름을 입력하십시오_

## 연결 관리

Harvard ManageMentor 커넥터를 설정한 후 Adobe Learning Manager에서 연결을 관리할 수 있습니다. 동기화 설정을 변경하고 수동으로 또는 일정에 따라 동기화를 실행할 수 있습니다.

### 연결 활성화

연결을 사용하려면 다음을 수행하십시오.

1. **Harvard ManageMentor** 타일에서 **연결 관리**&#x200B;를 선택합니다.

   ![](assets/harvard-managementor-connector4.png)
   _데이터 가져오기를 구성하고 예약하기 위한 연결 관리_

2. 연결을 선택합니다.
3. 왼쪽 탐색 창에서 **구성**&#x200B;을 선택합니다.
4. **연결 사용**&#x200B;을 선택한 다음 **저장**&#x200B;을 선택하십시오.

   ![](assets/harvard-managementor-connector5.png)
   _데이터를 가져오려면 Harvard ManageMentor 커넥터를 활성화하십시오_

### 동기화 예약

동기화를 예약하려면 다음을 수행합니다.

1. **Harvard ManageMentor** 타일에서 **연결 관리**&#x200B;를 선택합니다.
2. 연결을 선택합니다.
3. 왼쪽 탐색 창에서 **구성**&#x200B;을 선택합니다.
4. **예약 동기화** 섹션에서 **예약 사용**&#x200B;을 선택합니다.

   ![](assets/harvard-managementor-connector6.png)
   _Harvard ManageMentor에서 Adobe Learning Manager으로 데이터 가져오기 예약_

5. 시작 날짜 및 시간을 UTC로 선택합니다.
6. 동기화를 반복해야 하는 일 수를 입력합니다.
7. **저장**&#x200B;을 선택합니다.

동기화 설정이 저장됩니다. 이 커넥터는 일정에 따라 실행되며 Harvard ManageMentor의 데이터를 Adobe Learning Manager으로 가져옵니다.

## 온디맨드 동기화 실행

**온디맨드 동기화** 옵션을 사용하면 Harvard ManageMentor에서 Adobe Learning Manager으로 데이터를 수동으로 가져올 수 있습니다. 이 기능은 다음 예약된 동기화를 기다리지 않고 즉시 학습자 활동 데이터를 업데이트하려는 경우 유용합니다.

온디맨드 데이터 임포트를 실행하려면

1. **Harvard ManageMentor** 타일에서 **연결 관리**&#x200B;를 선택합니다.
2. 연결을 선택합니다.
3. 왼쪽 창에서 **온디맨드 실행**&#x200B;을 선택합니다.
4. **시작 날짜**&#x200B;를 선택합니다.

   ![](assets/harvard-managementor-connector7.png)
   _Harvard ManageMentor에서 Adobe Learning Manager으로 데이터를 즉시 가져오기 위한 온디맨드 요청 실행_

5. 다음 옵션 중 하나를 선택합니다.

   - **실행 중 Adobe Learning Manager에 대한 액세스를 사용하지 않도록 설정**: 동기화로 인해 다운타임이 발생할 수 있는 경우 권장됩니다.
   - **실행 중 Adobe Learning Manager에 대한 액세스를 사용합니다**: 서비스 중단을 방지하려면 이 옵션을 사용하는 것이 좋습니다.
6. 시작 날짜부터 현재까지의 모든 데이터를 가져오려면 **실행**&#x200B;을 선택하십시오.

### 실행 기록 보기

실행 상태 페이지에는 모든 동기화 실행이 순서대로 나열됩니다. 실행에 오류가 있으면 경고 아이콘이 나타납니다. 필요한 경우 오류 로그를 확인하고 CSV 파일을 수정한 다음 최신 동기화를 다시 실행할 수 있습니다.

실행 기록을 보려면 다음을 수행합니다.

1. 왼쪽 창에서 **실행 상태**&#x200B;를 선택합니다.
2. 다음 열을 볼 수 있습니다.
   - **실행**
   - **시작 날짜**
   - **기간**
   - **유형**(예약 또는 주문형)
   - **상태**(진행 중 또는 완료)

   ![](assets/harvard-managementor-connector8.png)
   _온디맨드 및 예약된 가져오기의 실행 상태 보기_

>[!NOTE]
>
>연결을 삭제하고 다시 생성해도 이전 실행에 대한 실행 기록이 계속 표시됩니다. 최신 동기화만 다시 실행할 수 있습니다.

### 동기화를 위한 요구 사항

다음 파일이 Harvard ManageMentor FTP 폴더에 있는지 확인하십시오.

- **hmm12_metadata.csv** 이 파일에는 강의 메타데이터가 포함되어 있습니다. 올바른 파일 이름 지정 형식을 따르십시오.
- **client_hmm12_yyyyMMdd.csv** 이 파일은 사용자 피드입니다. 날짜 형식은 yyyyMMdd와 일치해야 합니다.

**샘플 파일**

- [Harvard ManageMentor 커넥터의 과정 메타데이터 파일](https://experienceleague.adobe.com/docs/learning-manager/assets/hmm12-metadata.csv?lang=ko)
- [Harvard ManageMentor 커넥터의 사용자 피드 파일](https://experienceleague.adobe.com/docs/learning-manager/assets/client-hmm12-20170304.csv?lang=ko)
