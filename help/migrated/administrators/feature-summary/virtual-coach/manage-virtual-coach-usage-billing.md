---
description: Learning Manager 관리자가 Virtual Coach를 활성화하고 MAU 크레딧 사용을 모니터링하며 학습자 성능 보고서를 다운로드하는 방법을 알아봅니다
jcr-language: en_us
title: Virtual Coach 사용 및 청구 정보 관리
exl-id: 1f8f6465-51c3-4670-a1c7-9a7dfb091452
source-git-commit: 449f25df93867bf4d5ec11af057f8da7c405a09f
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%
---

# Virtual Coach 사용 및 청구 정보 관리

Virtual Coach를 활성화하고, 월간 활성 사용자(MAU) 크레딧 사용량을 모니터링하며, Adobe Learning Manager 관리자로서 학습자 성과 보고서를 다운로드합니다.

## 계정에 대한 Virtual Coach 활성화 {#activatevirtualcoach}

Virtual Coach는 Adobe Learning Manager의 추가 기능으로 사용할 수 있습니다. 구매 후 프로비저닝은 계정 관리자에게 이메일로 전송되는 활성화 키를 생성합니다.

1. 관리자 권한으로 Adobe Learning Manager에 로그인합니다.
2. 왼쪽 탐색 창에서 **결제** 페이지로 이동합니다.
3. **가상 코치** 섹션에서 이메일로 받은 활성화 키를 입력합니다.

   ![](/help/migrated/administrators/feature-summary/assets/virtual_coach12.png)
   *결제 페이지의 가상 코치 섹션에 활성화 키를 입력하여 기능을 켜십시오.*

4. **적용**&#x200B;을 선택합니다. 가상 코치가 계정에 대해 활성화되었습니다.

활성화되면 기능이 활성화되었음을 확인하는 앱 내 알림을 수신하게 됩니다. 작성자가 즉시 시작할 수 있도록 4개의 샘플 역할 재생 시나리오가 **콘텐츠 라이브러리**&#x200B;에 자동으로 추가됩니다.

>[!NOTE]
>
>활성화 키는 프로비저닝 중에 자동으로 생성되며 이메일로 공유됩니다. 활성화 키가 없는 경우 Adobe Learning Manager 고객 성공 관리자에게 문의하십시오.

## MAU 크레딧 잔액 보기

월간 활성 사용자(MAU) 크레딧은 매월 Virtual Coach를 사용하는 고유 학습자 수를 계산합니다.

1. **결제** 페이지로 이동합니다.
2. **가상 코치** 섹션에서 **사용 세부 정보 보기**&#x200B;를 선택합니다.

   ![](/help/migrated/administrators/feature-summary/assets/virtual-coach22.png)

3. **기간 선택** 드롭다운을 사용하여 검토할 날짜 범위를 선택합니다.

   **전체 사용량** 테이블에는 다음이 표시됩니다.

   - **사용 가능**: 구매한 총 MAU 크레딧
   - **사용됨**: 현재까지 사용된 크레딧.
   - **나머지**: 남은 계약 기간 동안 사용할 수 있는 크레딧.

   **월별 사용량** 테이블은 월별 고유 활성 학습자 수를 표시합니다.

   ![](/help/migrated/administrators/feature-summary/assets/virtual-coach23.png)

4. 전체 사용 데이터를 내보내려면 **자세한 보고서 다운로드**&#x200B;를 선택하세요.

   ![](/help/migrated/administrators/feature-summary/assets/virtual-coach-report-mau-billing-5.png)

## MAU 크레딧 사용 방법

MAU 크레딧은 학습자가 역월에 Virtual Coach 세션을 시작할 때 소비됩니다. 같은 달에 같은 학습자의 추가 세션은 추가 크레딧을 소비하지 않습니다. 계약 기간 종료 시 사용하지 않은 크레딧은 소멸되며 이월되지 않습니다.

| 시나리오 | 소비된 MAU |
|---|---|
| 한 학습자가 1월에 5개 세션을 완료합니다. | 1 |
| 동일한 학습자가 1월과 2월 모두에서 Virtual Coach를 사용함 | 2(월간 1개) |
| 1월에 각 100명의 학습자가 1개의 세션을 완료함 | 100 |

*MAU 크레딧은 각 학습자가 시작한 세션의 수에 관계없이 월별 고유 학습자당 계산됩니다.*

**예: 단일 학습자, 여러 세션** Sarah는 1월에 5개의 가상 코치 세션을 시작합니다. 해당 월에 단일 고유 사용자로 계산되므로 몇 번을 실행하든 상관없이 1개의 MAU가 소비됩니다.

**예: 동일한 학습자, 여러 달** Sarah는 1월(3개 세션)과 2월(2개 세션) 모두에서 Virtual Coach를 사용합니다. 각 달력 월은 개별적으로 계산되므로 1월의 경우 1개, 2월의 경우 1개의 MAU가 소비됩니다.

**예: 같은 달에 학습자가 여러 명 있습니다.** 100명의 영업 담당자가 1월에 Virtual Coach 세션을 하나씩 실행합니다. 각 고유 학습자는 해당 월에 하나의 MAU로 계산되므로 100개의 MAU가 소비됩니다.

**예: 시간 경과에 따른 팀 연습** 50명으로 구성된 팀은 1년 내내 Virtual Coach를 사용합니다. 50개 연습 중 5개만 해당 달에 5개의 MAU가 소비됩니다. 50개 모두 다시 연습하는 달에는 각 학습자가 해당 월 내에서 연습하는 횟수와 관계없이 월별로 한 번만 계산되므로 해당 월에 학습자를 반환하는 데 이미 소비된 것을 초과하는 0개의 추가 MAU가 소비됩니다.

가상 코치 보고서에 대해 알아보려면 [가상 코치 보고서](/help/migrated/administrators/feature-summary/virtual-coach/virtual-coach-reports.md)(으)로 이동하세요.
