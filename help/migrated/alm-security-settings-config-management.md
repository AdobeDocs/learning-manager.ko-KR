---
title: Adobe Learning Manager- 보안 설정 및 구성 관리
description: 이 문서에서는 Adobe Learning Manager 관리 계정 유형, 보안 관련 설정, 권장 보안 기본값, API 기능, 내보내기 기능, 구성 비교 방법, 게시 방법 및 버전 내역에 대해 설명합니다. 특권 계정의 작동 방식, 보안 관련 사항, 플랫폼 전체에서 구성 관리가 지원되는 방식에 대한 자세한 지침을 제공합니다.
jcr-language: en-us
source-git-commit: 579573cbc1baaea2ac8e6ebf17f32c46624ea798
workflow-type: tm+mt
source-wordcount: '1940'
ht-degree: 0%

---


# 소개

이 안내서에서는 Adobe Learning Manager(ALM)에 대한 FedRAMP 권장 사항(FRL-RSC-03 ~ FRL-RSC-08)에 대한 자세한 응답을 제공합니다. 보안 모범 사례, 권장 보안 기본값 및 권한 계정 설정 감사, 내보내기 및 관리를 위한 도구에 대해 간략히 설명합니다. 이 문서는 관리자 및 규정 준수 팀이 ALM 계정을 안전하게 구성하고 관리할 수 있도록 설계되었습니다.

또한 Adobe Experience League에서 사용할 수 있는 지원 문서 및 리소스에 대한 참조를 사용하여 ALM이 FedRAMP 표준을 충족하거나 부분적으로 충족하는 영역을 강조합니다.

+++Adobe Learning Manager에서 사용자 정의 관리자 또는 통합 관리자만 운영할 수 있는 보안 관련 설정은 무엇이며 보안상 어떤 영향을 미칩니까?

Adobe Learning Manager의 두 가지 권한 계정 유형(사용자 정의 관리자 및 통합 관리자)입니다. 각 폴더에는 문서화된 함의를 지닌 정의된 보안 관련 설정 세트가 있습니다.

**사용자 지정 관리자 - 수행할 수 있는 작업**:

* 사용자 정의 역할은 ALM 관리자 > 사용자 > 사용자 정의 역할에서 전체 관리자가 구성합니다. 사용자 정의 책임자에게는 계정 권한(공지, 게임화, 스킬, 사용자 관리), 기능 권한(카탈로그, 보고서, 태그) 및 학습 객체 권한(강의, 인증, 학습 경로) 중 하나 이상에 대한 액세스 권한을 부여할 수 있습니다.
* 범위는 가장 보안에 민감한 설정입니다. 사용자 정의 역할은 특정 사용자 그룹 및/또는 특정 카탈로그로 제한할 수 있습니다. 범위 제한 없이, 사용자 정의 역할은 전체 책임자가 사용할 수 있는 공간에 가깝게 해당 역할의 부여된 기능에 대한 플랫폼 전체 액세스를 효과적으로 제공합니다.
* 계정 권한에서 사용자 정의 롤에 설정 액세스 권한이 부여된 경우 해당 사용자 정의 관리자는 로그인 방법, 알림 설정 및 계정 수준 구성을 수정할 수 있습니다. 이는 명시적인 비즈니스 근거로만 부여되어야 하는 매우 영향력 있는 권한입니다.

**통합 관리자 — 관리자가 수행할 수 있는 작업**:

* 통합 책임자는 통합 책임자 > 응용 프로그램 > 등록에서 OAuth 2.0 응용 프로그램 등록을 관리합니다. 학습자 읽기 액세스에서 관리자 역할 읽기/쓰기 액세스에 이르기까지 6개의 OAuth 범위 중 하나를 선택합니다. 관리자 읽기/쓰기 범위는 등록된 응용 프로그램에 API를 통해 전체 관리자와 동일한 권한을 부여합니다.
* 통합 책임자는 사용자 레코드, 역할 할당 및 강의 완료를 가져오고 플랫폼 데이터를 외부 시스템으로 내보내는 FTP, SFTP, Salesforce, Workday 및 기타 커넥터를 구성합니다.
* 통합 관리자는 실시간 ALM 이벤트 데이터(등록, 완료, 역할 변경)를 외부 URL로 푸시하는 Webhook을 구성합니다. Webhook 엔드포인트가 손상되거나 잘못 구성된 경우 데이터 유출 위험이 있습니다.
* 통합 책임자는 LTI 통합을 구성할 수 있습니다. 일단 활성화되면 LTI를 비활성화할 수 없습니다.

**참조**:

* [사용자 정의 역할 | Adobe Learning Manager](https://experienceleague.adobe.com/en/docs/learning-manager/using/admin/custom-role)
* [CSV를 통해 사용자 정의 역할 관리 | Adobe Learning Manager](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/configure-role-csv-files)
* [응용 프로그램 개발자 설명서 | Adobe Learning Manager][https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/developer-manual]
* [Adobe Learning Manager 커넥터](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/connectors)

+++

+++Adobe Learning Manager의 최상위 관리 및 권한 계정에 권장되는 보안 기본값은 무엇이며 어디에 구성됩니까?

Adobe Learning Manager 문서에서는 관리자 역할과 권한 있는 계정 유형 모두에 대해 권장되는 특정 보안 기본값을 제공합니다.

* **최상위 관리자 계정 기본값(첫 번째 프로비전 시 구성)**:

* 내부 사용자의 로그인 방법: SAML 2.0을 통한 SSO(Single Sign-On): ALM 관리자 > 설정 > 로그인 방법에서 구성됩니다. 직원 또는 관리자용으로 Adobe ID을 사용하지 마십시오.
* 2단계 인증(2FA): 모든 사용자에 대해 적용됨: Adobe Admin Console > 설정 > 개인 정보 및 보안 > 인증 설정에서 구성됨.
* 최대 세션 수명: 8시간(또는 조직별 정책): Adobe Admin Console > 설정 > 개인 정보 및 보안 > 고급 설정에서 구성합니다.
* 최대 유휴 시간: 30분(또는 조직당 정책): 위와 같은 위치입니다.
* 비활성 사용자 자동 삭제: 조직에서 정의한 보존 기간(예: 90일 동안 사용하지 않음)으로 활성화됩니다. ALM 관리자 > 설정 > 일반.
* 외부 사용자 프로필 만료: 만들 때 모든 외부 프로필에 설정: ALM 관리자 > 사용자 > 외부 무제한 외부 프로필이 없습니다.
* IP 액세스 제한: 가능한 경우 승인된 IP 범위로 제한합니다. Admin Console > 설정 > 고급 설정.

**사용자 지정 관리자 역할 기본값(각 역할을 만들 때 구성됨)**:

* 등록된 응용 프로그램에 대한 OAuth 범위: 최소 필수 범위입니다. 꼭 필요한 경우가 아니면 관리자 역할의 읽기/쓰기 액세스 권한을 부여하지 마십시오.
* 사용자 정의 역할 범위: 특정 사용자 그룹 및 특정 카탈로그로 제한합니다. 함수에서 진정으로 필요한 경우가 아니면 모든 사용자 및 모든 카탈로그 범위로 사용자 정의 역할을 만들지 마십시오.
* 사용자 정의 역할에서의 설정 액세스: 권한 에스컬레이션 위험이 있는 경우 특정 기능에 필요한 경우가 아니면 부여하지 마십시오.

**통합 관리자 기본값**:

* API OAuth 범위: 통합 요구 사항을 충족하는 가장 제한적인 범위를 선택합니다. 학습자 읽기 액세스만 필요한 응용 프로그램에 책임자에게 읽기/쓰기 권한을 부여하지 마십시오.
* 커넥터 자격 증명, LTI 자격 증명 및 Webhook URL: 중요한 암호로 취급 - 이메일을 통해 공유하거나 소스 제어에 커밋하지 마십시오.

**참조**:

* [설정 | Adobe Learning Manager](https://experienceleague.adobe.com/en/docs/learning-manager/using/admin/custom-role)
* [사용자 인증 및 암호 보안 | Adobe Admin Console](https://helpx.adobe.com/enterprise/using/authentication-settings.html)
* [사용자 정의 역할 | Adobe Learning Manager](https://experienceleague.adobe.com/en/docs/learning-manager/using/admin/custom-role)

+++

+++Adobe Learning Manager에서 관리자가 현재 계정 설정을 권장 보안 기본값과 비교할 수 있는 방법을 제공합니까?

Adobe Learning Manager에는 현재 설정을 권장 보안 기본값과 함께 자동으로 표시하는 전용 비교 대시보드가 없습니다.

**사용자 지정 역할 보고서: 현재 권한 있는 역할 할당**:

* ALM에서 관리자 > 사용자 > 사용자 정의 역할로 이동한 다음 다운로드(오른쪽 위)를 클릭하여 모든 사용자 정의 역할, 권한 세트 및 범위 할당의 CSV를 내보냅니다.
* 이 내보내기를 FRR-RSC-02 섹션 8의 권장 기본값과 비교합니다. 특히 사용자 정의 역할에 문서화된 근거 없이 설정 액세스, 모든 사용자 범위 또는 모든 카탈로그 범위가 있는지 확인합니다.

**ALM REST API: 프로그래밍 구성 검색**:

* GET /계정 끝점은 계정 수준 구성 데이터를 JSON 형식으로 반환하며, 관리자 역할 OAuth 범위를 사용하여 액세스할 수 있습니다. 고객은 이 끝점을 프로그래밍 방식으로 호출하고 FRL-RSC-02 섹션 8에서 권장되는 기본값에서 파생된 기준에 대한 응답을 차등화할 수 있습니다.
* GET /사용자 끝점(with include=role filter)은 모든 사용자에 대한 현재 역할 할당을 반환하여 예기치 않은 역할 할당을 자동으로 감지합니다.

>[!NOTE]
>
>Adobe Learning Manager에서는 기본 나란히 비교 UI를 제공하지 않습니다. 자동 구성 규정 준수 확인이 필요한 고객은 ALM REST API를 기존 툴링과 통합해야 합니다.

**참조**

* [응용 프로그램 개발자 설명서 | Adobe Learning Manager](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/developer-manual)

+++

+++관리자가 Adobe Learning Manager의 현재 보안 관련 설정 및 구성을 기계가 읽을 수 있는 형식으로 내보낼 수 있습니까?

Adobe Learning Manager은 여러 메커니즘을 통해 보안 관련 구성 데이터 내보내기를 지원합니다. 단일 내보내기는 모든 보안 설정의 전체 스냅샷을 한 번에 생성하지 않지만 다음 내보내기는 보안 관련 데이터의 전체 범위를 포괄합니다.

**ALM REST API: 현재 역할 할당 및 계정 구성의 JSON 내보내기**:

* GET /account: 활성 로그인 구성 데이터 및 계정 메타데이터를 포함하여 JSON의 계정 수준 설정을 반환합니다.
* GET /users?include=role: JSON에서 현재 할당된 역할이 있는 모든 사용자를 반환합니다.
* GET /userGroups — 사용자 정의 역할 범위 감사와 관련된 모든 사용자 그룹 및 해당 멤버 자격을 반환합니다.
* 모든 API 응답은 JSON(vnd.api+json)입니다. 인증에서는 관리자 역할 읽기/쓰기 범위의 OAuth 2.0을 사용합니다.

**사용자 지정 역할 CSV 내보내기: 현재 권한 있는 역할 정의**:

* ALM 관리자 > 사용자 > 사용자 정의 역할 > 다운로드 는 모든 사용자 정의 역할 정의, 권한 범주 및 범위 할당의 CSV를 내보냅니다.
* 이 내보내기는 현재 권한 있는 계정 구성의 시스템 읽기 가능 스냅숏으로 사용할 수 있습니다.
**

**작업 API: 대량 사용자 및 역할 데이터**:

* ALM 작업 API는 CSV 형식으로 사용자 보고서(역할 할당 포함)의 온디맨드 생성을 지원합니다. 이는 외부 규정 준수 또는 SIEM 도구에 의해 예약 및 소비될 수 있습니다.

**참조**

* [응용 프로그램 개발자 설명서 | Adobe Learning Manager](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/developer-manual)

+++

+++Adobe Learning Manager에서 보안 관련 설정을 프로그래밍 방식으로 보고 조정할 수 있는 API를 제공합니까?

Adobe Learning Manager은 OAuth 2.0 인증을 사용하여 보안 관련 설정을 프로그래밍 방식으로 보고 조정할 수 있는 전체 REST API v2를 제공합니다. 다음은 보안 설정과 관련된 특정 API 기능입니다.

**인증 및 범위**:

* 응용 프로그램은 통합 책임자 > 응용 프로그램 > 등록에서 통합 책임자가 등록합니다. 애플리케이션별로 OAuth 2.0 클라이언트 ID 및 암호가 발급됩니다.
* 6개의 범위가 있습니다. 보안 설정 관리를 위해 관리자 역할 읽기/쓰기 액세스 권한이 필요합니다. 이렇게 하면 애플리케이션에 API를 통해 전체 관리자와 동일한 액세스 권한이 부여됩니다.
* 액세스 토큰은 표준 OAuth 인증 코드 또는 클라이언트 자격 증명 플로우를 통해 획득됩니다. 기본 URL: https://learningmanager.adobe.com/primeapi/v2/

**API를 통한 사용자 및 역할 관리**:

* GET /users: 모든 사용자 및 해당 현재 역할을 검색합니다.
* POST /users: 프로그래밍 방식으로 새 사용자를 프로비저닝합니다.
* PATCH /users/{id}: 역할 할당을 포함한 사용자 특성 업데이트
* DELETE /users/{id}: 사용자 계정 사용 안 함
* POST /users/{id}/제거: 사용자 및 모든 관련 레코드를 영구적으로 제거

계정 구성 검색:

* GET /account: complianceLabelDefaultID, showComplianceLabel 및 custom_insertions와 같은 필드를 포함하여 계정 설정 데이터를 JSON 형식으로 포함하는 계정 수준 구성을 반환합니다.

+++

+++Adobe Learning Manager은 보안 구성 지침을 OSCAL, JSON 또는 YAML과 같이 컴퓨터가 읽을 수 있는 형식으로 게시합니까?

Adobe Learning Manager은 현재 컴퓨터 판독 가능 형식으로 보안 구성 안내서를 게시하지 않습니다. [FRR-RSC-01](/help/migrated/alm-administrative-lifecycle.md) 및 [FRR-RSC-02](/help/migrated/alm-secure-administration-guide.md)의 지침은 HTML 및 다운로드 가능한 문서 형식으로 Adobe Experience League에 사람이 읽을 수 있는 설명서로 게시됩니다.

Adobe Learning Manager에 권장되는 보안 기본값을 인코딩하는 공개적으로 사용 가능한 OSCAL 구성 요소 정의, YAML 기준선 또는 JSON 정책 파일이 없습니다.

권장 기준 요소와 현재 설정을 자동으로 비교해야 하는 고객은 [ALM REST API](https://experienceleague.adobe.com/en/docs/learning-manager/using/integration/developer-manual)를 사용하여 현재 구성 데이터를 JSON 형식으로 검색해야 합니다.

+++

+++로그인 또는 특별 액세스 권한 없이 Adobe Learning Manager 보안 구성 안내서를 공개적으로 사용할 수 있습니까?

**공개적으로 사용 가능한 항목**:

* [FRR-RSC-01: 보안 관리 안내서](/help/migrated/alm-administrative-lifecycle.md): 최상위 관리 계정에 대한 전체 수명 주기 지침입니다.
* [FRR-RSC-02: 관리 보안 설정 및 의미](/help/migrated/alm-secure-administration-guide.md): 모든 보안 관련 설정, 의미 및 권장 기본값.
* FRR-RSC-03-10 (이 문서) — 8개의 FedRAMP SHOULD 권장 사항에 대한 Q&amp;A 응답

+++

+++Adobe Learning Manager에서 버전 관리 및 릴리스 내역을 제공하므로 기관에서 보안 관련 설정 및 권장 기본값에 대한 변경 내용을 시간별로 추적할 수 있습니까?

Adobe Learning Manager에서는 모든 제품 업데이트에 대해 공개적으로 사용 가능한 세부 릴리스 내역을 유지 관리합니다. 관리 설정, 인증 기능, API 끝점 및 역할 관리 기능에 대한 보안 관련 변경 사항은 각 릴리스에 설명되어 있습니다.

**ALM 릴리스 정보: 번호 매기기, 누적 변경 기록**:

* Adobe은 모든 Adobe Learning Manager 업데이트(예: 업데이트 100, 업데이트 99)에 대해 번호가 매겨진 릴리스 노트를 게시합니다. 이러한 기능은 Experience League 및 문서에 게시되고 모든 새로운 기능, 기존 설정 변경, API 추가 및 제거, 커넥터 변경 및 더 이상 사용되지 않는 기능을 문서화합니다.
* 각 릴리스 정보에는 API 변경 사항에 대한 전용 섹션이 포함되어 있으며, 보안 관련 구성 기능과 직접 관련된 새로운 끝점, 수정된 응답 필드 및 사용 중단 정보를 나열합니다.

**새로운 기능 페이지: 릴리스별 기능 요약**:

* 각 주요 릴리스에는 컨텍스트가 포함된 새로운 보안 관련 기능을 문서화하는 전용 &#39;새로운 기능&#39; 페이지가 있습니다. 예를 들어 릴리스 정보에는 사용자 정의 역할 권한 처리에 대한 변경 사항, 사용자 정의 역할에 대해 CSV로 생성된 권한 가시성 추가, 변경 사항을 제한하는 API 속도 제한 등이 포함됩니다.

**API 사용 중단 목록: 제거된 API 기능의 신뢰할 수 있는 레코드**:

* Adobe은 사용되지 않고 제거된 모든 ALM API 엔드포인트와 각각의 사용 중단 버전이 나열된 전용 API 사용 중단 페이지를 유지합니다.

**참조**:

* [Adobe Learning Manager 릴리스 정보](https://experienceleague.adobe.com/en/docs/learning-manager/using/introduction/release-notes)
* [Adobe Learning Manager의 새로운 기능](https://experienceleague.adobe.com/en/docs/learning-manager/using/introduction/whats-new-july-2024)
* [Adobe Learning Manager에서 API 사용 중단](https://experienceleague.adobe.com/en/docs/learning-manager/using/introduction/api-deprecations-list)

+++

