---
title: Forms 포털을 사용하여 적응형 양식을 데이터베이스에 제출
description: 기본 메타 모델을 확장하여 조직 고유의 패턴, 유효성 검사 및 엔티티를 추가하고, Automated forms conversion 서비스(AFCS)를 실행하는 동안 구성을 적응형 양식 필드에 적용합니다.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
source-git-commit: c2392932d1e29876f7a11bd856e770b8f7ce3181
workflow-type: tm+mt
source-wordcount: '1159'
ht-degree: 1%

---


# Forms 포털을 사용하여 적응형 양식과 데이터베이스 통합 {#submit-forms-to-database-using-forms-portal}

AFCS(automated forms conversion 서비스)를 사용하면 비대화형 PDF 양식, Acro 양식 또는 XFA 기반 PDF 양식을 적응형 양식으로 변환할 수 있습니다. 변환 프로세스를 시작하는 동안 데이터 바인딩을 사용하거나 사용하지 않고 적응형 양식을 생성할 수 있습니다.

데이터 바인딩 없이 적응형 양식을 생성하도록 선택한 경우, 변환된 적응형 양식을 변환 후 양식 데이터 모델, XML 스키마 또는 JSON 스키마와 통합할 수 있습니다. 그러나 데이터 바인딩이 있는 적응형 양식을 생성하는 경우 전환 서비스는 적응형 양식을 JSON 스키마와 자동으로 연결하고 적응형 양식에서 사용할 수 있는 필드와 JSON 스키마 사이에 데이터 바인딩을 만듭니다. 그런 다음 적응형 양식을 선택한 데이터베이스와 통합하고 양식에 데이터를 입력한 다음 Forms 포털을 사용하여 데이터베이스에 제출할 수 있습니다.

다음 그림은 Forms Portal을 사용하여 변환된 적응형 양식을 데이터베이스와 통합하는 여러 단계를 설명합니다.

![데이터베이스 통합](assets/database_integration.gif)

이 문서에서는 이러한 모든 통합 단계를 성공적으로 실행하기 위한 단계별 지침을 설명합니다.

이 문서에서 설명하는 샘플은 Forms 포털 페이지를 데이터베이스와 통합하기 위한 사용자 지정된 데이터 및 메타데이터 서비스의 참조 구현입니다. 샘플 구현에 사용되는 데이터베이스는 MySQL 5.6.24입니다. 그러나 Forms 포털 페이지를 원하는 데이터베이스와 통합할 수 있습니다.

## 전제 조건 {#pre-requisites}

* AEM 6.4 또는 6.5 작성자 인스턴스 설정
* AEM 인스턴스에 대해 [최신 서비스 팩](https://helpx.adobe.com/kr/experience-manager/aem-releases-updates.html) 설치
* 최신 버전의 AEM Forms 추가 기능 패키지
* [AFCS(Automated forms conversion 서비스) 구성](configure-service.md)
* 데이터베이스를 설정합니다. 샘플 구현에 사용되는 데이터베이스는 MySQL 5.6.24입니다. 그러나 변환된 적응형 양식을 원하는 데이터베이스와 통합할 수 있습니다.

## AEM 인스턴스와 데이터베이스 간의 연결 설정 {#set-up-connection-aem-instance-database}

AEM 인스턴스와 MYSQL 데이터베이스 간의 연결 설정은 다음과 같이 구성됩니다.

* [MYSQL 커넥터 패키지 설치](#install-mysql-connector-java-file)

* [데이터베이스에 스키마 및 테이블 생성](#create-schema-and-tables-in-database)

* [연결 설정 구성](#configure-connection-between-aem-instance-and-database)

* [Forms 포털 통합을 위한 샘플 패키지 설정 및 구성](#set-up-and-configure-sample)

### mysql-connector-java-5.1.39-bin.jar 파일 설치 {#install-mysql-connector-java-file}

모든 작성자 및 게시 인스턴스에서 다음 단계를 수행하여 mysql-connector-java-5.1.39-bin.jar 파일을 설치합니다.

1. http://[server]:[port]/system/console/depfinder로 이동하여 com.mysql.jdbc 패키지를 검색합니다.
1. 내보낸 사람 열에서 패키지를 번들로 내보내는지 확인합니다. 번들로 패키지를 내보내지 않는 경우 계속 진행합니다.
1. http://[server]:[port]/system/console/bundles로 이동하고 **[!UICONTROL Install/Update]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Choose File]**&#x200B;을(를) 클릭하고 mysql-connector-java-5.1.39-bin.jar 파일을 찾아 선택합니다. **[!UICONTROL Start Bundle]** 및 **[!UICONTROL Refresh Packages]**&#x200B;개의 확인란도 선택하십시오.
1. **[!UICONTROL Install]** 또는 **[!UICONTROL Update]**&#x200B;을(를) 클릭합니다. 완료되면 서버를 다시 시작합니다.
1. (Windows 전용) 운영 체제에 대한 시스템 방화벽을 끕니다.

### 데이터베이스에 스키마 및 테이블 생성 {#create-schema-and-tables-in-database}

데이터베이스에서 스키마와 테이블을 생성하려면 다음 단계를 수행합니다.

1. 다음 SQL 문을 사용하여 데이터베이스에 스키마를 만듭니다.

   ```sql
   CREATE SCHEMA `formsportal` ;
   ```

   여기서 **formsportal**&#x200B;은(는) 스키마 이름을 나타냅니다.

1. 다음 SQL 문을 사용하여 데이터베이스 스키마에 **data** 테이블을 만듭니다.

   ```sql
    CREATE TABLE `data` (
        `owner` varchar(255) DEFAULT NULL,
        `data` longblob,
        `metadataId` varchar(45) DEFAULT NULL,
        `id` varchar(45) NOT NULL,
        PRIMARY KEY (`id`)
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. 다음 SQL 문을 사용하여 데이터베이스 스키마에 **metadata** 테이블을 만듭니다.

   ```sql
   CREATE TABLE `metadata` (
       `formPath` varchar(1000) DEFAULT NULL,
       `formType` varchar(100) DEFAULT NULL,
       `description` text,
       `formName` varchar(255) DEFAULT NULL,
       `owner` varchar(255) DEFAULT NULL,
       `enableAnonymousSave` varchar(45) DEFAULT NULL,
       `renderPath` varchar(1000) DEFAULT NULL,
       `nodeType` varchar(45) DEFAULT NULL,
       `charset` varchar(45) DEFAULT NULL,
       `userdataID` varchar(45) DEFAULT NULL,
       `status` varchar(45) DEFAULT NULL,
       `formmodel` varchar(45) DEFAULT NULL,
       `markedForDeletion` varchar(45) DEFAULT NULL,
       `showDorClass` varchar(255) DEFAULT NULL,
       `sling:resourceType` varchar(1000) DEFAULT NULL,
       `attachmentList` longtext,
       `draftID` varchar(45) DEFAULT NULL,
       `submitID` varchar(45) DEFAULT NULL,
       `id` varchar(60) NOT NULL,
       `profile` varchar(255) DEFAULT NULL,
       `submitUrl` varchar(1000) DEFAULT NULL,
       `xdpRef` varchar(1000) DEFAULT NULL,
       `agreementId` varchar(255) DEFAULT NULL,
       `nextSigners` varchar(255) DEFAULT NULL,
       `eSignStatus` varchar(45) DEFAULT NULL,
       `pendingSignID` varchar(45) DEFAULT NULL,
       `agreementDataId` varchar(255) DEFAULT NULL,
       `enablePortalSubmit` varchar(45) DEFAULT NULL,
       `submitType` varchar(45) DEFAULT NULL,
       `dataType` varchar(45) DEFAULT NULL,
       `jcr:lastModified` varchar(45) DEFAULT NULL,
       PRIMARY KEY (`id`),
       UNIQUE KEY `ID_UNIQUE` (`id`)
       ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. 다음 SQL 문을 사용하여 데이터베이스 스키마에 **additionalmetadatable** 테이블을 만듭니다.

   ```sql
   CREATE TABLE `additionalmetadatatable` (
       `value` text,
       `key` varchar(255) NOT NULL,
       `id` varchar(60) NOT NULL,
       PRIMARY KEY (`id`,`key`),
       CONSTRAINT ‘additionalmetadatatable_fk’ FOREIGN KEY (`id`) REFERENCES `metadata` (`id`) ON DELETE CASCADE
       ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

1. 다음 SQL 문을 사용하여 데이터베이스 스키마에 **commentable** 테이블을 만듭니다.

   ```sql
   CREATE TABLE `commenttable` (
       `commentId` varchar(255) DEFAULT NULL,
       `comment` text DEFAULT NULL,
       `ID` varchar(255) DEFAULT NULL,
       `commentowner` varchar(255) DEFAULT NULL,
       `time` varchar(255) DEFAULT NULL);
   ```

### AEM 인스턴스와 데이터베이스 간의 연결 구성 {#configure-connection-between-aem-instance-and-database}

AEM 인스턴스와 MYSQL 데이터베이스 간에 연결을 만들려면 다음 구성 단계를 수행하십시오.

1. *http://[host]:[port]/system/console/configMgr*&#x200B;의 AEM 웹 콘솔 구성 페이지로 이동합니다.
1. 편집 모드로 **[!UICONTROL Forms Portal Draft and Submission Configuration]**&#x200B;을(를) 열려면 클릭하세요.
1. 다음 표에 설명된 대로 등록 정보 값을 지정합니다.

   <table> 
    <tbody> 
    <tr> 
    <th><strong>속성</strong></th> 
    <th><strong>설명</strong></th>
    <th><strong>값</strong></th> 
    </tr> 
    <tr> 
    <td><p>Forms 포털 초안 데이터 서비스</p></td> 
    <td><p>초안 데이터 서비스 식별자</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms 포털 초안 메타데이터 서비스</p></td> 
    <td><p>초안 메타데이터 서비스용 식별자</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms 포털 데이터 서비스 제출</p></td> 
    <td><p>데이터 전송 서비스에 대한 식별자</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms 포털 제출 메타데이터 서비스</p></td> 
    <td><p>메타데이터 서비스 제출용 식별자</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms 포털 대기 중 서명 데이터 서비스</p></td> 
    <td><p>대기 중 서명 데이터 서비스 식별자</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms 포털 대기 중 서명 메타데이터 서비스</p></td> 
    <td><p>대기 중 서명 메타데이터 서비스 식별자</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    </tbody> 
    </table>
1. 다른 구성을 그대로 두고 **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.
1. 웹 콘솔 구성에서 **[!UICONTROL Apache Sling Connection Pooled DataSource]**&#x200B;을(를) 찾아 클릭하여 편집 모드로 엽니다. 다음 표에 설명된 대로 등록 정보 값을 지정합니다.

   <table> 
    <tbody> 
    <tr> 
    <th><strong>속성</strong></th> 
    <th><strong>값</strong></th> 
    </tr> 
    <tr> 
    <td><p>데이터 소스 이름</p></td> 
    <td><p>데이터 소스 풀에서 드라이버를 필터링하기 위한 데이터 소스 이름입니다. 샘플 구현에서는 FormsPortal을 데이터 소스 이름으로 사용합니다.</p></td>
    </tr>
    <tr> 
    <td><p>JDBC 드라이버 클래스</p></td> 
    <td><p>com.mysql.jdbc.Driver</p></td>
    </tr>
    <tr> 
    <td><p>JDBC 연결 URI</p></td> 
    <td><p>jdbc:mysql://[host]:[port]/[schema_name]</p></td>
    </tr>
    <tr> 
    <td><p>사용자 이름</p></td> 
    <td><p>데이터베이스 테이블에 대해 인증하고 작업을 수행할 사용자 이름</p></td>
    </tr>
    <tr> 
    <td><p>암호</p></td> 
    <td><p>사용자 이름과 연계된 암호</p></td>
    </tr>
    <tr> 
    <td><p>트랜잭션 격리</p></td> 
    <td><p>READ_COMMIT</p></td>
    </tr>
    <tr> 
    <td><p>최대 활성 연결</p></td> 
    <td><p>1000년</p></td>
    </tr>
    <tr> 
    <td><p>최대 유휴 연결</p></td> 
    <td><p>100</p></td>
    </tr>
    <tr> 
    <td><p>최소 유휴 연결</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>초기 크기</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>최대 대기</p></td> 
    <td><p>100000</p></td>
    </tr>
     <tr> 
    <td><p>차입 시 테스트</p></td> 
    <td><p>선택됨</p></td>
    </tr>
     <tr> 
    <td><p>유휴 상태 테스트</p></td> 
    <td><p>선택됨</p></td>
    </tr>
     <tr> 
    <td><p>유효성 검사 쿼리</p></td> 
    <td><p>값의 예로는 SELECT 1(mysql), select 1 from dual(oracle), SELECT 1(MS Sql Server)(validationQuery)이 있습니다.</p></td>
    </tr>
     <tr> 
    <td><p>유효성 검사 쿼리 시간 초과</p></td> 
    <td><p>10000</p></td>
    </tr>
    </tbody> 
    </table>

### 샘플 설정 및 구성 {#set-up-and-configure-sample}

모든 작성자 및 게시 인스턴스에서 다음 단계를 수행하여 샘플을 설치하고 구성합니다.

1. 다음 **aem-fp-db-integration-sample-pkg-6.1.2.zip** 패키지를 파일 시스템에 다운로드합니다.

[파일 가져오기](assets/aem-fp-db-integration-sample-pkg-6.1.2.zip)

1. *http://[host]:[port]/crx/packmgr/*&#x200B;의 AEM 패키지 관리자로 이동합니다.
1. **[!UICONTROL Upload Package]**&#x200B;를 클릭합니다.
1. **aem-fp-db-integration-sample-pkg-6.1.2.zip** 패키지를 찾아 선택한 다음 **[!UICONTROL OK]**&#x200B;을(를) 클릭합니다.
1. 패키지를 설치하려면 패키지 옆에 있는 **[!UICONTROL Install]**&#x200B;을(를) 클릭합니다.

## Forms 포털 통합을 위해 변환된 적응형 양식 구성 {#configure-converted-adaptive-form-for-forms-portal-integration}

Forms 포털 페이지를 사용하여 적응형 양식 제출을 활성화하려면 다음 단계를 수행하십시오.
1. [변환을 실행](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process)하여 원본 양식을 적응형 양식으로 전환합니다.
1. 편집 모드에서 적응형 양식을 엽니다.
1. 양식 컨테이너를 누르고 ![적응형 양식 구성](assets/configure-adaptive-form.png)을 선택합니다.
1. **[!UICONTROL Submission]** 섹션의 **[!UICONTROL Submit Action]** 드롭다운 목록에서 **[!UICONTROL Forms Portal Submit Action]**&#x200B;을(를) 선택합니다.
1. 설정을 저장하려면 ![템플릿 정책 저장](assets/edit_template_done.png)을 탭하세요.

## Forms 포털 페이지 만들기 및 구성 {#create-configure-forms-portal-page}

다음 단계를 수행하여 Forms 포털 페이지를 만들고 이 페이지를 사용하여 적응형 양식을 제출할 수 있도록 구성하십시오.

1. AEM 작성자 인스턴스에 로그온하고 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Sites]**&#x200B;을(를) 탭합니다.
1. 새 Forms 포털 페이지를 저장할 위치를 선택하고 **[!UICONTROL Create]** > **[!UICONTROL Page]**&#x200B;을(를) 누릅니다.
1. 페이지의 템플릿을 선택하고 **[!UICONTROL Next]**&#x200B;을(를) 탭하고 페이지의 제목을 지정한 다음 **[!UICONTROL Create]**&#x200B;을(를) 탭합니다.
1. 페이지를 구성하려면 **[!UICONTROL Edit]**&#x200B;을(를) 탭하세요.
1. 페이지 헤더에서 ![템플릿 편집](assets/edit_template_sites.png) > **[!UICONTROL Edit Template]**&#x200B;을(를) 탭하여 페이지의 템플릿을 엽니다.
1. 레이아웃 컨테이너를 탭하고 ![템플릿 정책 편집](assets/edit_template_policy.png)을 탭합니다. **[!UICONTROL Allowed Components]** 탭에서 **[!UICONTROL Document Services]** 및 **[!UICONTROL Document Services Predicates]** 옵션을 사용하도록 설정하고 ![템플릿 정책 저장](assets/edit_template_done.png)을 탭합니다.
1. 페이지에 **[!UICONTROL Search & Lister]** 구성 요소를 삽입합니다. 따라서 AEM 인스턴스에서 사용할 수 있는 모든 기존 적응형 양식이 페이지에 나열됩니다.
1. 페이지에 **[!UICONTROL Drafts & Submissions]** 구성 요소를 삽입합니다. Forms 포털 페이지에 두 개의 탭 **[!UICONTROL Draft Forms]** 및 **[!UICONTROL Submitted Forms]**&#x200B;이(가) 표시됩니다. **[!UICONTROL Draft Forms]** 탭에는 [Forms 포털 통합을 위해 변환된 적응형 양식 구성](#configure-converted-adaptive-form-for-forms-portal-integration)에 언급된 단계를 사용하여 생성된 변환된 적응형 양식도 표시됩니다

1. **[!UICONTROL Preview]**&#x200B;을(를) 탭하고 전환된 적응형 양식을 탭하고 적응형 양식 필드에 대한 값을 지정하고 제출합니다. 적응형 양식 필드에 대해 지정하는 값이 통합 데이터베이스에 제출됩니다.
