---
title: Adobe Learning Manager 관리 계정 수명 주기
description: 이 문서에서는 FedRAMP 규정 준수 및 모범 보안 사례를 충족하기 위해 Adobe Learning Manager(ALM)에서 최상위 관리 계정을 안전하게 관리하는 방법에 대한 포괄적인 지침을 제공합니다.
jcr-language: en-us
source-git-commit: db3ed4dc44da75b418e923999bdf3776bf81b11f
workflow-type: tm+mt
source-wordcount: '2122'
ht-degree: 0%

---


# Adobe Learning Manager의 관리 계정 유형

## ALM 역할 매핑

Adobe Learning Manager에서 최상위 관리 계정은 관리자 역할입니다. 이 가이드가 FedRAMP 용어 &#39;최상위 관리 계정&#39;을 사용할 때마다 참조되는 역할입니다. 사용자 정의 관리자와 통합 관리자는 권한(범위) 계정으로 처리됩니다.

아래 테이블은 FedRAMP 계정 계층을 Adobe Learning Manager에서 사용되는 특정 역할에 매핑하는 것입니다.

| FedRAMP 기간 | ALM 역할 이름 | 설명 |
|--------------------------------------|----------------------------|-------------|
| 최상위 관리 계정 | 책임자 | ALM에서 가장 높은 권한 역할. 사용자, 역할, 학습 콘텐츠, 보고, 통합 및 모든 시스템 구성에 대한 완전한 제어. FedRAMP 최상위 관리 계정 정의에 직접 매핑합니다. |
| 권한이 부여된 계정(범위) | 사용자 정의 관리자 | 특정 기능(예: 보고, 카탈로그 관리)으로 범위가 지정된 관리자 권한의 정의된 하위 집합입니다. 전체 계정 수준 컨트롤이 없습니다. |
| 권한 있는 계정(통합) | 통합 책임자 | ALM과 외부 시스템 간의 통합과 API 기반 액세스를 관리합니다. 상위 권한은 통합 관리에만 적용됩니다. |


Adobe Learning Manager은 RBAC(역할 기반 액세스 제어) 모델을 사용하여 관리 액세스를 관리합니다. 관리 역할은 권한 있는 관리자만 할당합니다.

자세한 내용은 [Adobe Learning Manager의 사용자 지정 역할](https://experienceleague.adobe.com/ko/docs/learning-manager/using/admin/custom-role)을 참조하세요.

## ID 유형 및 권장 인증

Adobe Admin Console은 관리자 계정에 대해 세 가지 id 유형을 지원합니다. ID 유형을 선택하면 다음과 같은 직접적인 보안 관련 사항이 있습니다.

| ID 유형 | 설명 | 보안 권장 사항 |
|---------------------------|-----------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| Adobe ID (개인 ID) | 기본 유형, Adobe 관리 누구나 만들 수 있습니다. | 관리자에게는 권장되지 않습니다. 조직이 이 계정 유형을 관리할 수 없습니다. |
| Enterprise ID | Admin Console 시스템 관리자가 관리하는 조직 소유 계정입니다. | Federated ID/SSO를 사용할 수 없는 경우 허용됩니다. 2FA를 적용합니다. |
| Federated ID (SSO) | 조직 소유, SAML 2.0 SSO와 통합 조직은 인증을 완전히 제어합니다. | 권장. 조직의 IdP를 통해 인증하며, ID 공급자 수준에서 MFA 적용을 지원합니다. |

자세한 내용은 다음을 참조하십시오.

* [ID 유형](https://helpx.adobe.com/kr/enterprise/using/admin-console.html)
* [사용자 인증 및 암호 보안](https://helpx.adobe.com/kr/enterprise/using/authentication-settings.html)

## 역할 할당 및 액세스 제어

Adobe Learning Manager의 관리 계정에 대한 액세스는 기존 관리자가 명시적으로 [역할 할당](https://experienceleague.adobe.com/ko/docs/learning-manager/using/admin/user-management/add-users-user-groups)을 통해 제어합니다. 보안 관리 액세스의 주요 특성은 다음과 같습니다.

* 관리 역할은 권한 있는 관리자만 할당합니다.
* 액세스는 역할에 기반하며 할당된 권한에 따라 범위가 정해집니다.
* 조직은 합법적인 비즈니스 요구 사항이 있는 사용자에 대한 관리 액세스를 제한할 책임이 있습니다.

Adobe은 고객이 최소 권한 원칙을 준수하도록 관리 액세스를 주기적으로 검토하는 것이 좋습니다.

## MFA(다중 인증) 적용

Adobe은 관리자가 조직 전체에 대해 2단계 인증(2FA)을 적용할 것을 강력히 권장합니다. MFA는 Enterprise ID 및 Adobe ID 사용자에게 적용됩니다. Federated ID 사용자는 조직의 ID 공급자에 MFA를 적용해야 합니다.

Adobe Admin Console에서 2FA를 적용하려면 다음을 수행하십시오.

1. Adobe Admin Console에 로그인
2. 설정 > 개인 정보 및 보안 > 인증 설정으로 이동합니다.
3. 2단계 인증을 활성화하고 적용 옵션을 선택하여 사용자가 비활성화하지 못하도록 합니다.
4. 필요에 따라 IP 기반 액세스 제한 및 고급 세션 설정(최대 세션 수명 / 최대 유휴 시간)을 구성합니다.

>[!IMPORTANT]
>
>Adobe은 2FA를 적용하고 사용자가 이를 선택적으로 사용할 수 없도록 권장합니다. 2FA는 신청까지 최대 24시간이 소요될 수 있다. Federated ID 사용자의 경우 ID 공급자에서 MFA를 적용합니다.

자세한 내용은 [자세한 내용은 사용자 인증 보안](https://helpx.adobe.com/kr/enterprise/using/authentication-settings.html)을 참조하세요.


## 관리자로 로그인

ALM [관리자](https://experienceleague.adobe.com/ko/docs/learning-manager/using/get-started/getting-started-admin)는 Admin Console을 통해 관리되는 조직 자격 증명을 사용하여 ALM 플랫폼에 직접 로그인합니다.

### 관리자 역할 할당

ALM 플랫폼 내에서 관리자는 역할을 생성 및 관리하고, 사용자에게 권한을 할당하고, 운영 권한에 따라 권한 범위를 정의하여 관리 액세스를 구성합니다.

ALM에서 관리자 역할을 할당하려면 다음을 수행합니다.

1. 기존 관리자로 Adobe Learning Manager에 로그인합니다.
2. 사용자 > 내부 로 이동합니다.
3. 대상 사용자를 검색하거나 선택합니다.
4. 작업 > 역할 할당 > 관리자 지정을 선택합니다.

사용자 정의 관리 역할을 통해 고객은 계정 수준 권한에 대한 중앙 집중식 제어를 유지하면서 관리 작업을 위임할 수 있습니다. 사용자 정의 관리자의 범위는 특정 사용자 그룹 또는 카탈로그로 지정할 수 있습니다.

자세한 내용은 [사용자 및 사용자 그룹 추가](https://experienceleague.adobe.com/ko/docs/learning-manager/using/admin/user-management/add-users-user-groups)를 참조하십시오.

## 로그인 방법 및 SSO 구성

ALM 관리자는 다음과 같은 중요한 보안 관련 구성인 설정 > 로그인 방법 을 통해 모든 사용자가 사용할 수 있는 로그인 방법을 제어합니다.

* **내부 사용자**: 로그인 모드를 Adobe ID 또는 SSO(Single Sign-On)로 설정합니다. SAML 2.0을 통한 SSO가 적극 권장됩니다.
* **외부 사용자**: 로그인 모드를 Adobe ID, SSO 또는 Learning Manager ID로 설정합니다. 선택한 방법을 조직의 보안 정책에 맞춥니다.

Adobe은 모든 내부 사용자를 위한 로그인 방법으로 Federated ID/SAML 2.0 SSO를 사용할 것을 권장합니다. 이렇게 하면 조직의 ID 공급자가 인증을 완전히 제어하여 중앙 집중식 MFA 강제 적용 및 사용자 이탈 시 즉시 계정 철회를 활성화할 수 있습니다.

자세한 내용은 [설정](https://experienceleague.adobe.com/ko/docs/learning-manager/using/admin/settings)을 참조하세요.

## 프로비전 시 권장 보안 기본값

ALM Adobe을 처음 프로비저닝할 때 관리 사용자에게 작동 액세스 권한을 부여하기 전에 다음 기본 설정을 확인하는 것이 좋습니다.

| 설정 | 권장 보안 기본값 | 구성 위치 |
|------------------------------|------------------------------------------------------------------|-------------------------------------------------|
| 로그인 방법 - 내부 사용자 | SSO(Single Sign-On)/Federated ID | ALM > 설정 > 로그인 방법 |
| 2단계 인증(2FA) | 강제 적용(사용자에 대해 선택 사항이 아님) | Admin Console > 설정 > 개인 정보 보호 및 보안 |
| 최대 세션 수명 | 8시간 또는 조직 정책당 | Admin Console > 설정 > 고급 설정 |
| 최대 유휴 시간 | 30분 또는 조직 정책당 | Admin Console > 설정 > 고급 설정 |
| 관리자 역할 범위 | 최소 권한. 가능한 경우 사용자 정의 관리자 역할 사용 | ALM > 사용자 > 사용자 정의 역할 |
| 외부 사용자 만료 | 모든 외부 사용자 프로필에 만료 날짜 설정 | ALM > 사용자 > 외부 |

### 신규 관리자를 위한 초기 설정 체크리스트

새 최상위 관리자 계정을 프로비전할 때 운영 액세스 권한을 부여하기 전에 다음을 완료하십시오.

* ID 유형이 개인 Adobe ID이 아닌 Enterprise ID 또는 Federated ID인지 확인합니다.
* Admin Console 수준에서 2FA를 적용합니다([설정] > [인증 설정]).
* 아직 활성화하지 않은 경우 SSO/Federated ID을 구성합니다.
* [Admin Console] > [설정] > [고급 설정]에서 [최대 세션 수명] 및 [최대 유휴 시간]을 설정합니다.
* 관리자 역할 범위 제한 - 사용자의 책임에 필요한 권한만 할당합니다.
* 관리자 계정이 IT 팀이 제어하는 조직 이메일 주소에 연결되어 있는지 확인합니다.
* 조직의 권한 있는 액세스 등록에 계정을 기록합니다.

## 관리 계정 운영

### 일상적인 관리 작업

관리 계정은 다음과 같은 일상적인 운영 작업을 수행하는 데 사용됩니다.

* **사용자 수명 주기 관리**: 사용자를 만들고, 프로필을 업데이트하고, 역할을 변경합니다.
* **학습 콘텐츠 관리**: 강의, 학습 프로그램, 인증 및 카탈로그 관리.
* **보고 및 분석**: 학습자 진행률 및 플랫폼 사용에 대한 보고서를 생성하고 검토합니다.
* **통합 및 시스템 구성**: 커넥터, API 기반 액세스 및 시스템 수준 설정을 관리합니다.

관리자는 관리 작업을 수행할 때 조직의 내부 액세스 제어 및 변경 관리 정책을 따라야 합니다.

[Adobe Learning Manager 관리자를 위한 자주 묻는 질문](https://experienceleague.adobe.com/ko/docs/learning-manager/using/faq/frequently-asked-questions-for-administrators)을 확인하십시오.


### 역할 계층 구조 및 위임

Adobe Admin Console은 계층적 관리자 구조를 사용합니다. 시스템 관리자는 권한을 하위 권한 역할에 위임하여 최상위 관리자 계정의 공격 표면을 줄일 수 있습니다.

* 제품 관리자: 특정 Adobe 제품(예: Adobe Learning Manager)에 대한 액세스를 관리합니다.
* 제품 프로필 관리자: 특정 제품 프로필의 사용자 멤버십을 관리합니다.
* 사용자 그룹 관리자: 사용자 그룹 멤버십을 관리합니다.
* ALM 사용자 정의 관리자: 카탈로그 및 사용자 그룹별로 구성 가능한 권한을 가진 ALM 내의 범위 관리자입니다.

### 지속적인 거버넌스 사례

계속해서 ALM 관리 계정을 운영하는 조직은 다음 사례를 따라야 합니다.

* **정기 액세스 검토**: Admin Console(사용자 > 관리자) 및 ALM 관리자(사용자 > 내부)의 시스템 관리자 목록을 정기적으로 감사하여 현재 권한 있는 직원만 이러한 역할을 수행하도록 합니다.
* **감사 로그 모니터링**: Admin Console 감사 로그는 관리자가 변경한 모든 내용을 기록합니다. 시스템 관리자는 전체 가시성을 제공합니다. 승인되지 않은 변경 사항에 대해서는 정기적으로 로그를 검토하십시오.
* **최소 대기 액세스**: 일상적인 작업에 최상위 관리자 계정을 사용하지 마세요. 특별히 필요한 작업에 대해 전체 관리자 액세스 권한을 예약합니다.
* **세션 보안**: Admin Console > 설정 > 고급 설정에서 최대 세션 수명 및 최대 유휴 시간을 구성하여 무인 세션의 노출을 제한합니다.

자세한 내용은 [Admin Console 개요](https://helpx.adobe.com/kr/enterprise/using/admin-console.html)를 참조하십시오.

### 관리자가 관리하는 사용자 계정 관리

ALM 관리자는 내부 및 외부 사용자 계정을 관리합니다. 보안 관련 작업에는 다음이 포함됩니다.

* 사용자 자동 삭제: 설정에서 관리자는 비활성 내부 사용자가 지정된 일수 후에 자동으로 삭제되도록 구성하여 휴면 계정 위험을 줄일 수 있습니다.
* 외부 사용자 만료: 관리자가 외부 사용자 프로필을 만들 때 만료 날짜를 설정합니다. 만료된 계정은 자동으로 비활성 상태로 이동합니다.
* 사용자 삭제: 관리자는 사용자 > 내부 > 작업 > 사용자 삭제를 통해 사용자를 수동으로 삭제할 수 있습니다.
* 사용자 삭제: 삭제 후 관리자는 데이터 보존 정책을 준수하고 오래된 사용자 데이터에 대한 무단 액세스를 방지하기 위해 사용자 레코드를 영구적으로 제거할 수 있습니다.

자세한 내용은 다음을 참조하십시오.

* [사용자 및 사용자 그룹 추가](https://experienceleague.adobe.com/ko/docs/learning-manager/using/admin/user-management/add-users-user-groups)
* [사용자 제거](https://experienceleague.adobe.com/ko/docs/learning-manager/using/admin/purge-users)

## 관리 계정 비관리

더 이상 필요하지 않은 경우에는 관리 액세스를 제거해야 합니다. 관리 계정 해제 시 포함할 수 있는 사항은 다음과 같습니다.

* 사용자로부터 관리 역할 취소.
* 더 이상 전체 관리 액세스 권한이 필요하지 않을 때 권한을 줄일 수 있습니다.
* 해당하는 경우 시스템에서 사용자를 제거합니다.

정기적인 검토와 불필요한 관리 액세스의 제거는 가장 낮은 권한 액세스 권한을 유지하는 데 도움이 됩니다.

### 시스템 관리자 권한 제거(Admin Console)

시스템 관리자가 조직을 떠나거나 역할을 변경하면 권한을 즉시 취소해야 합니다.

1. 시스템 관리자로 Adobe Admin Console에 로그인합니다.
2. 사용자 > 관리자 로 이동합니다.
3. 제거할 관리자를 선택합니다.
4. 기타 옵션(...) 아이콘 > 관리자 편집 을 클릭하고 시스템 관리자 역할을 제거하거나 — 또는 사용자 제거 를 선택하여 사용자를 조직에서 완전히 제거합니다.
5. 관리자가 다른 역할(제품 관리자, 지원 관리자 등)을 보유한 경우 해당 역할도 취소합니다.

>[!IMPORTANT]
>
>떠나는 관리자가 조직의 약정 소유자인 경우, 약정 소유자 역할을 다른 사람에게 이전해야 해당 역할을 제거할 수 있습니다. 필요한 경우 Adobe 지원 센터에 문의하십시오.

자세한 내용은 다음을 참조하십시오.

* [Admin Console에서 사용자 계정 생성, 업데이트 또는 제거](https://helpx.adobe.com/kr/enterprise/using/manage-users-individually.html)
* [조직 소유 계정을 탈퇴하는 방법](https://helpx.adobe.com/kr/enterprise/using/leave-organization.html)

### ALM 관리자 역할 제거

사용자의 계정을 삭제하지 않고 ALM 관리자 액세스 권한을 해지하려면(예: 사용자가 학습자로 유지된 경우):

1. 관리자로 Adobe Learning Manager에 로그인합니다.
2. 사용자 > 내부 로 이동합니다.
3. 사용자를 검색하여 선택합니다.
4. 작업 > 역할 제거 > 관리자 제거를 선택합니다.

사용자가 학습자 역할로 돌아갑니다. 학습 기록 및 강의 등록이 유지됩니다.

자세한 내용은 [사용자 및 사용자 그룹 추가](https://experienceleague.adobe.com/ko/docs/learning-manager/using/admin/user-management/add-users-user-groups)를 참조하십시오.

### 사용자 삭제 및 제거

사용자가 조직을 완전히 종료하고 플랫폼에서 해당 계정을 제거해야 하는 경우:

* 사용자 삭제: 사용자 > 내부 > 사용자 선택 > 작업 > 사용자 삭제. 이렇게 하면 계정이 비활성화되고 활성 액세스가 제거됩니다.
* 사용자 제거: 삭제 후 사용자 > 사용자 정리로 이동하여 삭제 월을 선택하고 사용자를 선택한 다음 작업 > 사용자 제거를 선택합니다. 지우면 모든 사용자 레코드가 영구적으로 제거됩니다.

자세한 내용은 [사용자 제거](https://experienceleague.adobe.com/ko/docs/learning-manager/using/admin/purge-users)를 참조하십시오.


## 보안 및 공동 책임

Adobe Learning Manager은 다음과 같은 공유 책임 모델로 작동합니다.

* Adobe은 기본 ALM 플랫폼 및 인프라를 보호하는 역할을 합니다.
* 고객은 ALM 계정 내에서 관리 액세스, 역할 할당 및 사용자 수명 주기 활동을 관리할 책임이 있습니다.

Adobe Learning Manager 보안 지침에 대한 추가 정보는 [Adobe Learning Manager 보안 개요(PDF)](https://experienceleague.adobe.com/docs/learning-manager/assets/alm-security-whitepaper-2024.pdf?lang=ko)에서 확인할 수 있습니다.

## 문서 유지 관리

이 문서는 Adobe Learning Manager 기능 또는 관리 모범 사례의 변경 사항을 반영하도록 주기적으로 업데이트될 수 있습니다. 버전 및 마지막으로 업데이트된 날짜는 문서 메타데이터 및 FedRAMP 인증 패키지에서 유지됩니다. 고객은 Adobe Experience League에서 공개적으로 사용 가능한 버전을 참조하여 최신 지침을 사용하고 있는지 확인해야 합니다.

## 향상된 보안 기능 적용 범위

### SCG-ENH-CMP

Adobe은 문서화된 구성 요소 인벤토리, 소유권 및 수명 주기 관리 프로세스를 유지 관리하여 시스템 구성 요소 전반에서 구성 및 규정 준수를 제어합니다.

### SCG-ENH-API

Adobe은 문서화된 거버넌스 및 플랫폼 보호 장치에서 지원하는 인증, 권한 부여 및 모니터링을 포함한 표준화된 API 보안 제어를 적용합니다.

### SCG-ENH-MRG

Adobe은 시스템 무결성을 유지하고 배포 위험을 줄이기 위해 검토 및 승인 제어를 포함한 공식적인 변경 및 병합 관리 프로세스를 적용합니다.

### SCG-ENH-VRH

Adobe은 식별, 우선 순위 지정, 추적 및 적시 해결을 포함하는 정의된 취약성 관리 및 수정 프로세스를 따릅니다.
