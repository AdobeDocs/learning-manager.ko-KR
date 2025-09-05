---
jcr-language: en_us
title: Learning Manager는 GDPR을 준수함
description: Adobe Learning Manager의 GDPR 준수
contentowner: dvenkate
exl-id: 8ea31464-b4ce-49e8-b471-5630f0216aa4
source-git-commit: a01ec6117ad49a1f9af0b31d48ad19ddc8443dde
workflow-type: tm+mt
source-wordcount: '678'
ht-degree: 39%

---

# Learning Manager는 GDPR을 준수함

>[!IMPORTANT]
>
>본 문서의 내용은 법률자문이 아니며, 법률자문을 대신하는 것이 아니다. GDPR에 관한 자세한 내용은 회사 법무 부서에 문의하십시오.

Adobe Learning Manager은 GDPR 준수를 준수하여 사용자 데이터가 안전하고 투명하게 관리되도록 합니다. 사용자 삭제(모든 개인 데이터 영구 삭제) 기능과 같은 필수 GDPR 기능을 제공하고 책임자가 요청 시 사용자와 정보를 공유하기 위한 학습자 성적 증명서를 생성할 수 있도록 합니다.

모든 사용자 데이터는 SHA-256과 같은 표준을 사용하여 전송 및 저장 중에 강력한 암호화로 보호됩니다. 일부 통합의 경우 학습자는 데이터를 공유하기 전에 동의를 얻는지 확인하여 인증해야 합니다. 이러한 개인 정보 보호 및 보안 제어는 Adobe Learning Manager을 사용하는 조직이 GDPR을 준수하고 학습자 정보를 보호하는 데 도움이 됩니다.

+++GDPR은 무엇입니까?

GDPR은 2018년 5월 25일부터 시행되는 유럽 연합의 새로운 규정입니다. GDPR은 데이터 개인 정보 보호에 대한 강력한 규제를 적용하고 최종 사용자가 자신의 개인 데이터에 대해 책임질 수 있도록 합니다.

+++

+++GDPR은 Adobe Learning Manager 고객에게 어떤 방식과 이유로 적용됩니까?

GDPR은 EU 규정이지만 EU 거주자가 될 수 있는 모든 사용자의 개인 정보를 수집하는 전 세계 기업에 적용됩니다.  Learning Manager 고객인 경우 GDPR이 귀사에 적용될 수 있는지 검토하십시오.

+++

+++Adobe는 Learning Manager의 공급업체로서 어떤 역할을 수행합니까?

GDPR에 따라 기업에서 EU 거주자에게 제품 또는 서비스를 제공하고 개인정보를 수집, 추적 및 모니터링하는 방법과 이유를 결정하는 경우 [데이터 컨트롤러](https://gdpr-info.eu/art-24-gdpr/)로 간주됩니다. Adobe Learning Manager 고객의 경우 이러한 활동 중 하나를 수행한다면 데이터 컨트롤러로 간주됩니다.

컨트롤러 대신 데이터를 처리하는 비즈니스는 [데이터 프로세서](https://gdpr-info.eu/art-28-gdpr/)로 간주됩니다. 클라우드에서 호스팅되는 LMS Adobe Learning Manager의 공급업체로서 Adobe은 데이터 프로세서의 역할을 수행합니다. [GDPR 및 비즈니스](https://www.adobe.com/privacy/general-data-protection-regulation.html)에 대한 자세한 내용은 다음과 같습니다.

+++

+++Learning Manager로 어떻게 GDPR을 준수할 수 있습니까?

Learning Manager는 GDPR 준수를 지원하는 다음 도구와 프로세스에 내장되어 있습니다. 제품뿐 아니라 모든 프로세스가 규정을 완전히 준수하도록 지원하기 위해 계속해서 준수팀과 평가해야 할 수도 있습니다.

**삭제권(잊힐 권리) - 데이터 컨트롤러에게 도달:** GDPR에서는 데이터 컨트롤러가 해당 사용자를 위해 삭제권 기능을 지원하도록 요구합니다. 이는 모든 사용자가 데이터 컨트롤러에게 해당 사용자에 대해 저장된 모든 개인 데이터를 영구적으로 삭제하도록 요청할 권한이 있음을 의미합니다. 이러한 요청을 받고 해당 요청이 유효하다고 판단하는 경우, 이제 이 기능이 Learning Manager에서 [사용자 삭제](../administrators/feature-summary/purge-users.md) 기능을 통해 제공됩니다. 이 기능을 사용하면 개별 요청에 따라 책임자가 특정 개인과 관련된 모든 데이터를 영구적으로 삭제할 수 있습니다. 이때 Learning Manager에서는 해당 데이터베이스에서 데이터를 즉시 영구 삭제하고, 백업 로그(시스템 복구용)도 이어서 자동으로 삭제됩니다.

**삭제권(잊힐 권리) - 데이터 프로세서에게 도달:** 최종 사용자도 자신들의 PII를 삭제하기 위해 개별적으로 Adobe에 연락할 수 있습니다. 이 경우 Learning Manager에서는 해당 사용자의 PII를 소유한 계정을 자동으로 감지하며, Adobe에서는 그와 같은 요청을 즉시 관리자에게 알립니다. 그런 다음 책임자는 요청의 유효성을 평가하고 사용자 제거 기능을 통해 요청에 대한 호출을 수행할 수 있습니다.

**액세스 권한:** GDPR에서는 최종 사용자에게 컨트롤러가 해당 최종 사용자에게 저장했을 수 있는 데이터를 요청할 수 있는 권한을 허용합니다. 이 요청을 지원하기 위해 Learning Manager에서는 관리자가 사용자와 공유할 수 있는 Learner Transcript를 자체적으로 생성할 수 있습니다.

**설계에 따른 개인정보 보호, 데이터 암호화:** 데이터 보안을 보장하기 위해 업계 최고 수준의 암호화 표준을 사용하여 전송 중인 데이터와 저장 중인 데이터를 모두 처리합니다. 사용된 암호화 알고리즘은 SHA-256입니다. 이렇게 하면 사용자가 저장하는 모든 데이터를 다른 사람이 악용하지 못하도록 적절하게 보호할 수 있습니다.

+++
