---
jcr-language: en_us
title: 수정된 템플릿에서 트리거된 전자 메일 링크로 인해 발생한 Learning Manager 오류
description: 수정된 템플릿에서 트리거된 전자 메일 링크로 인해 발생한 Adobe Learning Manager 오류
contentowner: nluke
preview: true
source-git-commit: 6abc118c6ad7e66e3ded5bd26b9167c3a0b99e4b
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 73%

---



# 수정된 템플릿에서 트리거된 전자 메일 링크로 인해 발생한 Learning Manager 오류

## 문제

자동 전자 메일/환영 전자 메일/등록 전자 메일 링크를 클릭하면 오류가 발생합니다.

**오류**

HTTP 상태 400 - 잘못된 요청

![](assets/email-404.png)

## 원인

이 오류는 일반적으로 전자 메일 템플릿이 잘못 사용자 정의되었을 때 발생합니다.

**해결 방법**

사용자 정의로 인해 발생할 수 있는 연결이 끊어진 링크 관련 오류를 방지하려면 다음 단계를 따르십시오.

1. 책임자로 로그인합니다.
1. 왼쪽 패널에서 **[!UICONTROL 전자 메일 템플릿]**&#x200B;을 클릭합니다.

1. 필요한 템플릿으로 이동하여 클릭하여 수정합니다.

   그러면 **템플릿 미리 보기** 창이 열립니다.

   ![](assets/email-template.png)

   참고: 전자 메일 템플릿을 편집할 때 다음에 유의합니다.

   * 전자 메일 템플릿은 Learning Manager 인터페이스 내에서 수정하시는 것을 권장합니다.
   * 수정된 템플릿을 Notepad/Word 파일에 복사/붙여넣기 하여 변경 사항의 복사본을 저장합니다.
   * 파란색으로 강조 표시된 템플릿의 동적 텍스트는 변경하지 않습니다. 예: &quot;**조직 이름**&quot;, &quot;**학습자**&quot;, &quot;**여기를 클릭**&quot;, &quot;**인증서 이름**&quot; 등.

1. **[!UICONTROL 저장]**&#x200B;을 클릭하여 템플릿에 적용된 변경 내용을 확인합니다.
1. 전자 메일을 트리거하여 링크가 예상한 대로 작동하는지 확인합니다.
1. 수정된 템플릿에서 **원래로 돌아가기** 옵션을 클릭하여 설정을 원래대로 되돌립니다.
