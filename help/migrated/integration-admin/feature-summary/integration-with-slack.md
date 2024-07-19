---
jcr-language: en_us
title: Slack과 통합된 Learning Manager
description: Slack과 통합된 Learning Manager
contentowner: dvenkate
source-git-commit: 864b1796f1ca99ae7b5643e8c58d1756ff2461a1
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 44%

---



# Slack과 통합된 Learning Manager

Learning Manager에서 커넥터로 **제거** **Slack**&#x200B;을(를) 수행했습니다. 더 이상 Slack 커넥터에 액세스할 수 없습니다.

Slack 사용자는 사용 중인 Slack 팀의 Slack 앱 디렉터리에서 Adobe Learning Manager 앱을 설치한 뒤 Slack에서 바로 Learning Manager 콘텐츠를 탐색할 수 있습니다. Primebot과 상호 작용하여 새 강의를 검색하고, 권장 사항을 보고, 예정된 기한 알림을 받을 수 있습니다. Slack 내에서 학습에 등록하거나 학습으로 이동할 수도 있습니다.

Slack을 위한 Learning Manager 앱은 Learning Manager의 Azure 인스턴스에서 지원되지 않습니다.

## Adobe Learning Manager 앱 설치 {#installingadobecaptivateprimeapp}

학습자로서 귀하는 Slack 계정에 CP Prime 앱을 설치할 수 있습니다. 앱을 설치하려면 귀하의 Slack 계정에서 앱 디렉터리를 열고 Learning Manager를 검색합니다. 앱을 다운로드하고 설치합니다. 계정에서 앱이 승인되지 않는 경우 통합 책임자에게 승인을 요청합니다. 승인된 경우, 로그인할 수 있습니다.

## 통합 책임자로 학습자 로그인 승인 {#approvinglearnersigninasanintegrationadmin}

통합 책임자는 학습자가 Slack 시 Prime 응용 프로그램을 사용할 수 있는 권한을 승인하려면 다음 단계를 따르십시오.

1. 왼쪽 창에서 **[!UICONTROL 응용 프로그램]**&#x200B;을 선택한 다음 **[!UICONTROL 피처드 앱]** 탭을 클릭합니다.

   ![](assets/featuredapps.jpg)

1. **[!UICONTROL Slack]** 타일을 클릭하면 Slack 통합 페이지가 열립니다. 오른쪽 위 모서리에 있는 **[!UICONTROL 승인]**&#x200B;을 클릭하여 응용 프로그램을 승인합니다.

   ![](assets/approval.png)

1. **[!UICONTROL 응용 프로그램]** 페이지로 돌아갑니다. 승인이 완료되면 **[!UICONTROL 외부 앱]** 탭에 Slack이 표시됩니다.
1. 이제 학습자는 Slack으로 Prime 계정에 로그인할 수 있습니다.

## Primebot 기능 {#primebotfunctionalities}

이제 Primebot과 상호 작용을 시작할 수 있습니다. 봇의 기능은 다음과 같습니다.

1 - 명령

&#42;/prime&#42;은(는) Adobe Learning Manager 계정에 대한 일회성의 특정 쿼리에 사용할 수 있습니다.

사용 가능한 부 명령은 다음과 같습니다.

/prime `<query>` 찾기 - 강의, 인증 등을 검색합니다.

/prime recommend - 추천 표시

/prime deadlines - 지났거나 예정된 기한 표시

/prime enrollments - 등록 표시

/prime skills - 스킬 표시

/prime notifications - 알림 표시

/prime catalogs - 카탈로그 표시

/prime invite - [관리자 전용] 현재 팀에 Slack 사용자를 초대하여 primebot을 사용해 보십시오.

/prime profile- 프로필 표시

/prime logout - 이 Slack 팀에서 Prime 계정 로그아웃

/prime help - 도움말 메시지 표시

2 - 권장

`show my recommendations`과(와) 같은 구문을 시도하여 Adobe Learning Manager 계정에서 권장되는 강의, 인증, 학습 프로그램의 개인화 목록을 볼 수 있습니다.

3 - 검색

`search for machine learning` 또는 `search for artificial intelligence`과(와) 같은 구를 사용해 볼 수 있습니다. `search for machine learning certifications`, `search for artificial intelligence courses` 또는 `search for adobe photoshop job aids`과(와) 같은 구를 사용하여 학습 개체의 종류를 지정할 수 있습니다. 카탈로그 내에서 `search for machine learning in Lynda catalog`과(와) 같은 구문을 사용하여 검색할 수도 있습니다.

4 - 기한

`show my deadlines`과(와) 같은 구문을 사용하여 Adobe Learning Manager 계정에서 기한이 지났거나 예정된 기한 목록을 가져옵니다. `show my overdue deadlines` 또는 `show my upcoming deadlines`과(와) 같은 어구를 사용하여 기한이 지났거나 예정된 기한을 필터링할 수 있습니다.
