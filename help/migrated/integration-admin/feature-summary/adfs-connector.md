---
description: ADFS 커넥터를 Adobe Learning Manager과 통합하는 방법 알아보기
jcr-language: en_us
title: ADFS 커넥터
contentowner: mmanuel
source-git-commit: 8a5212062c6b172b0e9d4f3faa2e66d26c5c2b56
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 3%

---


# Adobe Learning Manager의 ADFS 커넥터

## 소개

Adobe Learning Manager의 ADFS 커넥터를 사용하면 ADFS(Active Directory Federation Services)를 사용하여 Microsoft Azure Active Directory와 통합할 수 있습니다. 이 통합을 통해 Azure AD에서 Learning Manager로 사용자 데이터를 자동으로 동기화할 수 있습니다. 속성 매핑, 사용자 필터링 및 예정된 가져오기와 같은 기능을 통해 커넥터는 사용자 관리를 간소화하고 학습자 데이터가 정확하고 최신 상태로 유지되도록 합니다. 중앙 집중식 ID 및 액세스 관리를 위해 ADFS에 의존하는 조직에 특히 유용합니다.

## 사전 요구 사항

Adobe Learning Manager에서 ADFS 커넥터를 구성하기 전에 Azure Portal에서 다음 단계를 완료하십시오.

- 응용 프로그램 등록
- 클라이언트 암호 생성
- API 권한 설정

### Azure에서 응용 프로그램 등록

Azure에서 응용 프로그램을 등록하려면:

1. [Azure Portal](https://portal.azure.com/)에 로그인합니다.
2. **Azure Active Directory**(으)로 이동합니다.
3. **추가**&#x200B;를 선택한 다음 **앱 등록**&#x200B;을 선택합니다.
4. 응용 프로그램 이름을 입력하고 **등록**&#x200B;을 선택하십시오.

### 클라이언트 암호 생성

클라이언트 시크릿을 만들려면:

1. 새로 등록된 앱에서 **인증서 및 시크릿**(으)로 이동합니다.
2. **새 클라이언트 암호**&#x200B;을(를) 선택합니다.
3. 설명을 추가하고 기한을 **24개월**(으)로 설정합니다.
4. **클라이언트 암호 값**&#x200B;을 안전한 위치에 저장합니다.

### API 권한 설정

API 권한을 추가하려면 다음을 수행합니다.

1. **API 권한**&#x200B;을 선택한 다음 **권한 추가**&#x200B;를 선택합니다.
2. **Microsoft 그래프**&#x200B;를 선택한 다음 **응용 프로그램 권한**&#x200B;을 선택합니다.
3. 다음 권한을 검색하고 선택합니다.

   - **Directory.Read.All** - 디렉터리 데이터 읽기
   - **User.Read.All** - 모든 사용자의 전체 프로필 읽기
4. **권한 추가**&#x200B;를 선택합니다.
5. 권한에 대해 **관리자 동의**&#x200B;를 부여합니다.

## Learning Manager에서 ADFS 커넥터 구성

Adobe Learning Manager에서 ADFS 커넥터를 구성하여 ADFS에서 사용자 데이터를 가져오고, 사용자 스킬을 다시 ADFS로 내보내고, 두 시스템을 최신 상태로 유지하기 위해 자동화된 동기화를 예약할 수 있습니다.

ADFS 커넥터를 구성하려면:

1. 통합 관리자로 Adobe Learning Manager에 로그인합니다.
2. **ADFS** 커넥터 타일 위로 마우스를 가져갑니다.
3. **연결**&#x200B;을 선택합니다.

   ![](assets/adfs-connector1.png)
   _연결을 선택하여 ADFS 커넥터 구성_

### 연결 세부 정보 입력

ADFS 구성 페이지에서 다음을 수행합니다.

1. 다음 세부 사항을 입력합니다.

   - 연결 이름
   - 클라이언트 ID
   - 클라이언트 시크릿

   ![](assets/adfs-connector2.png)
   _ADFS에 연결할 구성 세부 정보를 입력하십시오_

2. **연결**&#x200B;을 선택합니다.
3. Adobe Learning Manager이 Azure 포털에서 **테넌트 ID** 및 **기본 도메인**&#x200B;을 가져오고 자동으로 채웁니다.

## ADFS에서 사용자 가져오기

### 맵 속성

- 통합 책임자는 ADFS 속성을 Adobe Learning Manager의 해당 그룹화 가능 속성에 매핑할 수 있습니다.
- 이 매핑은 일회성 구성이며 이후의 모든 사용자 가져오기에 재사용됩니다.
- 필요한 경우 언제든지 속성 매핑을 수정할 수 있습니다.

### 자동으로 사용자 가져오기

- Adobe Learning Manager은 예약된 간격으로 ADFS에서 사용자 데이터를 자동으로 가져옵니다.
- 이렇게 하면 사용자 레코드가 시스템 간에 동기화되도록 하는 데 도움이 됩니다.

### 사용자 필터링

- 관리자는 필터를 적용하여 가져온 사용자를 제한할 수 있습니다.
- 예를 들어 특정 관리자 또는 부서의 사용자만 가져올 수 있습니다.
