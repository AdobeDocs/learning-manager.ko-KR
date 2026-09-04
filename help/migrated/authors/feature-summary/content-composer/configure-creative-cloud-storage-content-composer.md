---
jcr-language: en_us
title: Adobe Learning Manager Content Composer용 Creative Cloud 스토리지 구성
description: Adobe Learning Manager Content Composer용 Creative Cloud 스토리지를 구성하는 방법에 대해 알아봅니다. 이 가이드에서는 Creative Cloud 스토리지가 필요한 이유, 관리자가 Adobe Admin Console에서 무료 멤버십 오퍼를 할당하는 방법 및 스토리지 관련 액세스 문제를 해결하는 방법에 대해 설명합니다.
contentowner: saghosh
source-git-commit: 42512cc4cab0d0cdb1e9796610d6fc2f7b5c51d6
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 0%

---


>[!IMPORTANT]
>
>이 문서의 대상: Adobe Learning Manager 사용자가 Content Composer에 액세스하고 사용할 수 있도록 Creative Cloud 스토리지를 활성화해야 하는 관리자 이는 관리자가 스토리지 관련 로그인 또는 액세스 오류를 해결하고 Adobe Admin Console을 통해 무료 멤버십 혜택을 할당하는 데 특히 유용합니다.


Adobe Learning Manager(ALM) Content Composer를 사용하려면 Adobe 계정과 연결된 Creative Cloud 스토리지가 있어야 합니다. Creative Cloud 스토리지가 없는 사용자는 Content Composer에 액세스할 수 없고 로그인 또는 액세스 관련 오류가 발생할 수 있습니다.

조직이 영향을 받는 사용자에게 스토리지를 프로비저닝할 수 있도록 Adobe은 관리자가 Adobe Admin Console을 통해 할당할 수 있는 무료 멤버십 혜택을 제공합니다. 이 오퍼에는 Creative Cloud 스토리지가 포함되며 사용자에게 스토리지 권한을 제공하는 플랜이 아직 없는 경우 사용할 수 있습니다.

## 시작하기 전에

다음을 확인하십시오.

* Adobe Admin Console 관리자 액세스 권한이 있습니다.
* 콘텐츠 작성기 액세스 권한이 필요한 사용자가 식별됩니다.
* 사용자에게 Creative Cloud 스토리지가 포함된 플랜이 이미 있는지 확인했습니다.

## 사용자에게 Creative Cloud 스토리지가 필요한 이유

Content Composer는 Creative Cloud 스토리지를 사용하여 강의를 저장합니다. Adobe 프로필에 스토리지가 할당되지 않은 사용자는 Content Composer를 사용하려고 할 때 오류를 받을 수 있습니다.

![콘텐츠 컴포저 저장소 오류](../assets/coco-storage1.png)

많은 Adobe 고객이 이미 기존 Adobe 제품을 통해 Creative Cloud 스토리지를 보유하고 있으며 영향을 받지 않습니다. 그러나 일부 Adobe Learning Manager 고객은 기본적으로 스토리지가 프로비저닝되지 않을 수 있으며 이를 활성화하려면 관리자가 필요할 수 있습니다.

## 사용자용 무료 Creative Cloud 스토리지 활성화

사용자에게 Creative Cloud 스토리지가 없는 경우 Adobe Admin Console에서 무료 멤버십 혜택을 할당합니다.

1. 관리자 권한이 있는 계정을 사용하여 [Adobe Admin Console](https://adminconsole.adobe.com/)에 로그인합니다. 관리자만 사용자에게 제품 및 오퍼를 할당할 수 있습니다.
2. Admin Console에서 제품 > 체험판 및 특별 혜택을 선택합니다.

   ![Admin Console의 평가판 및 특별 혜택](../assets/coco-storage2.png)

3. 체험판 및 특별 혜택에서 사용할 수 있는 무료 멤버십 혜택을 살펴보십시오. 이는 아직 스토리지 권한이 없는 사용자를 위해 Creative Cloud 스토리지를 활성화하는 권장 방법으로 논의되는 오퍼입니다.

   ![무료 멤버십 혜택](../assets/coco-storage3.png)

4. 필요한 사용자에게 무료 멤버십 혜택을 할당합니다. 할당은 적절한 Admin Console 권한이 있는 관리자만 완료할 수 있습니다.
5. 할당 후 사용자에게 사용 가능한 Creative Cloud 스토리지가 있는지 확인하고 사용자에게 Content Composer에 다시 로그인하도록 요청합니다.

## 무료 멤버십을 통해 제공되는 스토리지

무료 멤버십 오퍼를 보유한 사용자는 Content Composer를 사용할 수 있도록 약 2GB의 Creative Cloud 스토리지를 받습니다.

## 문제 해결

**사용자가 콘텐츠 컴포저에 액세스할 때 오류가 발생합니다**

사용자에게 Adobe 프로필에서 사용할 수 있는 Creative Cloud 스토리지가 있는지 확인합니다.

**사용자가 무료 멤버십 혜택을 볼 수 없습니다.**

다음을 확인합니다.

* 관리자로 로그인됩니다.
* Adobe Admin Console의 제품 영역이 표시됩니다.
* 조직은 오퍼에 액세스할 수 있습니다.

## 자주 묻는 질문

**모든 Adobe Learning Manager 사용자가 자동으로 Creative Cloud 스토리지를 받습니까?**

아니요. 일부 ALM 사용자는 기본적으로 스토리지가 프로비저닝되지 않을 수 있으며 무료 멤버십 오퍼를 통해 추가 권한이 필요할 수 있습니다.

**사용자가 직접 저장소를 사용하도록 설정할 수 있습니까?**

아니요. 스토리지 권한은 Adobe 관리자가 Admin Console을 통해 할당해야 합니다.

**콘텐츠 컴포저에 Creative Cloud 저장소가 필요합니까?**

예. Content Composer는 Adobe 계정과 연결된 Creative Cloud 스토리지가 있는 사용자에 따라 다릅니다.

**사용자가 저장소 관련 오류를 발견하면 관리자는 어떻게 해야 합니까?**

사용자에게 Creative Cloud 스토리지 권한이 있는지 확인합니다. 그렇지 않으면 Adobe Admin Console을 통해 무료 멤버십 오퍼를 할당하고 사용자에게 다시 시도하도록 합니다.

**관리자에게 액세스 또는 권한 문제가 있는 경우 관리자는 어떻게 해야 합니까?**

Adobe Admin Console 관리자가 Creative Cloud 스토리지를 할당하거나 액세스 관련 문제를 디버깅하는 동안 문제가 발생하는 경우, 엔터프라이즈 계정 수준의 지원이 필요할 수 있습니다. 이러한 경우 Admin Console에서 사용 가능한 지원 옵션을 통해 Adobe 엔터프라이즈 지원에 문의하십시오.

자세한 내용은 [기업 지원 Adobe 옵션](https://helpx.adobe.com/kr/business/enterprise/get-help/support-options/support-for-enterprise.html)을 참조하세요.
