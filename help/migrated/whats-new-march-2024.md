---
description: Adobe Learning Manager 2024년 3월 릴리스의 새로운 기능 및 개선 사항에 대해 알아봅니다
jcr-language: en_us
title: 새로운 기능 요약
contentowner: jayakarr
exl-id: 603f1f1c-bf8d-4807-b9f7-b10ded19a91e
source-git-commit: c833d92533b7fbf5a87c980d8b5e088185d02ef5
workflow-type: tm+mt
source-wordcount: '3903'
ht-degree: 1%

---

# 새로운 기능 요약 {#new-features-summary}

Adobe Learning Manager 2024년 3월 릴리스의 새로운 기능 및 개선 사항에 대해 알아봅니다.

다음과 같은 몇 가지 최신 Adobe Learning Manager 기능을 살펴보십시오.

1. 외부 소스에서 스킬 가져오기
1. 다중 브랜딩 지원
1. 체크리스트 재평가 활동 모듈
1. 흰색 레이블이 지정된 모바일 학습 앱

>[!NOTE]
>
>이 릴리스의 새로운 기능에 대해 자세히 알아보려면 이 [웨비나](https://learningmanager.adobe.com/app/learner?accountId=98632#/course/9212121)를 확인하세요.


## 이 릴리스의 새로운 기능 {#whatsnewandchanged}

### 외부 소스에서 스킬 가져오기

각 커넥터를 사용하여 LinkedIn 및 Go1과 같은 콘텐츠 공급자에서 스킬을 가져옵니다. 이러한 향상된 기능은 Learning Manager가 외부 스킬 Clouds 및 인재 관리 시스템과 통합하는 것을 목표로 하는 부분입니다. 가져온 스킬은 Learning Manager의 책임자 정의 스킬에 추가되며, 강의 생성 워크플로 중에 작성자가 사용할 수 있습니다. 또한 계정에 광범위한 스킬이 있을 때 더 나은 검색 경험을 제공하기 위해 플랫폼 전체의 스킬 검색 기능이 개선되었습니다.

자세히 알아보려면 [스킬 가져오기](administrators/feature-summary/import-skills-external-sources.md)를 확인하세요.

### 사용자 정의 브랜딩

이제 계정에서 사용할 수 있는 사용자 그룹을 기반으로 조직 이름, 로고, UI 테마와 같은 특정 UI 요소를 사용자 정의할 수 있습니다. 예를 들어 여러 사업부가 있는 조직은 각 사업부에 대해 표시될 사용자 정의 로고와 UI 테마를 설정할 수 있습니다.

>[!NOTE]
>
>이 다중 브랜딩 기능은 관리자의 보기에는 적용되지 않습니다. 계정에는 항상 조직 수준 브랜딩이 표시됩니다. 이는 학습자 대면 기능이며 관리자의 계정에서 해당 기능을 원하지 않을 수 있기 때문입니다.

자세한 내용은 [여러 사용자 지정 브랜딩](administrators/feature-summary/themes.md#multiple-branding)을 참조하세요.


## 대규모 사용자 기반이 있는 계정의 변경 사항

### 책임자 - 강의 또는 학습 경로 페이지

강의에 50,000명 이상의 학습자가 등록되어 있는 경우 학습자 목록이 표시되지 않습니다. *학습자 검색* 검색 표시줄에서 학습자를 검색하거나 검색 표시줄 위쪽에 있는 **다운로드** 링크를 선택하여 학습자 목록을 다운로드할 수 있습니다.

### 책임자 - 학습자 페이지

사용자를 검색할 때 **학습자 다운로드** 및 **내보내기** 옵션은 동일한 보고서를 다운로드합니다. 그동안, 사용자 그룹을 검색하는 동안 이제 해당 사용자 그룹에서 필터링된 사용자를 다운로드할 수 있습니다. 사용자 그룹을 검색할 때
**학습자 목록 다운로드**&#x200B;가 **사용자 그룹에 대한 학습자 목록 다운로드**(으)로 변경됩니다. **내보내기** 옵션이 다시 전체 목록을 다운로드합니다.

### 관리자 - 사용자 페이지

#### 내부 사용자

예를 들어 사용자 수가 50,000명을 초과하면 추후 좀 더 자세한 분석을 위해 데이터를 다운로드하라는 메시지가 있을 것이다. 이제 검색 표시줄이 나타나고 *이름, 전자 메일 형식으로 사용자를 표시합니다. | UUID*.

>[!NOTE]
>
>UUID는 계정에 대해 UUID가 활성화된 경우에만 표시됩니다.

#### 외부 사용자

외부 사용자도 동일한 동작이 적용됩니다. 사용자 수가 많은 경우 사용자를 다운로드하고 *이름, 전자 메일 형식으로 검색 후 사용자의 세부 정보를 검색할 수도 있습니다. | UUID*.

#### 사용자 정리 페이지

사용자 정리 페이지에서 삭제된 사용자의 경우 **삭제된 날짜**&#x200B;에 정렬 기능을 제거했습니다. UUID만 정렬할 수 있습니다.

### 관리자 - 인스턴스 페이지

#### 강의 또는 학습 경로

등록 수가 많은 경우 Adobe Learning Manager에 학습자 수가 표시되지 않습니다. 대신, 학습자 수를 선택하고 보고 학습자 페이지로 이동할 수 있는 아이콘이 표시됩니다.

학습자 수는 대략적인 값으로 표시됩니다. 예를 들어 학습자 수가 50,000명을 초과하면 값이 50K+로 표시됩니다.

### 관리자- L1/L3 페이지

L1 피드백 페이지에서 강의 등록 횟수가 많으면 학습자 목록이 표시되지 않습니다. 대신 나중에 더 자세한 분석을 위해 사용자 목록을 내보낼 수 있습니다.

검색은 type-ahead를 지원하며 결과는 선택한 인스턴스로 제한됩니다.

#### 출석 및 점수 페이지

페이지에서 사용자를 검색하면 사용 가능한 모든 인스턴스에서 검색이 실행됩니다. 그러나 결과는 선택한 인스턴스에 대한 것입니다.

[출석] 페이지에서 사용자 그룹을 검색하고 사용자 수가 등록과 관계없이 사용자 그룹에서 10,000명을 초과하면 대량 레벨 작업만 수행할 수 있습니다. 사용자 목록을 볼 수 없습니다.

사용자 그룹의 사용자 수가 10,000명 미만인 경우 대량 수준 작업과 함께 개별 사용자 수준 작업을 수행할 수 있습니다. 이 경우 사용자 목록이 비활성화되지 않습니다.

### 관리자 - 인증 페이지

현재 버전의 Adobe Learning Manager에서는 인증에 등록한 사용자가 많은 경우 **상태** 드롭다운이 비활성화되어 있으므로 등록되지 않은 학습자를 볼 수 없습니다.

이번 Adobe Learning Manager 릴리스에서는 등록된 사용자 수가 많은 경우 **상태** 드롭다운에 **등록됨** 및 **등록 취소됨**&#x200B;의 두 가지 옵션만 표시됩니다. **등록됨** 옵션은 기본적으로 선택됩니다. **등록 취소됨**&#x200B;을 선택하면 등록 취소된 학습자 목록이 표시됩니다.

#### 사용자 그룹 변경 사항

사용자 그룹의 경우 사용자 그룹의 사용자 수가 50,000명 미만인 경우 **상태** 드롭다운에 인증, 할당 및 만료 옵션이 모두 표시됩니다.

사용자 그룹의 사용자 수가 많은 경우 **상태** 드롭다운에는 새로운 설계에 따라 **등록됨** 및 **등록 취소됨**&#x200B;의 두 가지 옵션만 표시됩니다.

### 비교 테이블

<table>
    <tbody>
        <tr>
            <td><b>페이지</b></td>
            <td><b>임계값 변경 전</b></td>
            <td><b>임계값 변경 후</b></td>
        </tr>
        <tr>
            <td>책임자 - 강의 인스턴스</td>
            <td>인스턴스는 다음 디자인으로 표시됩니다.
            <ul>
                <li>모듈</li>
                <li>학습자 등록됨</li>
                <li>세션</li>
                <li>배지</li>
                <li>L1 피드백 활성화됨</li>
                <li>알림 경보</li>
                <li>게임화 점수</li>
                <li>QR 코드</li>
                <li>학습 경로 확장</li>
            </ul>
            <td>
                <ul>
                    <li>등록 수가 미리 정의된 임계값을 초과하면 ALM이 수를 표시하지 않습니다. 수를 아이콘으로 대체하고 누르면 실제 학습자 수와 학습자 페이지로 이동하는 링크가 표시됩니다.</li>
                    <li>등록 수는 대략적인 형식으로 표시됩니다. 예를 들어 5만 명 이상인 경우 수강 레벨에서 개수가 50K+로 표시됩니다.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>책임자 - 학습자 페이지</td>
            <td>
                    <ul>
                        <li>학습자 목록은 각 인스턴스에 대해 표시됩니다.</li>
                        <li>강의에 등록된 사용자 또는 사용자 그룹을 검색할 수 있습니다.</li>
                        <li>내보낸 보고서는 사용자 그룹에 대한 필터로 구성되어 있지 않습니다.</li>
                    </ul>
            </td>
            <td>
                <ul>
                    <li>인스턴스 선택을 사용할 수 없습니다.</li>
                    <li>학습자 목록 다운로드 또한 한 가지 경우를 제외하고 동일한 데이터를 다운로드합니다. 사용자 그룹을 검색한 다음 학습자 목록 다운로드 를 선택하면 해당 사용자 그룹 데이터가 다운로드됩니다.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>관리자- L1/L3 피드백 페이지</td>
            <td>
                <p>기존 비헤이비어에 변경 없음</p>
            </td>
            <td>
                <ul>
                    <li>인스턴스 선택을 사용할 수 없습니다.</li>
                    <li>강의 등록이 50K 이상인 경우 ALM은 학습자를 나열하지 않고 검색 표시줄만 표시합니다. 등록이 50K 미만인 경우 ALM에 학습자 목록과 검색 표시줄이 모두 표시됩니다.</li>
                    <li>목록은 기본적으로 비활성화되어 있습니다.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>관리자 - 출석 및 점수 페이지</td>
            <td>
                <p>기존 비헤이비어에 변경 없음</p>
            </td>
            <td>
                <ul>
                    <li>사용자를 검색할 때 인스턴스 선택이 비활성화됩니다.</li>
                    <li>예를 들어, 사용자 수가 50,000명을 초과하면 나중에 좀 더 자세한 분석을 위해 데이터를 다운로드할 수 있는 추가 메시지가 있습니다. 이제 검색 표시줄이 나타나고 이름, 이메일 형식으로 사용자가 표시됩니다. | UUID.</li>
                    <li>사용자 그룹의 사용자 수가 등록과 관계없이 10,000명 미만이면 대량 수준 작업과 함께 개별 사용자 수준 작업을 수행할 수 있습니다. 이 경우 사용자 목록이 비활성화되지 않습니다.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>책임자- L2 퀴즈 점수 페이지</td>
            <td>
                    <ul>
                        <li>사용자 검색도 구현됩니다.</li>
                    </ul>
            </td>
            <td>
                <ul>
                    <li>사용자 검색도 구현됩니다. Typehead는 LO 수준에서 검색하지만, 목록은 현재 선택된 인스턴스로 필터링됩니다.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>관리자- 사용자 페이지(내부, 외부)</td>
            <td>
                    <ul>
                        <li>사용자를 검색하면 이메일 ID가 표시됩니다.</li>
                    </ul>
            </td>
            <td>
                <ul>
                    <li>예를 들어, 사용자 수가 50,000명을 초과하면 나중에 좀 더 자세한 분석을 위해 데이터를 다운로드할 수 있는 추가 메시지가 있습니다. 이제 검색 표시줄이 나타나고 이름, 이메일 형식으로 사용자가 표시됩니다. | UUID.</li>
                    <li>사용자 정리 페이지의 삭제된 사용자에 대해 **삭제된 날짜**&#x200B;에 정렬 기능이 제거되었습니다. UUID만 정렬할 수 있습니다.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>강사- 제출</td>
            <td>
                    <ul>
                        <li>제출할 모듈의 페이지네이션.</li>
                        <li>이제 강사가 상태, 검토 종료, 제출 보류 중, 합격 및 불합격에 따라 학습자의 파일 제출을 필터링할 수 있습니다. </li>
                    </ul>
            </td>
            <td>
                <ul>
                    <li>해당 인스턴스에서는 사용자 그룹만 검색할 수 있고 사용자 그룹은 검색할 수 없습니다.</li>
                </ul>
            </td>
        </tr>
        <tr>
            <td>학습자 페이지로 미리 보기 계산</td>
            <td>
                    <ul>
                        <li>숫자에는 상위 순서의 등록 데이터가 포함됩니다.</li>
                    </ul>
            </td>
            <td>
                <ul>
                    <li>더 높은 순서의 등록에서 데이터가 제외됩니다.</li>
                </ul>
            </td>
        </tr>
    </tbody>
</table>

## 고급 검색 기능

이번 릴리스에서는 검색 환경이 개선되었습니다. 메타데이터뿐만 아니라 의미적 검색, 내용적 검색을 기반으로 검색 결과를 가져와 정확성, 최근 내용 및 관련 내용을 기반으로 결과를 도출합니다.

이 변경 사항은 다음을 반영합니다.

* 카탈로그 및 내 학습 페이지: 강의, 학습 경로 및 인증의 마우스 오버 작업이 제거되었습니다.
* 검색 막대의 모양입니다.
* 학습 앱에 필터 태그가 추가되었습니다.

검색 기능을 활성화하려면 Adobe Learning Manager의 CSAM 팀에 문의하십시오.

## 사용자 인터페이스 변경 사항 {#ui-changes}

### 강의 생성 페이지

강의를 스킬 레벨에 매핑하는 동안 스킬 목록이 먼저 검색됩니다. 즉, 스킬을 검색하면 검색된 용어와 일치하는 스킬 목록이 표시됩니다.

### 사용자 그룹

#### 책임자: 학습자 페이지

사용자를 검색할 때 **학습자 다운로드** 및 **내보내기** 옵션은 동일한 보고서를 다운로드합니다. 그동안, 사용자 그룹을 검색하는 동안 이제 해당 사용자 그룹에서 필터링된 사용자를 다운로드할 수 있습니다. 사용자 그룹을 검색할 때 **학습자 목록 다운로드**&#x200B;가 **사용자 그룹에 대한 학습자 목록 다운로드**(으)로 변경됩니다. **내보내기** 옵션이 다시 전체 목록을 다운로드합니다.

## 보고서 변경 사항

* 교육 보고서의 태그 및 스킬 열이 태그 및 스킬로 변경됩니다.
* [게임화 감사 추적](administrators/feature-summary/reports.md#gamification-audit-trail) 보고서를 추가했습니다.
* 계정에 스킬에 할당된 학습자가 280000명 이상 포함되어 있으면 스킬 학습자 보고서가 압축된 csv로 다운로드됩니다.
계정에 250000명 미만의 학습자가 있으면 동일한 보고서가 CSV로 다운로드됩니다.
관리자 페이지에서 **관리자** > **스킬** > **스킬** > **학습자**&#x200B;를 선택합니다. 보고서는 CSV로 다운로드됩니다.
* [세션 요약 보고서](administrators/feature-summary/reports.md#session-summary-report)에는 위치 정보와 위치 영역이라는 두 개의 새 열이 있습니다.

## 강의실 생성 변경 사항

[관리자 설정](administrators/feature-summary/classroom.md#classroom-settings)에 따라 작성자는 [위치를 만들고, 수정하고, 삭제할 수 있습니다](administrators/feature-summary/classroom.md#add-classroom-location).

>[!NOTE]
>
>위치 및 카탈로그 레이블을 추가하는 동안 작성자(강의 생성 페이지) 및 책임자(인스턴스 페이지)에게 각각 위치 및 카탈로그 레이블의 자동 채워진 목록이 표시됩니다.

책임자는 작성자가 강의실 위치를 수정하거나 삭제할 수 없도록 제한할 수 있습니다. 자세한 내용은 [강의실 설정](administrators/feature-summary/classroom.md#classroom-settings)을 참조하세요.

## 유연한 학습 경로 변경

의 모든 계정(이전 및 새 계정)은 유연한 학습 경로를 위해 학습자 앱의 등록 마감 시한, 등록 취소 마감 시한 및 인원 제한을 포함하여 시작됩니다.
이제 학습자는 강의의 인스턴스를 선택하지 않고 유연한 학습 경로에 등록할 수 있습니다.

## 학습 계획에 대한 새로운 트리거

학습 계획 설정 페이지에 새 트리거가 추가되었습니다. 이제 작성자와 관리자는 학습자가 강의 모듈에 실패하면 액션을 트리거할 수 있습니다.

자세한 내용은 [학습 계획](administrators/feature-summary/learning-plans.md)을 참조하세요.

## 새 제출 상태

이제 강사가 상태, 검토 종료, 제출 보류 중, 합격 및 불합격에 따라 학습자의 파일 제출을 필터링할 수 있습니다.

자세한 내용은 [제출 상태](instructors/feature-summary/learners.md#filter-file-submissions)를 참조하세요.

## 체크리스트 개선 사항

Adobe Learning Manager의 2024년 3월 릴리스에서 체크리스트 워크플로우의 개선 사항은 다음과 같습니다.

### 체크리스트 실패 시 진행 허용 안 함

검사 목록을 만들 때 작성자는 필수 검사 목록 섹션에서 **활성화**&#x200B;를 선택할 수 있습니다. 그렇게 하면 학습자가 체크리스트에 실패한 경우 모듈에서 진행할 수 없습니다. 체크리스트를 통과해야 진행할 수 있습니다.

그러면, 체크리스트 검토자(즉, 강사 또는 관리자)가 체크리스트의 상태를 확인할 수 있습니다. 또한 검토자는 학습자의 체크리스트를 순서에 관계없이 검토할 수 있습니다.

### 체크리스트 재평가

검사 목록을 만들 때 작성자는 재평가 섹션에서 **활성화**&#x200B;를 선택할 수 있습니다. 그렇게 하면 관리자나 강사가 체크리스트를 통과할 때까지 학습자를 재평가할 수 있습니다.

모듈이 필수인 경우 재평가 확인란이 기본적으로 선택됩니다.

강사 또는 관리자는 재평가가 활성화된 경우 체크리스트의 상태를 실패에서 통과로 변경할 수 있습니다.

체크리스트 페이지에서 강사는 보류 중인 상태의 학습자 수를 확인할 수 있습니다. 강사는 학습자를 평가하고 합격할 수 있습니다. 학습자가 실패 상태인 경우 재평가가 활성화되지 않은 경우에만 체크리스트를 볼 수 있습니다.

즉, 검사 목록을 만드는 동안 재평가 섹션에서 **사용** 확인란이 선택되지 않았습니다. 이 확인란을 선택하면 강사 체크리스트 페이지에서 보기/재평가 버튼이 표시됩니다.

버튼을 선택하면 학습자를 다시 평가하고 합격 또는 불합격으로 표시할 수 있습니다.

>[!NOTE]
>
>재평가 와 필수 체크리스트 만들기 와 같은 두 가지 기능은 새로 생성된 모듈에만 적용됩니다. 강의를 한 번 게시하면 이를 설정/해제할 수 없습니다.


자세한 내용은 [체크리스트 만들기](authors/feature-summary/courses.md#checklist-fail)를 참조하세요.

## 기타 개선 사항

### 세션 관련 이메일 알림

Adobe Learning Manager의 이전 릴리스에서는 다음과 같은 경우 학습자가 세션 관련 전자 메일, 세션 세부 정보 업데이트, 세션 초대 및 세션 미리 알림을 보내지 않았습니다.

* 학습자가 강의를 완료했으나
* 새 세션이 강의에 추가됨 또는
* 기존 세션에 변경 사항이 있습니다.

Adobe Learning Manager 2024년 3월 릴리스의 새로운 변경 사항은 다음과 같습니다.

* 세션 세부 정보 업데이트 및 세션 초대(학습자 및 강사용)
   * 향후 세션의 경우 등록된 학습자 및 현재 강사에 대한 **세션 세부 정보 업데이트**, **세션 초대**&#x200B;에 대한 전자 메일은 더 이상 사용되지 않습니다. 지난 세션의 경우 등록된 학습자 및 현재 강사를 위한 **세션 세부 정보 업데이트** 및 **세션 초대**&#x200B;에 대한 전자 메일은 그대로 유지됩니다.
* 알림 이메일 (관리자 및 학습자용)
   * 이후 세션의 경우 **세션 미리 알림** 이메일만 전송됩니다.

>[!NOTE]
>
>메일은 세션 및 강의 완료에 따라 달라지지 않습니다.


### AEM 참조 사이트 변경 사항

AEM 참조 사이트에서 학습자 액세스 토큰에 관리자 새로 고침 토큰을 추가할 수 있는 기능이 추가되었습니다.

### 강사의 제출 숨기기

학습자가 파일 제출 워크플로우를 사용하여 파일을 업로드한 후 강사가 제출에 대해 어떠한 작업(승인 또는 거부)도 수행하지 않으면 미리 정의된 일수 후에 제출 URL이 보기에서 숨겨집니다. 일수를 설정하거나 변경하려면 Adobe Learning Manager의 CSAM 팀에 문의하십시오.

### 제품 용어 변경

제품 용어 어휘에 열 *인스턴스* 및 *학습자*&#x200B;을(를) 추가했습니다.

### 모바일 앱 변경 사항

이 모바일 앱 릴리스에서 학습자는 기한이 지난 강의 미리 알림을 예약하고 관리할 수 있습니다. 기한 경과 미리 알림 을 클릭하면 다음 옵션에 액세스할 수 있습니다.

* 취소
* 강의로 이동
* 3일 후 다시 알림
* 일주일 후에 다시 알림

Android: 푸시 알림을 클릭하면 **강의 개요** 페이지로 이동합니다.
iOS: 푸시 알림을 클릭하면 앱의 홈 페이지로 이동합니다. 이는 iOS에서 알려진 제한 사항입니다.

### Salesforce의 학습자 앱 체크리스트 변경 사항

학습자가 체크리스트에 실패하면 다음 모듈이나 강의로 진행할 수 없습니다. 필수 체크리스트 확인란을 선택하면 체크리스트에 실패한 경우 학습자가 강의를 진행할 수 없습니다.

웹 앱과 마찬가지로 학습자가 Salesforce 앱의 체크리스트에 실패하면 메시지가 표시되고 앞으로 이동하지 않습니다.

### Connect VC의 변경 사항

Adobe Learning Manager의 현재 릴리스에서 학습자는 Connect VC 세션에 등록되었을 때 **출석하지 않음**&#x200B;으로 표시되지만 완료 조건을 충족하지 않았습니다.

이번 릴리스에서는 상태가 **아직 표시 안 함**(으)로 변경됩니다.

### Adobe Learning Manager의 흰색 레이블 지정

Adobe Learning Manager 모바일 앱은 이제 흰색 레이블 지정을 지원합니다. 즉, 이제 사용자의 브랜딩으로 앱을 출시할 수 있습니다.

자세한 내용은 [Adobe Learning Manager 모바일 앱](white-label.md)에서 흰색 레이블 기능을 참조하십시오.

### 마이그레이션 CSV의 새 열

이번 릴리스에서는 다음 마이그레이션 CSV에 새로운 선택 열인 uniqueLoId가 있습니다.

* certification.csv
* course.csv
* learning_program.csv

>[!NOTE]
>
>**uniqueLoId** 열은 선택 사항입니다.


마이그레이션을 수행하여 기존 강의나 학습 계획 또는 인증을 업데이트하면 **uniqueLOId**&#x200B;을(를) 사용하는 강의나 학습 계획 또는 인증이 작성자 앱에 추가됩니다.

마이그레이션하는 동안 선택적 열이지만 강의 또는 학습 계획 또는 인증에 대한 CSV에서 **uniqueLOId** 값을 업데이트해야 합니다.

**uniqueLOId**&#x200B;을(를) 사용하여 기존 강의나 학습 계획 또는 인증을 업데이트하는 동안 마이그레이션을 수행하기 전에 **uniqueLoId** 열이 추가되지 않으면 마이그레이션 후에 **uniqueLOId** 값이 NULL 값으로 재정의됩니다.

>[!NOTE]
>
>열 **uniqueLoId**&#x200B;은(는) 작업 지원 CSV에 적용되지 않습니다.


>[!IMPORTANT]
>
>열 값은 계정 전체에서 고유해야 합니다. 강의 또는 인증과 동일한 값을 사용할 수 없습니다.

[마이그레이션 설명서](integration-admin/feature-summary/migration-manual.md#csv-specifications-and-sample-csvs)에서 CSV를 다운로드합니다.


### 앱 등급

학습자는 Adobe Learning Manager 앱에 대한 피드백을 제공하여 앱 경험을 더욱 향상시킬 수 있습니다. 학습자가 별 4개 이상을 평가하면 Play Store 또는 App Store에서 학습자에게 앱을 평가하도록 요청하는 팝업이 표시됩니다.

### Bluejeans는 2024년 2월에 서비스 종료(EOL)되었습니다

Bluejeans가 2024년 2월에 서비스 종료(EOL)되었음을 알려드립니다. 2024년 2월 이후에는 Bluejeans가 더 이상 업데이트 또는 지원을 받지 않습니다. CSAM 및 지원 팀은 이 전환 기간 동안 발생할 수 있는 질문이나 문제에 대해 도움을 줍니다.

커넥터 구성에 대한 자세한 내용은 [Adobe Learning Manager의 커넥터](integration-admin/feature-summary/connectors.md)를 참조하십시오.

### 로그인 액세스 보고서 변경 사항

Login Access 보고서는 지난 5분기 동안만 사용할 수 있습니다. 통합 책임자가 **로그인 액세스**&#x200B;를 선택한 상태에서 통합 내보내기의 온디맨드 다운로드를 요청하면 Adobe Learning Manager에 오류 메시지가 표시됩니다. 그러나 다른 보고서에는 영향을 주지 않습니다.

### ADFS 변경 사항

이제 매핑을 기반으로 Adobe Learning Manager에서 ADFS의 직원 유형 및 직원 ID 필드를 사용할 수 있습니다.

## 이 릴리스의 API 변경 사항

### 학습자 API

이번 릴리스에서는 학습자가 사용자 그룹 수준에서 브랜딩 로고와 개인화된 테마를 볼 수 있도록 API 지원을 추가했습니다.

API /account 및 /user?include=account 는 4개의 필드를 반환하며, 이 필드는 logoUrl, logoStyling 및 themeData에 속한 사용자의 활성 필드에 대해 재정의됩니다.

### 새 특성

learningObjectResource의 새 속성인 isExpiredSubmission은 리소스의 제출 만료 여부를 표시합니다.

* GET /account API: 새 특성 **expireSubmissionDuration** X를 반환합니다. 여기서 X는 설정된 일 수입니다. 설정하지 않으면 0이 반환됩니다.
* 리소스가 있는 GET /LO API에는 새 특성 **isExpiredSubmission**&quot;이(가) True 또는 False로 포함됩니다.
   * 제출 서류가 만료되고 &quot;submissionUrl&quot;이 표시되지 않으면 True입니다.
   * False이면 제출이 만료되지 않고 &quot;submissionUrl&quot;을 가져옵니다.

### 체크리스트의 API 변경 사항

강의는 여러 모듈로 구성될 수 있는데, 이 중 체크리스트는 모듈의 한 유형입니다. 이 체크리스트 모듈은 강사가 평가하며 평가를 기반으로 &#39;실패&#39; 또는 &#39;성공&#39;으로 표시할 수 있습니다.

그러나 두 경우 모두 체크리스트 상태가 완료됨으로 표시되고 이런 식으로 강의는 완료됨으로 표시됩니다.

이번 릴리스에서 LO API에는 *isChecklistMandatory* 매개 변수가 포함됩니다. 값이 True이면 체크리스트는 필수입니다.

### 다중 로케일 지원

이제 책임자는 원하는 언어로 L1 피드백 보고서를 다운로드할 수 있습니다. 단, 아직 Power BI에 대한 L1 피드백 보고서를 다운로드할 수 없습니다. API 요청에서 preferredLocale 매개 변수를 사용하여 원하는 로케일을 지정합니다.

### 인스턴스 수 변경 사항 요약

강의실/VC 강의 등록이 1,000개를 초과하는 계정에 적용됩니다.

1000보다 작은 경우 등록은 캐시를 무효화하고 등록 수, 완료 및 seatLimit와 같은 GET 요약 API 호출의 업데이트된 값을 반환합니다.

계정이 이 기능에 대해 활성화되어 있고 등록 수가 1,000개를 초과하면 캐시에서 값이 검색됩니다.

### 사용되지 않는 경로

현재 Learning Manager API는 포함 항목을 통해 API 모델을 탐색하여 데이터를 가져올 수 있는 그래프 데이터 구조를 따릅니다. API를 최대 7개 레벨까지 트래버스할 수 있지만 단일 API 호출을 사용하여 데이터를 가져오는 것은 계산상 비용이 많이 듭니다.

기존 및 신규 고객 모두 한 번의 큰 전화 대신 여러 번 작은 전화를 거는 것이 좋습니다. 이러한 접근 방식은 호출에 원하지 않는 데이터가 로드되는 것을 방지할 것이다.

#### 더 이상 사용되지 않는 경로

다음 경로는 사용되지 않습니다.

* /learningObject
   * 사용되지 않는 경로:
      * enrollment.loInstance.loResources.resources
      * instances.loResources.resources
   * 기존 패스:
      * enrollment.loInstance
      * instances.loResources
* /learningObjects/{id}
   * 사용되지 않는 경로:
      * enrollment.instances.subLoInstances.learningObject
   * 기존 경로:
      * enrollment.instances.subLoInstances
* /등록
   * 사용되지 않는 경로:
      * loInstance.learningObject.enrollment
   * 새 경로:
      * loInstance.learningObject
* /learningObjects/{id}
   * 사용되지 않는 경로:
      * instance.subLoInstances.learningObject.enrollment.loResourceGrades
   * 새 경로:
      * instance.subLoInstances

### 작업 API에 대한 로그인 액세스 및 사용자 감사 보고서 아카이브 변경 사항

이 릴리스에서는 작업 API가 최대 5개 분기의 로그인 액세스 보고서와 사용자 감사 보고서를 6개월 동안 보관합니다. 이 기간보다 오래된 데이터를 다운로드하려면 분기 및 연도를 지정하여 아카이브 매개변수를 전달해야 합니다. 샘플 페이로드를 참조하십시오.

```
{
    "data": {
        "type": "job",
        "attributes": {
            "description": "description of your choice",
            "jobType": "generateLoginAccessReport",
            "payload": {
                "fromDate": "2023-04-01T18:30:00.000Z",
                "toDate": "2023-04-30T18:30:00.000Z",
                "archive": {
                    "quarter": "4",
                    "year": "2021"
                }
            }
        }
    }
}
```

5분기를 초과하는 **로그인 액세스** 보고서를 다운로드하려고 하면 오류 메시지가 표시됩니다. 6개월이 지난 **사용자 감사** 보고서를 다운로드하려고 하면 유사한 오류 메시지가 표시됩니다.

### 사용되지 않는 API

제품에서 더 이상 사용되지 않는 모든 API의 누적 목록은 Adobe Learning Manager에서 [API 사용 중단](api-deprecations-list.md)을 확인하십시오.

## 이번 업데이트에서 수정된 문제 {#bug-fixes}

* 학습자가 강의에 등록한 후 다른 강의에 등록하려고 하면 경고 메시지가 표시됩니다.
* 사용자 그룹은 삭제된 후에도 검색에 표시됩니다.
* 사용자가 대용량 데이터로 많은 학습자 성적 증명서를 트리거하면 학습자 성적 증명서 큐가 차단되고 새 요청이 차단됩니다.
* 하위 계정이 상위 계정에 보고서 공유를 요청하는 경우, 상위 계정은 이를 수행할 수 없습니다.
* 강의 및 학습 경로의 URL이 잘못된 위치로 리디렉션됩니다.
* 학습자는 카탈로그 페이지에서 강의 링크를 클릭하면 다른 강의의 강의 인스턴스를 간헐적으로 볼 수 있습니다.
* 첫 번째 등록 후에 **등록 취소** 단추가 예상대로 표시되지 않지만 새로 고침 후에 표시됩니다.
* 이름에 공백이 있는 콘텐츠 또는 퀴즈를 저장할 수 없습니다.
* 관리자가 승인한 강의에서는 사용자 그룹에 학습자를 다시 등록할 수 있습니다.
* 경우에 따라 추가 활성 필드를 추가하려고 하면 &quot;활성 필드를 저장할 수 없습니다.&quot;라는 오류 메시지가 표시됩니다.
* 관련 강의 섹션의 강의 카드 안에 강의 이름으로 텍스트가 넘칩니다.
* 인스턴스를 전환하고 학습자를 인스턴스에 등록한 후에도 이전 인스턴스는 Outlook 일정에 계속 존재합니다.
* 피어 계정의 학습자가 강의 축소판을 선택하려고 하면 오류 메시지가 표시됩니다.
* 학습자가 강의에 등록하면 등록 알림이 여러 개 표시됩니다.
* 사용자가 커넥터에서 생성된 카탈로그의 이름을 수동으로 변경하면 새 카탈로그가 생성되고 강의가 잘못된 카탈로그에 게시됩니다.
* 비활성 계정에 속하는 사용자는 여전히 구독 전자 메일을 받습니다.

### API 관련 버그 수정

* API GET/사용자는 관리자의 세부 정보를 검색하지 않습니다.
* 계정에서 예약된 가동 중지 시간 동안 예약된 FTP 사용자 가져오기를 통해 사용자가 생성되었습니다.
* 모바일 앱 또는 몰입형 모드에서 강의 인스턴스를 삭제하거나 중단하고 다음 활성 인스턴스를 선택하면 **등록** 대신 **관심 등록** 버튼이 표시됩니다.
* 피어 계정의 학습자가 학습 객체 API를 사용하여 강의 축소판을 선택하려고 하면 오류 403이 표시됩니다.

## 시스템 요구 사항

[Adobe Learning Manager 시스템 요구 사항](system-requirements.md)을 확인하십시오.

## Adobe Learning Manager의 이전 릴리스

* [2023년 11월 릴리스](whats-new-november-2023.md)
* [2023년 7월 릴리스](whats-new-2023-july.md)
