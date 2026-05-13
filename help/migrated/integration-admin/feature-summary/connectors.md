---
description: 각 ALM 지원 커넥터에 대한 개요
jcr-language: en_us
title: ALM 지원 커넥터의 개요
contentowner: mmanuel
source-git-commit: fc9bf565de2f9491c793654645d2f2400ca49697
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 6%

---


# Adobe Learning Manager 커넥터

## 소개

Adobe Learning Manager(ALM)은 타사 애플리케이션 및 엔터프라이즈 시스템과의 원활한 통합을 가능하게 하는 포괄적인 커넥터 제품군을 제공합니다. 이러한 커넥터는 학습 관리 시스템과 외부 플랫폼 간의 다리 역할을 하며 자동화된 데이터 동기화, 사용자 관리, 콘텐츠 가져오기 및 학습 기록 내보내기를 용이하게 합니다.

이 문서는 조직의 학습 에코시스템에 적합한 커넥터를 이해하고 선택하는 전체 참조 안내서의 역할을 합니다. HR 시스템, 전자상거래 플랫폼, 가상 회의 도구 또는 비즈니스 인텔리전스 솔루션과 통합하려는 경우

Adobe Learning Manager에서 지원하는 전체 커넥터 목록은 왼쪽 목차에서 이 문서 바로 아래에 중첩된 커넥터 도움말을 참조하십시오.

>[!NOTE]
>
>이 기능은 FedRAMP 인증 환경에서 부분적으로 사용할 수 있습니다. 자세한 내용은 [FedRAMP 환경의 기능 가용성](/help/migrated/feature-availability-in-fedramp-authorized-environment.md)을 참조하세요.

>[!NOTE]
>
>Adobe Learning Manager의 2022년 11월 릴리스를 통해 Zoom은 2023년 6월까지 [JWT 인증](https://developers.zoom.us/docs/internal-apps/s2s-oauth/)을 중단합니다. 따라서 JWT가 지원되는 Zoom 커넥터는 언급한 날짜까지 작동하지만 사용자가 서버간 Oauth 앱을 생성하여 계정에서 해당 기능을 대체하는 것이 좋습니다. 모든 새로운 연결은 기본적으로 Zoom Oauth 인증을 거치게 됩니다.

## 커넥터 범주

Adobe Learning Manager 커넥터는 기본 목적 및 통합 기능에 따라 다음과 같은 여러 기능 범주로 구성할 수 있습니다.

| 카테고리 | 용도 | 커넥터 예 |
|---------|--------|-------------------|
| 데이터 전송 | 파일 기반 데이터 교환 및 대량 작업 | FTP, 사용자 정의 FTP, 상자 |
| 가상 교실 | 실시간 교육 및 회의 통합 | Microsoft Teams, 확대/축소, Adobe Connect |
| 엔터프라이즈 시스템 | HR 및 비즈니스 시스템 통합 | Workday, Salesforce, ADFS |
| 콘텐츠 플랫폼 | 외부 학습 콘텐츠 통합 | LinkedIn 학습, Harvard ManageMentor, getAbstract |
| 분석 및 BI | 보고 및 데이터 시각화 | Power BI, 교육 데이터 액세스 |
| 인증 | ID 관리 및 보안 | ADFS(SSO 기능) |
| 전자상거래 및 마케팅 | 영업 및 마케팅 통합 | Adobe Commerce, Marketo Engage |

## 데이터 전송 및 파일 관리 커넥터

이러한 커넥터는 파일 전송 프로토콜을 통해 자동화된 데이터 교환을 용이하게 하여 대량 작업 및 시스템 간 통신을 가능하게 합니다.

### Adobe Learning Manager FTP 커넥터

FTP 커넥터를 사용하여 조직은 널리 채택된 파일 전송 프로토콜을 사용하여 Adobe Learning Manager과 외부 시스템 간의 데이터 동기화를 자동화할 수 있습니다. 이 커넥터는 보안 강화를 위해 SFTP(SSH File Transfer Protocol) 및 FTPS(FTP Secure)를 포함한 보안 변형을 지원합니다.

#### 주요 기능:

- Adobe Learning Manager과 원격 서버 간에 파일을 업로드 및 다운로드합니다.
- 사용자 정보 및 교육 기록을 위한 자동 데이터 교환
- 보안 파일 전송 프로토콜(SFTP, FTPS) 지원
- 대용량 데이터 세트의 일괄 처리

자세한 내용은 [FTP 커넥터](/help/migrated/integration-admin/feature-summary/ftp-connector.md)를 참조하세요.

### 사용자 정의 FTP 커넥터

사용자 정의 FTP 커넥터는 보다 정교한 파일 전송 기능을 제공하며, 구조화된 데이터 형식 및 xAPI 명령문 교환을 지원합니다. 이 커넥터는 데이터 교환 프로세스를 보다 세부적으로 제어해야 하는 조직을 위해 설계되었습니다.

#### 주요 기능:

- 구조화된 CSV 파일을 통해 사용자 데이터를 가져오고 내보냅니다.
- 학습 기록 및 xAPI 명령문을 처리합니다.
- 지정된 FTP 폴더에서 자동 파일 처리.
- 민감한 데이터 전송을 위한 향상된 보안 기능.

자세한 내용은 [사용자 지정 FTP 커넥터](/help/migrated/integration-admin/feature-summary/custom-ftp-connector.md)를 참조하세요.

### Box 커넥터

Box 커넥터는 Box의 클라우드 스토리지 플랫폼을 활용하여 외부 시스템과 Adobe Learning Manager 간의 원활한 데이터 동기화를 지원합니다. 이 커넥터는 파일 관리에 Box를 이미 사용하고 있는 조직에 특히 유용합니다.

#### 주요 기능:

- 클라우드 기반 파일 스토리지 및 동기화.
- 자동화된 CSV 데이터 처리.
- 기존 Box 워크플로우와 통합.
- 지정된 폴더에서 실시간 데이터 업데이트.

## 가상 강의실 및 회의 커넥터

이러한 커넥터는 Adobe Learning Manager과 인기 있는 비디오 회의 및 가상 회의 플랫폼을 통합하여 라이브 교육 세션을 원활하게 제공할 수 있습니다.

자세한 내용은 [Box 커넥터](/help/migrated/integration-admin/feature-summary/box-connector.md)를 참조하십시오.

### Microsoft Teams 커넥터

Microsoft Teams 커넥터는 Teams의 회의 기능과 직접 통합함으로써 Adobe Learning Manager을 포괄적인 가상 강의실 솔루션으로 변환합니다. 이 커넥터는 Microsoft 365 에코시스템을 사용하는 조직에 필수적입니다.

#### 주요 기능:

- Adobe Learning Manager에서 직접 가상 강의실 세션을 예약하십시오.
- 자동 팀 회의 생성 및 관리.
- 별도의 회의 링크 없이 원활한 학습자 액세스

자세한 내용은 [MS Teams 커넥터](/help/migrated/integration-admin/feature-summary/install-microsoft-teams-connector.md)를 참조하십시오.

### Zoom 커넥터

Zoom 커넥터를 통해 조직은 Adobe Learning Manager 환경에서 Zoom의 강력한 화상 회의 기능을 직접 활용할 수 있으며 강사와 학습자 모두에게 원활한 환경을 제공합니다.

#### 주요 기능:

- Adobe Learning Manager에서 직접 Zoom 회의 예약.
- 회의 링크 생성 및 배포 자동화.
- 실시간 출석 모니터링.
- 기록 관리 및 재생 통합.
- 대화형 세션에 대한 소규모 회의실 지원.

자세한 내용은 [확대/축소 커넥터](/help/migrated/integration-admin/feature-summary/zoom-connector.md)를 참조하십시오.

### Adobe Connect 커넥터

Adobe Connect 커넥터는 Adobe의 가상 강의실 플랫폼과 완벽하게 통합되어 대화형 온라인 학습 경험을 위한 고급 기능을 제공합니다.

#### 주요 기능:

- 고급 대화형 기능(설문 조사, 퀴즈, 브레이크아웃).
- 고품질 화면 공유 및 프레젠테이션 도구.
- 포괄적인 세션 기록 및 재생.
- 모바일에 최적화된 가상 강의실 환경.

자세한 내용은 [Adobe Connect 커넥터](/help/migrated/integration-admin/feature-summary/adobe-connect-connector.md)를 참조하십시오.

## 기업 시스템 통합 커넥터

이러한 커넥터를 통해 Adobe Learning Manager은 핵심 비즈니스 시스템과 통합되므로 자동화된 사용자 관리 및 조직 데이터 동기화를 용이하게 할 수 있습니다.

### Workday 커넥터

Workday 커넥터는 HR 시스템과 학습 관리 플랫폼 간에 원활한 브리지를 만들어 직원 기록, 조직 구조 및 역할 할당이 두 시스템 간에 동기화된 상태를 유지하도록 합니다.

#### 주요 기능:

- Workday에서의 자동 사용자 프로비저닝.
- 실시간 직원 데이터 동기화.
- 조직 계층 구조 매핑입니다.
- 역할 기반 학습 할당 자동화.

자세한 내용은 [Workday 커넥터](/help/migrated/integration-admin/feature-summary/workday-connector.md)를 참조하십시오.

### Salesforce 커넥터

Salesforce 커넥터를 사용하여 조직은 고객 관계 관리 시스템을 학습 이니셔티브와 통합하여 영업 교육, 고객 교육 및 성과 추적에 대한 기회를 창출할 수 있습니다.

#### 주요 기능:

- Salesforce에서 자동화된 사용자 가져오기.
- 사용자 정의 데이터 필드 매핑.
- Salesforce로 학습 기록 내보내기.
- 영업 성과와 교육 이수 간의 상관 관계 분석
- 고객 교육 프로그램 관리.

자세한 내용은 [Salesforce 커넥터](/help/migrated/integration-admin/feature-summary/salesforce-connector.md)를 참조하십시오.

### ADFS(Active Directory Federation Services) 커넥터

ADFS 커넥터를 통해 조직은 엔터프라이즈급 인증 및 권한 부여를 구현할 수 있으며, 이를 통해 사용자는 기존 Active Directory 자격 증명을 사용하여 Adobe Learning Manager에 액세스할 수 있습니다.

#### 주요 기능:

- SSO(Single Sign-On) 구현
- 기업 보안 규정 준수
- 원활한 사용자 인증

자세한 내용은 [ADFS 커넥터](/help/migrated/integration-admin/feature-summary/adfs-connector.md)를 참조하십시오.

## 콘텐츠 및 학습 플랫폼 커넥터

이러한 커넥터는 외부 콘텐츠 라이브러리와 특수 학습 플랫폼을 통합하여 학습 카탈로그를 확장합니다.

### LinkedIn Learning 커넥터

linkedIn Learning 커넥터 를 통해 LinkedIn의 광범위한 전문 개발 과정 라이브러리를 이용할 수 있으므로 조직은 업계 최고 수준의 외부 콘텐츠를 통해 내부 교육을 보완할 수 있습니다.

#### 주요 기능:

- linkedIn Learning의 전체 강의 카탈로그 액세스.
- 자동화된 과정 검색 및 가져오기.
- Adobe Learning Manager 내에서 학습자 진행률 추적

자세한 내용은 [LinkedIn 커넥터](/help/migrated/integration-admin/feature-summary/linkedin-learning-connector.md)를 참조하십시오.

### Harvard ManageMentor 커넥터

Harvard ManageMentor 커넥터는 세계적 수준의 리더십 및 관리 교육 콘텐츠를 Adobe Learning Manager 환경에 직접 제공하여 Harvard Business School의 유명한 교육 리소스를 이용할 수 있도록 합니다.

#### 주요 기능:

- 프리미엄 하버드 비즈니스 스쿨 콘텐츠 액세스.
- 관리 및 리더십 개발 모듈.
- 원활한 콘텐츠 가져오기 및 구성.

자세한 내용은 [Harvard ManageMentor 커넥터](/help/migrated/integration-admin/feature-summary/harvard-managementor-connector.md)를 참조하세요.

### getAbstract 커넥터

getAbstract 커넥터는 간결한 비즈니스 서적 요약과 전문적인 통찰력에 대한 액세스를 제공하여 조직은 소화할 수 있는 콘텐츠 형식을 통해 지속적인 학습을 제공할 수 있도록 합니다.

#### 주요 기능:

- 업무 장부 요약과 통찰력에 액세스합니다.
- 사용 데이터 추적 및 보고.
- 자동 완료 기록 생성.

자세한 내용은 [getAbstract 커넥터](/help/migrated/integration-admin/feature-summary/getabstract-connector.md)를 참조하세요.

## 비즈니스 인텔리전스 및 분석 커넥터

이러한 커넥터는 학습 데이터를 외부 분석 플랫폼과 통합하여 고급 보고, 데이터 시각화 및 비즈니스 인텔리전스 기능을 지원합니다.

### Power BI 커넥터

Power BI 커넥터는 학습 메트릭스를 Microsoft의 강력한 비즈니스 인텔리전스 플랫폼과 자동으로 동기화하여 학습 데이터를 실행 가능한 비즈니스 인사이트로 전환합니다.

#### 주요 기능:

- 실시간 학습 데이터 동기화.
- 사용자 정의 대시보드 생성 및 관리
- 고급 데이터 시각화 및 보고 기능
- 학습자 성적 증명서 및 스킬 보고서 통합.

자세한 내용은 [Power BI 커넥터](/help/migrated/integration-admin/feature-summary/power-bi-connector.md)를 참조하십시오.

### 교육 데이터 액세스 커넥터

교육 데이터 액세스 커넥터를 사용하여 조직은 교육 데이터 및 과정 정보에 대한 API 액세스를 제공하여 사용자 정의 학습 인터페이스 및 헤드리스 학습 경험을 만들 수 있습니다.

**주요 기능:**

- 강의 및 학습 경로 데이터에 대한 공개 API 액세스
- 사용자 정의 사용자 인터페이스 개발 지원.
- 헤드리스 학습 경험 생성.
- 고급 검색 및 필터링 기능.

자세한 내용은 [교육 데이터 액세스 커넥터](/help/migrated/integration-admin/feature-summary/training-data-access-connector.md)를 참조하십시오.

## 전자 상거래 및 마케팅 커넥터

이러한 커넥터를 통해 학습 콘텐츠를 수익화하고 마케팅 자동화 플랫폼과 통합할 수 있습니다.

### Adobe Commerce 커넥터

Adobe Commerce 커넥터는 Adobe Learning Manager을 포괄적인 학습 상거래 플랫폼으로 변환하여 조직이 완전히 통합된 전자 상거래 경험을 통해 강의, 인증 및 교육 프로그램을 판매할 수 있도록 합니다.

**주요 기능:**

- 원활한 전자 상거래 플랫폼 통합.
- 강의 카탈로그 및 가격 관리.
- 결제 처리 및 등록 자동화.

자세한 내용은 [Adobe Commerce 커넥터](/help/migrated/integration-admin/feature-summary/adobe-commerce-connector.md)를 참조하십시오.

### Marketo Engage 커넥터

Marketo Engage 커넥터는 학습 활동과 마케팅 캠페인 간에 강력한 시너지 효과를 만들어 조직에서 리드 육성 및 고객 개발을 위한 교육적 참여를 활용할 수 있도록 합니다.

#### 주요 기능:

- 자동 리드 생성 및 업데이트.
- 마케팅 인사이트를 위한 학습 활동 추적.
- 강의 등록 및 완료 이벤트가 트리거됩니다.

자세한 내용은 [Marketo Engage 커넥터](/help/migrated/integration-admin/feature-summary/marketo-engage-connector.md)를 참조하십시오.
