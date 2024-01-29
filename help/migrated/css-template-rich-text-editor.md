---
jcr-language: en_us
title: 서식 있는 텍스트 편집기용 CSS 템플릿
description: 서식 있는 텍스트 편집기용 CSS 템플릿
contentowner: saghosh
preview: true
source-git-commit: 9325abb9cda8c8a019c9d72c1944a8284f38f83e
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---



# 서식 있는 텍스트 편집기용 CSS 템플릿

## CSS가 필요한 이유는 무엇입니까?

서식 있는 텍스트는 HTML 태그로 구성됩니다. 태그를 그대로 렌더링하면 브라우저에서 기본 스타일을 적용합니다. 이것은 종종 회사의 스타일 지침과 맞지 않습니다. 지침을 충족하려면 CSS가 필요합니다.

## 기본 스타일

첨부된 CSS 스타일시트에는 Learning Manager에서 적용한 스타일이 포함되어 있습니다. 스타일은 대부분의 사용 사례를 고려하여 조정됩니다. 첨부된 CSS 파일을 다운로드하고 규칙 및 빌드 시스템에 따라 웹 앱으로 가져옵니다. 정의된 CSS 클래스는 ql-editor 클래스에서 네임스페이스 지정되어 있으며 기존 스타일을 방해하지 않습니다.

## 스타일 사용자 정의

기본 스타일은 모든 사용자의 요구를 충족시키지 못할 수도 있습니다. 사용자 정의는 제공된 CSS를 재정의하여 수행할 수 있습니다. 모든 스타일은 ql-editor에서 하위 항목 선택기로 래핑됩니다. 다음 클래스가 사용됩니다.

* **들여쓰기**: li.ql-indent-$number. $number는 1-9사이의 숫자입니다.
* **크기**: ql-size-small, ql-size-large, ql-size-huge
* **맞춤**: ql-align-center, ql-align-justify, ql-align-right
* **색상**: ql-color-$color. $color는 흰색, 빨간색, 주황색, 노란색, 녹색, 파란색, 자주색입니다
* **배경**: ql-bg-$color. $color는 검은색, 빨간색, 주황색, 노란색, 녹색, 파란색, 자주색입니다
* **html 태그**: p, ol, ul, pre, blockquote, h1, h2, h3, h4, h5, h6

[사용자 정의에 사용할 CSS 파일입니다.](assets/ql-headless.css)
