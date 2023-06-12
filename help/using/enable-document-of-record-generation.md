---
title: 전환 중 기록 문서 생성
seo-title: Generate Document of Record during conversion
description: 변환에 사용되는 소스 양식의 유형에 따라 DoR을 생성하는 권장 경로입니다.
seo-description: Recommended paths to generate a DoR based on the type of source forms used for conversion.
page-status-flag: never-activated
uuid: 7f0f5bf3-21be-449a-b23e-5946a9fd7ed4
contentOwner: khsingh
discoiquuid: 75f6e6bc-7636-4b40-919c-8b20a6ccbb1f
exl-id: c24313cd-2b9b-4209-9505-a8e14d8dc530
source-git-commit: 298d6c0641d7b416edb5b2bcd5fec0232f01f4c7
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 2%

---

# 적응형 양식의 기록 문서 생성 활성화를 위한 권장 워크플로우 {#recommended-workflows-dor-generation}

기록 문서(DoR)를 사용하면 제공한 정보를 기록하고 적응형 양식에 제출하여 나중에 참조할 수 있습니다.
DoR은 기본 템플릿을 사용하여 레이아웃을 정의합니다. 기본 템플릿을 사용하거나 다른 템플릿을 적응형 양식과 연결하여 DoR을 생성할 수 있습니다.

![생성된 기록 문서](assets/document_of_record.gif)

DoR 생성에 대한 자세한 내용은 [적응형 양식을 위한 기록 문서 생성](https://helpx.adobe.com/experience-manager/6-5/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.html).

다음 [Automated forms conversion 서비스](/help/using/introduction.md) 다음 소스 양식을 적응형 양식으로 전환합니다.

* 비대화형 PDF forms
* 아크로 Forms
* XFA 기반 PDF forms

변환에 사용하는 소스 양식을 기반으로 다음을 사용하여 DoR을 생성할 수 있습니다.

* 기본 템플릿
* 소스 양식을 템플릿으로 연결 - 이 옵션을 선택하면 변환 서비스에서 소스 양식을 변환된 적응형 양식과 DoR 템플릿으로 자동 연결합니다.
* 다른 템플릿을 변환된 적응형 양식과 연결

다음 표에서는 사용하는 DoR 템플릿이 생성된 DoR의 레이아웃에 미치는 영향의 예를 보여 줍니다.

<table> 
 <tbody>
 <tr>
  <td><p><strong>소스 양식</strong></p></td>
  <td><p><strong>생성된 DoR</strong></p></td> 
   </tr>
  <tr>
   <td><img src="assets/source_xdp_updated.png"/></td>
   <td><p>기본 템플릿을 사용하여 DoR을 생성하는 경우:</br><img src="assets/source_form_default_updated.png"/></td>
   </tr>
   <tr>
   <td></td>
   <td><p>소스 양식을 템플릿으로 사용하여 DoR을 생성하는 경우:</br></p><img src="assets/source_form_dor_updated.png"/></td>
   </tr>
  </tbody>
</table>

표에 표시된 대로 소스 양식을 템플릿으로 사용하는 경우 DoR은 소스 양식의 레이아웃을 유지합니다.
이 문서에서는 세 가지 유형의 소스 양식을 기반으로 DoR을 생성하는 권장 경로에 대해 설명합니다.

<table> 
 <tbody> 
  <tr> 
   <th><strong>소스 양식</strong></th> 
   <th><strong>DoR 생성 방법</strong></th> 
  </tr> 
  <tr> 
   <td><p>비대화형 PDF forms</p></td> 
   <td> 
    <ul> 
     <li><a href="#generate-document-of-record-using-cloud-configuration">적응형 양식 변환 전에 DoR 생성을 활성화하여 기본 템플릿을 사용하여 DoR을 생성합니다.</a></li> 
     <li><a href="#edit-adaptive-form-properties-generate-document-of-record">적응형 양식 전환 후 적응형 양식 속성을 편집하여 기본 또는 기타 양식 템플릿을 사용한 DoR 생성 활성화</a></li> 
    </ul> </td> 
  </tr>
  <tr> 
   <td><p>Acro Forms 또는 XFA 기반 PDF forms</p></td> 
   <td> 
    <ul> 
     <li><a href="#use-input-form-as-template-to-generate-document-of-record">적응형 양식 변환 전 DoR 생성을 활성화하여 소스 양식을 템플릿으로 사용하는 DoR 생성</a></li> 
     <li><a href="#edit-adaptive-form-properties-to-generate-document-of-record">적응형 양식 전환 후 적응형 양식 속성을 편집하여 기본 템플릿, 소스 양식을 템플릿으로 또는 기타 양식 템플릿을 사용하여 DoR 생성 가능</a></li> 
    </ul> </td> 
  </tr>    
 </tbody> 
</table>

## 비대화형 PDF forms에 대한 기록 문서 생성 {#generate-document-of-record-non-interactive-pdf}

비대화형 PDF 양식을 Automated forms conversion 서비스의 소스 양식으로 사용하는 경우 다음을 수행할 수 있습니다.

* 적응형 양식 변환 전에 DoR 생성을 활성화하여 기본 템플릿을 사용하여 DoR을 생성합니다.
* 또는 적응형 양식 전환 후 적응형 양식 속성을 편집하여 기본 또는 기타 양식 템플릿을 사용한 DoR 생성 가능

### 변환 전 DoR 생성을 활성화하여 기본 템플릿을 사용하여 DoR 생성 {#generate-document-of-record-using-cloud-configuration}

1. 선택 **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > 변환에 사용되는 클라우드 구성의 속성 > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** 옵션을 선택합니다.

   ![클라우드 구성을 사용하여 기록 문서 생성](assets/generate_dor_cloud_config.gif)

1. 누르기 **[!UICONTROL Save & Close]** 설정을 저장합니다.

1. [전환 실행](/help/using/convert-existing-forms-to-adaptive-forms.md). 이 지침 중 1단계에서 편집한 클라우드 구성을 사용해야 합니다.
변환된 적응형 양식을 제출하면 기본 템플릿을 사용하여 DoR이 자동으로 생성됩니다.

### 전환 후 적응형 양식 속성을 편집하여 DoR 생성 활성화 {#edit-adaptive-form-properties-generate-document-of-record}

에서 소스 양식을 적응형 양식으로 변환하기 전에 DoR 생성을 활성화하지 않으면 변환 후에도 활성화할 수 있습니다.

1. [전환 실행](/help/using/convert-existing-forms-to-adaptive-forms.md) PDF 를 사용하여 적응형 양식을 생성할 수 있습니다.

1. 에서 적응형 양식 선택 **[!UICONTROL output]** 폴더 및 탭 **[!UICONTROL Properties]**.

1. 다음에서 **[!UICONTROL Form Model]** 탭을 확장하고 **[!UICONTROL Document of Record Template Configuration]** 섹션 및 선택 **[!UICONTROL Generate Document of Record]**.

   ![기록 문서 생성](assets/generate_dor_af_properties.png)

1. 누르기 **[!UICONTROL Save & Close]** 설정을 저장합니다.

변환된 적응형 양식을 제출하면 기본 템플릿을 사용하여 DoR이 자동으로 생성됩니다. 다른 DoR 템플릿을 변환된 적응형 양식과 연결하려면 다음을 선택할 수 있습니다. **[!UICONTROL Associate form template as the Document of Record template]** 옵션을 선택합니다.

## Acro Forms 또는 XFA 기반 PDF forms에 대한 기록 문서 생성 {#generate-document-of-record-acroform-xfaform}

Acro 양식 또는 XFA 기반 PDF 양식을 Automated forms conversion 서비스의 소스 양식으로 사용하는 경우 다음을 수행할 수 있습니다.

* 적응형 양식 변환 전에 DoR 생성을 활성화하여 소스 양식을 템플릿으로 사용하는 DoR을 생성합니다.

* 또는 적응형 양식 전환 후 적응형 양식 속성을 편집하여 기본 템플릿, 소스 양식을 템플릿으로 또는 기타 양식 템플릿을 사용하여 DoR 생성 가능

### 변환 전 DoR 생성을 활성화하여 소스 양식 템플릿을 사용하여 DoR 생성 {#use-input-form-as-template-to-generate-document-of-record}

1. 선택 **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > 변환에 사용되는 클라우드 구성의 속성 > **[!UICONTROL Advanced]** > **[!UICONTROL Generate Document of Record]** 옵션을 선택합니다.

1. 누르기 **[!UICONTROL Save & Close]** 설정을 저장합니다.

1. [전환 실행](/help/using/convert-existing-forms-to-adaptive-forms.md). 이 지침 중 1단계에서 편집한 클라우드 구성을 사용해야 합니다.
변환 서비스는 Acro 양식 또는 XFA 기반 PDF 양식을 변환된 적응형 양식에 DoR 템플릿으로 자동 연결합니다.
적응형 양식 속성을 열고 DoR 템플릿을 **[!UICONTROL Document of Record Template Configuration]** 섹션 / **[!UICONTROL Form Model]** 탭.

   ![기록 문서 생성을 위한 적응형 양식 속성 편집](assets/generate_dor_af_properties_xdp_acro.png)

   변환된 적응형 양식을 제출하면 소스 양식 템플릿을 사용하여 DoR이 자동으로 생성됩니다.

### 전환 후 적응형 양식 속성을 편집하여 DoR 생성 활성화 {#edit-adaptive-form-properties-to-generate-document-of-record}

1. [전환 실행](/help/using/convert-existing-forms-to-adaptive-forms.md) PDF 를 사용하여 적응형 양식을 생성할 수 있습니다.

1. 에서 적응형 양식 선택 **[!UICONTROL output]** 폴더 및 탭 **[!UICONTROL Properties]**.

1. 다음에서 **[!UICONTROL Form Model]** 탭을 확장하고 **[!UICONTROL Document of Record Template Configuration]** 섹션 및 선택 **[!UICONTROL Generate Document of Record]** 기본 템플릿을 사용하여 DoR 생성을 활성화합니다.
다음을 선택할 수도 있습니다. **[!UICONTROL Associate form template as the Document of Record template]** 옵션을 선택하고 템플릿을 선택하여 소스 양식 템플릿 또는 기타 양식 템플릿을 사용하여 DoR 생성을 활성화합니다.

1. 누르기 **[!UICONTROL Save & Close]** 설정을 저장합니다.
