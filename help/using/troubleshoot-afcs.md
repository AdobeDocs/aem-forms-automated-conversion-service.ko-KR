---
title: AFCS(자동 양식 전환 서비스) 문제 해결
description: 일반적인 AFCS 문제 및 해결 방법
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: forms
role: Admin, Developer
level: Beginner, Intermediate
contentOwner: khsingh
exl-id: e8406ed9-37f5-4f26-be97-ad042f9ca57c
source-git-commit: c2392932d1e29876f7a11bd856e770b8f7ce3181
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 85%

---

# AFCS(자동 양식 전환 서비스) 문제 해결

이 문서에서는 일반적인 오류에 대한 기본적인 문제 해결 단계를 설명합니다.

<!--The article provides information on installation, configuration and administration issues that may arise in an Automated Forms Conversion Service production environment. -->

## 일반적인 오류 {#commonerrors}

| 오류 | 예 |
|--- |--- |
| **오류 메시지** <br> 액세스 토큰 헤더를 사용할 수 없습니다. <br><br> **원인** <br> 관리자가 여러 개의 IMS 구성을 작성했거나 IMS 구성을 Adobe Cloud의 AFCS 서비스에 연결할 수 없습니다. <br><br>**해결 방법** <br> 구성이 여러 개인 경우 모든 구성을 삭제하고 [새 구성을 생성](configure-service.md#obtainpubliccertificates)합니다. <br> 단일 구성이 있는 경우 **상태 점검** 을 사용하여 [연결 상태를 확인](configure-service.md#createintegrationoption)합니다. | ![액세스 토큰 헤더를 사용할 수 없습니다](assets/invalid-ims-configurations.png) |
| **오류 메시지** <br> 서비스에 연결할 수 없습니다.  <br><br>**이유** <br> AFCS(Automated forms conversion 서비스) 클라우드 서비스에서 서비스 URL이 잘못되었거나 서비스 URL이 언급되지 않았습니다. <br><br>**해결 방법** <br> 정답 [서비스 URL](configure-service.md#configure-the-cloud-service) AFCS(Automated forms conversion 서비스) Cloud Services. | ![서비스에 연결할 수 없습니다.](assets/wrong-service-url-configured.png) |
| **오류 메시지** <br> 이 서비스에서 양식을 전환하지 못했습니다.  <br><br>**원인** <br> 사용자 측 네트워크 연결 문제입니다. 예약된 유지 보수 또는 Adobe Cloud의 중단으로 인해 서비스가 중단되었습니다. <br><br>**해결 방법** <br> 사용자 측의 네트워크 연결 문제를 해결하고 https://status.adobe.com/에서 서비스 상태를 통해 계획된 운영 중단인지, 아니면 계획되지 않은 운영 중단인지 확인합니다. | ![서비스에 연결할 수 없습니다.](assets/conversion-failure.png) |
| **오류 메시지** <br> 페이지 수가 15페이지를 넘습니다.  <br><br>**원인** <br> 소스 양식의 길이가 15페이지를 넘습니다.  <br><br>**해결 방법** <br> 15페이지 이상의 양식인 경우 Adobe Acrobat을 사용하여 페이지를 나눕니다. 양식의 페이지 수를 15개 미만으로 줄입니다. | ![서비스에 연결할 수 없습니다.](assets/number-of-pages.png) |
| **오류 메시지** <br> 파일 수가 15개를 넘습니다.  <br><br>**원인** <br>  폴더에 15개 이상의 양식이 있습니다. <br><br>**해결 방법** <br> 폴더의 양식 수를 15개 이하로 줄입니다. 폴더의 총 페이지 수를 50개 미만으로 줄입니다. 폴더 크기를 10MB 미만으로 줄입니다. 하위 폴더에 양식을 보관하지 마십시오. 소스 양식을 8~15개 양식의 배치로 구성합니다. | ![서비스에 연결할 수 없습니다.](assets/number-of-pages.png) |
| **오류 메시지** <br> 소스 파일 형식이 지원되지 않습니다.  <br><br>**원인** <br> 소스 양식이 포함된 폴더에 지원되지 않는 파일이 있습니다. <br><br>**해결 방법** <br> 이 서비스는 .xdp 및 .pdf 파일만 지원합니다. 폴더에서 다른 확장자가 있는 파일을 제거하고 전환을 실행합니다. | ![서비스에 연결할 수 없습니다.](assets/unsupported-file-formats.png) |
| **오류 메시지** <br> 스캔한 양식이 지원되지 않습니다.  <br><br>**원인** <br> PDF 양식에는 양식의 스캔한 이미지만 포함되어 있으며 콘텐츠 구조는 포함되어 있지 않습니다. <br><br>**해결 방법** <br> 이 서비스는 스캔한 양식이나 양식의 이미지를 즉시 사용 가능한 적응형 양식으로 전환하는 것을 지원하지 않습니다. 그러나 Adobe Acrobat을 사용하면 양식의 이미지를 PDF 양식으로 전환할 수 있습니다. 그런 다음 이 서비스를 사용하여 PDF 양식을 적응형 양식으로 전환합니다. Acrobat에서 전환하려면 항상 고품질 양식 이미지를 사용하십시오. 전환 품질이 향상됩니다. | ![서비스에 연결할 수 없습니다.](assets/scanned-forms-error.png) |
| **오류 메시지**<br> 암호화된 PDF 양식은 지원되지 않습니다.  <br><br>**원인** <br> 폴더에 암호화된 PDF 양식이 포함되어 있습니다. <br><br>**해결 방법** <br> 이 서비스는 암호화된 PDF 양식을 적응형 양식으로 전환하는 것을 지원하지 않습니다. 암호화를 제거하고 암호화되지 않은 양식을 업로드하고 전환을 실행합니다. | ![서비스에 연결할 수 없습니다.](assets/secured-pdf-form.png) |
| **오류 메시지** <br> 메타 모델 JSON 스키마를 구문 분석할 수 없습니다.  <br><br>**원인** <br> 이 서비스에 제공된 JSON 스키마 형식이 제대로 지정되지 않았거나, 잘못된 문자를 포함하거나, 구성 요소를 매핑하는 데 잘못된 구문을 사용합니다.  <br><br>**해결 방법** <br> JSON 파일의 형식을 확인합니다. 모든 온라인 JSON 유효성 검사기를 사용하여 스키마의 형식 및 구조를 확인할 수 있습니다. 메타 모델 구문에 대한 자세한 내용은 [기본 메타 모델 확장](extending-the-default-meta-model.md) 문서를 참조하십시오. | ![서비스에 연결할 수 없습니다.](assets/invalid-meta-model-schema.png) |
| **오류(온-프레미스 환경만 해당)** <br> 다음 **[!UICONTROL Source Language]** 이 옵션에는 적응형 양식의 올바른 언어가 나열되지 않습니다. <br><br>**이유** <br> 적응형 양식의 jcr:language 속성이 올바르게 설정되지 않았습니다.  <br><br>**해결 방법** <br> CRX-DE Lite를 열고 로 이동합니다. `/content/forms/af/`를 열고 `jcr:content` 를 누르고 노드의 값을 올바른 언어로 설정합니다. 지원되는 언어 목록은 다음을 참조하십시오. [지원되지 않는 로케일에 대한 현지화 지원 추가](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/supporting-new-language-localization.html#add-localization-support-for-non-supported-locales). | ![서비스에 연결할 수 없습니다.](assets/aem-forms-translation-project-language-unavailable.png) |

<!--

<table>
<thead>
<tr>
<th>Error</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Error Message</strong> <p> The access token header is not available. </p><br><strong>Reason</strong> <br> An administrator has created multiple IMS configurations or IMS configuration is not able to reach AFCS service on Adobe Cloud. <br><br><strong>Resolution</strong> <br> If there are multiple configurations, delete all the configurations and <a href="configure-service.md#obtainpubliccertificates">create a new configuration</a>. <br> If there is a single configuration, use <strong> Health Check </strong> to <a href="configure-service.md#createintegrationoption">check connectivity</a>.</td>
<td><img alt="The access token header is not available" src="assets/invalid-ims-configuration.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Unable to connect to the service.  <br><br><strong>Reason</strong> <br> Incorrect service URL or no service URL is mentioned in Automated Forms Conversion Service (AFCS) cloud services. <br><br><strong>Resolution</strong> <br> Correct <a href="configure-service.md#configure-the-cloud-service">Service URL</a> in Automated Forms Conversion Service (AFCS) Cloud services.</td>
<td><img alt="Unable to connect to the service." src="assets/wrong-endpoint-configured.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The service failed to convert the form.  <br><br><strong>Reason</strong> <br> Network connectivity issues at your end, the service is down due to scheduled maintenance, or outage on Adobe Cloud. <br><br><strong>Resolution</strong> <br> Resolve network connectivity issues at your end and check the status of the service on <a href="https://status.adobe.com/">https://status.adobe.com/</a> for a planned or unplanned outage.</td>
<td><img alt="The service failed to convert the form." src="assets/service-failure.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The number of pages is more than 15.  <br><br><strong>Reason</strong> <br> The source form is more than 15 pages long.  <br><br><strong>Resolution</strong> <br> Use Adobe Acrobat to split forms with more than 15 pages. Bring the number of pages in a form to less than 15.</td>
<td><img alt="The number of pages is more than 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The number of files is more than 15.  <br><br><strong>Reason</strong> <br>  The folder contains more than 15 forms. <br><br><strong>Resolution</strong> <br> Bring the number of forms in a folder to less than or equal to 15. Bring the total number of pages in a folder less than 50. Bring the size of the folder to less than 10 MB. Do not keep forms in a sub-folder. Organize source forms into a batch of 8-15 forms.</td>
<td><img alt="The number of files is more than 15." src="assets/number-of-pages.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> The source file format is not supported.  <br><br><strong>Reason</strong> <br> The folder containing source forms have some unsupported files. <br><br><strong>Resolution</strong> <br> The service supports only .xdp and .pdf files. Remove files with any other extension from the folder and run the conversion.</td>
<td><img alt="The source file format is not supported." src="assets/unsupported-file-formats.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Scanned forms are not supported.  <br><br><strong>Reason</strong> <br> The PDF form contains only scanned images of the form and contains no content structure. <br><br><strong>Resolution</strong> <br> The service does not support converting scanned forms or an image of a form to an adaptive out-of-the-box. However, you use Adobe Acrobat to convert the image of a form to a PDF Form. Then, use the service to convert the PDF Form to an adaptive form. Always use a high-quality image of the form for conversion in Acrobat. It improves the quality of the conversion.</td>
<td><img alt="Scanned forms are not supported." src="assets/scanned-forms-error.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Encrypted PDF form is not supported.  <br><br><strong>Reason</strong> <br> The folder contains encrypted PDF forms. <br><br><strong>Resolution</strong> <br> The service does not support converting an encrypted PDF form to an adaptive form. Remove the encryption, upload the non-encrypted form, and run the conversion.</td>
<td><img alt="Encrypted PDF form is not supported." src="assets/secured-pdf-form.png" /></td>
</tr>
<tr>
<td><strong>Error Message</strong> <br> Unable to parse meta-model JSON schema.  <br><br><strong>Reason</strong> <br> The JSON schema supplied to the service is not properly formatted, contains invalid characters, or uses invalid syntax to map components.  <br><br><strong>Resolution</strong> <br> Check the formatting of the JSON file. You can use any online JSON validator to check the formatting and structure of the schema. See, <a href="extending-the-default-meta-model.md">Extend the default meta-model</a> article for information on meta-model syntax.</td>
<td><img alt="Unable to parse meta-model JSON schema" src="assets/invalid-meta-model-schema.png" /></td>
</tr>
</tbody>
</table>
-->
