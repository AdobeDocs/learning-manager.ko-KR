---
description: Zoom 커넥터와 Adobe Learning Manager을 통합하는 방법 알아보기
jcr-language: en_us
title: Zoom 커넥터
contentowner: mmanuel
product_v2:
  - id: ed12e5b7-96e3-45e7-a17f-de222065ebcb
    internal-label: Learning Manager
source-git-commit: 3628dd3701949da127b138e0e1ffc2db8e84eab1
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 2%
---

# Adobe Learning Manager의 Zoom 커넥터

## 소개

Adobe Learning Manager의 Zoom 커넥터를 사용하여 조직은 라이브 가상 강의실 세션을 제공하고, 학습자 등록을 관리하고, 출석과 완료를 추적할 수 있습니다. 또한 단일 계정 내에서 여러 Zoom 연결을 지원하여 통합 책임자가 역할이나 사용자 그룹을 기반으로 액세스를 관리하고 작성자가 강의 세션에 사용 가능한 연결을 선택할 수 있도록 합니다. 세션 후 출석 및 성과 데이터는 보고 및 추적을 위해 Adobe Learning Manager에 다시 동기화됩니다.

## Zoom 커넥터 설정

Zoom 커넥터를 구성하려면:

1. 통합 관리자로 Adobe Learning Manager에 로그인합니다.
2. **확대/축소** 타일 위로 마우스를 가져갑니다.

   ![](assets/zoom-connector1.png)
   _Adobe Learning Manager에서 Zoom 커넥터 구성_

3. **연결**&#x200B;을 선택합니다. Zoom 커넥터 설정 페이지가 열립니다.
4. 각 필드에 다음 계정 세부 정보를 입력합니다. Zoom 계정 관리자로부터 다음 자격 증명을 얻을 수 있습니다.

   * 연결 이름
   * Zoom 계정 ID
   * 클라이언트 ID
   * 클라이언트 시크릿
   * 최고 관리자 이메일 주소
   * 이 커넥터를 사용할 수 있는 역할 또는 그룹(선택 사항)

   ![](assets/zoom-connector2.png)
   _Zoom 커넥터를 설정하려면 구성 세부 정보를 입력하십시오_

5. **연결**&#x200B;을 선택하여 통합을 설정합니다.

>[!NOTE]
>
>커넥터를 활성화할 때 **학습자는 Zoom 계정과 Adobe Learning Manager 계정 모두에 대해 동일한 전자 메일 주소**&#x200B;를 사용하여 사용자 데이터가 올바르게 동기화되도록 해야 합니다.

## 여러 확대/축소 연결 추가

각 연결이 다른 Zoom 계정에 연결되어 있는 여러 Zoom 연결을 Adobe Learning Manager에 추가할 수 있습니다. 예를 들어, 서로 다른 파트너 또는 팀에 대해 별도의 연결을 생성하고 각 연결을 사용할 수 있는 역할 또는 사용자 그룹을 지정할 수 있습니다.

추가할 수 있는 연결 수는 Adobe Learning Manager 계정 계층에 따라 다릅니다.

| **계정 계층** | **최대 확대/축소 연결** |
|---|---|
| Prime | 6 |
| Ultimate | 50 |

## 확대/축소 과정 만들기

연결이 설정되면:

1. **작성자**(으)로 로그인하여 새 가상 강의실 강의를 만드십시오.
2. 회의 시스템으로 **확대/축소**&#x200B;를 선택한 다음 목록에서 사용할 Zoom 연결을 선택하십시오.
   >[!NOTE]
   >
   >목록에는 역할이나 사용자 그룹에 사용할 수 있는 연결만 표시되며 세션은 한 번에 하나의 연결을 사용합니다.
3. 책임자, 관리자 또는 자가 등록을 통해 강의에 학습자를 할당합니다.
4. 등록 시 학습자는 강의 세부 정보가 포함된 이메일을 수신하게 됩니다.
5. 학습자는 Adobe Learning Manager 계정에 로그인하여 강의에 액세스하고 Zoom 세션에 참여할 수 있습니다.

## 작성자가 사용할 수 있는 확대/축소 연결

강의 세션을 생성하거나 편집할 때 역할이나 사용자 그룹에 사용할 수 있는 Zoom 연결에서 선택할 수 있습니다. 통합 책임자는 각 Zoom 연결에 액세스할 수 있는 역할 또는 사용자 그룹을 정의합니다.

예를 들어 통합 관리자가 두 개의 확대/축소 연결(**파트너 A 확대/축소** 및 **파트너 B 확대/축소**)을 구성하고 각 연결을 다른 사용자 그룹에 할당한다고 가정해 보겠습니다.

* Partner A 와 Partner B 그룹 모두에 속하는 경우, 두 가지 연결 중 하나를 선택할 수 있습니다.
* 파트너 A 그룹에만 속하는 경우 **파트너 A 확대/축소**&#x200B;를 선택할 수 있습니다.
* 어느 그룹에도 속하지 않으면 이러한 연결을 선택할 수 없습니다.

>[!NOTE]
>
>세션에는 하나의 Zoom 연결만 사용할 수 있습니다. 여러 연결을 사용할 수 있는 경우 세션에 사용할 연결을 선택합니다.

## 확대/축소 연결 관리

**연결 관리** 페이지에 계정에 대해 구성된 확대/축소 연결이 표시됩니다. **표시 대상** 열은 각 연결을 사용할 수 있는 역할 또는 사용자 그룹을 나타냅니다. 이 페이지에서 기존 Zoom 연결을 편집, 활성화 또는 비활성화 및 삭제할 수 있습니다.

![연결, 자격 증명 및 역할 또는 그룹 설정 사용이 포함된 확대/축소 연결 구성 페이지](assets/zoom-connection-configure-page.png "연결, 자격 증명 및 역할 또는 그룹 설정 사용이 포함된 확대/축소 연결 구성 페이지")

### Zoom 연결 편집

기존 확대/축소 연결을 편집하려면 다음을 수행합니다.

1. 편집할 **연결 관리** 페이지에서 연결을 선택하십시오.
1. 구성 탭에서 다음 중 하나를 업데이트합니다.

   1. Zoom 계정 자격 증명을 업데이트하려면 **자격 증명** 옆의 **편집**&#x200B;을 선택하고 필요한 세부 정보를 업데이트하십시오.
   1. 연결을 사용할 수 있는 사용자를 변경하려면 이 커넥터를 사용할 수 있는 **역할 또는 그룹**&#x200B;을 업데이트하십시오.

1. **저장**&#x200B;을 선택합니다.

### Zoom 연결 활성화 또는 비활성화

새 확대/축소 연결은 기본적으로 활성화되어 있습니다. 연결을 비활성화하여 작성자가 연결을 삭제하지 않고 사용하지 못하도록 할 수 있습니다.

연결을 비활성화하려면 다음을 수행하십시오.

1. **연결 관리** 페이지에서 비활성화할 연결을 선택합니다.
1. **연결 사용**&#x200B;을 켭니다.
1. **저장**&#x200B;을 선택합니다.

   연결된 역할 또는 그룹의 사용자는 더 이상 비활성화된 연결을 사용할 수 없습니다.

연결을 다시 사용하도록 설정하려면 **연결 사용**&#x200B;을 선택한 다음 **저장**&#x200B;을 선택하십시오.

### Zoom 연결 삭제

Zoom 연결을 삭제하려면

1. **연결 관리** 페이지에서 삭제할 연결로 이동합니다.
1. 연결 옆의 **삭제** 아이콘을 선택합니다.
1. **삭제**&#x200B;를 선택합니다.

## 출석 및 완료 추적

가상 세션이 종료된 후:

* Adobe Learning Manager은 Zoom에서 완료 상태를 자동으로 수신합니다.
* 책임자는 Adobe Learning Manager에서 출석 및 점수 보고서를 보고 학습자의 참여와 성과를 추적할 수 있습니다.

## Zoom 서버 간 OAuth 앱 만들기

Adobe Learning Manager에서 Zoom 커넥터를 사용하려면 Zoom 서버-서버 OAuth 앱을 만들고 필요한 범위를 구성해야 합니다.

### 필수 OAuth 범위

확대/축소에서 응용 프로그램을 만들 때 다음 범위가 선택되어 있는지 확인하십시오.

| 원하는 기능 | 이 키워드 검색 | 그런 다음 선택 |
|---|---|---|
| 모든 사용자 모임 보기 | 회의 | `meeting:read:meeting:admin, meeting:read:list_meetings:admin` |
| 모든 사용자 회의 보기/관리 | 회의 | `meeting:update:meeting:admin, meeting:delete:meeting:admin, meeting:write:meeting:admin` |
| 보고서 데이터 보기 | 보고서 | `report:read:meeting:admin, report:read:user:admin`(끝점과 일치하는 항목을 선택하십시오.) |
| 모든 사용자 정보 보기 | 사용자 | `user:read:user:admin, user:read:list_users:admin` |
| 사용자 관리 | 사용자 | `user:update:user:admin, user:write:user:admin` |
| 모임 등록자 추가 | 등록자 | `meeting:write:registrant:admin` |
| 모든 모임 등록자 나열 | 등록자 | `meeting:read:list_registrants:admin` |
| 하위 거래처 회의 | 모임 + :master 찾기 | `meeting:write:meeting:master` |
| 모임 참가자 보고서 | 참가자 | `report:read:list_meeting_participants:admin` |

