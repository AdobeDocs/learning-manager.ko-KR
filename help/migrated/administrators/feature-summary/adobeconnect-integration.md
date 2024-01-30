---
jcr-language: en_us
title: Adobe Connect 통합
description: 작성자는 강의 생성 절차 중 Adobe Connect로 가상 강의실 강의를 생성할 수 있습니다. Learning Manager 계정에서 Adobe Connect를 허용하려면 조직의 관리자에게 문의하십시오.
contentowner: jayakarr
source-git-commit: 0052ccb2f5a8f9617bca2c7bad91c0cd18338b66
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 70%

---



# Adobe Connect 통합

조직 관리자는 Adobe Connect 통합을 사용할 수 있도록 Learning Manager 계정 설정을 구성할 수 있습니다.

## Adobe Connect 구성 {#configureadobeconnect}

1. 관리자 로그인의 왼쪽 창에서 **[!UICONTROL &#39;설정&#39;]**&#x200B;을 클릭하여 회사 기본 정보를 봅니다. 다음을 수행합니다. **[!UICONTROL Adobe Connect]** 왼쪽 창에.

   ![](assets/left-pane.png)

   *왼쪽 창에서 Adobe Connect 선택*

1. 다음을 수행합니다. **[!UICONTROL 지금 구성]** 링크 인 **[!UICONTROL Adobe Connect 구성]** 섹션으로 이동하십시오.

   <!--![](assets/configure-now-connect.png)-->

1. 회사의 Adobe Connect 도메인 이름과 로그인 자격 증명을 제공합니다.

   ![](assets/adobeconnect-config.png)

   *도메인 이름 및 자격 증명 추가*

   Adobe Connect URL 샘플: mycompany.adobeconnect.com\
   Adobe Connect 계정 책임자의 전자 메일 ID를 제공해야 합니다.

   Learning Manager에서는 Adobe에서 호스팅된 연결 계정만 지원됩니다. 예: &#39;.adobeconnect.com&#39;.

1. 다음을 수행합니다. **[!UICONTROL 통합].**

   전자 메일 ID를 인증한 후 Connect가 성공적으로 통합되면 Learning Manager에 메시지가 표시됩니다. Adobe Connect를 사용하여 가상 강의실 강의를 자동으로 볼 수 있습니다.

   Adobe Connect 계정 책임자는 Adobe Connect 사용 약관에 동의해야 합니다. 이 권한이 수락되지 않으면 로그인 인증이 실패할 수 있습니다. Adobe Connect 계정을 생성한 후 계정에 한 번 로그인합니다. 처음 로그인하면 약관 페이지가 나타납니다.

   <!--![](assets/mail-confirmation.png)-->

## 가상 강의실 세션 정보 추가 {#addvirtualclassroomsessioninformation}

가상 강의실 강의 작성자가 세션 정보를 제공하지 않으면 책임자가 세션 세부 정보를 넣을 수 있습니다.

책임자 로그인 상태에서 VC 강의 이름을 클릭합니다. 다음을 수행합니다. **[!UICONTROL 인스턴스]** 왼쪽 창에서 을 클릭합니다. **[!UICONTROL 세션 세부 정보]**.  세션 정보를 추가하려면 세션 세부 정보 페이지의 오른쪽 모서리에 있는 편집 아이콘을 클릭합니다.

![](assets/session-creation-admin.png)

*가상 강의실 세션 정보 추가*

가상 강의실 모듈 또는 세션을 생성하기 위한 Adobe Learning Manager와 Adobe Connect의 통합으로, Connect 계정은 사용 사례에 적합한 수의 회의실과 동시 사용자를 지원해야 합니다. 이러한 회의실은 Learning Manager 가상 강의실 모듈을 호스팅하는 데 사용됩니다. Learning Manager의 각 가상 강의실 모듈이나 세션은 새로운 연결 미팅룸을 동적으로 만듭니다.

Adobe Learning Manager와 별도로 Adobe Connect를 구입해야 합니다.

## 학습자 출결사항 {#learnersattendance}

가상 강의실 강의 호스트가 세션에 참석하지 않으면 세션에 참석한 학습자의 출결이 자동으로 등록되지 않습니다. 이러한 시나리오에서 관리자는 출석을 수동으로 기록할 수 있습니다.

가상 교실 강좌를 클릭하고 다음 페이지의 왼쪽 창에서 &#39;출석&#39;을 클릭하여 출석을 기록합니다.
