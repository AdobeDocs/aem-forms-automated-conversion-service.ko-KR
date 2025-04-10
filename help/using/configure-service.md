---
title: AFCS(자동 양식 전환 서비스) 구성
description: AEM 인스턴스가 AFCS(자동 양식 전환 서비스)를 사용할 수 있도록 준비
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: forms
role: Admin, Developer, User
level: Beginner, Intermediate
exl-id: 8f21560f-157f-41cb-ba6f-12a4d6e18555
source-git-commit: 54cd2cf2fdc4f9b420125e4c04c87bec1b7f368d
workflow-type: tm+mt
source-wordcount: '2366'
ht-degree: 5%

---

# AFCS(자동 양식 전환 서비스) 구성 {#about-this-help}

이 문서에서는 AEM 관리자가 PDF forms을 적응형 Forms으로 자동 전환하도록 AFCS(자동 양식 전환 서비스)를 구성하는 방법에 대해 설명합니다. 이 문서는 조직의 IT 및 AEM 관리자를 위한 것입니다. 제공된 정보는 이 문서를 읽는 누구나 다음 기술에 친숙하다는 가정을 기반으로 합니다.

* Adobe Experience Manager 및 AEM 패키지 설치, 구성 및 관리

* Linux® 및 Microsoft® Windows® 운영 체제 사용

<!--- >[!VIDEO](https://video.tv.adobe.com/v/29267/) 

**Watch the video or read the article to configure Automated Forms Conversion service (AFCS)** -->

## 온보딩{#onboarding}

이 서비스는 AEM 6.5 Forms On-Premise 기간제 고객 및 Adobe Managed Service 기업 고객에게 무료로 제공됩니다. Adobe 영업팀 또는 Adobe 담당자에게 문의하여 서비스 액세스를 요청할 수 있습니다. 또한 이 서비스는 AEM Forms as a Cloud Service 고객을 위해 무료로 사전 활성화됩니다.

Adobe는 조직에 대한 액세스 권한을 활성화하고 조직의 책임자로 지정된 사람에게 필요한 권한을 제공합니다. 관리자는 서비스에 연결할 조직의 AEM Forms 개발자(사용자)에게 액세스 권한을 부여할 수 있습니다.

## 사전 요구 사항 {#prerequisites}

AFCS(자동 양식 전환 서비스)를 사용하려면 다음이 필요합니다.

* 조직에 대해 AFCS(자동 양식 전환 서비스)가 활성화되어 있습니다
* 전환 서비스에 대한 관리자 권한이 있는 Adobe ID 계정
* 최신 AEM 서비스 팩이 포함된 실행 중인 AEM 6.5 또는 최신 업데이트가 포함된 AEM Forms as a Cloud Service 작성자 인스턴스.
* Forms-user 그룹의 멤버인 AEM 사용자(AEM 인스턴스)

## 환경 설정 {#setuptheservice}

서비스를 사용하기 전에 AEM 작성자 인스턴스를 준비하여 Adobe Cloud에서 실행 중인 서비스에 연결합니다. 나열된 순서로 다음 단계를 수행하여 서비스에 대한 인스턴스를 준비합니다.

1. [AEM 6.5 또는 온보드 AEM Forms as a Cloud Service을 다운로드하여 설치합니다.](#aemquickstart)
1. [(AEM 6.5만 해당) 최신 AEM 서비스 팩 다운로드 및 설치](#servicepack)
1. [(AEM 6.5만 해당) 최신 AEM Forms 추가 기능 패키지 다운로드 및 설치](#downloadaemformsaddon)
1. [사용자 지정 테마 및 템플릿 만들기](#referencepackage)

### 1. AEM 6.5 또는 온보드 AEM Forms as a Cloud Service 다운로드 및 설치 {#aemquickstart}


AFCS(자동 양식 전환 서비스)는 AEM 작성자 인스턴스에서 실행됩니다. AEM 작성자 인스턴스를 설정하려면 AEM 6.5 또는 AEM Forms as a Cloud Service이 필요합니다.

* AEM 6.5가 설치되어 있지 않고 실행 중인 경우 아래 위치에서 다운로드하십시오. AEM을 다운로드한 후 AEM 작성자 인스턴스를 설정하는 방법은 [배포 및 유지 관리](https://helpx.adobe.com/kr/experience-manager/6-5/sites/deploying/using/deploy.html#defaultlocalinstall)를 참조하십시오.

   * 기존 AEM 고객의 경우 [Adobe 라이선스 웹 사이트](http://licensing.adobe.com)에서 AEM 6.5를 다운로드합니다.

   * Adobe 파트너인 경우 [Adobe 파트너 교육 프로그램](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q)을 사용하여 AEM 6.5를 요청합니다.

* AEM Forms as a Cloud Service을 사용하는 경우 [AEM Forms as a Cloud Service에 온보딩](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/setup-environment/setup-forms-cloud-service.html?lang=en#setup-environment) 및 [로컬 개발 환경 설정](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/setup-environment/setup-local-development-environment.html?lang=en#setup-environment)을 참조하십시오.

### 2. (AEM 6.5만 해당) AEM 최신 서비스 팩 다운로드 및 설치 {#servicepack}

최신 AEM 서비스 팩을 다운로드하여 설치합니다. 자세한 지침은 [AEM 6.5 서비스 팩 릴리스 정보](https://experienceleague.adobe.com/ko/docs/experience-manager-65/content/release-notes/release-notes)를 참조하세요.

### 3. (AEM 6.5만 해당) AEM Forms 추가 기능 패키지 다운로드 및 설치   {#downloadaemformsaddon}

AEM 인스턴스에는 기본 양식 기능이 포함되어 있습니다. 전환 서비스에는 AEM Forms의 모든 기능이 필요합니다. AEM Forms의 모든 기능을 사용하려면 AEM Forms 추가 기능 패키지를 다운로드하여 설치하십시오. 변환 서비스를 설정하고 실행하려면 패키지가 필요합니다. 자세한 지침은 [데이터 캡처 기능 설치 및 구성을 참조하십시오.](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi)
https://adminconsole.adobe.com/
>[!NOTE]
> 추가 기능 패키지를 설치한 후 필수 사후 설치 구성을 수행해야 합니다.
>

<!-- ### (Optional) Download and install connector package  {#installConnectorPackage}

The connector package provides early access to the [Auto-detect logical sections](convert-existing-forms-to-adaptive-forms.md#run-the-conversion) features and improvements delivered in release AFC-2020.03.1. Do not install the package if you do not require feature and improvements delivered in AFC-2020.03.1.  You can [download the connector package from AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1). -->


### 4. 사용자 지정 테마 및 템플릿 만들기 {#referencepackage}

참조 패키지에는 샘플 테마 및 템플릿이 들어 있습니다. AFCS(자동 양식 전환 서비스)에서 PDF 양식을 적응형 양식으로 전환하려면 적어도 하나의 테마와 하나의 템플릿이 필요합니다. 사용자 지정 테마 및 템플릿을 만들어 서비스를 사용하기 전에 사용자 지정 템플릿 및 테마를 사용하도록 [서비스 구성](#configure-the-cloud-service)을 가리킵니다.

작성자 인스턴스에 [AEM Forms 참조 Assets](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) 패키지를 다운로드하여 설치할 수도 있습니다. 몇 가지 참조 테마와 템플릿을 만듭니다.

## 액세스 및 권한 구성

서비스를 구성하고 Adobe Cloud에서 실행 중인 서비스와 인스턴스를 연결하기 전에 서비스에 연결하는 데 필요한 가상 사용자 및 권한에 대해 알아보십시오. 이 서비스는 관리자 및 개발자의 두 가지 다른 유형의 가상 사용자를 사용합니다.

* **관리자**: 관리자는 조직의 Adobe 소프트웨어 및 서비스를 관리할 책임이 있습니다. 관리자는 조직의 개발자에게 Adobe Cloud에서 실행되는 AFCS(Automated Forms Conversion Service)에 연결할 수 있는 액세스 권한을 부여합니다. 조직에 대한 관리자가 프로비저닝되면 관리자는 제목이 **[!UICONTROL 'You now have administrator rights to manage Adobe software and services for your organization']**&#x200B;인 이메일을 수신합니다. 관리자인 경우 이전에 언급된 제목이 있는 전자 메일이 있는지 사서함에서 확인하고 [조직의 개발자에게 액세스 권한 부여](#adduseranddevs)로 진행하십시오.

![관리자 액세스 권한 부여 전자 메일](assets/admin-console-adobe-io-access-grantedx75.png)

* **개발자**: 개발자는 AEM Forms 작성자 인스턴스를 Adobe Cloud에서 실행되는 AFCS(Automated Forms Conversion Service)에 연결합니다. 관리자가 개발자에게 AFCS(자동 양식 전환 서비스)에 연결할 수 있는 권한을 부여하면 조직의 Adobe API 통합을 관리할 수 있는 개발자 액세스 권한이 있다는 제목의 이메일이 개발자에게 전송됩니다. 개발자인 경우 이전에 언급된 제목이 있는 전자 메일을 사서함에서 확인하고 [로컬 AEM 인스턴스를 Adobe Cloud의 자동 양식 전환 서비스에 연결합니다.](#connectafcadobeio)

![개발자 액세스 권한 부여 전자 메일](assets/email-developer-accessx94.png)

### 조직의 개발자에게 액세스 권한 부여

Adobe이 조직에 대한 액세스를 활성화하고 관리자에게 필요한 권한을 제공하면 관리자가 Admin Console(아래 세부 지침)에 로그인하여 프로필을 만들고 개발자를 프로필에 추가할 수 있습니다. 개발자는 AEM Forms 인스턴스를 Adobe Cloud의 AFCS(Automated Forms Conversion Service)에 연결할 수 있습니다.

개발자는 전환 서비스를 실행하도록 지정된 조직의 멤버입니다. Adobe AFCS(자동 양식 전환 서비스) 프로필에 추가된 개발자만 AFCS(자동 양식 전환 서비스)를 사용할 수 있습니다.
프로필을 만들고 개발자를 추가하려면 아래 단계를 수행하십시오. 조직의 개발자에게 필요한 액세스 권한을 부여하려면 최소 하나의 프로필이 필요합니다.

1. [Admin Console](https://adminconsole.adobe.com/)에 로그인합니다. AFCS(자동 양식 전환 서비스)를 사용하여 로그인하도록 제공된 관리자의 **Adobe ID**&#x200B;을(를) 사용합니다.
1. **[!UICONTROL Automated Forms Conversion]** 옵션을 클릭합니다.
1. **[!UICONTROL Products]** 탭에서 **[!UICONTROL New Profile]**&#x200B;을(를) 클릭합니다.
1. 프로필에 대해 **[!UICONTROL Name]**, **[!UICONTROL Display Name]** 및 **[!UICONTROL Description]**&#x200B;을(를) 지정하십시오. **[!UICONTROL Done]**&#x200B;를 클릭합니다. 예를 들어 프로필을 **AFC_Flamingo_Test_Dev**(으)로 만듭니다.

   ![새 프로필에 대한 세부 정보를 지정하십시오.](assets/create-new-profile-details.png)

1. 프로필에 개발자를 추가합니다. 개발자를 추가하려면:
   1. [Admin Console](https://adminconsole.adobe.com/enterprise)에서 개요 탭으로 이동합니다.
   1. 필요한 제품 카드에서 **[!UICONTROL Assign Developers]**&#x200B;을(를) 클릭합니다.
   1. 개발자 이메일 주소와 이름 및 성을 입력합니다(선택 사항).
   1. 제품 프로필을 선택합니다. **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다.

모든 사용자에 대해 위의 단계를 반복합니다. 개발자 추가에 대한 자세한 내용은 [개발자 관리](https://helpx.adobe.com/enterprise/using/manage-developers.html)를 참조하십시오.

관리자가 Adobe I/O 프로필에 개발자를 추가하면 개발자에게 이메일로 알립니다(구성된 경우).

<!--
### Configure email notification for local AEM Forms instance

Automated Forms Conversion service (AFCS) uses the Day CQ mail service to send email notifications. These email notifications contain information about successful or failed conversions. If you choose not receive notification, skip these steps. Perform the following steps to configure the Day CQ Mail Service:

* **For AEM 6.5 Forms**:

   1. Go to AEM configuration manager at `http://[server]:[port]/system/console/configMgr`
   2. Open the Day CQ Mail Service configuration. Specify a value for the **[!UICONTROL SMTP server host name]**, **[!UICONTROL SMTP server port]**, and **[!UICONTROL From address]** fields. Click **[!UICONTROL Save]**.

      You can contact your email service provider or IT administrator for information about host name and port of SMTP server. You can use any valid email address in the from field. For example, notification@example.com or donotreply@example.com.

   3. Open the **[!UICONTROL Day CQ Link Externalizer]** configuration. In the **[!UICONTROL Domains]** field, specify the actual host name or IP address and port number for local, author, and publish instances. Click **[!UICONTROL Save]**.

* For AEM Forms as a Cloud Service, [log a support ticket to enable the email service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#sending-email). -->

### forms-users 그룹에 사용자 추가 {#adduserstousergroup}

서비스를 실행하도록 지정된 AEM 사용자의 프로필에 이메일 주소를 지정합니다. 사용자가 **forms-users** 그룹의 구성원인지 확인하십시오. 전환을 실행하는 사용자의 이메일 주소로 이메일이 전송됩니다. 사용자의 이메일 주소를 지정하고 사용자를 양식 사용자 그룹에 추가하려면 다음을 수행합니다.

1. AEM Forms 작성자 인스턴스에 AEM 관리자로 로그인합니다. 로컬 AEM 자격 증명을 사용하여 로그인합니다.
1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**&#x200B;을(를) 클릭합니다.
1. 전환 서비스를 실행하도록 지정된 사용자를 선택하고 **[!UICONTROL Properties]**&#x200B;을(를) 클릭합니다. **사용자 설정 편집** 페이지가 열립니다.
1. **[!UICONTROL Email]** 필드에 전자 메일 주소를 지정하고 **[!UICONTROL Save]**&#x200B;을(를) 클릭합니다. 전환이 완료되거나 실패하는 경우 이메일이 지정된 이메일 주소로 전송됩니다.

   ![전자 메일 지정](/help/using/assets/specify-email.png)
1. **그룹** 탭을 클릭합니다. 그룹 선택 탭에서 **forms-users** 그룹을 입력하고 선택합니다.
1. **저장 및 닫기**&#x200B;를 클릭합니다. 이제 사용자는 forms-users 그룹의 멤버입니다.

   ![사용자 그룹 추가](/help/using/assets/add-user-group.png)

## AEM Forms 인스턴스를 Adobe Cloud의 AFCS(Automated Forms Conversion Service)에 연결합니다

관리자가 개발자 액세스 권한을 부여하면 AEM Forms 인스턴스를 Adobe Cloud에서 실행되는 AFCS(Automated Forms Conversion Service)에 연결할 수 있습니다.
AEM Forms 인스턴스를 자동 양식 전환 서비스에 연결하려면 다음 단계를 수행하십시오.

[1. Adobe Developer Console에서 서비스 API 구성](#configure-the-service-apis-on-adobe-developer-console)

[2. Adobe IMS 구성 만들기](#2-create-adobe-ims-configurations)

[3. 자동 양식 전환 구성 만들기](#3-create-automated-forms-conversion-configuration)

### 1. Adobe Developer Console에서 서비스 API 구성

AFCS(자동 양식 전환 서비스)를 사용하려면 프로젝트를 만들고 **자동화된 Forms 구성 서비스** API를 Adobe Developer Console의 프로젝트에 추가하십시오. 통합은 API 키, 클라이언트 암호, 기술 계정 ID, 범위 및 조직 ID를 생성합니다.
Adobe Developer Console에서 자동 양식 전환 서비스 API를 구성하려면 다음 단계를 수행하십시오.

1. https://developer.adobe.com/console에 로그인합니다. 관리자가 Adobe I/O 콘솔에 로그인할 수 있도록 프로비저닝한 Adobe ID 개발자 계정을 사용하여 로그인합니다.
1. 오른쪽 상단에서 조직을 선택합니다. 조직을 모르는 경우에는 관리자에게 문의하십시오.
1. **[!UICONTROL Create new project]**&#x200B;를 클릭합니다. 새 프로젝트를 시작하는 화면이 나타납니다.

   ![새 API 프로젝트 만들기](/help/using/assets/create-new-api-project.png)

1. **[!UICONTROL Add API]**를 클릭합니다. 계정에 대해 활성화된 모든 API 목록이 포함된 화면이 나타납니다.
   ![API 추가](/help/using/assets/add-api.png)

1. **[!UICONTROL Automated Forms Conversion service]**&#x200B;을(를) 선택하고 **[!UICONTROL Next]**을(를) 클릭합니다. API 구성 화면이 나타납니다.
   ![AFCS API 선택](/help/using/assets/select-afcs-api.png)

1. **OAuth 서버 간** 인증 방법을 선택하십시오.
1. **[!UICONTROL Credential Name]**&#x200B;을(를) 지정하고 **[!UICONTROL Next]**을(를) 클릭합니다.
   ![자격 증명 이름 지정](/help/using/assets/specify-credential-name.png)
1. **제품 프로필**&#x200B;을 선택하세요. 예를 들어 프로필을 **AFC_Flamingo_Test_Dev**(으)로 선택합니다.
1. **[!UICONTROL Save configured API]**를 클릭합니다.
   ![프로필 선택](/help/using/assets/select-profile.png)

   >[!NOTE]
   >
   > 조직의 개발자에게 액세스 권한을 부여하는 동안 생성된 프로필을 선택합니다. 선택할 프로필을 모르는 경우 관리자에게 문의하십시오.

1. AEM 인스턴스를 AFCS(자동 양식 전환 서비스)에 연결하는 데 필요한 API 키, 클라이언트 암호 및 기타 정보를 보려면 **[!UICONTROL OAuth Server-to-Server]**을(를) 클릭하십시오.
   ![Oath 자격 증명 선택](/help/using/assets/select-oauth-credential.png)

   [AEM 작성자 인스턴스에서 IMS 기술 구성 만들기](#2-create-ims-technical-configuration-on-aem-author-instance) 섹션에 설명된 대로 페이지의 정보를 사용하여 IMS 구성을 만듭니다.

   ![OAuth 자격 증명 세부 정보](/help/using/assets/oauth-credentials-details.png)

### 2. Adobe IMS 구성 만들기

작성자 인스턴스에 로그인하여 Adobe IMS 구성을 만듭니다. **OAuth 자격 증명 세부 정보**&#x200B;를 사용하여 API 키, 클라이언트 암호, 기술 계정 ID, 범위 및 조직 ID를 검색하십시오.

1. AEM Forms 작성자 인스턴스에 로그인합니다. **[!UICONTROL Tools]**> **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**(으)로 이동합니다.
1. **[!UICONTROL Create]**&#x200B;를 클릭합니다.

   ![IMS Adobe 구성 만들기](/help/using/assets/create-ims-conf.png)

1. **[!UICONTROL Adobe IMS Technical Account Configuration]** 페이지가 나타납니다.

   ![Adobe IMS 기술 계정 구성 페이지](assets/adobe-ims-technical-account-configuration.png)
1. **클라우드 솔루션**&#x200B;에서 **[!UICONTROL Automated Forms Conversion Service]**&#x200B;을(를) 선택하십시오.
1. 다음을 지정하십시오.

   * **제목**: 제목을 지정합니다.
   * **인증 서버**: [https://ims-na1.adobelogin.com](https://ims-na1.adobelogin.com)
   * [Adobe Developer Console에서 서비스 API 구성](#1-configure-the-service-apis-on-adobe-developer-console) 섹션에서 다음을 검색하십시오.
      * **클라이언트 ID**: **API 키(클라이언트 ID)**&#x200B;를 복사하여 붙여 넣습니다.
      * **클라이언트 암호**: **클라이언트 암호**&#x200B;을(를) 복사하여 붙여 넣습니다.
      * **범위**: **범위**&#x200B;를 복사하여 붙여 넣습니다.
      * **조직 ID**: **기술 계정 ID**&#x200B;를 복사하여 붙여 넣습니다.

     ![IMS Adobe 구성 만들기](/help/using/assets/save-ims-configuration.png)

1. **[!UICONTROL Save]**&#x200B;를 클릭합니다. Adobe IMS 구성이 만들어집니다.

   >[!CAUTION]
   >
   > IMS 구성을 하나만 만듭니다. IMS 구성을 두 개 이상 만들지 마십시오.

1. **Adobe IMS 구성**&#x200B;을(를) 선택하고 **[!UICONTROL Check Health]**을(를) 클릭합니다. 대화 상자가 나타납니다.
   ![상태 확인](/help/using/assets/check-health.png)

   **확인** 대화 상자가 나타납니다.

1. **[!UICONTROL Check]**&#x200B;를 클릭합니다.

   ![상태 확인](/help/using/assets/check-dialog.png)

   연결에 성공하면 *토큰이 검색되었습니다*&#x200B;라는 메시지가 나타납니다.

   ![연결이 성공하면 토큰이 검색되었습니다. 메시지가 나타납니다. ](/help/using/assets/healthy-dialog.png)

1. **닫기**&#x200B;를 클릭합니다.

### 3. 자동 양식 전환 구성 만들기

AEM 인스턴스를 전환 서비스에 연결하려면 자동 양식 전환 구성을 만드십시오. 또한 전환을 위한 템플릿, 테마 및 양식 조각을 지정할 수 있습니다. 각 양식 세트에 대해 별도로 여러 클라우드 서비스 구성을 만들 수 있습니다.
예를 들어 판매 부서 양식에 대해 별도의 구성을 가지고 고객 지원 양식에 대해 별도의 구성을 가질 수 있습니다. 클라우드 서비스 구성을 만들려면 다음 단계를 수행하십시오.

1. AEM Forms 인스턴스에서 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]**> **[!UICONTROL Cloud Services]** > **[!UICONTROL Automate Forms Conversion Configuration]**&#x200B;을(를) 클릭합니다.
1. **[!UICONTROL Global]** 폴더를 선택하고 **[!UICONTROL Create]**을(를) 클릭합니다.
**자동 양식 전환 구성 만들기** 페이지가 나타납니다. 구성이 **전역** 폴더에 만들어집니다. 존재하는 다른 폴더에 구성을 만들거나 구성에 대한 폴더를 만들 수도 있습니다.
   ![전역 폴더 선택](/help/using/assets/create-afcs-cloud-conf.png)
1. **[!UICONTROL Create Automated Forms Conversion Configuration]** 페이지에서 다음 필드에 대한 값을 지정하고 **[!UICONTROL Next]**&#x200B;을(를) 클릭합니다.

   ![AFCS 구성](/help/using/assets/create-afcs-config.png)

   | 필드 | 설명 |
   |--- |--- |
   | 제목 | 구성에 대한 고유 제목입니다. 제목을 전환을 시작하는 데 사용되는 UI에 표시합니다. |
   | 이름 | 구성의 고유 이름입니다. 구성은 지정된 이름으로 CRX-저장소에 저장됩니다. 이름은 제목과 동일할 수 있습니다. |
   | 썸네일 위치 | 구성에 대한 썸네일 위치입니다. |
   | 서비스 URL | Adobe Cloud에서 AFCS(Automated Forms Conversion Service)의 URL. `https://aemformsconversion.adobe.io/` URL을 사용합니다. |
   | 템플릿 | 변환된 양식에 적용할 기본 템플릿입니다. 전환을 시작하기 전에 언제든지 다른 템플릿을 지정할 수 있습니다. 템플릿에는 적응형 양식에 대한 기본 구조와 초기 콘텐츠가 포함되어 있습니다. 기본 제공되는 템플릿 중에서 템플릿을 선택할 수 있습니다. 사용자 지정 템플릿을 만들 수도 있습니다. |
   | 테마 | 변환된 양식에 적용할 기본 테마입니다. 전환을 시작하기 전에 언제든지 다른 테마를 지정할 수 있습니다.  아이콘을 클릭하여 즉시 제공된 테마를 선택할 수 있습니다. 사용자 지정 테마를 만들 수도 있습니다. |
   | 기존 조각 | 기존 조각의 위치(있는 경우). |
   | 맞춤형 메타 모델 | 사용자 지정 메타 모델의 .schema.json 파일 경로. 영어, 프랑스어, 독일어, 스페인어, 이탈리아어 및 포르투갈어에 대해 별도의 메타 모델을 만들 수 있습니다. |

1. **[!UICONTROL Create Automated Forms Conversion Configuration]** 페이지의 **[!UICONTROL Advanced]** 탭에서 다음 필드에 대한 값을 지정하십시오.
   ![AFCS 구성](/help/using/assets/afcs-config.png)

   <table>
   <thead>
   <tr>
   <th>필드</th>
   <th>설명</th>
   </tr>
   </thead>
   <tbody>
   <tr>
   <td >기록 문서 생성</td>
   <td>변환된 양식에 대해 기록 문서를 자동으로 생성하려면 옵션을 선택합니다. 옵션은 XFA 기반 양식(XDP 및 PDF forms)에만 해당됩니다. 옵션을 활성화하면 양식을 제출한 후 고객이 나중에 참조할 수 있도록 양식에 입력한 정보를 인쇄 또는 문서 형식으로 기록할 수 있습니다. 이를 기록 문서라고 합니다.</td>
   </tr>
   <tr>
   <td>Analytics 활성화</td>
   <td>(AEM 6.5의 경우) 변환된 모든 양식에서 Adobe Analytics을 활성화하려면 옵션을 선택합니다. 옵션을 사용하기 전에 AEM Forms 인스턴스에 대해 Adobe Analytics이 활성화되어 있는지 확인하십시오.</td>
   </tr>
   </tbody>
   </table>

   * 소스가 확장자가 .XDP인 XFA 기반 양식인 경우 출력 DOR은 XFA 레이아웃을 유지하며, 그렇지 않은 경우 전환 서비스는 기본 제공 템플릿을 사용하여 다른 XFA 기반 양식에 대한 DOR을 생성합니다.
   * XFA 양식을 제출하면 양식의 제출 데이터가 XML 요소 또는 속성으로 저장됩니다. 예, `<Amount currency="USD"> 10.00 </Amount>`. 통화는 속성으로 저장되고 통화 금액, 10.00은 요소로 저장됩니다. 적응형 양식의 데이터 제출에는 속성이 없으며 요소만 있습니다. 따라서 XFA 기반 양식이 적응형 양식으로 변환되면 적응형 양식 제출 데이터는 이러한 각 속성에 대한 요소를 포함합니다. 예:

   ```css
      {
         "Type": "Principal",
   
         "Amount": "10.00",
   
         "currency": "USD"
      }
   ```

1. **[!UICONTROL Create]**&#x200B;를 클릭합니다. 클라우드 구성이 만들어집니다. AEM Forms 인스턴스가 레거시 양식을 적응형 Forms으로 전환할 준비가 되었습니다.
