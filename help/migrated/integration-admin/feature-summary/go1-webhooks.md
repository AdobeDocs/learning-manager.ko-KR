---
description: 학습자가 브라우저를 일찍 닫는 경우에도 Go1 완료 Webhook을 통해 Adobe Learning Manager에서 강의 완료를 캡처하는 방법에 대해 알아봅니다
jcr-language: en_us
title: Webhook을 사용한 Go1 완료 추적
exl-id: 25c9c401-905f-4408-89ac-ac630a45a0c7
source-git-commit: aaea92d190b8ab22ce9f08c309faf5caa0b58a69
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%
---

# Webhook을 사용한 Go1 완료 추적

## 개요

이제 Adobe Learning Manager에서 Go1 콘텐츠에 대한 Webhook 기반 완료 추적을 지원합니다. 이 개선은 Go1과 Learning Manager 간의 강의 완료 동기화의 안정성을 개선합니다. 완료 이벤트는 학습자가 강의를 완료한 후 바로 강의 플레이어를 종료할 때도 캡처됩니다.

Go1은 학습자가 Go1 강의를 완료할 때마다 Learning Manager에 강의 완료 알림을 보내기 위해 Webhook을 사용합니다. Learning Manager는 학습자의 브라우저 세션과는 별도로 이러한 완료 이벤트를 수신하고 처리합니다.

Go1은 Learning Manager가 완료 이벤트 수신을 확인할 때까지 Webhook 전달을 다시 시도합니다. 이를 통해 학습 기록 누락 또는 불완전 생성을 방지할 수 있습니다.

## 이 개선으로 해결되는 문제

이전에는 학습자의 브라우저 세션이 활성 상태인 동안 완료 추적은 Go1 플레이어와 Learning Manager 간의 통신에 의존했습니다. 완료 상태가 완전히 처리되기 전에 학습자가 브라우저 창을 닫거나 다른 곳으로 이동했다면 완료 기록은 유실될 수 있습니다.

결과:

* 강의 완료 내용이 학습자 성적 증명서에 나타나지 않을 수 있습니다.
* 관리자는 실제 완료와 기록된 완료 사이의 불일치를 찾을 수 있습니다.
* 누락된 완료 이벤트는 자동으로 복구할 수 없습니다.

## 이벤트 워크플로우

1. 학습자는 Go1 과정을 실행하고 완료합니다.
1. Go1은 완료를 기록합니다.
1. Go1은 완료 Webhook을 Learning Manager로 전송합니다.
1. Learning Manager는 완료 이벤트를 확인하고 수락합니다.
1. Learning Manager는 학습자의 완료 상태를 업데이트합니다.
1. Learning Manager에서 이벤트를 승인하지 않으면 Go1은 자동으로 전달을 다시 시도합니다.

## 자주 묻는 질문

**이 변경을 수행하려면 관리자 구성이 필요합니까**

아니요. 이 변경에는 관리자 구성이 필요하지 않습니다.

**영향을 받는 기존 Go1 과정**

아니요. 기존 Go1 강의는 영향을 받지 않습니다. 이 개선은 Go1 콘텐츠에 대한 완료 동기화를 개선합니다.

**학습자가 브라우저를 일찍 닫으면 어떻게 됩니까**

Go1은 학습자의 브라우저 세션과 관계없이 완료 Webhook을 보냅니다. 학습자가 강의 플레이어를 종료하더라도 Learning Manager에서 완료 이벤트를 인식할 때까지 Go1은 계속 전달을 다시 시도합니다.
