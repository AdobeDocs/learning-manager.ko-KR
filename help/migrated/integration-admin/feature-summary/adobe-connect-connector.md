---
description: Adobe Connect 커넥터와 Adobe Learning Manager을 통합하는 방법 알아보기
jcr-language: en_us
title: Adobe Connect 커넥터
contentowner: mmanuel
source-git-commit: 8a5212062c6b172b0e9d4f3faa2e66d26c5c2b56
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 2%

---


# Adobe Learning Manager의 Adobe Connect 커넥터

## 소개

Adobe Learning Manager은 Adobe Connect과 통합되어 가상 강의실 교육을 제공하고 관리할 수 있습니다. 이 통합을 통해 세션을 예약하고, 지속적이거나 역동적인 회의실을 사용하고, 출석을 캡처하고, 퀴즈 결과를 가져오고, 학습자에게 세션 녹음을 제공할 수 있습니다.

## Adobe Connect 구성

Adobe Connect을 구성하려면 다음을 수행하십시오.

1. 통합 관리자로 Adobe Learning Manager에 로그인합니다.
2. **Adobe Connect** 타일 위로 마우스를 가져간 다음 **연결**&#x200B;을 선택합니다.

   ![](assets/adobe-connect-connector1.png)
   _연결을 선택하여 Adobe Connect 커넥터 구성_

3. 다음 세부 사항을 입력합니다.

   - **연결 이름**
   - **Adobe Connect URL**
   - **관리자 전자 메일 연결**
4. **연결 관리자 로그인 ID**&#x200B;을 입력합니다(Adobe Connect에 대한 전자 메일 로그인을 사용하지 않는 경우 필수).

   ![](assets/adobe-connect-connector2.png)
   _Adobe Connect 구성에 필요한 세부 정보 입력_

5. **연결 인증 사용**&#x200B;을 선택합니다.

   >[!NOTE]
   >
   >Adobe 호스팅 Connect 계정만 지원됩니다. (도메인은 .adobeconnect.com으로 끝나야 함)

6. **연결**&#x200B;을 선택합니다.

관리자 이메일 ID를 인증한 후:

- Adobe Learning Manager에 Connect가 통합되었음을 확인하는 성공 메시지가 표시됩니다.
- 요청이 승인을 위해 Adobe Connect 백엔드 팀으로 이동합니다. 이것은 보통 1~2일 걸립니다.

>[!IMPORTANT]
>
>Adobe Connect 계정 관리자는 처음 로그인할 때 사용 약관에 동의해야 합니다. 이 작업이 완료되지 않으면 로그인 인증이 실패할 수 있습니다.

## 가상 강의실 세션 정보 추가

작성자가 가상 강의실 강의에 대한 세션 세부 정보를 제공하지 않으면 책임자가 추가할 수 있습니다.

1. 책임자로 로그인합니다.
2. VC 강의를 선택합니다.
3. **인스턴스**&#x200B;를 선택한 다음 **세션 세부 정보**&#x200B;를 선택합니다.
4. **편집** 아이콘을 선택하여 세션 정보를 추가하거나 업데이트합니다.

>[!NOTE]
>
>Connect 계정에는 동시 사용자가 가상 클래스룸을 실행할 수 있는 충분한 회의실과 용량이 있어야 합니다. 지속 회의실을 사용하지 않는 한 각 Adobe Learning Manager 가상 강의실 세션은 자동으로 새 Connect 회의실을 생성합니다.

## 지속 회의실

Adobe Connect은 재사용할 수 있는 지속 회의실을 지원합니다.

- Connect에서 기존의 지속 회의실을 사용하여 가상 강의실 세션을 만들 수 있습니다.
- 또한 Adobe Learning Manager에서 대신 각 세션에 대해 동적 회의실을 만들도록 선택할 수 있습니다.

학습자가 Adobe Connect을 사용하여 세션에 참석하면 보안 인증을 사용하여 Learning Manager를 통해 회의실에 입장합니다.

세션 완료 후 학습자는 Learning Manager 앱에서 세션 기록 및 암호에 액세스할 수 있습니다.

## Adobe Connect에서 퀴즈 점수 가져오기

Adobe Learning Manager은 Adobe Connect 세션에서 퀴즈 데이터를 가져와 다른 보고 워크플로우와 결합할 수 있습니다. 여기에는 퀴즈 점수, 학습자 응답 및 완료 데이터(예: 자가 진행식 모듈 작동 방식)가 포함됩니다.

### 퀴즈 가져오기 워크플로우

#### Adobe Connect (호스트)

- Connect 호스트는 과정을 생성하고 대화형 퀴즈를 포함하는 콘텐츠를 업로드합니다.
- 호스트는 가상 교실(VC) 교육을 설정하고 과정을 VC에 연결하거나 **과정 공유** 옵션을 사용하여 세션 중에 공유합니다.

#### Adobe Learning Manager (작성자)

- 작성자는 모듈 유형이 **가상 교실**&#x200B;로 설정된 Adobe Learning Manager에서 과정을 만듭니다.
- **회의 시스템** 드롭다운에서 **연결**&#x200B;을 VC 공급자로 선택합니다.
- Connect에서 호스트가 만든 **지속 회의실**&#x200B;을 선택하십시오.
- 강사를 할당하고, 강의를 저장하고, 게시합니다.

#### Adobe Learning Manager (학습자)

- 학습자는 강의에 등록하고 Connect VC 세션에 참여합니다.
- 연결 호스트를 통해 학습자는 세션에 액세스할 수 있습니다.

### Adobe Connect(주최자 및 학습자)

- 호스트는 세션의 퀴즈를 공유합니다.
- 학습자가 퀴즈를 완료하고 세션을 종료합니다.

### Adobe Learning Manager (동기화 및 관리자)

- 세션이 종료되면 Adobe Learning Manager은 퀴즈 데이터를 자동으로 동기화합니다.
- 예약된 기간이 종료되면 퀴즈 가져오기 워크플로우가 시작됩니다.
- 통합 책임자는 진행률을 추적하기 위해 Adobe Connect 커넥터에서 **실행 상태**&#x200B;를 확인할 수 있습니다.
- 가져오기가 완료되면 상태가 **완료됨**(으)로 업데이트됩니다.

그러면 책임자는 가져온 결과를 검토할 수 있습니다.

- **출석 및 점수:** 최종 퀴즈 점수 및 출석을 봅니다.
- **L2 퀴즈 점수:**
   - **사용자별:** 개별 점수를 포인트 및 백분율로 표시합니다.
   - **질문별:** 보고서 차트에 퀴즈 결과를 표시합니다.
