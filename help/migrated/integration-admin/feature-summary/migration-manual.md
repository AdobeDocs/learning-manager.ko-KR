---
description: 기존 LMS를 Adobe Learning Manager LMS로 마이그레이션하려는 통합 책임자를 위한 참조 설명서
jcr-language: en_us
title: 마이그레이션 설명서
exl-id: bfdd5cd8-dc5c-4de3-8970-6524fed042a8
source-git-commit: 8801cee7914c7bea849d47f272b19996a5e28f4d
workflow-type: tm+mt
source-wordcount: '4483'
ht-degree: 58%

---

# 마이그레이션 설명서

기존 LMS를 Learning Manager LMS로 마이그레이션하려는 통합 책임자를 위한 참조 설명서

<!-- ## Overview {#overview} -->

## 사용 시나리오 {#usagescenario}

일반적으로 대규모 기업은 내부 LMS 또는 공급업체에서 제공한 레거시 학습 관리 시스템을 갖고 있습니다. LMS는 기업 교육 콘텐츠와 교육 데이터로 구성됩니다. 기업에서 Learning Manager를 구매하는 경우, 기존 LMS 콘텐츠와 데이터를 Learning Manager로 이동하여 조직의 레거시 데이터를 그대로 보존하면서도 현대적이고 직관적인 LMS의 혜택을 활용하고자 하실 것입니다.

Learning Manager는 조직의 통합 책임자가 마이그레이션 작업을 설정하고 수행하는 데 필요한 도구 및 사양을 제공합니다.

오늘부로 조직의 책임자가 Adobe 지원팀에 문의하면 Learning Manager에 있는 마이그레이션 기능에 액세스할 수 있습니다. 계정에서 마이그레이션 기능을 활성화하려면 Adobe Learning Manager 지원 팀에 문의하십시오.

## 마이그레이션 프로세스 {#apidescription}

마이그레이션에 대한 사전 요구 사항, 마이그레이션 프로세스에 관련된 주요 단계, 마이그레이션 스프린트, 사양, 데이터 및 콘텐츠 마이그레이션 단계는 이 섹션에서 다음과 같이 설명합니다.

### 중요 마이그레이션 자문

마이그레이션 타임라인은 데이터의 품질과 크기에 크게 좌우됩니다. 온보딩 중 마이그레이션이 필요한 경우 미리 이 활동을 계획하고 Adobe Learning Manager 온보딩 팀과 긴밀하게 협력하여 지연을 방지하십시오.

### 필수 구성 요소 {#prerequisites}

Learning Manager 팀은 조직의 통합 책임자가 마이그레이션 프로세스에 착수하기 전에 다음 작업을 수행하기를 권장합니다.

* 통합 책임자는 현재 사용하는 LMS에서 데이터와 콘텐츠를 추출한 뒤, 데이터를 Learning Manager에서 정의된 파일 형식으로 변환합니다.
* Learning Manager는 마이그레이션 프로세스에 사용자 가져오기를 지원하지 않습니다. 조직에서 커넥터를 사용하여 사용자를 가져와야 합니다. Adobe 시스템은 마이그레이션 프로세스 이전에 해당 커넥터를 구성하기를 권장합니다. 자세한 내용은 [Learning Manager 커넥터 도움말](connectors.md)을 참조하십시오.

Learning Manager는 책임자가 데이터와 콘텐츠를 Learning Manager 제작 환경에 마이그레이션하기 전에 평가판 계정에서 마이그레이션 프로세스를 시도해 보는 것을 추천합니다.

### 마이그레이션 프로세스 주요 단계 {#keystepsofmigrationprocess}

기존 LMS에서 Learning Manager로 콘텐츠 및 데이터를 마이그레이션하는 주요 단계는 다음과 같습니다.

1. 통합 책임자 또는 파트너가 마이그레이션할 LMS 데이터 및 콘텐츠를 평가합니다.
1. 통합 책임자는 Learning Manager에서 데이터 및 콘텐츠를 수용하기 위해 제공하는 도구 및 사양을 평가합니다.
1. 통합 책임자는 이전 LMS에서 제공하는 기능을 기반으로 이전 LMS의 교육 데이터 및 콘텐츠를 내보내는 데 필요한 코드를 작성하거나 수동 작업에 착수합니다.
1. 교육 데이터 및 콘텐츠가 준비되면 통합 책임자는 데이터와 콘텐츠를 분석 및 매핑하여 Learning Manager 마이그레이션 사양에 일치시킵니다.
1. 통합 책임자는 다음 순서로 Learning Manager에서 제공하는 도구를 사용합니다.

   1. Learning Manager에 학습자를 전송
   1. Learning Manager에 교육 콘텐츠를 전송합니다.
   1. 마지막으로 Learning Manager에 교육 데이터를 전송합니다.

조직은 레거시 콘텐츠와 Learning Manager LMS를 함께 사용할 수 있습니다.

### 마이그레이션 객체 범위 {#scopeofmigrationobjects}

다음 학습 객체에 대해서만 콘텐츠를 마이그레이션할 수 있습니다.

* 모듈
* 배지
* 강의
* 모듈 버전
* 강의 인스턴스
* 강의 모듈
* 스킬
* 스킬 레벨
* 스킬 강의
* 인증
* 인증 강의
* 인증 커밋
* 학습 프로그램
* 학습 프로그램 강의
* 학습 프로그램 인스턴스
* 학습 프로그램 강의 인스턴스
* 작업 지원
* 작업 지원 버전
* 작업 지원 강의
* 작업 지원 스킬
* 등록
* 인증 등록
* 학습 프로그램 등록
* 작업 지원 등록
* 사용자 강의 등급

### 마이그레이션의 주요 개념 {#keyconceptsofmigration}

빠른 참조를 위해 Learning Manager 마이그레이션 프로세스의 주요 개념 중 일부를 다음과 같이 간단히 설명합니다.

**마이그레이션 프로젝트**

Learning Manager에서 마이그레이션 프로젝트는 하나 이상의 스프린트로 구성됩니다. 계정에 여러 마이그레이션 프로젝트를 보유할 수 있습니다. Learning Manager의 마이그레이션 프로세스는 마이그레이션 프로젝트를 생성하는 것으로 시작합니다.

**스프린트**

Learning Manager 마이그레이션 프로젝트에서 스프린트는 기존 LMS에서 마이그레이션하기로 선택한 마이그레이션 항목 세트로 정의됩니다. 마이그레이션 항목은 강의 모듈, 학습자 기록 또는 강의 세트일 수 있습니다. 한 스프린트에 여러 학습 데이터 항목을 보유할 수 있습니다. 각 스프린트에서 마이그레이션 작업을 실행할 수 있습니다.

**스프린트 실행**

스프린트 실행은 스프린트 마이그레이션 작업을 시작하는 프로세스입니다. 실행 중에도 언제든지 스프린트를 중단할 수 있습니다.

**스프린트 재실행**

마이그레이션 스프린트가 완료된 후에도 언제든지 재실행할 수 있습니다. 스프린트를 재실행하는 상황은 스프린트 항목에 데이터를 추가하고 해당 데이터를 응용 프로그램에 다시 마이그레이션하거나 CSV의 오류를 수정할 때 발생합니다.

**CSV 사양**

Learning Manager는 [표준 CSV 사양](migration-manual.md#main-pars_header_140933605) 세트를 제공합니다. 마이그레이션 프로세스를 시작하기 전에 CSV 사양을 살펴보는 것이 좋습니다. 조직의 통합 책임자는 기존의 데이터 형식을 분석하고 매핑하여 Learning Manager에서 제공한 CSV 템플릿 항목에 일치시킵니다.

**마이그레이션 프로젝트 태그**

Adobe 시스템은 Learning Manager 응용 프로그램 내에서 쉽게 마이그레이션 프로젝트를 식별할 수 있도록 일련의 키워드를 태그로 사용하는 것을 추천합니다. 태그는 Learning Manager 응용 프로그램 내부에서 언제든지 프로젝트를 식별하게 해줍니다.

**콘텐츠리스 모듈**

Learning Manager에서는 콘텐츠가 없는 모듈을 업로드할 수 있습니다. Adobe 시스템은 Learning Manager에서 해당 형식을 콘텐츠리스 모듈로 간주합니다. 콘텐츠 없이 기존 LMS에서 레거시 데이터를 마이그레이션하고자 하는 경우, URL 참조 없이 module_version.csv 파일을 업로드할 수 있습니다.

## CSV 사양 및 샘플 CSV {#csv}

아래에서 기존 LMS 마이그레이션 데이터를 매핑하는 데 사용하는 표준 CSV 사양을 확인할 수 있습니다. Zip 파일을 다운로드하려면 csv-specifications 및 sample-csvs를 클릭합니다. 다운로드한 csv-specifications.zip에는 7개의 Excel 스프레드시트 파일이 포함되어 있습니다. 이 엑셀 시트 파일에는 .csv 파일을 채우는 방법을 파악하게 해주는 설명과 사양이 들어 있습니다. 이 .xlsx 파일에 설명된 것과 같이 해당 .csv 파일은 각 필드에 지정된 형식의 데이터를 갖고 있어야 합니다.

<table border="1" cellspacing="0" cellpadding="0" width="100%">
 <tbody>
  <tr>
   <th>
    <p><b>Sl.no</b></p></th>
   <th>
    <p><b>파일 이름</b></p></th>
   <th>
    <p><b>콘텐츠 설명</b></p></th>
   <th>
    <p>노트</p></th>
  </tr>
  <tr>
   <td>
    <p>1</p></td>
   <td>
    <p>module.xlsx</p></td>
   <td>
    <p>Metadata for module.csv</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>2</p></td>
   <td>
    <p>badge.xlsx</p></td>
   <td>
    <p>badge.xlsx에 대한 메타데이터</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>3</p></td>
   <td>
    <p>course.xlsx</p></td>
   <td>
    <p>Metadata for course.csv</p></td>
   <td>
    <p>강의마다 하나의 작성자 이름을 입력합니다. 마이그레이션 후 작성자 이름이 정확하게 표시되지 않는 경우가 있습니다. </p></td>
  </tr>
  <tr>
   <td>
    <p>4</p></td>
   <td>
    <p>module_version.xlsx </p></td>
   <td>
    <p>module_version.csv용 메타데이터</p></td>
   <td>
    <p>콘텐츠를 업로드한 Box 계정 폴더에 URL 경로를 입력했는지 확인하십시오. </p></td>
  </tr>
  <tr>
   <td>
    <p>5</p></td>
   <td>
    <p>course_instance.xlsx</p></td>
   <td>
    <p>course_instance.csv용 메타데이터 </p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>6</p></td>
   <td>
    <p>Session.xlsx</p></td>
   <td>
    <p>Metadata for session.csv</p></td>
   <td>
    <p>세션 CSV의 모든 항목이 최소한 1개의 강의실/가상 강의실 모듈과 연결되어 있는지 확인하십시오.</p></td>
  </tr>
  <tr>
   <td>
    <p>7</p></td>
   <td>
    <p>course_module.xlsx</p></td>
   <td>
    <p>course_module.csv용 메타데이터</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>8</p></td>
   <td>
    <p>skill.xlsx</p></td>
   <td>
    <p>Metadata for skill.csv</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>9</p></td>
   <td>
    <p>skill_level.xlsx</p></td>
   <td>
    <p>skill_level.csv용 메타데이터</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>10</p></td>
   <td>
    <p>skill_course.xlsx</p></td>
   <td>
    <p>skill_course.csv용 메타데이터</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>11</p></td>
   <td>
    <p>certification.xlsx</p></td>
   <td>
    <p>Certification.csv용 메타데이터</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>12</p></td>
   <td>
    <p>certification_course.xlsx</p></td>
   <td>
    <p>certification_course.csv용 메타데이터</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>13</p></td>
   <td>
    <p>certification_commit.xlsx</p></td>
   <td>
    <p>certification_commit.csv용 메타데이터</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>14</p></td>
   <td>
    <p>learning_program.xlsx</p></td>
   <td>
    <p>learning_program.csv용 메타데이터</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>15</p></td>
   <td>
    <p>learning_program_course.xml </p></td>
   <td>
    <p>learning_program_course.csv용 메타데이터 </p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>16</p></td>
   <td>
    <p>learning_program_instance.xlsx </p></td>
   <td>
    <p>Metadata for learning_program_instance.csv</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>17</p></td>
   <td>
    <p>learning_program_instance_course_instance.xlsx </p></td>
   <td>
    <p>Metadata for learning_program_instance_course_instance.csv</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>18</p></td>
   <td>
    <p>job_aid.xlsx</p></td>
   <td>
    <p>Metadata for job_aid.csv</p></td>
   <td>
    <p>모든 마이그레이션된 job_aid는 하나 이상의 job_aid 버전을 가져야 합니다.</p></td>
  </tr>
  <tr>
   <td>
    <p>19</p></td>
   <td>
    <p>Job_aid_version.xlsx</p></td>
   <td>
    <p>job_aid_version.csv용 메타데이터</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>20</p></td>
   <td>
    <p>job_aid_course.xlsx</p></td>
   <td>
    <p>job_aid_course.csv용 메타데이터</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>21</p></td>
   <td>
    <p>job_aid_skills.xlsx</p></td>
   <td>
    <p>Metadata for job_aid_skills.csv</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>22</p></td>
   <td>
    <p>enrollments.xlsx</p></td>
   <td>
    <p>Metadata for enrollments.csv</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>23</p></td>
   <td>
    <p>certification_enrollement.xlsx</p></td>
   <td>
    <p>certification_enrollement.csv용 메타데이터</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>24</p></td>
   <td>
    <p>learning_program_enrollment.xlsx</p></td>
   <td>
    <p>Metadata for learning_program_enrollment.csv<br><br></p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>25</p></td>
   <td>
    <p>job_aid_enrollment.xlsx</p></td>
   <td>
    <p>job_aid_enrollment.csv용 메타데이터</p></td>
   <td> </td>
  </tr>
  <tr>
   <td>
    <p>26</p></td>
   <td>
    <p>user_course_grade.xlsx</p></td>
   <td>
    <p><br>
      user_course_grade.csv용 메타데이터</p></td>
   <td>
    <p>필수 항목이 아니더라도 필요한 학습자 기록 데이터를 .csv 파일에 입력합니다. 해당 정보가 없는 경우 .csv의 마이그레이션이 처리된 후에도 Learning Manager 응용 프로그램이 데이터를 반영하지 못할 수 있습니다. sample-csvs.zip 파일에는 위와 같이 유사한 명명 규칙을 따르는 7개의 .csv 파일이 포함되어 있습니다.</p></td>
  </tr>
  <tr>
   <td>
    <p>27</p></td>
   <td>
    <p>user_skill.xlsx</p></td>
   <td>
    <p><br>
      user_skill.csv용 메타데이터</p></td>
   <td>
    <p> </p></td>
  </tr>
 </tbody>
</table>

Learning Manager는 UTF 8 및 32비트 형식으로만 날짜 및 시간 값을 지원합니다. CSV 파일에서 범위를 벗어난 날짜를 2038-07-17T08:53:21.000Z 또는 1980-04-17T08:13:25.322Z로 언급하면 마이그레이션 중 오류가 발생할 수 있습니다.

* [sample-csvs.zip](assets/sample-csvs.zip)
* [csv_specifications.zip](assets/csv-specifications.zip)

가져오기 중 다음 CSV 파일의 종속성에 대해 알고 있어야 합니다.

* module_version.csv는 module.csv에 종속됩니다.
* course_instance.csv는 course.csv에 종속됩니다.
* course_instance.csv는 course.csv, module.csv 및 module_version.csv에 종속됩니다.
* course_instance.csv는 course.csv에 종속됩니다.
* session.csv는 course.csv 및 module.csv에 종속됩니다.
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

## 마이그레이션 절차 {#migrationprocedure}

마이그레이션 절차를 시작하기 전에 다음 사항에 유의해야 합니다.

* 한 시점에 하나의 계정으로 오직 하나의 마이그레이션 프로젝트만 진행할 수 있습니다. 한 시점에 한 프로젝트에서는 오직 한 개의 스프린트만 활성화할 수 있습니다.
* 이미 실행한 마이그레이션 프로젝트는 취소할 수 없습니다. 다만, Learning Manager의 각 기능에서 지원하는 기존의 삭제 옵션을 사용하여 데이터 또는 콘텐츠 마이그레이션을 취소할 수 있습니다.
* 마이그레이션 프로젝트를 시작하는 즉시 &#39;마이그레이션 중&#39; 상태로 이동합니다. 마이그레이션 중에는 통합 책임자 역할만 Learning Manager에 로그인할 수 있습니다.

### FTP 및 Box 계정 생성 {#creatingftpandboxaccounts}

마이그레이션 프로젝트 계획은 아주 중요합니다. 각 스프린트에서 마이그레이션할 내용을 쉽게 식별할 수 있도록 프로젝트를 여러 스프린트로 나누는 것이 좋습니다. 프로젝트가 끝난 후 한 번의 막대한 확인 단계를 거치는 대신 각 스프린트의 데이터가 제대로 마이그레이션되었는지 매번 확인하면 더욱더 좋습니다. 마이그레이션 프로젝트의 스프린트를 시작하기 전에, 데이터와 콘텐츠를 FTP 및 Box 서버에 각각 업로드해야 합니다. 사용자 정의 FTP 및 Box에 대한 계정이 없는 경우 만들 수 있습니다.

<!--**Create FTP account**-->

<!--Click **[!UICONTROL Request for CSV FTP folder]**. A pop-up dialog appears prompting you to enter your e-mail id. Go through online instructions and create an FTP account. As soon as you create your account, you can view your migration project and sprint project folders in FTP. 

A sample snapshot of project files and folder of FTP is shown below for your reference. -->

<!--![](assets/exavault-migration-upload-folders.png)-->

**Box 계정 생성**

FTP 폴더 생성에서 했던 것과 유사한 절차를 따라 콘텐츠 업로드 폴더를 생성합니다. 왼쪽 창에서 &#39;마이그레이션&#39;을 클릭하면 나타나는 페이지의 아래에 있는 &#39;콘텐츠 업로드 폴더 요청&#39;을 클릭합니다.

Box에서 공유 폴더 링크가 포함된 전자 메일을 전송합니다. Box 계정이 없는 경우 &#39;가입&#39;을 클릭하여 계정을 생성합니다. 통합 책임자 전자 메일 ID로 로그인 지침이 전송됩니다.

**FTP 폴더 또는 Box 폴더에 데이터 업로드(.csv 파일)**

FTP 또는 Box 계정 생성은 마이그레이션 프로젝트의 전제 조건입니다. 따라서 이 단계에서 Learning Manager 응용 프로그램에서 마이그레이션 프로젝트 및 스프린트를 생성할 수 있습니다.  마이그레이션 프로젝트를 만들려면 이 페이지의 **데이터 및 콘텐츠 마이그레이션 절차** 섹션을 참조하십시오.

FTP 또는 Box 계정에서 프로젝트 폴더 이름을 클릭한 다음 스프린트 이름을 클릭합니다. 스프린트 폴더에 마이그레이션할 .csv 데이터 파일을 업로드할 수 있습니다. 업로드하려면 FTP 또는 Box 서버의 상단에 있는 파일 업로드 버튼을 클릭하고 .csv 파일을 삭제합니다. FTP에 업로드된 후의 샘플 스냅샷은 아래를 참조하십시오.

<!--![](assets/exavault-upload.png)-->

Learning Manager 마이그레이션 프로젝트로 돌아와 **[!UICONTROL 새로 고침]**&#x200B;을 클릭한 다음 마이그레이션 스프린트에 나열된 전체 .csv 데이터 유형을 볼 수 있습니다.

**콘텐츠 폴더에 교육 콘텐츠 업로드**

Box 계정에 기존 LMS 교육 콘텐츠를 업로드합니다. 이미 마이그레이션 프로젝트와 스프린트를 생성했다면 Box 계정에 마이그레이션 프로젝트와 스프린트 이름을 채울 수 있습니다. 같은 경로로 콘텐츠를 업로드할 수 있습니다. 마이그레이션 프로젝트를 만들려면 이 페이지의 **데이터 및 콘텐츠 마이그레이션 절차** 섹션을 참조하십시오.

콘텐츠 파일을 드래그 앤 드롭하거나 **[!UICONTROL &#39;업로드&#39;]**&#x200B;를 클릭하여 데스크톱에서 파일을 선택할 수 있습니다. 콘텐츠의 파일 크기가 큰 경우, 파일 업로드에 지연이 발생할 수 있습니다. 파일 크기에 따라 파일을 Box 계정에 업로드하는 데 걸리는 시간이 달라집니다.

아래에 있는 Box 계정에 콘텐츠를 업로드한 후의 샘플 스냅샷을 참조하십시오.

![](assets/box-account.png)

Box 계정의 *파일*

파일이 Box 계정에 업로드 된 후, module_version.csv 파일에 해당 Box 콘텐츠 파일의 상대 경로를 입력했는지 확인하십시오. 이는 모듈 콘텐츠 경로를 표시하는 데 필수적인 단계입니다.

FTP 및 Box 서버에 로그인한 다음 콘텐츠를 업로드했다면, 아래의 스냅샷과 같이 Learning Manager에 CSV 위치가 나타납니다.

![](assets/after-setup.jpg)

Box 계정의 *CSV 위치*

## 데이터 및 콘텐츠 마이그레이션 절차 {#dataandcontentmigrationprocedure}

기업 LMS 데이터 및 콘텐츠를 Learning Manager에 마이그레이션하는 절차는 다음과 같이 설명할 수 있습니다.

마이그레이션을 시작하기 전에 마이그레이션 프로세스의 전제 조건을 확인합니다. 이 페이지의 [CSV 사양 및 샘플 CSV](migration-manual.md#main-pars_header_140933605) 섹션을 참조하여 데이터 및 콘텐츠 마이그레이션에 사용할 CSV를 준비합니다.

1. 통합 책임자로 Learning Manager 응용 프로그램에 로그인한 다음 왼쪽 창의 **[!UICONTROL 마이그레이션]**&#x200B;을 클릭합니다.

   마이그레이션 프로젝트 홈페이지가 나타납니다. 조직에서 이미 마이그레이션 프로젝트를 생성한 경우, 이 페이지에서 전체 마이그레이션 목록을 볼 수 있습니다.

1. 마이그레이션 프로젝트를 생성하려면 페이지 오른쪽 상단 모서리에 있는 **[!UICONTROL &#39;신규&#39;]**&#x200B;를 클릭합니다. 또는 페이지의 **[!UICONTROL &#39;마이그레이션 프로젝트 생성&#39;]** 링크를 클릭하여 마이그레이션 프로젝트를 생성할 수 있습니다. 마이그레이션 프로젝트 생성 페이지가 나타납니다.

   아직 FTP 폴더를 생성하지 않은 경우 계정에 FTP 폴더를 생성하라는 메시지가 표시됩니다. 이는 마이그레이션 프로젝트 생성을 시작하기 전에 반드시 수행해야 하는 작업입니다.

   ![](assets/create-project.png)
   *FTP 폴더 만들기*

   마이그레이션 프로젝트에 프로젝트 이름, 프로젝트 태그, 강의 카탈로그 및 설명을 입력합니다. **[!UICONTROL [만들기]]**&#x200B;를 클릭합니다.

   마이그레이션 데이터 항목은 이 마이그레이션 프로젝트 태그로 식별됩니다. 특정 강의 카탈로그가 없는 경우, 드롭다운에서 기본 카탈로그를 선택합니다. 마이그레이션 프로젝트를 사용하여 마이그레이션하는 모든 강의는 이 단계에서 선택하는 카탈로그에 포함됩니다. 카탈로그를 선택하지 않는 경우 마이그레이션된 모든 강의는 기본 카탈로그의 일부가 됩니다.

1. 다음 스냅샷과 같이 스프린트 구성 페이지가 나타납니다. 마이그레이션 프로젝트의 일부로 스프린트를 생성해야 합니다. 스프린트 이름을 선택하고 스프린트에 대한 간략한 설명을 입력합니다. 해당 스프린트의 일부로 콘텐츠를 마이그레이션하고 싶다면 &#39;예&#39;를 선택합니다. **[!UICONTROL 다음]**&#x200B;을 클릭하세요.

   ![](assets/users-modified-sprint.png)
   *스프린트 마이그레이션*

   Learning Manager 응용 프로그램과 사용자 목록을 동기화하려면 제목이 **마지막 실행 이후 사용자가 추가 또는 수정되었습니다**&#x200B;인 확인란을 선택합니다. Learning Manager응용 프로그램으로 콘텐츠와 데이터를 마이그레이션하는 경우, 해당 단계는 필수가 아닐 수 있습니다. 그러나 이전 스프린트 마이그레이션과 최신 스프린트 마이그레이션 사이에 시차가 있는 경우, 사용자 목록을 동기화하는 것이 좋습니다. 이 단계를 거치면 Learning Manager 데이터베이스가 LMS 사용자와 동기화됩니다.

   이 동기화 단계는 enrollment.csv 및 user_course_grade.csv 파일을 마이그레이션할 때 시행하는 것이 좋습니다. 이 단계를 통해 Learning Manager 데이터베이스를 마이그레이션 데이터베이스와 동기화하며 스프린트에 기록이 마이그레이션된 모든 사용자를 마이그레이션 데이터베이스에서 사용할 수 있게 해줍니다.

1. 업로드된 데이터 및 콘텐츠로 스프린트 마이그레이션을 시작할 수 있습니다. FTP 및 콘텐츠 폴더를 Learning Manager 응용 프로그램과 동기화하는 스프린트 실행을 시작하기 전에 **[!UICONTROL 새로 고침]** 링크를 클릭하십시오.

   ![](assets/sprint1-filesupload.png)
   *스프린트 마이그레이션 시작*

   페이지의 오른쪽 상단 모서리에 있는 **[!UICONTROL 시작]**&#x200B;을 클릭합니다. 스프린트 마이그레이션을 중단하려면 스프린트 마이그레이션 프로세스 중 언제든지 **[!UICONTROL 중지]**&#x200B;를 클릭할 수 있습니다.

   마이그레이션 상태는 각 스프린트 데이터 항목 및 콘텐츠에 표시됩니다. 마이그레이션 스프린트 실행의 일부로 성공 및 실패 항목을 확인합니다.

   모듈 콘텐츠를 업로드하는 경우, 콘텐츠 폴더의 경로가 module_version.csv에 입력되어 있는지 확인합니다. 이 단계를 빠트린 경우, 마이그레이션 중 에러가 발생할 수 있습니다. 예를 들어 비디오와 같은 자가 진행식 모듈 콘텐츠를 업로드하는 경우, module_version.csv에 상대 Box URL 경로를 지정해야 합니다. 활동 모듈 콘텐츠에는 URL 이름을 지정할 수 있습니다.

   진행 대화 상자에 대해 아래에 있는 샘플 스냅샷을 참조하십시오. 스냅샷과 같이, 각 마이그레이션 데이터 항목에 대하여 처리된 기록의 개수와 성공 및 실패 항목 상태를 볼 수 있습니다. 오류 로그를 다운로드해서 보려면 실패 항목에 대한 &#39;오류 기록 다운로드&#39;를 클릭합니다. CSV에서 오류를 해결하여 FTP에 다시 업로드할 수 있습니다.

   ![](assets/sample-sprint-progress-status.png)
   *스프린트 진행률 보기*

   마이그레이션 프로젝트의 전체 스프린트 목록을 보려면 왼쪽 창의 스프린트 목록을 클릭합니다. 아래의 스냅샷에 보이는 것처럼 전체 스프린트 목록, 각 스프린트에서 실행한 횟수, 시작 날짜, 지속 기간 및 완료 상태를 확인할 수 있습니다.

   ![](assets/sprint-list.png)
   *스프린트 목록 보기*

1. 최신 버전으로 업데이트된 CSV를 업로드한 후, 페이지 오른쪽 상단 모서리에 있는 &#39;재실행&#39;을 클릭합니다. 모든 데이터 항목에 대한 프로세스를 재실행합니다. 변경 사항이 없는 항목은 무시합니다. 스프린트의 데이터 항목 마이그레이션에 만족한다면 페이지 위쪽의 단추를 클릭하여 스프린트 마이그레이션을 완료로 표시할 수 있습니다. 나중에 데이터 항목을 추가하여 새 스프린트를 시작할 수 있습니다. 스프린트를 완료로 표시한 후에는 재실행할 수 없습니다. 마찬가지로 마이그레이션 프로젝트에는 스프린트 수 제한이 없습니다. 모든 스프린트의 마이그레이션 상태가 만족스러우면 스프린트 목록 페이지에서 **프로젝트 완료 표시** 링크를 클릭하여 마이그레이션 프로젝트를 완료로 표시할 수 있습니다.

   마이그레이션 프로젝트를 완료로 표시하기 전에 프로젝트의 모든 스프린트가 완료되었는지 확인합니다. 마이그레이션을 완료로 표시한 후에는 뒤로 돌아가서 해당 프로젝트에서 스프린트를 생성하거나 해당 프로젝트 내용을 수정할 수 없습니다. 다른 마이그레이션 프로젝트를 생성하여 스프린트를 추가해야 합니다.

## 마이그레이션 인증 {#registration}

조직의 레거시 LMS에서 학습 데이터 및 콘텐츠 마이그레이션을 한 후, 다양한 학습 객체 기능을 사용하여 가져온 데이터와 콘텐츠를 확인할 수 있습니다. 예를 들어 책임자로 Learning Manager에 로그인하여 가져온 모듈과 강의 데이터 및 콘텐츠를 사용할 수 있는지 확인할 수 있습니다.

## API를 사용한 마이그레이션

Adobe Learning Manager(ALM)는 주로 레거시 LMS 플랫폼에서 마이그레이션하는 데 사용되는 외부 시스템의 데이터 또는 콘텐츠를 인제스트하는 마이그레이션 기능을 제공합니다.

그러나 일부 조직에서는 이 프로세스를 일회성 가져오기가 아닌 정규 일정(예: 야간 또는 주간)으로 실행해야 할 수 있습니다.

예를 들어, 가상 고객(NovaFX)이 가상 외부 공급업체(SquareCorp)와 통합되고 예정된 마이그레이션을 자동화하는 방법을 확인할 수 있습니다. 이 통합을 통해 다음과 같은 작업을 수행할 수 있습니다.

* SquareCorp 강의가 NovaFX 학습자를 위한 ALM 내의 학습 개체로 나타납니다.
* NovaFX는 SquareCorp 호스팅 과정에 대한 학습자 진행률을 ALM에서 직접 추적합니다.

### 통합 요구 사항

SquareCorp는 다음을 제공해야 합니다.

* 강의 메타데이터 정보: NovaFX가 액세스할 수 있는 강의 메타데이터를 공유하는 API입니다.
* 진행률 데이터 정보: 학습자의 진행률 및 완료 정보를 주기적으로 공유하는 API입니다.

### 주요 정의

* **활성 프로젝트:** 프로젝트가 &quot;진행 중&quot; 또는 &quot;초기화됨&quot;인 경우 활성화됩니다.
* **활성 스프린트:** 스프린트가 &quot;진행 중&quot; 또는 &quot;초기화됨&quot;인 경우 활성화됩니다.

### 스프린트 실행 자동화

일정대로 다음을 수행하는 앱 또는 스크립트를 빌드합니다.

1. SquareCorp에서 과정 메타데이터, 사용자 등록 및 학습자 성적을 가져옵니다.
2. CSV 파일을 생성합니다.
3. 파일을 Box 또는 FTP에 업로드합니다.
4. 마이그레이션 API를 사용하여 스프린트를 트리거합니다.

### API 세부 정보

#### 마이그레이션 실행 시작

**끝점:** POST /primeapi/v2/bulkimport/startrun

매개 변수:

* **lockaccount(부울):** 매개 변수는 실행 시작 시 계정을 잠그는지 여부를 결정합니다. 기본적으로 false로 설정됩니다. 계정을 잠가야 할 정당한 이유가 없으면 이 매개 변수를 사용하지 않는 것이 좋습니다.
* **카탈로그 ID(정수):** 이 매개 변수를 사용하면 마이그레이션하는 동안 대상 카탈로그를 선택할 수 있습니다. 마이그레이션 프로젝트를 만들 때 설정되지만 개별 실행에 대해 조정할 수 있습니다. 카탈로그 ID가 변경되면 나중에 실행할 때 추가된 학습 객체가 가장 최근에 선택한 카탈로그에 배치됩니다. 마이그레이션 프로젝트를 만드는 동안 선택한 카탈로그로 다시 돌아가야 하는 경우 이 역시 명시적으로 지정해야 합니다.
* **migrationProjectId(정수):** 계정에서 API 사용 실행이 여러 개 활성화된 경우 특정 마이그레이션 프로젝트를 트리거하기 위해 매개 변수가 필요합니다.

#### 동기화를 시작할 수 있는지 확인

콘텐츠를 스프린트 폴더에 동기화할 수 있는지 확인합니다. 이 API가 성공적인 응답 개체를 반환하지 않는 한 콘텐츠 또는 메타데이터 파일을 FTP 폴더에 복사하지 마십시오.

**끝점:** GET /primeapi/v2/bulkimport/cansync

매개 변수:

* **migrationProjectId(정수)** 계정에서 API 사용 실행이 여러 개 활성화된 경우 특정 마이그레이션 프로젝트를 트리거하기 위해 매개 변수가 필요합니다.

<b>응답 성공</b>

```
{  
    "status": "OK",  
    "title": "BULKIMPORT_CAN_SYNC_NOW",  
    "source": {  
        "info": "Yes"  
    }  
} 
```

<b>응답 성공</b>

```
{ 
    "status": "BAD_REQUEST", 
    "title": "BULKIMPORT_ERROR_CANNOT_SYNC", 
    "source": { 
        "info": "Error, No active projects" 
    } 
} 
```

<b>가능한 API 응답</b>

| 액션 | 유형 | 메시지 |
| ------------------------------------- | ------- | ------------------------------------------------------------------------------------- |
| BULKIMPORT_RUN_INITIATED_SUCCESSFULLY | 성공 | 실행이 시작되었습니다. |
| BULKIMPORT_ERROR_CANNOT_INITATE_RUN | 오류 | 실행이 진행 중입니다. |
| BULKIMPORT_ERROR_CANNOT_INITATE_RUN | 오류 | 하나 이상의 활성 프로젝트가 있습니다. |
| BULKIMPORT_ERROR_CANNOT_INITATE_RUN | 오류 | 스프린트가 두 개 이상 있습니다 |
| BULKIMPORT_ERROR_CANNOT_INITATE_RUN | 오류 | 활성 프로젝트 없음 |
| BULKIMPORT_ERROR_CANNOT_INITATE_RUN | 오류 | 활성 스프린트 없음 |
| BULKIMPORT_ERROR_CANNOT_INITATE_RUN | 오류 | 제공된 카탈로그가 유효한 ID가 아니거나 prime 계정에 속하지 않습니다. |
| BULKIMPORT_CAN_SYNC_NOW | 정보 | 지금 동기화 가능 |
| BULKIMPORT_ERROR_CANNOT_SYNC | 오류 | 실행이 진행 중입니다. |
| BULKIMPORT_ERROR_CANNOT_SYNC | 오류 | 하나 이상의 활성 프로젝트가 있습니다. |
| BULKIMPORT_ERROR_CANNOT_SYNC | 오류 | 스프린트가 두 개 이상 있습니다 |
| BULKIMPORT_ERROR_CANNOT_SYNC | 오류 | 활성 프로젝트 없음 |
| BULKIMPORT_ERROR_CANNOT_SYNC | 오류 | 활성 스프린트 없음 |
| BULKIMPORT_ERROR_CANNOT_SYNC | 오류 | 폴더에 유효한 파일이 없습니다. |

### 샘플 통합 플로우

1. cansync API를 확인합니다.
2. CSV 파일을 생성하고 업로드합니다.
3. startrun API를 사용하여 스프린트를 트리거합니다.
4. 응답을 모니터링하고 오류를 처리합니다.

### 제한 사항

마이그레이션 API는 스프린트 실행 후 출력 CSV 파일에서 직접 마이그레이션 관련 오류를 확인하는 기능을 제공하지 않습니다. 그러나 이러한 오류는 스프린트 실행 후 통합 관리자 사용자 인터페이스에 액세스하여 CSV 파일 내에서 행으로 검토할 수 있습니다.

### API를 통한 마이그레이션 확인

마이그레이션 API `runStatus`을(를) 사용하면 통합 관리자가 API를 통해 트리거된 마이그레이션 실행의 진행률을 추적할 수 있습니다.

`runStatus` API는 완료된 실행을 위해 오류 로그를 CSV 형식으로 다운로드할 수 있는 직접 링크도 제공합니다. 다운로드 링크는 7일 동안 활성 상태로 유지되며 로그는 1개월 동안 유지됩니다.

**샘플 컬**

**엔드 포인트**

```
GET /bulkimport/runStatus
```

**매개 변수**

* **migrationProjectId**: (필수). 마이그레이션 프로젝트의 고유 식별자입니다. 마이그레이션 프로젝트는 기존 LMS(교육 관리 시스템)에서 Adobe Learning Manager으로 데이터와 콘텐츠를 전송하는 데 사용됩니다. 각 마이그레이션 프로젝트는 마이그레이션 작업 단위의 작은 스프린트인 다중 스프린트로 구성될 수 있습니다.

* **sprintId**: (필수). 마이그레이션 프로젝트 내 스프린트의 고유 식별자입니다. 스프린트는 기존 LMS에서 Adobe Learning Manager으로 마이그레이션할 특정 학습 항목(예: 강의, 모듈, 학습자 기록)이 포함된 마이그레이션 작업의 하위 집합입니다. 각 스프린트는 독립적으로 실행될 수 있어 단계적인 마이그레이션이 가능합니다.

* **sprintRunId**:(필수). 마이그레이션 프로젝트 내에서 특정 스프린트의 실행을 추적하는 데 사용되는 고유 식별자입니다. 스프린트에 정의된 항목의 실제 마이그레이션 프로세스와 연결됩니다. sprintRunId는 마이그레이션 작업을 모니터링, 문제 해결 및 관리하는 데 유용합니다.

**응답**

```
{
  "sprintId": 2510080,
  "sprintRunId": 2740845,
  "migrationProjectId": 2509173,
  "startTime": 1746524711052,
  "endTime": 1746524711052,
  [
    {
      "id": 2609923,
      "lastHeartbeatTime": 1746524711052,
      "objectName": "content",
      "jobState": "COMPLETED",
      "errorCsvLink": "",
      "errorLogLink": "migration/5830/2509173/2510080/2740845/content_err.csv",
      "sequenceNumber": 1
    },
    {
      "id": 2609922,
      "lastHeartbeatTime": 1746524713577,
      "objectName": "course",
      "jobState": "WAITING_IN_QUEUE",
      "errorCsvLink": "",
      "errorLogLink": null,
      "sequenceNumber": 2
    }
  ]
}
```

또한 이제 `startRun` API 응답에는 새 상태 끝점을 쿼리하는 데 필요한 마이그레이션 프로젝트 ID, 스프린트 ID 및 스프린트 실행 ID가 포함됩니다.

```
curl -X GET --header 'Accept: text/html' 'https://learningmanager.adobe.com/primeapi/v2/bulkimport/runStatus?migrationProjectId=001&sprintId=10001&sprintRunId=7'
```

다음 응답을 생성합니다. 응답에는 다음이 포함됩니다.

* `migrationId`
* `sprintId`
* `sprintRunId`

**응답**

```
{
  "status": "OK",
  "title": "BULKIMPORT_RUN_INITIATED_SUCCESSFULLY",
  "source": {
    "info": "Success",
    "migrationInfo": {
      "migrationProjectId": "001",
      "sprintId": "10001",
      "sprintRunId": "7"
    }
  }
}
```

## 마이그레이션 보강 {#retrofittinginmigration}

이 통합 기능은 레거시 학습 관리 시스템의 학습 객체에 있는 기록 데이터를 Learning Manager에서 생성된 활성 강의에 보강하게 해줍니다.

아래에서 기존 LMS 마이그레이션 데이터를 매핑하는 데 사용하는 표준 CSV 사양을 확인할 수 있습니다. Zip 파일을 다운로드하려면 csv-specifications 및 sample-csvs를 클릭합니다. 다운로드한 csv-specifications.zip 파일에는 4개의 엑셀 시트 파일이 포함되어 있습니다. 이 엑셀 시트 파일에는 .csv 파일을 채우는 방법을 파악하게 해주는 설명과 사양이 들어 있습니다. 이 .xlsx 파일에 설명된 것과 같이 해당 .csv 파일은 각 필드에 지정된 형식의 데이터를 갖고 있어야 합니다.

1-enrollment.xlsx-에는 retrofit_enrollment.csv 파일에 필요한 메타 데이터에 대한 설명이 포함되어 있습니다.

2-certification_enrollment.xlsx-에는 retrofit_certification_enrollment.csv 파일에 필요한 메타 데이터에 대한 설명이 포함되어 있습니다.

3-learning_program_enrollment.xlsx-에는 retrofit_learning_program_enrollment.csv 파일에 필요한 메타 데이터에 대한 설명이 포함되어 있습니다.

4-user_course_grades.xlsx-retrofit_user_course_grades.csv 파일에 필요한 메타데이터의 설명이 포함되어 있습니다.
[csv-specifications.zip](assets/csv-specifications.zip)

>[!NOTE]
>
>UUID(Universal Unique Id)도 마이그레이션 csv의 열입니다.


## 마이그레이션 문제 해결 {#troubleshootingmigrationissues}

통합 책임자가 기존 LMS에서 Learning Manager 응용 프로그램으로 데이터와 콘텐츠를 마이그레이션하는 중 마주칠 수 있는 문제에 대한 해결 방법/솔루션에 대한 자세한 내용은 이 [문서](../../kb/troubleshooting-migration.md)를 참조하십시오.

## 사용자 관리에 대한 팁 {#usermanagement}

이 주제는 Learning Manager에서 사용자를 처리하고 관리하는 방법에 대한 이해를 돕는 팁을 확인할 수 있습니다. 이러한 개념은 Learning Manager의 CSV 가져오기, 커넥터 및 마이그레이션 기능을 사용할 때 사용자를 더 쉽게 관리하게 해줍니다.

## Learning Manager ID {#captivateprimeids}

Learning Manager는 사용자에게 두 가지 유형의 고유 ID를 제공합니다.

* 이메일 ID
* UUID(보편적 고유 ID)

Learning Manager는 조직에서 유연한 사용자 제어를 할 수 있도록 UUID를 지원합니다. 책임자가 계정에 사용자 UUID가 있는 경우, 해당 계정에 대한 사용자의 전자 메일 ID를 수정할 수 있습니다.

**조직 내 UUID 사용 시나리오**

직원 A가 Learning Manager라는 회사에 계약자로 입사하는 시나리오를 생각해 보십시오. 계약 기간 동안 Learning Manager 회사는 ```A@example.com```(으)로 회사 전자 메일 ID를 제공할 수 없으며, 대신 회사는 ```A@gmail.com```과(와) 같은 직원의 개인 전자 메일 계정만 고려할 수 있습니다. 6개월의 계약 기간을 완료한 후, 동일한 직원 A가 Learning Manager에 정규직으로 입사하면 Learning Manager는 전자 메일 ID를 회사 전자 메일 ID ```A@example.com```으로 변경해야 할 수 있습니다.

사용자 계정에 대한 UUID 액세스 권한이 있으면 위에서 언급한 시나리오에서 회사 Learning Manager에 도움이 됩니다. Learning Manager 회사는 직원 A의 개인 이메일 아이디를 공식 이메일 아이디로 쉽게 대체할 수 있습니다. 이 계정과 연관된 직원의 기록은 해당 변경 사항에 영향을 받지 않습니다.

## 단일 사용자 식별 {#singleuseridentification}

Learning Manager는 단일 사용자가 자가 등록, CSV 업로드, 사용자 인터페이스 또는 API 방식 중 어떤 방법으로 추가되었는지 식별 및 기억합니다.

* 단일 사용자가 사용자 인터페이스(UI) 또는 API로 추가된 경우, UI 또는 API를 통해 해당 유형의 단일 사용자를 삭제할 수 있습니다.
* CSV 업로드 프로세스를 통해 단일 사용자를 업데이트할 수 있습니다. 그러나, 단일 사용자는 CSV 사용자로 간주되며 해당 사용자에게는 CSV 작업 과정이 적용된다는 것을 기억하십시오.

## 관리자 역할 할당 {#assigningmanagerrole}

Learning Manager에서는 모든 사용자에게 관리자 역할을 직접 할당할 수 없습니다. 사용자 X는 해당 계정에서 어떤 사용자(예: Y)의 관리자 속성이 X로 설정된 경우에만 Learning Manager 책임자가 될 수 있습니다.

X가 사용자 A, B, C의 관리자라는 시나리오를 생각해 봅시다. X가 조직을 떠난다면 A, B, C의 관리자 속성이 새 관리자로 설정되어 있는지 확인해야 합니다. 또는 해당 사용자의 관리자 속성을 일시적으로 루트로 설정한 다음 새로운 관리자 이름을 할당할 수도 있습니다.

이 항목에 대한 자세한 내용은 다음 도움말 내용을 참조하십시오.

* [CSV 업로드 관련 자주 묻는 질문](/help/migrated/administrators/feature-summary/add-users-user-groups.md#bulk-upload-internal-users/)
* [사용자 추가 기능 도움말](/help/migrated/administrators/feature-summary/add-users-user-groups.md)
