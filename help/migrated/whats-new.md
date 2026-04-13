---
description: Adobe Learning Manager 2026년 4월 릴리스의 API 및 Webhook 변경 사항을 포함한 새로운 기능 및 개선 사항에 대해 알아봅니다.
jcr-language: en_us
title: Adobe Learning Manager 2026년 4월 릴리스의 새로운 기능
source-git-commit: f4ff53bf053b2c8c756961af990505d23ab22db3
workflow-type: tm+mt
source-wordcount: '1768'
ht-degree: 0%

---


# Adobe Learning Manager 2026년 4월 릴리스의 새로운 기능

**학습자용:** 이제 Fluidic Player에 다음 모듈 이름과 명확한 종료 단추가 표시됩니다. 플랫폼 간 일관된 경험을 위해 LTI를 통해 플레이어 언어를 설정할 수 있다. 사용자 정의 매개 변수 이름은 &#39;locale&#39;이며 로케일 코드를 허용합니다. 예를 들면 locale=fr-FR입니다. Captivate 내용에는 통합 목차, 슬라이드 수준 완료 틱 및 신뢰할 수 있는 노트 내보내기가 포함됩니다. 다국어 지원은 작업 지원, 체크리스트 질문 및 VTT(비디오 텍스트 트랙)에 사용할 수 있습니다. AI 어시스턴트를 통해 학습자는 학습 경험에서 답을 얻을 수 있습니다.

**관리자 및 작성자의 경우:** Zoom 커넥터는 여러 개의 동시 VILT 세션을 지원합니다. 피어 계정의 공유 강의에 &#39;외부 작성자&#39; 대신 실제 작성자가 표시됩니다. 관리자는 모듈 시작 시기를 제한할 수 있습니다. 학습 개체 만료 날짜는 학습자 API에 노출됩니다. 체크리스트 모듈은 가중치 점수, 다국어 질문 텍스트 및 선택적 검토자 주석을 지원합니다. 사용자 정의 인증서는 동적 필드와 AI 생성 배경이 있는 드래그 앤 드롭 편집기를 제공합니다. 로그인하지 않은 Experience Builder를 사용하면 로그인하지 않고도 공개 학습 페이지를 구축할 수 있습니다.

**강사의 경우:** 인스턴스 등록 및 세션 참석에 대한 QR 코드를 생성합니다. 체크리스트 평가 중 주석 또는 피드백을 추가합니다.

**보고 및 분석:** SCORM 콘텐츠가 이제 L2 보고에서 여러 퀴즈 시도를 보고할 수 있습니다. 학습자 성적 증명서에서 학습 소요 시간 계산 개선 책임자용 학습 성적 증명서 보고서가 업데이트되었습니다. 고급 검색 개선 사항을 사용할 수 있습니다.

**로그인 방법:** Adobe Learning Manager에서 학습자, 작성자, 관리자를 위해 OpenID Connect 로그인이 작동하는 방법을 알아봅니다. OIDC(OpenID Connect)는 웹 표준을 기반으로 하는 일반적인 로그인 방법입니다. 많은 조직에서 사용
직원 및 파트너용 ID 공급자(예: Okta, Google Workspace 또는 Microsoft Entra ID).

자세한 내용은 [OIDC로 로그인](/help/migrated/oidc.md)을 참조하세요.

## 대체 및 동급의 Webhook 및 마이그레이션

### Webhook

학습자가 대체 또는 관계를 통해 강의를 완료하면 ALM은 표준 강의 완료 Webhook와 별도의 Webhook 이벤트를 트리거합니다. 이렇게 하면 통합이 필요한 경우 대체 완료에 다르게 응답할 수 있습니다. Webhook 이벤트는 과거 업데이트 및 관계 변경을 포함하여 소급 완료 또는 소급 미완료가 발생하는 경우에도 트리거됩니다.

자세한 내용은 [Webhooks](/help/migrated/integration-admin/feature-summary/webhooks.md#webhooks-for-alternates)을(를) 참조하십시오.

### 마이그레이션

시스템에 LO(학습 개체)와 동등한 기능을 도입하기 위한 CSV 기반 데이터 모델 및 마이그레이션 동작은 [Webhooks](/help/migrated/integration-admin/feature-summary/migration-manual.md#migration-for-alternates-and-equivalents)에 설명되어 있습니다.

## 삭제된 사용자 자동 제거

삭제된 사용자 자동 제거는 ALM에서 이미 삭제된 사용자의 데이터를 제거하는 기능입니다. 제거는 구성 가능한 보존 기간 후에 발생하며, 대량의 작업에 중점을 두어 큰 고객 계정을 성능 저하 없이 효율적으로 처리할 수 있도록 합니다.

자세한 내용은 [삭제된 사용자 자동 제거](/help/migrated/administrators/feature-summary/purge-users.md#auto-purge-of-deleted-users)를 참조하십시오.

## 모듈 액세스 시간 제어 설정

이 향상된 기능을 통해 Adobe Learning Manager의 작성자와 관리자는 학습자가 모듈을 시작할 수 있는 시간 창을 정의할 수 있습니다. 구성된 시작/종료 창 외부에서 모듈은 강의 구조에 계속 표시되지만 학습자는 시작할 수 없습니다.

자세한 내용은 [모듈 액세스 시간 제어 설정](/help/migrated/administrators/feature-summary/module-access-time-control.md)을 참조하세요.

## 학습자 성적 증명서 변경 사항

이 릴리스에서는 보다 명확한 감사 기능과 규정 준수 지원으로 학습 성적 증명서(LT) 보고서를 개선합니다.

* 관리자 LT의 새로운 완료 방법 열에는 완료가 직접, 대체 또는 취소되었는지 여부가 표시되지만, 대체 완료는 이제 소스 교육에서 상속된 날짜를 사용하고 소스가 취소되거나 직접 완료가 발생할 때 업데이트하는 상태, 완료 날짜 및 완료 소스에 영향을 줍니다.
* 취소 대체는 모든 적격 관계가 소급 미완료로 설정된 상태로 제거되면 상태, 완료 일자 및 완료 출처를 자동으로 조정합니다.
* 체크리스트 모듈의 검토자 피드백은 책임자 및 학습자 LT와 모든 내보내기 채널의 이름이 변경된 검토자 발언 열 아래에 표준화되어 있습니다.
* 마지막으로, 학습 시간 계산은 활성 시간과 유휴 시간을 더 잘 구별하여 참여 및 규정 준수 보고의 정확성을 향상시킵니다.

자세한 내용은 [학습자 성적 증명서의 변경 사항](/help/migrated/administrators/feature-summary/reports/changes-in-learner-transcript.md)을 참조하세요.

## 검토자를 위한 주석 달기 기능이 있는 체크리스트

이 기능을 사용하면 체크리스트 평가 중에 검토자가 댓글이나 피드백을 추가할 수 있습니다. 각 학습자에게 개별화되고 실행 가능한 피드백을 제공할 수 있습니다. 또한 투명도를 위해 주석과 함께 이름을 표시하도록 선택할 수 있습니다. 모든 발언은 학습자의 성적 증명서에 저장되고 체크리스트 보고서에 포함됩니다.

자세한 내용은 [주석 달기로 검사 목록 구성](/help/migrated/authors/feature-summary/courses.md#checklist-with-commenting)을 참조하십시오.

## 체크리스트에 대한 다국어 지원

이 기능을 사용하면 여러 언어로 체크리스트 모듈을 만들고 관리할 수 있습니다. 각 체크리스트 문항, 수업 및 평가 준거를 번역하여 검토자와 학습자가 선호하는 언어로 체크리스트와 상호 작용할 수 있도록 하였다. 시스템은 사용자가 선택한 컨텐츠 언어로 체크리스트를 표시하여 글로벌 팀의 접근성 및 준수를 향상시킵니다.

[모듈에서 다국어 검사 목록 만들기](/help/migrated/authors/feature-summary/courses.md#create-a-multi-language-checklist) 보기

## 강사 평가를 위한 체크리스트 질문 가중치

이 기능을 사용하면 체크리스트 질문마다 다른 최대 점수(가중치)를 할당할 수 있습니다. 문항별로 중요도나 난이도가 달라지는데 이를 반영할 수 있어 보다 정확하고 의미 있는 평가를 뒷받침한다. 시스템은 사용자의 입력을 기반으로 총 점수를 계산하고 사용자가 설정한 기준에 따라 학습자의 합격 또는 불합격 여부를 결정합니다.

[가중치 체크리스트 질문 만들기](/help/migrated/authors/feature-summary/courses.md#how-to-create-a-weighted-checklist) 보기

## 사용자 정의 인증서

ALM(Adobe Learning Manager)의 사용자 정의 인증서를 사용하면 관리자와 작성자가 학습자를 위해 개인화된 인증서를 디자인하고, 관리하고, 발급할 수 있습니다.

이 기능에는 드래그 앤 드롭 편집기, 동적 필드, 다국어 지원 및 AI 생성 배경이 포함되어 있어 조직에서 기술 전문 지식 없이도 브랜드 인증서를 만들 수 있습니다.

[사용자 지정 인증서 디자인](/help/migrated/administrators/feature-summary/create-customize-certificate.md) 보기

## Experience Builder에 로그인하지 않은 경험

Experience Builder에 로그인하지 않은 환경을 통해 조직은 로그인하지 않은 사용자를 포함하여 모든 방문자에게 학습 콘텐츠 및 포털 페이지를 표시할 수 있습니다. 이 기능은 로그인 또는 등록을 요청하기 전에 교육 서비스의 부드럽고 브랜드 미리보기를 제공하여 잠재 학습자를 모으고, 알리고, 참여하도록 설계되었습니다.

Experience Builder에서 [로그인하지 않은 환경](/help/migrated/administrators/feature-summary/experience-builder/non-logged-in-experience.md) 보기

## 고급 검색 개선 사항

이제 고급 검색에서 검색 결과가 더 정확하고 관련성이 높아졌습니다. 콘텐츠 내 검색과 메타데이터에서 일치하는 키워드가 더 높게 검색되므로 학습자가 찾고 있는 항목을 더 쉽게 찾을 수 있습니다.

학습자는 이제 등록된 학습 개체가 액세스 가능한 카탈로그에 포함되지 않더라도 검색 결과에서 볼 수 있으므로 관련 콘텐츠가 누락되지 않도록 할 수 있습니다. 또한 고급 검색과 콘텐츠 내 검색 모두에서 작업 지원 순위가 향상되어 가장 관련 있는 리소스를 더 빠르게 검색할 수 있습니다.

## 다국어 작업 지원

Adobe Learning Manager(ALM)의 다국어 작업 지원을 통해 작성자와 관리자는 단일 작업 지원 항목 내에서 지원 문서, 안내선 또는 리소스를 다국어로 제공할 수 있습니다. 다른 지역의 학습자가 선호하는 언어로 관련 자료에 액세스할 수 있어 이해력, 준수성 및 사용자 경험이 향상됩니다.

자세한 내용은 [다국어 작업 지원 추가](/help/migrated/authors/feature-summary/job-aids.md#create-a-multilingual-job-aid)를 참조하세요.

## VTT(다국어 비디오 텍스트 트랙) 지원(작성자용)

Adobe Learning Manager에서 다국어 비디오 텍스트 트랙(VTT)을 지원하면 작성자가 비디오 및 오디오 콘텐츠에 대한 자막과 캡션을 여러 언어로 제공할 수 있습니다. 이 기능은 로컬라이제이션을 간소화하여 글로벌 사용자가 교육에 액세스할 수 있도록 하고 접근성 표준을 준수하도록 합니다. 작성자는 플랫폼 내에서 직접 VTT 파일을 자동 생성, 번역, 검토 및 편집할 수 있습니다.

자세한 내용은 [다국어 VTT 지원](/help/migrated/authors/feature-summary/content-library.md#multi-lingual-vtt-support)을 참조하세요.

## 피어 계정에서 공유 강의의 원본 작성자 표시

카탈로그를 통해 피어 계정으로 강의를 공유하면 Adobe Learning Manager에서는 현재 수신 계정의 학습자, 책임자 및 작성자 보기에서 작성자를 &#39;외부 작성자&#39;로 레이블 지정합니다. 따라서 특히 대기업의 경우 문제나 질문이 발생할 때 적절한 컨텐츠 소유자를 파악하고 연락하기가 어려워짐에 따라 학습자와 관리자에게 많은 문제가 발생할 수 있습니다.

향상된 기능을 통해 작성자 정보가 일반적인 자리 표시자로 대체되지 않고 피어 계정의 공유 강의에 대해 보존 및 표면화됩니다.

### 새로운 기능

피어 계정에서 공유 강의의 실제 작성자 이름 표시

외부 또는 피어 카탈로그를 통해 공유된 강의의 경우, 이제 원본 계정의 원본 작성자 이름이 &#39;외부 작성자&#39; 대신 수신 계정에 표시됩니다.

이는 다음 경우에 적용됩니다.

* 학습자 앱(강의 카드 또는 강의 세부 정보).
* 학습자로 미리 볼 때 책임자 및 작성자가 확인합니다.

자세한 내용은 [공유 강의 작성자 이름 표시](/help/migrated/administrators/feature-summary/peer-account.md#author-name-display-for-shared-courses-including-previously-acquired-courses)를 참조하세요.

## 해당 항목과 대체 항목

ALM에서 원활한 학습 환경을 제공하고 동급 제품 및 대체 제품을 사용한 중복 교육을 없앱니다. 이 새로운 기능을 통해 관리자는 단방향(대체) 또는 양방향(등가물) 규칙을 구성할 수 있습니다. 여기서 한 교육을 완료하면 다른 교육에 대한 대체 완료가 자동으로 부여됩니다. 대규모 학습 에코시스템을 간소화하도록 설계된 이 기능은 학습자가 이미 마스터한 콘텐츠를 우회하도록 하고, 조직은 관리자 지원 티켓을 크게 줄이고, 수동 재정의를 제거하고, 더 깨끗하고 정확한 학습자 기록을 유지합니다.

자세한 내용은 [해당 항목 및 대체 항목](/help/migrated/administrators/feature-summary/alternates-equivalence.md)을 참조하세요.

## 인스턴스 등록 및 세션 출석에 대한 강사 QR 코드

강사는 다음에 대한 QR 코드를 직접 생성할 수 있습니다.

* 강의 인스턴스 등록
* 세션 출석 또는
* 등록 + 함께 참석

을 참조하십시오. 학습자가 물리적 또는 하이브리드 클래스룸에 입장하고 QR 코드를 사용하여 출석을 등록하고 기록하려면 빠른 셀프서비스 옵션이 필요한 상황을 위해 설계되었습니다.

자세한 내용은 [학습자 등록 및 출석을 위한 QR 코드 다운로드](/help/migrated/instructors/feature-summary/learners.md#download-qr-codes-for-learner-enrollment-and-attendance)를 참조하세요.

## 세션 링크가 있는 ICS(일정 초대)

Adobe Learning Manager에는 학습자와 강사에게 보낸 **세션 참가 링크(ICS 파일)가 일정 초대**&#x200B;에 직접 포함됩니다. 이렇게 하면 참가자가 세션 전자 메일을 검색하지 않고도 캘린더에서 직접 세션에 참여할 수 있습니다.

이 개선은 **Gmail** 및 **Outlook**&#x200B;과 같은 일정 클라이언트의 환경을 개선합니다.

자세한 내용은 [세션 링크가 있는 일정 초대](/help/migrated/instructors/feature-summary/learners.md#joining-a-session-from-gmail)를 참조하세요.

## 학습자용 AI 지원

학습자용 AI 어시스턴트(베타)는 전체 강의를 탐색하지 않고도 할당된 학습 콘텐츠에서 답변을 빠르게 찾을 수 있도록 도와줍니다. 일반 언어로 질문을 하고 관련 강의 콘텐츠에 대한 소스 링크를 통해 정확하고 집중적인 응답을 받을 수 있습니다.

기능의 진화에 따라 기능, 지원되는 시나리오 및 제한 사항이 변경될 수 있습니다. AI Assistant는 신뢰할 수 있는 학습 콘텐츠를 사용하여 빠르고 정확한 답변을 제공하는 Adobe Learning Manager의 생성형 AI 기반 채팅 보조 프로그램입니다. 인용문이 포함되어 있어 항상 정보의 출처를 알 수 있다.

[학습자용 AI 도우미](/help/migrated/learners/feature-summary/learner-ai-assistant.md) 보기


## 릴리스의 API 변경 사항

Adobe Learning Manager의 2026년 4월 릴리스에는 대체 및 대응 항목과 관련하여 공개 API가 중점적으로 개선되고, 콘텐츠의 시간 창을 통한 액세스, 콘텐츠 중심의 퀴즈 시도, 로그인하지 않은 경험, 작업 지원 처리가 도입되었습니다. 변경 사항은 보다 정밀한 통합을 가능케 하면서 대부분 이전 버전과 호환되도록 설계되었습니다.

[4월 릴리스의 API 변경 내용 보기](/help/migrated/api-changes-alm.md)

## 시스템 요구 사항

[Adobe Learning Manager 시스템 요구 사항](/help/migrated/system-requirements.md)을 확인하십시오.

## 릴리스 정보

최신 릴리스 업데이트는 [릴리스 정보](/help/migrated/release-note/release-notes.md)를 확인하십시오.

## Adobe Learning Manager의 이전 릴리스

* [Adobe Learning Manager 2025년 10월 릴리스](/help/migrated/whats-new-october-2025.md)
* [Adobe Learning Manager 2025년 5월 릴리스](/help/migrated/whats-new-may-2025.md)
