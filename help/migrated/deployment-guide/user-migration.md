---
jcr-language: en_us
title: Learning Manager 배포 안내서 - 섹션 2
contentowner: sanm
preview: true
source-git-commit: fba5e5ddc1964b485be473bf356806f234688cf4
workflow-type: tm+mt
source-wordcount: '2232'
ht-degree: 0%

---



# Learning Manager 배포 안내서 - 섹션 2

## 기술 설정 {#technicalsetup}

Learning Manager 계정의 기술적 설정은 주로 기업 사용자에게 필요합니다. 이 문서에서는 조직에 대한 SSO(Single Sign-On) 구성 및 Learning Manager와 타사 커넥터 통합에 대해 설명합니다.

### Single Sign-On 구성 {#configuresinglesignon}

Admin Console의 시스템 관리자로서 첫 번째 작업 중 하나는 최종 사용자를 인증할 ID 시스템을 정의하고 설정하는 것입니다. 조직에서 Learning Manager 라이선스를 구매하므로 최종 사용자에게 해당 라이선스를 프로비저닝해야 합니다. 이를 위해 이들 사용자를 인증할 수 있는 방법이 필요합니다. 다음 절차를 수행하여 사용자에 대한 SSO를 구성합니다.

1. Learning Manager 홈 페이지에서 **[!UICONTROL **&#x200B;설정&#x200B;**>**&#x200B;로그인 방법&#x200B;**.]**

   ![](assets/configure-sso-step1.png)

1. 사용자 유형에 따라 다음 중 하나를 선택합니다 **[!UICONTROL **&#x200B;내부 사용자&#x200B;**또는**&#x200B;외부 사용자&#x200B;**.]**



1. **[!UICONTROL **로그인**]**드롭다운 필드, **[!UICONTROL ** Single Sign-On **.]**

   ![](assets/configure-sso-step3.png)

1. 단일 인증 설정을 구성하려면 **[!UICONTROL **&#x200B;변경&#x200B;**.]**

   ![](assets/configure-sso-step4.png)

1. (으)로 ****[!UICONTROL IDP 시작 인증 URL]**** 필드에 서비스 공급자가 제공한 인증 URL을 입력합니다.



   ![](assets/configure-sso-step5.png)

1. 확인 을 **[!UICONTROL **업로드&#x200B;**]**옆에 있는**[!UICONTROL  **IDP 메타데이터 XML 파일&#x200B;**]******를 입력하고 XML 파일을 업로드합니다.
1. 다음을 수행합니다. **[!UICONTROL **&#x200B;저장&#x200B;**.]**
1. 계정에 대한 SSO 인증이 성공적으로 구성되었습니다. SSO를 사용하여 Learning Manager 계정에 로그인할 수 있습니다.

   ***Learning Manager에서 구성하는 SSO는 SAML 2.0을 지원해야 합니다.***

## 사용자 데이터 마이그레이션 {#migrationofuserdata}

관리자가 기업에서 Learning Manager를 구매할 때 수행해야 하는 중요한 단계 중 하나는 마이그레이션입니다. 기존의 교육 콘텐츠와 사용자 데이터를 Learning Manager로 옮겨야 합니다. 아래의 마이그레이션 작업 과정은 조직의 레거시 데이터를 그대로 보존하면서 현대적이고 직관적인 LMS의 이점을 활용하는 데 도움이 됩니다.

Learning Manager를 사용하면 마법사의 단계적 안내에 따라 스프린트를 반복하여 기존의 LMS에서 새로운 LMS로 마이그레이션할 수 있습니다. 레거시 데이터를 Adobe Learning Manager로 마이그레이션하는 동안 학습자가 다운타임을 전혀 겪지 않도록 각 스프린트의 상태를 완벽하게 파악할 수 있습니다.

마이그레이션 작업 과정을 수행하려면 통합 책임자 권한이 필요합니다. 책임자는 통합 책임자의 역할을 직접 맡거나 책임자 역할을 다른 사용자에게 배정할 수 있습니다.

**여기서 Shaleen의 도움을 받아 시각적 효과를 만들 수 있습니다.**

1. 필수 구성 요소
1. 기존 콘텐츠 및 사용자 데이터 평가
1. 기존 LMS의 데이터 내보내기 및 매핑
1. 마이그레이션용 FTP 및 BOX 폴더 생성
1. 학습자를 Learning Manager로 이전
1. Learning Manager에 학습 콘텐츠 이전
1. 나머지 데이터를 Learning Manager로 전송



### 필수 구성 요소 {#prerequisite}

마이그레이션 프로세스를 시작하기 전에 다음 선행 작업을 수행해야 합니다.

* 기존 LMS에서 데이터와 콘텐츠를 추출하고 Learning Manager에서 정의된 파일 형식으로 데이터를 변환합니다.
* FTP 및 BOX 커넥터를 사용하여 사용자 가져오기. 통합 책임자는 마이그레이션 프로세스를 시작하기 전에 커넥터가 구성되었는지 확인해야 합니다.



***책임자가 데이터와 콘텐츠를 Learning Manager 제작 환경으로 마이그레이션하기 전에 평가판 계정에서 마이그레이션 프로세스를 시도해보는 것이 좋습니다. ***

### 데이터 평가 및 내보내기 {#evaluatingandexportingdata}

통합 책임자는 먼저 현재 LMS에서 사용 가능한 데이터를 확인해야 합니다. 통합 책임자는 다음과 같은 학습 개체만 마이그레이션할 수 있습니다.

* 모듈
* 강의
* 모듈 버전
* 강의 인스턴스
* 강의 모듈
* 스킬
* 스킬 레벨
* 스킬 과정
* 인증
* 인증 과정
* 인증 커밋
* 학습 프로그램
* 학습 프로그램 과정
* 학습 프로그램 인스턴스
* 학습 프로그램 강의 인스턴스
* 등록
* 인증 등록
* 학습 프로그램 등록
* 사용자 강의 등급



기존 데이터를 평가하고 나면 이 데이터를 Learning Manager의 표준 CSV 사양과 매핑해야 합니다. 다음 샘플 다운로드 ***csv-specifications.zip*** 이 마이그레이션에 필요한 7개의 excel 시트가 포함된 파일입니다. 이 Excel 시트에서 기존 데이터를 .csv 파일의 필드와 매핑하는 방법에 대한 이해를 돕는 설명과 함께 사양이 기술되어 있습니다.

<!--
<Download link to the zip file>
-->

각 .csv 파일에 지정된 형식의 각 필드에 대한 데이터가 포함되어 있는지 확인합니다.

<table> 
 <tbody> 
  <tr> 
   <th width="7%" valign="top"><p><strong>아니요.</strong></p></th> 
   <th width="29%" valign="top"><p><strong>Excel 스프레드시트 이름</strong></p></th> 
   <th width="31%" valign="top"><p><strong>콘텐츠 설명</strong></p></th> 
   <th width="31%" valign="top"><p><strong>노트</strong></p></th> 
  </tr> 
  <tr> 
   <td><p>1</p></td> 
   <td><p>module.xlsx</p></td> 
   <td><p>module.csv용 메타데이터</p></td> 
   <td><p> </p></td> 
  </tr> 
  <tr> 
   <td><p>2</p></td> 
   <td><p>course.xlsx</p></td> 
   <td><p>course.csv용 메타데이터</p></td> 
   <td><p>강의마다 하나의 작성자 이름을 입력합니다. 마이그레이션 후 작성자 이름이 정확하게 표시되지 않는 경우가 있습니다. </p></td> 
  </tr> 
  <tr> 
   <td><p>3</p></td> 
   <td><p>module_version.xlsx </p></td> 
   <td><p>module_version.csv용 메타데이터</p></td> 
   <td><p>콘텐츠를 업로드한 Box 계정 폴더의 URL 경로가 입력되어 있는지 확인합니다. </p></td> 
  </tr> 
  <tr> 
   <td><p>4</p></td> 
   <td><p>course_instance.xlsx</p></td> 
   <td><p>course_instance.csv용 메타데이터 </p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>5</p></td> 
   <td><p>course_module.xlsx</p></td> 
   <td><p>course_module.csv용 메타데이터</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>6</p></td> 
   <td><p>skill.xlsx</p></td> 
   <td><p>skill.csv용 메타데이터</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>7</p></td> 
   <td><p>skill_level.xlsx</p></td> 
   <td><p>skill_level.csv용 메타데이터</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>8</p></td> 
   <td><p>skill_course.xlsx</p></td> 
   <td><p>skill_course.csv용 메타데이터</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>9</p></td> 
   <td><p>Certification.xlsx</p></td> 
   <td><p>Certification.csv용 메타데이터</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>10</p></td> 
   <td><p>certification_course.xlsx</p></td> 
   <td><p>certification_course.csv용 메타데이터</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>11</p></td> 
   <td><p>certification_commit.xlsx</p></td> 
   <td><p>certification_commit.csv용 메타데이터</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>12</p></td> 
   <td><p>learning_program.xlsx</p></td> 
   <td><p>learning_program.csv용 메타데이터</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>13</p></td> 
   <td><p>learning_program_course.xml </p></td> 
   <td><p>learning_program_course.csv용 메타데이터 </p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>14</p></td> 
   <td><p>learning_program_instance.xlsx </p></td> 
   <td><p>learning_program_instance.csv용 메타데이터</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>15</p></td> 
   <td><p>learning_program_instance_course_instance.xlsx </p></td> 
   <td><p>learning_program_instance_course_instance.csv용 메타데이터</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>16</p></td> 
   <td><p>enrollments.xlsx</p></td> 
   <td><p>Metadata for enrollments.csv</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>17</p></td> 
   <td><p>certification_enrollment.xlsx</p></td> 
   <td><p>certification_enrollment.csv용 메타데이터</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>18</p></td> 
   <td><p>learning_program_enrollment.xlsx</p></td> 
   <td><p>learning_program_enrollment.csv용 메타데이터</p></td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td><p>19</p></td> 
   <td><p>User_course_grade.xlsx</p></td> 
   <td><p>User_course_grade.csv용 메타데이터</p></td> 
   <td><p>필수 항목이 아니더라도 필요한 학습자 기록 데이터를 .csv 파일에 입력합니다. 해당 정보가 없는 경우 .csv의 마이그레이션이 처리된 후에도 Learning Manager 응용 프로그램이 데이터를 반영하지 못할 수 있습니다. </p></td> 
  </tr> 
 </tbody> 
</table>

***Learning Manager는 UTF 8 및 32비트 형식으로만 날짜 및 시간 값을 지원합니다. CSV 파일에 2038-07-17T08과 같이 범위를 벗어난 날짜를 지정한 경우 마이그레이션 중 오류가 발생할 수 있습니다:53:21.000Z 또는 1980-04-17T08:13:25.322Z.***

### 데이터를 csv 파일로 가져오는 동안의 종속성 {#dependencieswhileimportingdatatocsvfiles}

기존 데이터를 표준 csv 형식으로 가져오는 동안 다음 종속성에 유의하십시오.

* module_version.csv는 module.csv에 종속됩니다.
* course_instance.csv는 course.csv에 종속됩니다.
* course_module.csv는 course.csv, module.csv 및 module_version.csv에 종속됩니다.
* course_instance.csv는 course.csv에 종속됩니다.
* enrollment.csv는 course.csv에 종속됩니다.
* user_course_grade.csv는 course.csv 및 module.csv에 종속됩니다.
* skill_course.csv는 course.csv에 종속됩니다.
* skill_level.csv는 skill.csv에 종속됩니다.
* learning_program_instance.csv는 learning_program 및 learning_program_course.csv에 종속됩니다.
* learning_program_course.csv는 learning_program.csv에 종속됩니다.
* learning_program_enrollment.csv는 learning_program 및 learning_program_instance.csv에 종속됩니다.
* learning_program_instance_course_instance.csv는 learning_program.csv, learning_program_instance.csv 및 course_instance.csv에 종속됩니다.
* certification_course.csv는 certification.csv 및 course.csv에 종속됩니다.
* certification_commit.csv는 certification.csv 및 certification_course.csv에 종속됩니다.
* certification_enrollment.csv는 certification.csv, certification_course.csv 및 certification_enrollment.csv에 종속됩니다.



데이터를 내보낸 후 로컬 컴퓨터에 .csv 파일을 저장합니다. 이제 파일을 FTP 또는 BOX 폴더에 저장할 준비가 되었습니다.

## 마이그레이션용 FTP 및 BOX 폴더 생성 {#setupftpandboxfoldersforthemigration}

모든 콘텐츠를 실제로 마이그레이션하는 과정을 계획하고 시작하기에 앞서 FTP 폴더와 BOX 폴더부터 만들어야 합니다. .csv 파일을 이 폴더에 저장하려면 이 폴더가 필요합니다. FTP 폴더와 BOX 폴더에 .csv 파일 형식의 레거시 콘텐츠가 준비되면 Learning Manager에서 해당 데이터를 사용할 수 있습니다.

### FTP 계정 설정 {#setupanftpaccount}

통합 책임자 홈 페이지에서 **[!UICONTROL ** CSV FTP 폴더 요청&#x200B;**.]** 팝업 대화 상자가 나타나면 전자 메일 ID를 입력합니다. 온라인 마법사를 통해 Exavault FTP 계정을 만듭니다. 계정을 만들면 즉시 Exavault FTP에 마이그레이션 프로젝트 폴더와 스프린트 프로젝트 폴더가 생성됩니다.

ExaVault의 프로젝트 파일 및 폴더 스냅샷 예시를 참조하십시오.

![](assets/set-up-an-ftp-account.png)

FTP 폴더를 생성하는 데 성공하면 &quot;FTP 폴더 생성이 완료되었습니다&quot;라는 메시지가 표시됩니다.

## BOX 계정 설정 {#setupaboxaccount}

BOX 계정을 만들고 BOX 폴더를 설정하려면 다음 단계를 수행하십시오.

통합 책임자 홈 페이지에서 마이그레이션 을 선택합니다.

설정 섹션에서 Box 폴더 요청 을 클릭합니다.

![](assets/set-up-a-box-account.png)

(으)로 ****[!UICONTROL 이메일 입력]**** 필드에 Box에 접속하는 데 필요한 로그인 지침을 받아볼 전자 메일 ID를 입력합니다.

다음을 수행합니다. **[!UICONTROL ** Connect **.]**

그러면 Box에서 공유 폴더 링크가 포함된 전자 메일을 전송합니다. Box 계정이 없는 경우 &#39;가입&#39;을 클릭하여 계정을 만듭니다. 그러면 로그인 지침이 통합 책임자 전자 메일 ID로 전송됩니다.

연결을 저장하면 마이그레이션 페이지에 &#39;Box 폴더 생성이 완료되었습니다&#39;라는 메시지가 표시됩니다.

## 콘텐츠를 Learning Manager로 마이그레이션 {#migratingthecontenttocaptivateprime}

마이그레이션을 시작하기 전에 다음 사항에 유의해야 합니다.

* 한 시점에 하나의 계정으로 오직 하나의 마이그레이션 프로젝트만 진행할 수 있습니다. 한 프로젝트 내에서 특정 시점에 하나의 스프린트만 활성화할 수 있습니다.
* 이미 처리 중인 실행은 실행 취소할 수 없습니다. 그러나 Learning Manager의 각 기능에서 지원하는 기존의 삭제 옵션을 사용하여 데이터 또는 콘텐츠 마이그레이션을 취소할 수 있습니다.

마이그레이션 프로젝트를 시작하는 즉시 프로젝트의 상태가 &#39;마이그레이션 중&#39;으로 변경됩니다. 이 상태에서는 통합 책임자를 제외한 나머지 사용자가 Learning Manager에 로그인할 수 없습니다.

Content 폴더에 교육 콘텐츠 업로드:

통합 책임자 홈 페이지에서 **[!UICONTROL 마이그레이션.]**

이미 조직에 생성된 마이그레이션 프로젝트가 마이그레이션 홈 페이지에 표시됩니다.

확인 을 **[!UICONTROL **새로운 기능**]**페이지 오른쪽 상단 모서리에 마이그레이션 프로젝트를 생성합니다.

***FTP 폴더를 생성하지 않은 경우 Exavault 계정용 FTP 폴더를 생성하라는 메시지가 표시됩니다. 이는 마이그레이션 프로젝트 생성을 시작하기 전에 반드시 수행해야 하는 작업입니다. ***

(으)로 ****[!UICONTROL 새 마이그레이션 프로젝트 만들기]**** 페이지에서 프로젝트 이름을 지정합니다.

![](assets/migrating-the-content-1.png)

프로젝트 태그와 강의 카탈로그를 지정하고 마이그레이션 프로젝트 설명을 입력합니다. 마이그레이션 데이터 항목은 마이그레이션 프로젝트 태그를 사용하여 식별됩니다. 특정 강의 카탈로그가 없는 경우 드롭다운 메뉴에서 기본 카탈로그를 선택합니다. 마이그레이션 프로젝트를 통해 마이그레이션하는 모든 강의는 이 단계에서 선택한 카탈로그에 포함됩니다. 카탈로그를 선택하지 않으면 마이그레이션된 모든 강의는 기본 카탈로그에 추가됩니다.

다음을 수행합니다. **[!UICONTROL 만들어 보세요.]**

스프린트 구성 페이지에서 마이그레이션 프로젝트용 스프린트를 생성합니다. Learning Manager 마이그레이션 프로젝트에서 스프린트는 기존 LMS에서 마이그레이션하기로 선택한 마이그레이션 항목 세트로 정의됩니다.

![](assets/migrating-the-content-2.png)

스프린트의 이름을 지정하고 스프린트 설명을 입력합니다.

선택 ****[!UICONTROL 마지막 실행 이후 사용자가 추가 또는 수정되었습니다. 확인란]****&#x200B;를 클릭하여 사용자 목록을 Learning Manager 응용 프로그램과 동기화합니다. Learning Manager 응용 프로그램으로 콘텐츠와 데이터를 마이그레이션하는 경우, 해당 단계는 필수가 아닐 수 있습니다. 그러나 이전 스프린트 마이그레이션과 최신 스프린트 마이그레이션 사이에 시차가 있는 경우 사용자 목록을 동기화하는 것이 좋습니다. 이 단계를 거치면 Learning Manager 데이터베이스가 LMS 사용자와 동기화됩니다.

***이 동기화 단계는 enrollment.csv 및 user_course_grade.csv 파일을 마이그레이션할 때 시행하는 것이 좋습니다. 이 단계를 통해 Learning Manager 데이터베이스를 마이그레이션 데이터베이스와 동기화하며 스프린트에 기록이 마이그레이션된 모든 사용자를 마이그레이션 데이터베이스에서 사용할 수 있게 해줍니다.***

다음을 수행합니다. **[!UICONTROL **&#x200B;다음&#x200B;**.]**

확인 을 **[!UICONTROL **시작**]**업로드된 데이터 및 콘텐츠로 스프린트 마이그레이션을 시작합니다. 다음을 수행합니다. ****[!UICONTROL 새로 고침]**** 스프린트 실행을 시작하기 전에 FTP 및 콘텐츠 폴더를 Learning Manager와 동기화하십시오.

![](assets/migrating-the-content-3.png)

**** 클릭[!UICONTROL 중지]****스프린트 마이그레이션을 중단하려면 스프린트 마이그레이션 프로세스 중 언제든지

각 스프린트 데이터 항목 및 콘텐츠에 마이그레이션 상태가 표시됩니다. 마이그레이션 스프린트 실행의 일부로 성공 및 실패 항목을 확인합니다.

모듈 콘텐츠를 업로드하는 경우 콘텐츠 폴더의 경로가 *module_version.csv *파일에 입력되어 있는지 확인합니다. 이 단계를 빠트린 경우, 마이그레이션 중 에러가 발생할 수 있습니다. 예를 들어 비디오와 같은 자가 진행식 모듈 콘텐츠를 업로드하는 경우 *module_version.csv *파일에 상대 Box URL 경로를 지정해야 합니다.

아래에 있는 마이그레이션 프로세스 스냅샷 예시를 참조하십시오. 스냅샷에 나타난 것처럼 각 마이그레이션 데이터 항목에 대해 처리된 기록의 개수와 성공 및 실패 항목 상태를 확인할 수 있습니다. 오류 로그를 다운로드하고 보려면 실패한 항목에 대해 오류 기록 다운로드 를 클릭합니다. CSV에서 문제를 수정하고 FTP에 다시 업로드할 수 있습니다.

![](assets/migrating-the-content-4.png)

마이그레이션 프로젝트의 전체 스프린트 목록을 보려면 **를 클릭합니다&#x200B;[!UICONTROL **스프린트**]**왼쪽 탐색 창. 아래의 스냅샷에 보이는 것처럼 전체 스프린트 목록, 각 스프린트에서 실행한 횟수, 시작 날짜, 지속 기간 및 완료 상태를 확인할 수 있습니다.

![](assets/migrating-the-content-5.png)

마이그레이션 프로젝트의 전체 스프린트 목록을 보려면 **를 클릭합니다&#x200B;[!UICONTROL **스프린트**]**왼쪽 탐색 창. 아래의 스냅샷에 보이는 것처럼 전체 스프린트 목록, 각 스프린트에서 실행한 횟수, 시작 날짜, 지속 기간 및 완료 상태를 확인할 수 있습니다.

마이그레이션 프로젝트의 전체 스프린트 목록을 보려면 **를 클릭합니다&#x200B;[!UICONTROL **스프린트**]**왼쪽 탐색 창. 아래의 스냅샷에 보이는 것처럼 전체 스프린트 목록, 각 스프린트에서 실행한 횟수, 시작 날짜, 지속 기간 및 완료 상태를 확인할 수 있습니다.

***마이그레이션 프로젝트를 완료로 표시하기 전에 프로젝트의 모든 스프린트가 완료되었는지 확인합니다. 일단 마이그레이션 프로젝트를 완료로 표시하면 뒤로 돌아가 해당 프로젝트에서 스프린트를 생성할 수 없습니다. 해당 프로젝트를 수정할 수 없습니다. 마이그레이션 프로젝트를 새로 생성하고 거기에 스프린트를 추가하는 것만 가능합니다.***

레거시 LMS의 학습 데이터와 콘텐츠를 마이그레이션한 후 데이터와 콘텐츠를 제대로 가져왔는지 확인합니다. 책임자로 로그인하여 가져온 모듈 및 강의 데이터와 콘텐츠가 정상인지 확인합니다

유용한 마이그레이션 리소스는 다음을 참조하십시오.

* 마이그레이션 문제 해결
* CSV 업로드 관련 자주 묻는 질문

