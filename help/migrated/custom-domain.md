---
jcr-language: en_us
title: 사용자 정의 도메인 지원
description: 사용자 정의 도메인은 Learning Manager의 Azure 인스턴스에서 지원되지 않습니다.
contentowner: saghosh
source-git-commit: 8635072782253cbac3f913953797cae7c0bc5ef4
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 67%

---



# 사용자 정의 도메인 지원

사용자 정의 도메인은 Learning Manager의 Azure 인스턴스에서 지원되지 않습니다.

## 개요 {#overview}

사용자 정의 도메인 지원을 통해 고객은 Learning Manager에서 계정에 사용할 수 있는 도메인 이름에 대한 완전한 제어 기능을 확보할 수 있습니다. 고객은 별도로 사용자 정의 도메인을 구매하고 Adobe 팀과 함께 학습 플랫폼에 대한 로그인 URL로 이를 설정해야 합니다.

이렇게 하면 고객은 로그인 및 액세스 환경을 화이트 레이블링할 수 있어 사용자는 Adobe 또는 Adobe Learning Manager의 존재를 보지 못합니다.

예를 들어, 사용자가 Adobe 도메인에 있는 것과 동일한 환경을 얻을 수 있도록 도메인을 사용자 정의하려는 경우. 만약 ABC사가 그들의 고객들을 교육시키기를 원한다면, 그것은 그들이 라는 지역에 착륙하기를 원한다 `abc.com/mylearning`, 대신 `learningmanager.adobe.com/abc-inc/mylearning`.

>[!NOTE]
>
>전제 조건으로 도메인을 등록해야 합니다. 그러면 Adobe이 URL을 사용자 정의하는 과정을 안내합니다.


사용자 정의 도메인 기능은 추가 비용으로 사용할 수 있습니다. 자세한 내용은 고객 성공 관리자에게 문의하십시오.

* 학습자 역할의 경우 도메인이 다음으로 시작합니다. `https://cdn.<customer_custom_domain>/` 예를 들면 다음과 같습니다. `https://cdn.elearningstage1.cpdomaintest.in/`
* 다른 모든 역할의 경우 도메인은으로 시작합니다. `https://<customer_custom_domain>/`. For example, `https://elearningstage1.cpdomaintest.in/`

`<customer_custom_domain>` 은 사용자 정의 가능한 부품입니다.

## 계정에서 사용자 정의 도메인을 설정하는 방법 {#howtosetupacustomdomainonanaccount}

전제 조건으로 고객은 도메인 이름을 소유하고 공급업체로부터 도메인을 구매해야 합니다.

한 예로 고객이 가상의 도메인 **acme.com**&#x200B;을 소유하고 있다고 생각해 보겠습니다. 고객은 **learning.acme.com**&#x200B;에서 Learning Manager 콘텐츠가 제공되기를 바랍니다.

아래 단계에 따라 사용자 정의 도메인을 설정하십시오.

1. 고객은 도메인에 **세 개의 CNAME 레코드를 추가**&#x200B;해야 합니다.

   * **learning.acme.com:** Adobe이 공유한 Learning Manager의 ALB 공용 엔드 포인트
   * **lrs.learning.acme.com:** learning.acme.com에서 가리키는 ALB 공용 끝점
   * **cdn.learning.acme.com:** Adobe이 공유하는 CDN 끝점

1. 고객은 다음 도메인에 대한 SSL 인증서를 제공해야 합니다.

   * learning.acme.com
   * lrs.learning.acme.com
   * cdn.learning.acme.com

1. Adobe는 도메인에 요청을 제공하기 위해 이러한 SSL 인증서를 AWS ALB에 업로드합니다.
1. Adobe는 SAN 인증서에 learning.acme.com을 추가합니다.
1. Adobe는 메타데이터에 사용자 정의 도메인 URL이 포함되므로 고객에 대한 SP 메타데이터를 생성합니다.

   * 고객이 소셜 로그인을 보유하고자 하는 경우 Adobe는 허용된 URL 목록에 소셜 사이트의 리디렉션 URL 패턴을 포함해야 합니다.
   * 고객이 SSO를 활성화하면 고객은 IDP와 함께 리디렉션 URL에 도메인을 포함시키도록 해야 합니다. 고객은 Adobe와 IDP 메타데이터 XML을 공유해야 합니다. 그러면 Adobe는 고객 계정의 SSO 설정을 업데이트해야 합니다.

1. 그러면 Adobe는 고객의 도메인을 포함하도록 S3 CORS 규칙을 수정합니다.
