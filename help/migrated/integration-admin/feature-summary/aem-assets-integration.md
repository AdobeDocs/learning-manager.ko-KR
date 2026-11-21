---
description: Adobe Experience Manager Assets에서 Adobe Learning Manager으로 학습 콘텐츠 및 이미지를 가져오고 연결된 콘텐츠를 자동으로 최신 상태로 유지합니다.
jcr-language: en_us
title: AEM Assets 통합
exl-id: cd33c0f2-59df-4f35-a7d9-d7bff6b9ffba
source-git-commit: 3c0f45721777421361401cf836a21b88cee3a259
workflow-type: tm+mt
source-wordcount: '3405'
ht-degree: 0%
---

# AEM assets 통합

## 개요

이제 Adobe Learning Manager이 Adobe Experience Manager Assets as a Cloud Service으로 통합되었습니다. 팀은 학습 콘텐츠와 이미지를 Adobe Experience Manager Assets에 저장하고, Adobe Learning Manager으로 가져오고, 한 곳에서 업데이트를 관리할 수 있습니다. 에셋이 변경되면 콘텐츠 라이브러리의 연결된 콘텐츠가 자동으로 업데이트되므로 작성자가 파일을 다시 업로드할 필요가 없습니다.

조직에서 에셋을 한 곳에서 관리하기 때문에 작성자는 사본을 다운로드하고 다시 업로드하는 대신 현재 브랜드 승인을 받은 파일을 사용합니다. Adobe Experience Manager Assets은 또한 각 파일의 버전 기록을 유지하므로 사용 중인 버전과 시기를 기록할 수 있습니다.

셋업은 일회성 작업이고, 가장 주의가 필요한 부분입니다. 설정 후 에셋 가져오기는 다른 업로드와 동일하게 작동합니다.

>[!NOTE]
>
>이 통합은 Prime 계정과 Ultimate 계정을 모두 포함하여 Adobe Experience Manager Assets 라이선스가 있는 모든 Adobe Learning Manager 계정에 사용할 수 있습니다. 동일한 설명서가 두 항목에 모두 적용됩니다.

## 누가 무엇을 하나요

| 역할 | 기능 |
|---|---|
| ALM 통합 관리자 | 계정을 연결하고 통합 설정을 선택합니다. |
| Adobe Admin Console 관리자 | 생성된 기술 계정을 올바른 AEM Assets 제품 프로필에 할당합니다. |
| ALM 관리자 | 통합을 사용하여 다양한 위치에서 이미지를 가져옵니다. |
| ALM 작성자 | 콘텐츠 및 이미지를 가져오고 과정을 빌드합니다. |

각 역할은 통합을 설정하고 사용하는 데 별도의 부분이 있습니다.

## 지원되는 배포

| 항목 | 지원됨 |
|---|---|
| Adobe Experience Manager Assets as a Cloud Service, 작성자 인스턴스 | 예 |
| Adobe Experience Manager Assets as a Cloud Service, 게시 또는 전송 인스턴스 | 아니오 |
| Adobe Experience Manager 온-프레미스 | 아니오 |

>[!NOTE]
>
>Adobe Learning Manager은 에셋이 생성되고 관리되기 때문에 작성자 인스턴스에만 연결됩니다. Publish 및 전송 인스턴스는 현재 통합에 포함되지 않습니다.

## 통합 설정

Adobe Learning Manager을 Adobe Experience Manager Assets에 연결하고 기술 계정을 할당한 다음 업데이트 설정을 선택합니다.

이 작업 과정은 통합 책임자용입니다. 작성자에게 자동 업데이트가 작동하도록 모든 단계를 완료합니다. 설정에는 다섯 가지 부분이 있습니다. IMS 조직에 연결, 기술 계정 찾기, Adobe Admin Console에서 할당, 설정 선택, 작성자에게 액세스 권한 부여.

### 사전 요구 사항 {#setup-prerequisites}

이 모든 요건을 충족해야 합니다. 이 중 하나가 누락되는 것이 연결에 실패하는 가장 일반적인 이유입니다.

* Adobe Learning Manager에는 통합 책임자 역할이 있습니다. 연결 워크플로우는 이 역할에서만 사용할 수 있습니다.
* 선택한 IMS(Adobe Identity Management 시스템) 조직의 IMS 조직 관리자입니다.
* AEM Assets 인스턴스가 Learning Manager와 연결될 수 있는 최소 한 개 이상의 조직에 액세스할 수 있습니다.

IMS 조직 관리자가 아닌 경우 IT 관리자에게 액세스 권한을 부여하거나 사용자와 연결을 실행하도록 요청합니다.

### Adobe Learning Manager이 IMS 조직에 매핑하는 방법

각 Adobe Learning Manager 계정은 하나의 IMS 조직(IMS 프로필이라고도 함)에 연결됩니다. 설정을 계획할 때는 다음 사항에 유의하십시오.

* IMS 조직은 여러 프로그램 및 환경을 포함할 수 있으며 각 프로그램은 Adobe Experience Manager Assets 인스턴스를 포함할 수 있습니다. 연결된 계정에서 이러한 인스턴스를 사용할 수 있습니다.
* 다른 IMS 조직의 인스턴스는 해당 계정과 함께 사용할 수 없습니다.
* 하나의 Adobe Learning Manager 계정에 연결된 IMS 조직은 동시에 다른 계정에 연결할 수 없습니다.

>[!NOTE]
>
>회사에 둘 이상의 IMS 조직이 있는 경우 Adobe Experience Manager Assets 라이선스 및 작성자가 사용할 인스턴스가 있는 조직을 선택하십시오.

### IMS 조직에 연결

1. **통합 관리자**(으)로 Adobe Learning Manager에 로그인합니다.
1. 커넥터 유형으로 **Adobe Experience Manager Assets**&#x200B;을 선택합니다.

   ![](assets/aem-assets-integrationstep1.png)

1. **연결**&#x200B;을 선택합니다.

   ![](assets/aem-assets-integrationstep2.png)

1. 메시지가 표시되면 Adobe ID으로 로그인하고 Adobe Experience Manager Assets 인스턴스가 포함된 IMS 조직을 선택합니다.

   ![](assets/aem-assets-integrationstep3.png)

   ![](assets/aem-assets-integrationstep4.png)

그런 다음 Adobe Learning Manager에서 IMS 조직 관리자 역할 및 인스턴스 액세스를 확인합니다. 두 검사가 모두 통과되면 사용자의 계정이 AEM Assets Author API 범위를 사용하여 이미 생성된 IMS 계정에 선택된 IMS 조직으로 링크되고 조직에 대한 기술 계정이 생성됩니다. 그러면 연결 개요 페이지가 열리고 기술 계정 세부 정보가 표시됩니다.

### 기술 계정 찾기

기술 계정은 조직을 위해 특별히 생성됩니다. Adobe Learning Manager은 백그라운드에서 AEM Assets [열기 API](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)를 사용하여 읽거나 쓰는 데 사용합니다.

1. **통합 관리자**(으)로 로그인하여 **Adobe Experience Manager Assets** 연결 개요 페이지를 엽니다.
1. **자격 증명** 섹션에서 **기술 계정 전자 메일**&#x200B;을(를) 찾습니다.
1. 기술 계정 이메일을 복사합니다. **Adobe Admin Console**&#x200B;에서 계정을 찾는 데 사용합니다.

### Adobe Admin Console에서 기술 계정 할당

Adobe Learning Manager에서 사용할 각 Adobe Experience Manager Assets 인스턴스의 제품 프로필에 기술 계정을 추가합니다. 예를 들어 인스턴스가 10개 있고 이 중 6개만 Adobe Learning Manager에서 작업하도록 하려면 해당 6개의 인스턴스의 프로필에 계정을 할당해야 합니다.

1. 동일한 IMS 조직의 관리자로 **Adobe Admin Console**&#x200B;에 로그인합니다.
2. **제품 및 서비스**&#x200B;를 선택한 다음 **Adobe Experience Manager as a Cloud Service**&#x200B;을 선택합니다.

   ![](assets/aem-assets-integration6.png)

3. Adobe Learning Manager에서 사용할 인스턴스를 선택합니다.

   ![](assets/aem-assets-integration7.png)

4. Adobe Learning Manager에 필요한 액세스 권한이 있는 제품 프로필을 엽니다. 예: AEM 관리자 프로필

   ![](assets/aem-assets-integration8.png)

5. **API 자격 증명 추가**&#x200B;를 선택합니다.

   ![](assets/aem-assets-integration9.png)

6. 기술 계정을 검색합니다. 통합 책임자로부터 복사한 기술 계정 전자 메일과 일치시킵니다. 계정은 보통 목록의 맨 아래에 있습니다.

   ![](assets/aem-assets-integration10.png)

7. 기술 계정을 선택한 다음 **저장**&#x200B;을 선택하십시오.
8. 사용하려는 각 인스턴스에 대해 3~7단계를 반복합니다.

프로필의 API 자격 증명 목록이 비어 있으면 기술 계정이 아직 할당되지 않습니다. 제품 프로필 및 API 자격 증명에 대한 자세한 내용은 Adobe Admin Console 설명서를 참조하십시오.

>[!IMPORTANT]
>
>이 단계를 건너뛰지 마십시오. 기술 계정을 할당하지 않은 경우 작성자는 Adobe Experience Manager Assets에서 에셋을 가져올 수 있지만 자동 업데이트는 작동하지 않습니다. 그런 다음 콘텐츠를 수동으로 업데이트해야 합니다.

### 통합 설정 선택

연결한 후 연결을 활성화하고 Adobe Learning Manager에서 업데이트 및 미리 보기를 처리하는 방법을 선택하십시오.

| 설정 | 기능 |
|---|---|
| 자동 업데이트 | Adobe Experience Manager Assets에서 에셋이 변경될 때 연결된 콘텐츠 라이브러리 항목을 업데이트합니다. |
| 학습 객체 업데이트 | 또한 콘텐츠 라이브러리 항목을 사용하는 학습 개체에도 업데이트를 적용합니다. |
| 공개 미리 보기 링크 | 지원되는 콘텐츠에 대한 미리보기 링크를 만들어 AEM Assets의 에셋 메타데이터에 저장합니다. |

학습 객체 업데이트는 자동 업데이트의 하위 설정입니다. 자동 업데이트가 먼저 활성화된 경우에만 활성화할 수 있습니다. 자동 업데이트를 끄면 작성자가 콘텐츠 라이브러리에서 수동으로 콘텐츠를 업데이트합니다.

>[!IMPORTANT]
>
>이러한 설정의 변경 내용은 끄기 등의 방법으로 최대 1시간 정도 걸릴 수 있습니다. 연결을 활성화한 후에도 동일하게 적용됩니다. 연착이 뭔가 잘못되었다는 뜻은 아니에요. 테스트하기 전에 최대 1시간 정도 기다리세요.

### 작성자에게 Adobe Experience Manager Assets에 대한 액세스 권한 부여 {#give-authors-access}

통합을 설정해도 작성자에게 에셋에 대한 액세스 권한이 부여되지 않습니다. 에셋을 가져오는 Adobe Learning Manager 작성자 또는 관리자는 해당 Adobe Experience Manager Assets 작성자 인스턴스에도 액세스할 수 있어야 합니다.

* 동일한 IMS 조직에서 작성자를 Adobe Experience Manager Assets 작성자 인스턴스의 사용자로 추가합니다.
* 에셋을 검색하고 선택하는 데 필요한 액세스 권한 이상을 부여하십시오. 사용할 역할 및 제품 프로필은 Adobe Experience Manager 관리자가 결정합니다.

>[!NOTE]
>
>이 액세스 권한을 부여하는 것은 Adobe Experience Manager 관리자로서 귀하의 책임입니다. Adobe Learning Manager은 특정 역할을 규정하지 않습니다. 사용자 및 프로필에 대한 도움말은 Adobe Experience Manager Assets 설명서를 참조하십시오.

### 설정 확인

1. 위에서 설명한 설정 지연이 경과될 때까지 기다립니다.
1. 인스턴스에 대한 액세스 권한을 가지는 작성자로 로그인합니다.
1. **콘텐츠 라이브러리**&#x200B;에서 **찾아보기**&#x200B;를 선택하고 **장치** 옆에 **AEM Assets**&#x200B;가 표시되는지 확인합니다.
1. 에셋을 가져와 가져오는지 확인합니다.
1. 에셋이 교체되거나 새 버전이거나 다시 처리되는 경우 몇 분 내에 업데이트되거나 드물게 최대 1시간 정도 소요될 수 있습니다. 1시간 이상 걸리는 경우에는 AEM Assets에서 에셋을 다시 처리할 수 있습니다.

## Adobe Experience Manager Assets에서 콘텐츠 가져오기

Adobe Experience Manager Assets에서 학습 콘텐츠 및 이미지를 가져오고 최신 상태의 콘텐츠에 강의를 빌드합니다.

이 작업 과정은 작성자용입니다. 통합 책임자는 먼저 통합을 설정해야 합니다.

### 사전 요구 사항 {#import-prerequisites}

* 통합 관리자가 계정을 연결하고 연결을 활성화했습니다.
* 연결된 IMS 조직에서 에셋을 보유하고 있는 Adobe Experience Manager Assets 작성자 인스턴스에 액세스할 수 있습니다. Adobe Experience Manager 관리자가 이 액세스 권한을 부여합니다. [작성자에게 Adobe Experience Manager Assets에 대한 액세스 권한 부여](#give-authors-access)를 참조하십시오.

통합이 활성화되면 이를 지원하는 Adobe Learning Manager의 모든 업로드 옵션에 두 개의 소스(장치 및 AEM Assets)가 표시됩니다. 여기에는 강의 이미지에 대한 콘텐츠 라이브러리 및 업로드 옵션이 포함됩니다. 장치는 계속 사용할 수 있으므로 컴퓨터에서 파일을 업로드할 수 있습니다.

### 가져올 수 있는 위치

AEM Assets 옵션이 이를 지원하는 업로드 위치에 표시됩니다. 장치에서 업로드는 유지됩니다. 다음을 가져올 수 있습니다.

* 콘텐츠 라이브러리의 모듈 콘텐츠
* 강의 표지 이미지 및 배너 이미지와 같은 이미지.
* 작업 지원

해당 업로드 위치에서 지원되는 파일 유형만 표시됩니다. 예를 들어 표지 이미지 옵션은 이미지만 표시합니다. 지원되는 유형에는 이미지(JPEG, PNG, SVG), 비디오(MP4) 및 문서(PDF, SCORM 패키지, PowerPoint 및 Word)가 포함됩니다. 파일 확장자 및 크기 제한은 해당 위치의 다른 업로드와 동일합니다.

### 콘텐츠와 이미지는 서로 다르게 처리됩니다.

| 항목 | 처리 방식 |
|---|---|
| 콘텐츠 라이브러리의 콘텐츠 | 소스 에셋이 복사되고 링크되어 자동으로 업데이트될 수 있습니다. |
| 이미지(예: 커버 및 배너 이미지) | 선택하면 복사됩니다. 연결되지 않고 자동으로 업데이트되지 않습니다. |

### 콘텐츠 라이브러리로 콘텐츠 가져오기

1. **콘텐츠 라이브러리**&#x200B;를 열고 콘텐츠를 추가합니다.
1. **찾아보기**&#x200B;를 선택합니다.
1. **AEM Assets**&#x200B;을 선택합니다.
1. 메시지가 표시되면 Adobe ID으로 로그인하십시오.
1. **Adobe Experience Manager Assets** 창에서 에셋을 찾습니다. 둘 이상의 저장소(AEM Assets에서 활성화된 AEM 인스턴스)에 액세스할 수 있는 경우 필요에 따라 저장소 간에 전환합니다.
1. 에셋을 선택한 다음 업로드를 완료하고 저장합니다.
1. 콘텐츠 그룹을 사용하여 강의를 생성합니다.

다음 사항에 유의하십시오.

* 에셋은 한 번에 하나씩 선택합니다. 일괄 가져오기 및 폴더 가져오기를 사용할 수 없으며 기존 콘텐츠 라이브러리를 Adobe Experience Manager Assets으로 마이그레이션할 수 없습니다.
* 에셋 선택기를 사용하여 Adobe Experience Manager Assets에서 에셋을 열 수 있습니다.
* Adobe Learning Manager에서는 Adobe Experience Manager Assets에서 직접 콘텐츠를 제공하지 않습니다. 가져온 각 에셋을 복사하고 로컬 사본을 보관합니다.
* 가져온 콘텐츠는 학습자 도우미를 위한 받아쓰기를 포함하여 Adobe Learning Manager의 다른 콘텐츠와 마찬가지로 처리됩니다.

### 작업 지원 추가

콘텐츠 라이브러리 콘텐츠를 가져올 때와 같은 방법으로 AEM Assets에서 PDF 및 참조 문서와 같은 작업 지원 파일을 선택합니다.

### 액세스 권한이 없는 작성자

작성자가 연결된 IMS 조직의 Adobe Experience Manager Assets에 액세스할 수 없는 경우 AEM Assets을 선택하면 제한된 액세스에 대한 메시지가 표시됩니다.

## 콘텐츠를 최신 상태로 유지

Adobe Experience Manager Assets에서 에셋이 변경될 때 연결된 컨텐츠 라이브러리 항목을 최신 상태로 유지합니다.

### 자동 업데이트 작동 방식

통합 책임자 섹션에서 자동 업데이트가 켜져 있고 기술 계정이 할당되면 Adobe Learning Manager은 콘텐츠 라이브러리를 Adobe Experience Manager Assets과 동기화된 상태로 유지합니다.

1. **Adobe Experience Manager Assets**&#x200B;에서 새 버전의 에셋을 업로드하거나 이전 버전을 복원하십시오.
1. Adobe Experience Manager Assets에서 에셋 처리가 완료됩니다. 에셋이 교체되는 경우 대부분 몇 분 안에 업데이트되거나 드물게 최대 1시간 정도 소요될 수 있습니다. 1시간 이상 걸리는 경우에는 AEM Assets에서 에셋을 다시 처리할 수 있습니다.
1. Adobe Learning Manager이 연결된 **콘텐츠 라이브러리** 항목을 업데이트하고 버전 번호를 증가시킵니다.
1. **학습 개체 업데이트**&#x200B;가 켜져 있으면 해당 항목을 사용하는 학습 개체도 업데이트됩니다. 현재 등록된 학습자와 이후 학습자 모두 최신 버전을 받게 됩니다.
1. 학습자는 다음에 콘텐츠를 실행할 때 최신 버전을 받게 됩니다. 이미 콘텐츠가 열려 있는 학습자는 해당 콘텐츠를 닫고 다시 실행해야 합니다.

업데이트는 즉시 적용되지 않습니다. 잠시 기다린 후 콘텐츠 라이브러리를 새로 고쳐 변경 사항을 확인합니다.

### 수동으로 콘텐츠 업데이트

자동 업데이트가 꺼져 있거나 Adobe Admin Console에 기술 계정이 할당되지 않은 경우 콘텐츠를 수동으로 업데이트하십시오.

1. **콘텐츠 라이브러리**&#x200B;에서 항목을 엽니다.
1. **AEM Assets**&#x200B;에서 업데이트된 파일을 선택합니다.
1. **저장**&#x200B;을 선택합니다.

### 로케일에서 업데이트가 적용되는 방법

다국어 콘텐츠 라이브러리 항목의 여러 로케일이 동일한 에셋을 사용하는 경우 해당 에셋을 업데이트하면 해당 로케일이 모두 업데이트됩니다. 다른 에셋을 사용하는 로케일은 영향을 받지 않습니다.

### 에셋이 가질 수 있는 콘텐츠 그룹 수

하나의 에셋을 최대 10개의 콘텐츠 그룹에 연결할 수 있습니다.

>[!NOTE]
>
>이를 염두에 두고 콘텐츠 그룹을 계획하십시오. 동일한 소스에서 10개 이상의 콘텐츠 그룹이 필요한 경우 추가 그룹에 대한 에셋의 사본을 사용하십시오.

## Adobe Experience Manager Assets에서 콘텐츠 미리 보기

미리 보기 링크를 사용하여 학습자로 실행하지 않고 SCORM 및 HTML 콘텐츠를 검토할 수 있습니다.

공개 미리 보기 링크 설정이 사용 설정되면 Adobe Learning Manager은 콘텐츠 라이브러리로 가져오는 지원되는 콘텐츠에 대한 미리 보기 링크를 만들어 Adobe Experience Manager Assets의 에셋 메타데이터에 저장합니다.

미리 보기 링크는 다음 컨텐츠 유형에 대해 생성됩니다.

* SCORM 1.2
* SCORM 2004
* HTML

링크를 찾아 사용하려면 다음을 수행하십시오.

1. Adobe Experience Manager Assets에서 에셋의 속성을 엽니다.
1. 메타데이터에서 미리 보기 링크를 찾습니다.

   <!-- TODO: The source document says "path to be mentioned here". Add the exact metadata location (confirm with Kranthi). -->

1. 링크를 복사하여 브라우저에 붙여넣어 에셋을 미리 봅니다.

에셋의 메타데이터를 여는 사용자는 이 링크를 보고 사용할 수 있습니다.

>[!NOTE]
>
>미리 보기 링크 사용은 ALM 라이선스 사용에 고려되지 않습니다. 공개 미리 보기 링크를 끄면 Adobe Learning Manager이 Adobe Experience Manager Assets에서 만든 미리 보기 파일이 제거됩니다.

## 에셋, 액세스 또는 연결이 변경되는 경우

에셋을 삭제하거나, 액세스 권한을 잃거나, 연결을 해제하면 콘텐츠에 어떤 영향을 미치는지 이해합니다.

### 에셋을 삭제하면 어떻게 됩니까? {#delete-asset}

이미 콘텐츠를 사용하는 강의는 소스 에셋을 삭제하더라도 계속 작동합니다. 삭제가 콘텐츠 라이브러리에 미치는 영향은 콘텐츠 그룹의 로케일에 따라 다릅니다.

| 시나리오 | 조치 사항 |
|---|---|
| 에셋은 다국어 콘텐츠 그룹의 한 로케일에서 사용됩니다 | 해당 로케일이 제거됩니다. 다른 로케일은 남아 있습니다. |
| 에셋이 콘텐츠 그룹 뒤에 있는 유일한 에셋입니다. | 콘텐츠 그룹이 제거되었습니다. |

콘텐츠 그룹이 사용 중지되는 경우:

* 기존 강의는 복사한 콘텐츠를 계속 재생합니다.
* 콘텐츠 그룹을 사용하여 새 강의 연결을 만들 수 없습니다.
* 콘텐츠 그룹을 편집할 수 없습니다.

### 작성자가 액세스 권한을 상실하면 어떻게 됩니까?

이전에 만든 이가 가져온 콘텐츠는 계속 작동합니다. 하지만 작성자는 해당 인스턴스에서 새 에셋을 가져오거나 콘텐츠 그룹을 만들거나 이를 사용하는 기존 콘텐츠 그룹을 편집할 수 없습니다.

### 연결을 끊으면 어떻게 됩니까?

가져온 콘텐츠 및 이미지는 사본이므로 Adobe Learning Manager에 남아 있습니다. 소스 에셋에 대한 링크가 끊어져 연결된 콘텐츠는 더 이상 업데이트되지 않습니다. 학습 객체 및 콘텐츠 그룹은 계속 작동합니다.

## 문제 해결

**연결할 수 없거나 커넥터를 볼 수 없습니다**

Adobe Learning Manager에서 통합 관리자 역할이 있는지 확인하십시오.

**IMS 조직 관리자인 경우에도 연결이 실패합니다**

선택한 IMS 조직에서 하나 이상의 Adobe Experience Manager Assets 인스턴스에도 액세스할 수 있는지 확인하십시오. 이 문제는 IT 지원 팀이 조직을 관리하지만 Adobe Experience Manager Assets 제품에 할당되지 않은 경우에 발생할 수 있습니다. Adobe Experience Manager 관리자에게 인스턴스에 사용자를 추가하도록 요청한 다음 다시 연결합니다.

**내 Adobe Experience Manager Assets 인스턴스가 나열되지 않음**

인스턴스가 Adobe Learning Manager 계정에 연결된 IMS 조직에 속하고 Adobe Experience Manager Assets as a Cloud Service의 작성자 인스턴스인지 확인하십시오.

**업로드 옵션으로 AEM Assets이 표시되지 않음**

통합 책임자에게 문의하여 연결이 활성화되었는지 확인하고, 활성화 후 최대 1시간 동안 허용합니다.

**작성자가 에셋을 볼 수 없거나 가져올 수 없습니다.**

Adobe Experience Manager 관리자에게 문의하여 작성자에게 연결된 IMS 조직의 Adobe Experience Manager Assets 작성자 인스턴스에 대한 액세스 권한을 부여합니다.

**콘텐츠가 업데이트되지 않았거나 내 강의에 이전 콘텐츠가 표시됨**

1. 통합 책임자 설정에서 자동 업데이트가 켜져 있는지 확인하고 변경 내용이 적용될 시간을 허용합니다.
2. Adobe Admin Console에서 기술 계정이 인스턴스의 제품 프로필에 할당되었는지 확인합니다.
3. 콘텐츠를 다시 실행합니다. 여전히 이전 콘텐츠가 표시되는 경우 수동으로 업데이트하십시오.

**콘텐츠 그룹이 사용 중지됨**

Adobe Experience Manager Assets에서 원본 에셋이 삭제되었습니다. [에셋을 삭제할 때 발생하는 내용](#delete-asset)을 참조하세요.

**미리 보기 링크가 에셋 메타데이터에 표시되지 않음**

공개 미리 보기 링크가 켜져 있고, 콘텐츠가 SCORM 1.2, SCORM 2004 또는 HTML으로 설정되어 있으며 설정을 켠 후 최대 1시간 동안 기다렸는지 확인합니다.

## AEM Assets 통합 - FAQ

**Q. ALM이 AEM Assets에서 직접 학습 콘텐츠를 제공합니까?**

**A.** 아니요. 당사는 AEM Assets에서 ALM으로 콘텐츠를 복사하고 ALM에 로컬 사본을 보관합니다.

**Q. AEM Assets에서 에셋을 업데이트하면 어떻게 됩니까?**

**A.** ALM에서 자동 업데이트 옵션이 활성화되면 AEM Assets과 연결된 해당 콘텐츠도 업데이트되고 버전도 업데이트됩니다.

**Q. 책임자가 AEM 업데이트를 통해 강의에 자동으로 접속할 수 있는지 여부를 제어할 수 있습니까?**

**A.** 예. 통합 중에 통합 책임자는 자동 업데이트를 선택하고 해당 업데이트가 학습 개체에도 자동으로 적용되는지 확인해야 합니다. 계정 설정에 따라 학습 개체 업데이트가 작동합니다.

**Q. 작성자가 컴퓨터에서 파일을 업로드할 수 있습니까?**

**A.** 예

**Q. 고객이 기존 ALM 콘텐츠 라이브러리를 AEM Assets으로 마이그레이션할 수 있습니까?**

**A.** 아니요. 오늘날에는 그런 조항이 없다.

**Q. 전체 AEM Assets 폴더를 콘텐츠 라이브러리로 가져올 수 있습니까?**

**A.** 아니요. 오늘날에는 그런 조항이 없다.

**Q. 통합이 에셋의 대량 가져오기를 지원합니까?**

**A.** 아니요, 오늘부로 이러한 제공 항목이 없습니다.

**Q. AEM Assets에서 선택할 수 있는 ALM 콘텐츠는 무엇입니까?**

**A.** 각 업로드 위치에서 현재 지원하는 것과 동일한 파일 확장명을 지원합니다. 이 필터는 해당 업로드 접점에서 AEM Content Advisor를 열 때 적용됩니다.

**Q. 콘텐츠 에셋과 이미지 에셋이 동일한 방식으로 작동합니까?**

**A.** 자동 업데이트 기능은 콘텐츠 에셋에만 적용할 수 있으며 ALM의 다른 에셋에는 적용할 수 없습니다.

**Q. 원래 AEM Assets에서 가져온 이미지를 나중에 로컬 파일로 바꿀 수 있습니까?**

**A.** 예

**Q. ALM 작성자가 볼 수 있는 AEM Assets은 무엇입니까?**

**A.** ALM 작성자는 AEM Assets에서의 사용자 권한에 따라 액세스 권한이 있는 모든 폴더와 파일을 볼 수 있습니다.

**Q. 작성자의 AEM 액세스가 제거되면 어떻게 됩니까?**

**A.** 작성자는 AEM Content Advisor를 통해 해당 IMS 프로필의 에셋 인스턴스에 더 이상 액세스할 수 없으므로 AEM Assets에서 콘텐츠 그룹을 편집하거나 만들 수 없습니다.

**Q. AEM Assets 통합이 비활성화되거나 연결이 끊어지면 어떻게 됩니까?**

**A.** 학습 개체 및 콘텐츠 그룹은 계속 작동하지만 해당 에셋의 자동 업데이트 기능이 중지되며 더 이상 진행되지 않습니다.

**Q. 통합이 AEM 온-프레미스를 지원합니까?**

**A.** 아니요. 클라우드 인스턴스만 지원합니다.

**Q. 하나의 ALM 계정이 여러 AEM Assets 계정에 연결할 수 있습니까?**

**A.** ALM 계정은 IMS 프로필에 매핑되며 IMS 프로필의 모든 AEM Assets 인스턴스를 연결하고 사용할 수 있습니다. IMS 프로필이 ALM 계정에 연결되면 IMS 프로필을 다른 ALM 계정에 연결할 수 없습니다.

**Q. AEM Assets에서 가져온 콘텐츠를 학습자 도우미에서 사용할 수 있습니까?**

**A.** AEM Assets에서 가져온 콘텐츠가 강의를 만드는 데 사용되는 경우 관련 대화에서 학습자 도우미가 동일한 콘텐츠를 참조할 수 있습니다.

**Q. 작성자가 AEM 에셋을 선택하기 전에 미리 볼 수 있습니까?**

**A.** 아니요. AEM Assets에서는 일부 파일 포맷에 대한 미리보기를 지원하지만 에셋을 선택하기 전에는 미리보기 기능을 사용할 수 없습니다.

**Q. ALM이 공개 미리 보기 링크를 생성합니까?**

**A.** 예, SCORM 1.2, SCORM 2004 및 HTML 파일에만 해당됩니다. 통합 책임자가 공개 미리 보기 기능을 활성화했을 때만 가능합니다.
