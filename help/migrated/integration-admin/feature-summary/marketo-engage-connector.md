---
description: Marketo Engage 커넥터와 Adobe Learning Manager을 통합하는 방법 알아보기
jcr-language: en_us
title: Marketo Engage 커넥터
contentowner: mmanuel
source-git-commit: 8a5212062c6b172b0e9d4f3faa2e66d26c5c2b56
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 3%

---


# Adobe Learning Manager의 Marketo Engage 커넥터

## 소개

Marketo Engage 커넥터를 통해 Adobe Learning Manager은 마케팅 자동화 플랫폼인 Marketo Engage과 원활하게 통합할 수 있습니다. 이 통합은 마케팅 담당자들이 Adobe Learning Manager 데이터베이스와 동기화하여 Marketo의 학습자 동작 데이터를 추적하고 작업할 수 있도록 도와줍니다.

Marketo Engage 커넥터를 통해 두 시스템 간의 원활한 데이터 동기화가 가능하며 마케팅 담당자들이 학습 활동 데이터를 사용하여 타기팅된 마케팅 캠페인을 생성할 수 있습니다.

Marketo Engage 커넥터를 사용하여 다음을 수행할 수 있습니다.

- 사용자가 Adobe Learning Manager에 추가되면 Marketo Engage 데이터베이스에 잠재 고객을 자동으로 추가하거나 업데이트합니다.
- Marketo에서 강의 등록, 완료, 스킬 할당 및 스킬 완료와 같은 사용자 학습 동작을 사용자 정의 개체로 동기화합니다.
- **스마트 목록**&#x200B;과 같은 기능을 활용하여 이 데이터를 사용하여 Marketo에서 동적 캠페인을 만듭니다.

이 통합은 마케터들이 Adobe Learning Manager 내에서의 학습 여정을 기반으로 하여 대상자를 타겟팅하도록 도와줍니다.

## 주요 기능

- Adobe Learning Manager 사용자를 기반으로 자동화된 리드 생성 및 업데이트.
- 학습 활동(등록, 완료, 스킬 성과)을 사용자 정의 개체로 Marketo에 내보냅니다.
- 온디맨드로 내보내기를 예약하거나 트리거합니다.
- 통합 보고서 지원:
   - 사용자 보고서
   - 학습 성적 증명서
   - 사용자 스킬 보고서

## 사전 요구 사항

통합하기 전에 Marketo 계정이 API를 통한 스키마 생성을 지원하는지 확인합니다.

연결을 생성하려면 다음 세부 정보가 필요합니다.

- **연결 이름**
- **클라이언트 ID**
- **클라이언트 암호**
- **Marketo Engage 도메인**

>[!NOTE]
>
>**LaunchPoint**&#x200B;의 Marketo Engage 앱에서는 클라이언트 ID와 클라이언트 암호를, **웹 서비스** 섹션에서는 도메인을 가져올 수 있습니다.

## 커넥터 설정

Marketo Engage 커넥터를 설정하려면:

1. 통합 관리자로 Adobe Learning Manager에 로그인합니다.
2. **Marketo Engage** 타일 위로 마우스를 가져간 다음 **연결**&#x200B;을 선택합니다.

   ![](assets/marketo-engage-connector1.png)
   _연결을 선택하여 Marketo Engage 커넥터 구성_

3. 필요한 자격 증명 입력

   - 연결 이름
   - 클라이언트 ID
   - 클라이언트 시크릿
   - Marketo Engage 도메인

   ![](assets/marketo-engage-connector2.png)
   _Marketo Engage 커넥터에 필요한 세부 정보를 입력하십시오_

4. **연결**&#x200B;을 선택하여 연결을 설정합니다.

## 이벤트 및 캠페인 트리거

다음 이벤트에 따라 Marketo Engage으로 데이터 내보내기를 트리거할 수 있습니다.

- 새 사용자가 Adobe Learning Manager에 추가됩니다.
- 사용자가 강의에 등록되어 있습니다.
- 사용자가 강의를 완료합니다.
- 사용자가 스킬에 등록되어 있습니다.
- 사용자가 스킬을 완료합니다.

이러한 이벤트는 **요청 시** 또는 **예정된 단위로** 내보낼 수 있습니다.

## 열 매핑

Marketo은 다음 두 가지 데이터베이스를 사용합니다.

- **잠재 고객 데이터베이스** - 사용자 레코드(잠재 고객)
- **사용자 지정 개체 데이터베이스** - 사용자 지정 활동 및 이벤트 레코드용

Adobe Learning Manager과 Marketo 간에 필드를 매핑하는 방법:

1. Adobe Learning Manager의 **사용자 보고서** 필드가 한 열에 표시됩니다.
2. 해당 **Marketo 필드**&#x200B;가 인접한 열에 나열됩니다.
3. Learning Manager에서 Marketo으로 적절한 필드를 매핑하여 리드를 생성하고 업데이트합니다.
4. 매핑 후 내보낸 모든 사용자는 Marketo Lead 데이터베이스에 Lead 로 표시됩니다.

**Marketo 사용자 지정 개체** 섹션에 내보낸 보고서의 접두사는 &quot;cp_&quot;입니다.

## 지원되는 내보내기 이벤트

다음 사용자 관련 이벤트를 Marketo Engage 인스턴스로 내보낼 수 있습니다.

- 새 사용자 추가됨
- 사용자 메타데이터 업데이트됨
- 사용자 활동 업데이트됨
- 교육 등록
- 자가 등록
- 스킬 완료

이러한 내보내기는 학습 활동 데이터를 사용하여 참여를 촉진하고 아웃리치 캠페인을 개인화하는 데 도움이 됩니다.
