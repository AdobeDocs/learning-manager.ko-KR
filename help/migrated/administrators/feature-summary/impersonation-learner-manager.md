---
description: 관리자는 대리 로그인 세션을 시작하여 학습자 및 관리자 계정을 보유한 사용자 대신 로그인할 수 있습니다.
jcr-language: en_us
title: 학습자 및 관리자의 대리 로그인
contentowner: saghosh
exl-id: 0306f255-283f-43b9-9494-11b3dc3765da
source-git-commit: b5bbb184fc86965255b0247195a50cc65a03cd1a
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 56%

---

# 학습자 및 관리자의 대리 로그인 {#impersonation-of-learner-and-manager}

대규모 조직의 고객 지원 담당자가 학습자의 문제를 해결하려면 대리 로그인 기능이 필요합니다.

책임자는 다른 사용자를 대신해 로그인하여 같은 조직의 학습자와 관리자의 모든 활동을 확인하고 테스트해볼 수 있습니다.

>[!NOTE]
>
>사용자 정의 관리자는 사용자를 대신해 로그인할 수 없습니다. 관리자만 사용자 대신 로그인할 수 있습니다.

## 작동 방식

관리자는 사용자(내부 또는 외부)를 검색한 다음 해당 사용자를 대신해 로그인할 수 있습니다. 그런 다음 책임자가 사용자 페이지(해당하는 경우 관리자 앱 또는 그 밖의 경우 학습자 앱)로 리디렉션된 후 세션에서 로그아웃합니다. 그런 다음 책임자는 대신 로그인한 사용자의 프로필 작성 페이지로 리디렉션됩니다.

대리 로그인 기능을 사용할 때는 다음과 같은 사항을 유념해야 합니다.

* 모든 관리자에게는 기본적으로 이 기능이 표시됩니다.
* 대리 로그인 대상은 계정의 활성 사용자로 한정됩니다.
* 책임자는 자신을 대신해 로그인할 수 없습니다.
* 책임자는 60분 동안만 로그인할 수 있습니다.
* 읽기 전용 액세스 권한이 있는 사용자 정의 관리자는 사용자를 대신해 로그인할 수 없습니다.

## 사용자 대리 로그인

사용자 대신 로그인하려면 다음 단계를 따르십시오.

1. 책임자로 앱에 로그인합니다.
1. &#39;프로필&#39; > &#39;사용자 대리 로그인&#39;을 선택합니다.

   대리 로그인 대상은 한 번에 한 명의 사용자로 한정됩니다.

1. 대리 로그인 모드에 있는 검색 상자에 (내부/외부) 사용자를 입력하여 검색합니다. 대리 로그인 대상은 한 번에 한 명의 사용자로 한정됩니다. &#39;진행&#39;을 선택합니다.

   사용자 이메일, UUID 등으로도 검색할 수 있습니다.

1. 사용자 대신 로그인한다는 확인 메시지가 나타납니다.

   &#39;진행&#39;을 선택합니다.

   &quot;가장 모드: &quot;사용자 이름(사용자 이메일)&quot;으로 로그인했습니다. 로그아웃&quot;이라는 내용의 확인 메시지가 페이지 헤더에 나타납니다.

**가장된 세션은 60분 동안 유지됩니다.**

학습자 또는 관리자 역할로 변경하면 책임자가 사용자의 대리 로그인 상태에 있다는 메시지가 표시됩니다.

## 로그인 및 액세스 보고서

책임자의 로그인 및 액세스 내역이 로그인 및 액세스 보고서에 기록됩니다. 책임자가 사용자 대신 로그인할 때마다 그 내역을 기록한 보고서가 생성됩니다.

다음과 같은 열이 보고서에 추가됩니다.

* 사용자 이름을 사용한 대리 로그인
* 사용자 이메일을 사용한 대리 로그인

이 두 개의 열은 보고서 끝에 추가됩니다.

로그인할 때마다 따로 보고서에 산정됩니다.

## 지원되지 않는 환경

* AEM 구성 요소를 사용한 대리 로그인
* 모바일 앱에서 대리 로그인
* 모바일 몰입형 앱에서 대리 로그인
* 몰입형 앱에서 대리 로그인 ALM 앱에만 적용됩니다.

## 자주 묻는 질문

+++대리 로그인 상태에서도 Adobe Learning Manager에 로그인할 수 있습니까?

그렇습니다. 사용자는 대리 로그인과 무관하게 로그인할 수 있습니다.
+++

+++대리 로그인 이벤트는 각기 따로 산정됩니까?

그렇습니다. 대리 로그인 상태에서 관리자의 로그인 액세스/방문 횟수는 각기 따로 산정됩니다.
+++

+++대리 로그인 제한 시간은 얼마입니까?

60분입니다. 대리 로그인 대상인 사용자가 60분 이내에 브라우저 창을 닫고 기본 URL로 이동하더라도 대리 로그인 활동이 계속되고 배너 메시지가 표시됩니다.
+++
