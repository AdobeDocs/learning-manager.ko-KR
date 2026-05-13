---
description: Workday 커넥터와 Adobe Learning Manager을 통합하는 방법 알아보기
jcr-language: en_us
title: Workday 커넥터
contentowner: mmanuel
source-git-commit: 8a5212062c6b172b0e9d4f3faa2e66d26c5c2b56
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 1%

---


# Adobe Learning Manager의 Workday 커넥터

## 소개

**Workday**&#x200B;은 조직에서 직원 및 재무 데이터를 관리하는 데 도움이 되는 클라우드 기반 시스템입니다. 주로 채용, 급여, 성과 추적 등 HR 업무에 사용됩니다. Adobe Learning Manager과 연결하면 두 플랫폼 간 사용자 및 스킬 데이터를 자동으로 동기화할 수 있습니다.

Workday 커넥터를 통해 Adobe Learning Manager을 조직의 Workday 테넌트와 원활하게 통합할 수 있습니다. 이러한 통합을 통해 두 시스템 간에 사용자 데이터와 기술을 자동으로 동기화할 수 있으므로 데이터의 정확성을 높이고 수작업을 줄일 수 있습니다.

## 주요 이점

- Workday에서 Adobe Learning Manager으로 사용자를 가져옵니다.
- Workday과 Adobe Learning Manager 간에 속성을 매핑합니다.
- Adobe Learning Manager에서 Workday으로 사용자 스킬을 내보냅니다.
- 데이터 동기화 작업이 자동으로 실행되도록 예약합니다.

## 사전 요구 사항

Workday 커넥터를 구성하기 전에 Workday 관리자로부터 다음 세부 정보를 얻으십시오.

- 호스트 URL
- 테넌트 ID
- 사용자 이름
- 암호

## Workday 커넥터 구성

Adobe Learning Manager에서 Workday 커넥터를 구성하여 Workday에서 사용자 데이터를 가져오고, 사용자 스킬을 다시 Workday으로 내보내고, 자동화된 동기화를 예약하여 두 시스템을 최신 상태로 유지할 수 있습니다.

Workday 커넥터를 구성하려면:

1. 통합 관리자로 Adobe Learning Manager에 로그인합니다.
2. **Workday** 타일 위로 마우스를 가져간 다음 **연결**&#x200B;을 선택합니다.

   ![](assets/workday-connector1.png)
   _데이터를 가져오고 내보내도록 Workday 커넥터 구성_

3. 다음 연결 세부 정보를 입력합니다.
   - **연결 이름**: 연결할 이름입니다.
   - **호스트 Url**: Workday 관리자가 제공했습니다.
   - **테넌트**: Workday 관리자의 내부 식별자입니다.
   - **사용자 이름 및 암호**: Workday 관리자는 필요한 보안 권한을 가진 ISU(통합 시스템 사용자)를 만들고 통합 책임자와 공유합니다.

   ![](assets/workday-connector2.png)
   _Workday 커넥터를 구성하는 데 필요한 세부 정보를 추가합니다_

4. **연결**&#x200B;을 선택하여 설정을 완료합니다.

>[!NOTE]
>
>계정에서 여러 Workday 연결을 설정할 수 있습니다.

## Workday에서 사용자 가져오기

### 맵 속성

Workday 커넥터를 사용하여 Workday 테넌트의 활성 사용자를 Adobe Learning Manager으로 가져올 수 있습니다. 이 통합은 직원 기록을 동기화하여 사용자 관리를 간소화합니다. Workday 외에도 Adobe Learning Manager은 FTP 및 Salesforce와 같은 다른 데이터 원본에서의 사용자 가져오기를 지원합니다.

사용자를 가져오기 전에 Workday과 Learning Manager 간에 사용자 속성을 매핑해야 합니다.

1. Workday 커넥터에서 **개요** 페이지로 이동합니다.
2. **가져오기** 섹션에서 **내부 사용자**&#x200B;를 선택합니다.

   ![](assets/workday-connector3.png)
   _사용자 특성을 매핑할 내부 사용자 선택_

3. **특성 매핑** 옵션을 사용하여 두 시스템 간에 필드를 연결합니다.
   - **Adobe Learning Manager** 열에서 해당하는 Adobe Learning Manager 특성을 선택합니다.
   - **Workday** 열에서 드롭다운 메뉴를 사용하여 일치하는 Workday 특성을 선택합니다.

   ![](assets/workday-connector4.png)
   _Workday 특성을 Adobe Learning Manager 필드와 매핑_

   >[!NOTE]
   >
   >Adobe Learning Manager은 현재 Workday에서 최대 **69개의 사용자 특성**&#x200B;을 가져올 수 있습니다. Adobe Learning Manager에서 **활성 필드** 기능을 사용하여 추가 필드를 활성화할 수 있습니다. 사용자 정의 Workday 속성을 추가하려면 고객 성공 계정 관리자(CSAM)에 문의하십시오.

4. 임시 작업자를 가져오지 않도록 하려면 **임시 작업자 제외** 확인란을 선택합니다.
5. 필요한 경우 필터를 적용합니다. 예를 들어 특정 관리자 아래에 사용자를 가져오려면 다음을 수행합니다.

>[!IMPORTANT]
>
>UUID, 이메일 주소 및 직원 이름이 고유한지 확인합니다. 값이 잘못되었거나 중복되면 통합 오류가 발생할 수 있습니다.

## 지원되는 Workday 속성

지원되는 Workday 특성 목록:

```
wd:User_ID wd:Worker_ID manager wd:Personal_Data.wd:Name_Data.wd:Preferred_Name_Data.wd:Name_Detail_Data.@wd:Formatted_Name wd:Personal_Data.wd:Name_Data.wd:Legal_Name_Data.wd:Name_Detail_Data.@wd:Formatted_Name wd:Personal_Data.wd:Name_Data.wd:Legal_Name_Data.wd:Name_Detail_Data.wd:Prefix_Data.wd:Title_Descriptor wd:Personal_Data.wd:Name_Data.wd:Preferred_Name_Data.wd:Name_Detail_Data.wd:Prefix_Data.wd:Title_Descriptor wd:Personal_Data.wd:Name_Data.wd:Preferred_Name_Data.wd:Name_Detail_Data.wd:First_Name wd:Personal_Data.wd:Name_Data.wd:Preferred_Name_Data.wd:Name_Detail_Data.wd:Last_Name wd:Personal_Data.wd:Name_Data.wd:Legal_Name_Data.wd:Name_Detail_Data.wd:First_Name wd:Personal_Data.wd:Name_Data.wd:Legal_Name_Data.wd:Name_Detail_Data.wd:Last_Name wd:Personal_Data.wd:Contact_Data.wd:Address_Data.0.@wd:Formatted_Address wd:Personal_Data.wd:Contact_Data.wd:Address_Data.0.wd:Postal_Code wd:Personal_Data.wd:Contact_Data.wd:Email_Address_Data.0.wd:Email_Address wd:Personal_Data.wd:Contact_Data.wd:Address_Data.0.wd:Country_Region_Descriptor wd:Personal_Data.wd:Contact_Data.wd:Phone_Data.0.@wd:Formatted_Phone wd:Personal_Data.wd:Contact_Data.wd:Phone_Data.0.wd:Country_ISO_Code wd:Personal_Data.wd:Contact_Data.wd:Phone_Data.0.wd:International_Phone_Code wd:Personal_Data.wd:Contact_Data.wd:Phone_Data.0.wd:Phone_Number wd:Personal_Data.wd:Primary_Nationality_Reference.wd:ID.1.$ wd:Personal_Data.wd:Gender_Reference.wd:ID.1.$ wd:Personal_Data.wd:Identification_Data.wd:National_ID.0.wd:National_ID_Data.wd:ID wd:Personal_Data.wd:Identification_Data.wd:Custom_ID.0.wd:Custom_ID_Data.wd:ID wd:User_Account_Data.wd:Default_Display_Language_Reference.wd:ID.1.$ wd:Role_Data.wd:Organization_Role_Data.wd:Organization_Role.0.wd:Organization_Role_Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Position_Title wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Title wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Name wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Address_Data.@wd:Formatted_Address
wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Classification_Summary_Data.0.wd:Job_Classification_Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Classification_Summary_Data.0.wd:Job_Group_Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Work_Space__Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Profile_Summary_Data.wd:Job_Family_Reference.0.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Profile_Summary_Data.wd:Job_Profile_Name wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Profile_Summary_Data.wd:Job_Profile_Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Address_Data.0.wd:Country_Reference.wd:ID.2.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Worker_Type_Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Address_Data.0.@wd:Formatted_Address wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Job_Profile_Summary_Data.wd:Management_Level_Reference.wd:ID.1.$ wd:Employment_Data.wd:Worker_Status_Data.wd:Active wd:Employment_Data.wd:Worker_Status_Data.wd:Active_Status_Date wd:Employment_Data.wd:Worker_Status_Data.wd:Hire_Date wd:Employment_Data.wd:Worker_Status_Data.wd:Original_Hire_Date wd:Employment_Data.wd:Worker_Status_Data.wd:Retired wd:Employment_Data.wd:Worker_Status_Data.wd:Retirement_Date wd:Employment_Data.wd:Worker_Status_Data.wd:Terminated wd:Employment_Data.wd:Worker_Status_Data.wd:Termination_Date wd:Employment_Data.wd:Worker_Status_Data.wd:Termination_Last_Day_of_Work wd:Organization_Data.wd:Worker_Organization_Data.0.wd:Organization_Data.wd:Organization_Code wd:Organization_Data.wd:Worker_Organization_Data.0.wd:Organization_Data.wd:Organization_Name wd:Organization_Data.wd:Worker_Organization_Data.0.wd:Organization_Data.wd:Organization_Type_Reference.wd:ID.1.$ wd:Organization_Data.wd:Worker_Organization_Data.0.wd:Organization_Data.wd:Organization_Subtype_Reference.wd:ID.1.$ wd:Qualification_Data.wd:Education.0.wd:School_Name wd:Qualification_Data.wd:External_Job_History.0.wd:Job_History_Data.wd:Job_Title wd:Qualification_Data.wd:External_Job_History.0.wd:Job_History_Data.wd:Company wd:Management_Chain_Data.wd:Worker_Supervisory_Management_Chain_Data.wd:Management_Chain_Data.0.wd:Manager.Employee_ID Primary Work Email wd:Organization_Type_Reference_Cost_Center_ID wd:Organization_Type_Reference_Cost_Center_Name wd:Organization_Type_Reference_Company wd:Organization_Subtype_Reference_Department
wd:Organization_Subtype_Reference_Division wd:Universal_ID wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Address_Data.0.wd:Country_Region_Descriptor wd:Employment_Data.wd:Worker_Job_Data.0.wd:Position_Data.wd:Business_Site_Summary_Data.wd:Address_Data.0.wd:Country_Region_Reference.wd:ID.2.$ wd:Personal_Data.wd:Contact_Data.wd:Address_Data.0.wd:Municipality
```

## Workday으로 사용자 스킬 내보내기

모든 활성 사용자 스킬을 Adobe Learning Manager에서 Workday으로 내보낼 수 있습니다. 중단된 스킬은 내보내지 않습니다.

>[!IMPORTANT]
>
>- 여러 Adobe Learning Manager 계정의 스킬을 동일한 Workday 계정으로 동시에 내보내지 마십시오.
>- 여러 Adobe Learning Manager 계정에서 동일한 Workday 계정을 사용하는 경우 충돌을 방지하기 위해 스킬 이름이 계정 간에 일관성을 유지하도록 하십시오.

### 예약된 내보내기 구성

예약된 내보내기를 구성하려면 다음을 수행합니다.

1. **사용자 스킬**&#x200B;을 선택한 다음 **Workday 개요** 페이지에서 **일정 구성**&#x200B;을 선택합니다.

   ![](assets/workday-connector5.png)
   _내보내기를 예약할 사용자 스킬 선택_

2. **이 연결을 사용하여 사용자 스킬 내보내기 사용** 확인란을 선택합니다.
3. **예약 사용**&#x200B;을 선택합니다.
4. 시작 날짜, 시간 및 되풀이 간격을 설정합니다.

   ![](assets/workday-connector6.png)
   _Workday 커넥터에서 일정 내보내기 구성_

5. **저장**&#x200B;을 선택하여 일정을 적용합니다.

### 온디맨드 내보내기

온디맨드 내보내기를 생성하려면

1. **Workday 개요** 페이지에서 **온디맨드**&#x200B;를 선택합니다.
2. 보고서를 시작할 시작 날짜를 입력합니다.
3. 보고서를 실행하려면 **실행**&#x200B;을 선택하십시오.

### 실행 상태 보기

1. **실행 상태**&#x200B;로 이동합니다.
2. 모든 작업의 상태를 보고 필요에 따라 오류 보고서를 다운로드합니다.

## 동기화 작업 예약

데이터 동기화 작업을 자동으로 실행하도록 커넥터를 구성할 수 있습니다.

- Workday에서 Learning Manager로 일일 사용자 가져오기를 예약합니다.
- Workday으로 정기적으로 사용자 스킬 내보내기를 예약합니다.

>[!NOTE]
>
>스케줄링을 통해 두 시스템에서 사용자 기록 및 스킬 데이터가 항상 최신 상태인지 확인할 수 있습니다.

## 유의 사항

- Workday에서 생성한 UUID 필드는 클라이언트가 있는 LMS 관리자가 삭제할 수 없습니다.
- **사용자 제거** 기능은 실행당 최대 50명의 사용자만 지원합니다. UUID가 있는 사용자를 가져올 때는 주의합니다.
- 스킬은 Workday의 스킬 이름 및 레벨을 사용하여 Adobe Learning Manager의 스킬 항목 레벨로 매핑됩니다.
