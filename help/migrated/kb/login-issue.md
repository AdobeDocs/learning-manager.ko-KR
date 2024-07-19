---
jcr-language: en_us
title: Learning Manager의 로그인 문제
description: Adobe Learning Manager의 로그인 문제
contentowner: nluke
exl-id: 516c1a20-f185-4ace-a1e7-2cd89644863c
source-git-commit: a0c01c0d691429bd66a3a2ce4cfc175ad0703157
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 87%

---

# Learning Manager의 로그인 문제

## 문제

Adobe Learning Manager에 로그인할 수 없습니다.

## 오류

Adobe Learning Manager에 로그인하려고 하면 아래와 같은 오류 메시지가 표시됩니다.

![](assets/cp-error.png)

*만료된 세션에 대한 오류 메시지*

## 이유

사용자가 SSO로 로그인할 때 브라우저에 저장되는 세션 쿠키가 생성됩니다. 또한 사용자가 다른 응용 프로그램에 로그인할 수도 있습니다. 대부분의 SSO는 24시간 후에 로그아웃하도록 구성되어 있습니다. 새 세션에 대해 사용자가 다시 인증해야 합니다.

특정 인스턴스에 따라 오래된 SSO 쿠키 때문에 사용자가 시스템에 액세스할 수 없습니다. 해당 쿠키는 인증을 위해 Adobe Learning Manager로 전달됩니다. 사용자가 브라우저를 오랫동안 닫지 않거나 로그아웃하지 않으면 세션이 종료되지 않습니다.

Adobe Learning Manager은 이러한 오래된 쿠키를 거부하여 오류가 발생합니다.

## 해결 방법

Adobe Learning Manager에서 오래된 쿠키가 거절되는 경우 아래 옵션을 확인합니다.

1. 브라우저 쿠키와 캐시를 지웁니다. 자세한 내용은 이 [문서](unable-log-in-learning-manager.md)를 확인합니다.

   또는 IDP 관리자가 특정 설정 시간 이후 강제 로그아웃을 정의할 수 있습니다. 이 단계에서는 사용자가 새 세션을 시작하도록 다시 인증합니다.

오류가 발생하는 다른 이유도 있지만 위 오류는 일반적인 시나리오입니다.

## 참조 링크:

[Microsoft: 평생 동안 조건부 액세스 세션](https://docs.microsoft.com/ko-kr/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime)
