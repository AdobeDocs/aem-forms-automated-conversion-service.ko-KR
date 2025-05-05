---
title: 자주 묻는 질문
description: 일반적인 쿼리 또는 자주 묻는 질문
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: introduction
role: Admin, Developer
level: Beginner, Intermediate
exl-id: 3a29f8d4-8ea0-49eb-bfe0-0eab5f0c52c7
source-git-commit: c2392932d1e29876f7a11bd856e770b8f7ce3181
workflow-type: tm+mt
source-wordcount: '1777'
ht-degree: 3%

---

# 자주 묻는 질문{#frequently-asked-questions}

1. **AFCS(Automated forms conversion 서비스)에서 지원하는 AEM Forms 버전은 무엇입니까?**
   <p>AFCS(automated forms conversion 서비스)는 AEM 6.4 Forms 및 AEM 6.5 Forms을 지원합니다. OSGi의 AEM Forms과 JEE의 AEM Forms에서 모두 작동합니다. 서비스를 사용하려면 AEM 작성자 인스턴스 위에 최신 AEM Forms 추가 기능 패키지가 필요합니다. 자세한 지침은 <a href="configure-service.md">Automated forms conversion 구성</a> 서비스를 참조하십시오.</p> 
    <br>

1. **서비스를 온-프레미스에 설치할 수 있습니까?**
   <p>Adobe은 변환 정확도를 개선하기 위해 새로운 데이터 세트를 사용하여 정기적으로 Automated forms conversion 서비스(AFCS)의 AI 및 ML 알고리즘을 교육합니다. 업데이트된 알고리즘은 주기적으로 Adobe 클라우드에서 실행되는 전환 서비스에 배포됩니다. 서비스의 모든 고객은 업데이트된 알고리즘에서 혜택을 받을 수 있습니다. 따라서 클라우드 호스팅 중앙 배포는 모든 고객에게 지속적으로 향상된 기능을 배우고 제공할 수 있는 Automated forms conversion 서비스(AFCS)에 가장 적합합니다.</p> 
    <p>이 서비스는 빈 양식을 적응형 양식으로 전환합니다. 이 서비스는 채워진 양식 및 채워진 양식에서 데이터 추출을 지원하지 않습니다. 양식에 채워진 데이터를 제거하고 양식의 독점 정보를 전환용으로 양식에서 전송하기 전에 제거하거나 허용 목록에 추가하다합니다.</p> <br>

1. **서비스가 모든 형식의 PDF forms을 지원합니까? 지원되는 모든 언어는 무엇입니까?**
   <p>이 서비스는 비대화형 PDF forms, XFA 기반 XDP와 PDF forms, AcroForms를 적응형 양식으로 전환할 수 있습니다. 이 서비스는 스캔되거나 채워진 양식을 지원하지 않습니다. 다른 제한 사항에 대해서는 <a href="known-issues.md">알려진 문제</a> 문서를 참조하십시오.<br /> </p> 
    <p>다른 소스 유형에 대한 지원을 정기적으로 추가하고 있습니다. 새로 추가된 기능에 대한 정기적인 업데이트를 위해 감시 목록에 <a href="introduction.md">supportedPDF forms</a> 섹션을 보관하십시오.</p>

   이 서비스는 영어, 프랑스어, 독일어, 스페인어, 이탈리아어 및 포르투갈어 언어 양식만 적응형 양식으로 전환할 수 있습니다. [AEM 번역 워크플로를 사용하여 생성된 적응형 양식을 다른 언어로 번역할 수 있습니다.](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)</br> </br>

1. **서비스에서 적응형 양식 대신 XDP를 생성할 수 있습니까?**
   <p>서비스가 XDP 출력을 생성하지 않습니다. 우리는 정기적으로 기능에 및 서비스를 추가하고 있습니다. 새로 추가된 기능에 대한 정기적인 업데이트를 보려면 감시 목록에 <a href="introduction.md">지원되는 언어 및 PDF forms</a> 섹션을 유지하십시오.</p> <br>

1. **생성된 스키마의 유형은 무엇입니까?**
   <p>서비스를 사용하여 다음을 생성할 수 있습니다. </p>

   * JSON 스키마에 바인딩된 적응형 양식 및
   * <br><br> 스키마에 바인딩되지 않은 적응형 양식

1. **서비스에서 Microsoft Word 양식을 적응형 양식으로 변환할 수 있습니까?**
   <p>아니요. 이 서비스는 Microsoft Word 양식을 적응형 양식으로 전환하지 않습니다. Microsoft Word 양식을 PDF 양식으로 저장하고 PDF 양식을 적응형 양식으로 변환할 수 있습니다. 전체 프로세스는 다음과 같습니다 </p> <br>

   1. Adobe Acrobat을 사용하여 [Word 문서를 비대화형 PDF으로 변환](https://helpx.adobe.com/acrobat/how-to/create-pdf-files-word-excel-website.html)할 수 있습니다.
   1. Adobe Acrobat을 사용하여 [생성된 PDF forms을 입력 가능한 PDF 양식으로 변환](https://helpx.adobe.com/acrobat/how-to/convert-word-excel-paper-pdf-forms.html)합니다.
   1. Adobe Acrobat을 사용하여 양식 필드를 수동으로 업데이트하고 수정합니다.
   1. PDF 양식을 저장합니다. 이제 전환 서비스와 함께 양식을 사용하여 적응형 양식을 생성할 수 있습니다. 이 양식을 기록 문서 템플릿으로 사용할 수도 있습니다.


1. **서비스가 스캔한 종이 양식과 컬러 양식을 적응형 양식으로 변환할 수 있습니까?**
   <p>이 서비스는 색상 PDF forms을 적응형 양식으로 전환할 수 있습니다. 이 서비스는 스캔되거나 채워진 양식을 지원하지 않습니다. 다른 제한 사항에 대해서는 <a href="known-issues.md">알려진 문제</a> 문서를 참조하십시오.</p> <br>

1. **서비스가 스캔한 양식이나 양식의 이미지만 적응형 양식으로 전환할 수 있습니까?**
   <p>이 서비스는 스캔한 양식이나 양식의 이미지를 즉시 사용 가능한 적응형 양식으로 전환하는 것을 지원하지 않습니다. 그러나 Adobe Acrobat을 사용하면 양식의 이미지를 PDF 양식으로 전환할 수 있습니다. 그런 다음 이 서비스를 사용하여 PDF 양식을 적응형 양식으로 전환합니다. Acrobat에서 전환하려면 항상 고품질 양식 이미지를 사용하십시오. 전환 품질이 향상됩니다.</p> <br>

1. **일부 XDP 기반 양식에서 양식 단편을 사용하는데 이러한 양식 단편을 업로드해야 하는 위치**
   <p class="MsoNormal">양식 조각을 전환 폴더에 업로드하고 원래 폴더 구조를 유지합니다. XDP 기반 양식 및 양식 조각에 사용된 상대 경로를 보존하는 데 도움이 됩니다.</p> <br>

1. **서비스에서 스키마 바인딩된 XDP 양식을 지원합니까? 스키마에 바인딩된 XDP가 있는 경우 스키마를 XDP에 포함시켜야 합니까?**
   <p>예. 이 서비스는 스키마 바인딩 XDP 양식을 지원하며 소스 XDP 양식에 스키마를 임베드해야 합니다. 스키마 바인딩 XDP 양식을 변환할 때 서비스는 JSON 스키마를 생성합니다. JSON 스키마는 소스 XDP 양식의 XSD 스키마와 구조적으로 유사합니다.</p> <br>

1. **서비스에서 양식을 전환하지 못했습니다. 그 이유와 해결 방법은 무엇입니까?**
전환 실패의 가장 일반적인 원인은 다음과 같습니다.</p>
   * 보안 PDF forms은 전환을 위해 제공됩니다. 암호로 보호되거나 보안된 PDF forms을 전환에 사용하지 마십시오.
   * 인터넷 연결이 중단되었습니다. 변환 중에 인터넷에 연결되어 있는지 확인합니다.
   * Source PDF에 실제 양식 대신 양식 이미지가 있습니다.
   * 서비스가 잘못 구성되었거나 서비스 URL이 제공되지 않았거나 제공된 서비스 URL이 잘못되었습니다. **[!UICONTROL AEM]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion configuration]**&#x200B;에서 [서비스 구성](configure-service.md#configure-the-cloud-service)을(를) 확인하십시오.
   * IMS 구성이 제대로 구성되지 않았습니다. IMS 구성이 제대로 작동하는지 확인하려면 상태 검사를 수행하십시오. IMS 구성이 올바른지 확인하려면:
      1. `http://[servername]:[port]/libs/cq/adobeims-configuration/content/configurations.html`(으)로 이동
      2. 구성을 선택합니다. 헤더에서 **[!UICONTROL Check Health]**&#x200B;을(를) 클릭하고 **[!UICONTROL Check]**&#x200B;을(를) 클릭합니다. 성공하면 **[!UICONTROL Token retrieved successfully!]**&#x200B;개의 메시지가 표시됩니다. <br> <br>

1. **사용자 지정 글꼴을 사용하는 것이 전환에 영향을 줍니까?**
   <p>비대화형 PDF 양식을 적응형 양식으로 변환하면 변환 품질을 개선하기 위해 PDF 양식에 글꼴이 포함됩니다. 글꼴 임베드 지원은 비대화형 PDF forms으로 제한됩니다. AcroForm 및 XFA 기반 PDF forms의 변환을 최적화하기 위해 대체 글꼴이 사용됩니다.</p> 
    <p><strong> CQ-DAM-Handler-Gibson 글꼴 관리자 서비스</strong> 구성의 <strong>Customer fonts 디렉터리</strong> 필드에 나열된 사용자 지정 글꼴 디렉터리에서 사용할 수 있는 양식만 비대화형 PDF 양식에 포함됩니다.</p> 
    <p> </p> <br>

1. **서비스가 출력 적응형 양식에서 원본 PDF의 글꼴을 식별하고 사용합니까?**
   <p>반응형 HTML 양식의 스타일 및 레이아웃은 일반적으로 PDF 또는 용지 기반 양식과 다릅니다. 조직 전체에서 일관된 레이아웃 및 스타일을 지원하기 위해 적응형 양식은 <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html">테마를 사용하여 양식 스타일을 지정</a>합니다. 변환 서비스는 변환 중에 적용된 테마에 지정된 글꼴과 글꼴 스타일을 사용합니다. 테마의 글꼴과 글꼴 스타일을 변경하여 적응형 양식의 구성 요소에 뚜렷한 모양과 느낌을 제공할 수 있습니다.</p> <br>

1. **서비스가 XDP 기반 양식에서 JavaScript을 자동으로 추출하여 해당 적응형 양식에 적용합니까?**
   <p>이 서비스는 XFA 기반 양식 또는 Acro Forms의 스크립트를 해당 적응형 양식 규칙으로 자동 전환하지 않습니다. <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html">규칙 편집기</a>를 사용하여 적응형 양식에 대화형 기능을 추가할 수 있습니다.</p> <br>

1. **일부 양식 개체가 적응형 양식 구성 요소로 올바르게 변환되지 않았습니다. 문제를 해결하는 방법**
   <p>Automated forms conversion 서비스(AFCS)는 다양한 양식 세트에서 교육됩니다. 그러나 AI/ML 기반 애플리케이션은 교육 데이터와 패턴에 따라 제한됩니다. 인간의 인식에는 식별이 가능하지만 자동화된 인식에는 어려운 필드 유형, 레이아웃, 패턴 및 컨텍스트가 여러 개 존재할 수 있다. 서비스는 이러한 객체를 식별하지 못하거나 잘못 인식할 수 있습니다. <a href="review-correct-ui-edited.md" target="_blank">검토 및 수정</a> 편집기를 사용하여 입력 양식의 친숙한 용지 양식 기반 레이아웃에서 필요한 수정 작업을 수행할 수 있습니다.</p> <br/>

1. **일부 수정 내용이 양식에서 반복됩니다. 서비스가 향후 전환에서 이러한 모든 인스턴스를 식별하고 수정할 수 있습니까?**

   이 서비스는 양식 및 패턴에 대한 지속적인 교육입니다. 그것은 매일 새로운 패턴을 배웁니다. 양식에서 반복되는 수정 사항의 자동 적용은 아직 시작하지 않았습니다. 이러한 기능을 사용할 수 있도록 프리릴리스 양식을 주시하십시오. <br/><br/>

   메타 모델을 사용하여 양식 개체를 선택한 적응형 양식 구성 요소에 매핑하고 구성 요소에 대한 유효성 검사, 규칙, 데이터 패턴, 도움말 텍스트 및 접근성 속성을 미리 구성할 수 있습니다. 지정된 모든 속성은 변환 중에 적용됩니다. 메타 모델을 사용하여 필드에 공통 속성을 적용할 수 있습니다. 여러 양식에서 반복되는 문제를 줄이는 데 도움이 됩니다.<br/><br/>

1. **PII(개인 식별 정보) 정보와 같은 중요한 데이터가 있는 양식의 옵션은 무엇입니까?**
이 서비스는 비어 있거나 채워지지 않은 양식만 지원합니다. 채워진 양식이나 PII(개인 식별 정보)가 있는 양식을 업로드하지 마십시오. 또한 소스 양식에서 미리 채워진 데이터, PII(개인 식별 정보), 기밀 및 독점 정보를 제거합니다. <br/>

1. **머리글과 바닥글을 배치할 위치**
   <p>적응형 양식 템플릿에 머리글과 바닥글을 배치합니다. 소스 PDF 양식에 머리글과 바닥글이 있으면, 서비스는 전환 중에 감지된 머리글과 바닥글을 적응형 양식 템플릿에서 사용할 수 있는 머리글과 바닥글로 감지하고 대체합니다. 적응형 양식에 추가 머리글이나 바닥글이 포함되어 있으면 <a href="review-correct-ui-edited.md">검토 및 수정</a> 편집기를 사용하여 이러한 머리글이나 바닥글을 수정하거나 제거할 수 있습니다.</p> <br />

1. **적응형 양식을 계획하고, 에셋(테마, 템플릿)을 만들고, 만들고, 게시하는 수동 프로세스와 비교하여 서비스가 절약하는 시간은 얼마나 됩니까?**
   <p>시간은 입력 양식의 크기 및 복잡성과 요청 수에 따라 다릅니다. 이 서비스는 PDF forms을 적응형 양식으로 전환하는 과정이 수작업으로 이뤄지는 것보다 훨씬 빠른 속도로 전환해 가치 창출 시간을 대폭 단축하겠다는 취지다. </p> <br />

1. **RSA 라이브러리 관련 오류가 발생하면 어떻게 해야 합니까? 오류 메시지는 아래에 언급된 메시지와 유사합니다.** <br/>
   `*ERROR* [0:0:0:0:0:0:0:1 [1565757652491] POST /content/dam/formsanddocuments/demo004.affBatchProcessor.html HTTP/1.1] org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.NoClassDefFoundError: Could not initialize class com.rsa.cryptoj.o.dl at com.rsa.jsafe.JSAFE_SecureRandom.getInstance(Unknown Source) at com.adobe.internal.pdfm.util.Util.appendRandomNumberToPrefix(Util.java: 169) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34] at com.adobe.internal.pdfm.logging.JobLog.&lt;init&gt;(JobLog.java:126) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34]` <br>
앞서 언급한 오류는 RSA/BouncyCastle 라이브러리에 대해 부팅 위임이 구성되지 않은 경우 발생합니다. 아래 단계를 수행하여 문제를 해결하십시오.
   <p> </p>

   1. AEM 인스턴스를 중지합니다. `[AEM installation directory]\crx-quickstart\conf\` 폴더로 이동합니다. 편집할 sling.properties 파일을 엽니다. `[AEM installation directory]\crx-quickstart\bin\start.bat`을(를) 사용하여 AEM 인스턴스를 시작하는 경우 `[AEM_root]\crx-quickstart\`에 있는 sling.properties를 편집하십시오.
   1. sling.properties 파일에 다음 속성을 추가하십시오.<br/> `sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*`<br />  `sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*`<br /> `sling.bootdelegation.xerces=org.apache.xerces.*`
   1. 파일을 저장하고 닫습니다. <br/>
   1. AEM 인스턴스를 시작합니다.<br/>

   <br/>

1. **적응형 양식 텍스트의 대/소문자를 자동으로 변경하는 방법**
   <p>테마 또는 스타일 편집기에서 적응형 을 사용하여 적응형 양식 필드의 대/소문자를 변경할 수 있습니다. 예를 들어 테마 편집기를 열고 모든 양식 텍스트의 Case 속성 값을 대문자, 소문자 또는 카멜 대/소문자로 설정할 수 있습니다. 테마 편집기의 CSS 오버라이드 옵션을 사용하여 다양한 유형의 스타일을 만들 수도 있습니다.</p>

1. **AFCS(Automated forms conversion 서비스)에서 Adobe Sign 텍스트 태그를 사용할 수 있습니까?**
   <p> AFCS(Automated forms conversion 서비스)를 사용하여 PDF 양식을 적응형 양식으로 전환하는 경우 PDF 양식에 Adobe Sign 텍스트 태그가 포함되어 있으면 해당 태그가 적응형 양식 필드로 전환되고 서명자 세부 정보가 자동으로 채워집니다.  이 기능은 Acro Forms에 대해서만 사용할 수 있으며 적응형 양식은 제한된 수의 Adobe Sign 필드를 지원합니다.</p>  </br>

1. **Adobe Sign 사용 PDF 양식을 만드는 방법**
   </p>Adobe Sign이 활성화된 PDF 양식을 만들려면 다음을 수행하십시오.</p>

   필드 이름에 [Adobe Sign 텍스트 태그](https://helpx.adobe.com/sign/using/text-tag.html)를 추가하거나 [Adobe Sign 양식으로 변환](https://helpx.adobe.com/sign/using/create-forms-with-acrobat.html) 옵션을 사용하십시오.
