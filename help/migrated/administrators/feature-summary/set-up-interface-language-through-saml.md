---
description: SAML을 사용하여 인터페이스 언어를 구성하는 방법에 대해 알아보십시오.
jcr-language: en_us
title: SAML을 통해 인터페이스 언어 설정
contentowner: chandrum
source-git-commit: 448119eda15c8d7dfe10150c09fbbe7c530f35e8
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---


# SAML을 통해 인터페이스 언어 설정

이제 Adobe Learning Manager(ALM)에서 언어에 대한 SAML 속성을 허용합니다. 그런 다음 이 속성이 사용자의 인터페이스 및 콘텐츠 언어 설정에 매핑되어 선호하는 언어로 LMS와 원활한 상호 작용을 보장합니다. 이러한 언어 설정의 구성은 SSO(Single Sign-On)용 SAML을 사용하는 IAM(Identity and Access Management) 플랫폼을 통해 관리됩니다. 이렇게 하면 SP(서비스 공급자) 시작 로그인과 IdP(신원 공급자) 시작 로그인을 모두 지원하여 사용자가 선택한 언어로 인터페이스와 콘텐츠를 볼 수 있습니다. 워크플로우는 다음과 같습니다.

1. Okta에서 응용 프로그램 만들기
2. Okta에서 사용자 추가
3. ALM에서 SSO 구성

## Okta에서 응용 프로그램 만들기

Okta에서 애플리케이션을 만들려면 다음 단계를 따르십시오.

1. 회사 이메일을 사용하여 Okta에서 개발자 계정을 만들고 계정에 로그인합니다.
2. **[!UICONTROL 응용 프로그램]** > **[!UICONTROL 앱 통합 만들기]**&#x200B;를 선택합니다.
3. **[!UICONTROL SAML 2.0]**&#x200B;을 선택한 다음 **[!UICONTROL 다음]**&#x200B;을 선택합니다.
4. 응용 프로그램 이름을 입력하고 [다음]을 선택합니다.
5. 다음 필드를 구성합니다.

   * **[!UICONTROL Single Sign-On URL]**: 응용 프로그램을 연결할 특정 도메인 URL을 입력하십시오(예: [https://learningmanagerstage.adobe.com/saml/SSO](https://learningmanagerstage.adobe.com/saml/SSO)). 필요한 경우 환경 URL을 변경합니다.
   * **[!UICONTROL 대상 그룹 URI(SP 엔터티 ID)]**: 위와 동일한 환경 URL을 사용하십시오.
   * **[!UICONTROL 이름 ID 형식]**: 전자 메일 주소를 선택하십시오.
   * **[!UICONTROL 응용 프로그램 사용자 이름]**: Okta 사용자 이름을 선택하십시오.

6. 속성 명령문에서 다음(또는 필요에 따라 추가 필드)을 추가합니다.
   * **이름**: 로케일
   * **이름 형식**: 정의되지 않음
   * **값**: user.locale

7. 다음 을 선택한 다음 마침 을 선택합니다.
8. 완료되면 SAML 서명 인증서 로 스크롤합니다.

   * 상태가 **[!UICONTROL 활성]**&#x200B;인 행을 찾습니다.
   * **[!UICONTROL 작업]** > **[!UICONTROL IdP 메타데이터 보기]**&#x200B;를 선택합니다.
   * 이렇게 하면 XML 파일이 새 탭에서 열립니다. XML 코드를 복사하여 로컬에서 .xml 파일로 저장합니다.

## Okta에서 사용자 추가

Okta에서 사용자를 만들려면 다음 단계를 따르십시오.

1. **[!UICONTROL 디렉터리]** > **[!UICONTROL 인물]**&#x200B;을 선택한 다음 **[!UICONTROL 인물 추가]**&#x200B;를 선택합니다.
2. 사용자에 필요한 세부 정보를 입력하고 **[!UICONTROL 저장]**&#x200B;을 선택합니다.
3. 새 사용자의 사용자 이름을 검색하여 선택합니다.
4. **[!UICONTROL 응용 프로그램 할당]**&#x200B;을 선택합니다.
5. 이전에 만든 응용 프로그램을 선택한 다음 **[!UICONTROL 저장]**&#x200B;을 선택합니다.
6. 사용자의 프로필로 이동하여 **[!UICONTROL 편집]**&#x200B;을 선택합니다.
7. 로캘 필드에서 필요한 값(예: fr_FR, en_US)을 입력하고 **[!UICONTROL 저장]**&#x200B;을 선택합니다.

## ALM에서 SSO 구성

ALM에서 SSO를 구성하려면 다음 단계를 따르십시오.

1. 관리자로 로그인합니다.
2. **[!UICONTROL 설정]** > **[!UICONTROL 로그인 방법]**&#x200B;을 선택합니다.
3. **[!UICONTROL SSO(Single Sign-On) 구성]** 탭으로 이동합니다.
4. **[!UICONTROL 새 SSO 구성 추가]**&#x200B;를 선택합니다.

   ![](assets/sso-add.PNG)
   _ALM에서 sso 추가_

5. 다음 세부 정보를 구성하고 저장 을 선택합니다.
   * 구성 이름을 입력합니다.
   * **[!UICONTROL SSO(Single Sign-On) 설정]** 드롭다운에서 **[!UICONTROL IDP 시작]**&#x200B;을 선택합니다.
   * **[!UICONTROL IDP 시작 인증 URL]**&#x200B;의 경우:

      * 이전에 다운로드한 메타데이터 XML 파일을 엽니다.
      * 위치 값을 검색하고 복사합니다.
      * IDP 시작 인증 URL 필드에 이 값을 붙여넣습니다.

   * **[!UICONTROL 메타데이터 XML 파일]**&#x200B;의 경우: 이전에 다운로드한 .xml 파일을 업로드합니다.

6. **[!UICONTROL 설정]** 탭으로 돌아갑니다.
7. 드롭다운에서 **[!UICONTROL Single Sign-On 구성]**&#x200B;을 선택합니다.
8. **[!UICONTROL SSO 설정]** 드롭다운에서 이전에 만든 구성 이름을 선택합니다.
9. **[!UICONTROL 저장]**&#x200B;을 선택합니다.

## 사용자 로그인 및 언어 설정

사용자가 SSO를 통해 자격 증명을 사용하여 로그인하면 IDP로부터 전달된 언어 속성이 ALM의 사용자 인터페이스 및 콘텐츠 언어 필드에 매핑됩니다. 언어 설정은 캐싱 시간 없이 사용자 인터페이스 및 콘텐츠에 즉시 반영됩니다.

사용자는 사용자 프로필 섹션에서 언어 설정을 수동으로 업데이트할 수 있습니다. 이렇게 수동으로 업데이트된 언어 환경 설정은 계속 적용되며 향후 로그인 시 IDP 설정에 의해 재정의되지 않습니다.

사용자가 ALM에서 소프트 삭제된 경우 언어 설정은 데이터베이스에 유지됩니다. 동일한 사용자가 다시 추가되면 이전에 설정한 언어가 복원됩니다.

관리자는 사용자 활동, 학습 요약 및 준수 대시보드 보고서에서 언어별 세부 정보를 확인할 수 있습니다.


