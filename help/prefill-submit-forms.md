---
title: 적응형 양식을 위한 권장 데이터 소스 기반 미리 채우기 및 제출 워크플로우
seo-title: 적응형 양식을 위한 미리 채우기 및 제출 옵션
description: automated forms conversion 서비스를 사용하여 생성된 적응형 양식을 위한 데이터 소스 기반 미리 채우기 및 제출 워크플로우입니다.
seo-description: automated forms conversion 서비스를 사용하여 생성된 적응형 양식을 위한 데이터 소스 기반 미리 채우기 및 제출 워크플로우입니다.
uuid: 91409a82-141c-4233-82b1-1539a0b250f8
contentOwner: khsingh
topic-tags: forms
discoiquuid: cad34fff-7f9f-4a27-8b5c-d0a523903eec
privatebeta: true
exl-id: 5deef8f5-5098-47c1-b696-b2db59e92931
source-git-commit: 1a3f79925f25dcc7dbe007f6e634f6e3a742bf72
workflow-type: tm+mt
source-wordcount: '2459'
ht-degree: 2%

---

# 적응형 양식을 위한 권장 데이터 소스 기반 미리 채우기 및 제출 워크플로우 {#recommended-data-source-btased-prefill-and-submit-workflows-for-adaptive-forms}

automated forms conversion 서비스를 사용하여 변환된 적응형 양식에 다음 데이터 소스를 사용할 수 있습니다.

* 양식 데이터 모델, OData 또는 기타 타사 서비스
* JSON 스키마
* XSD 스키마

데이터 소스를 기반으로 데이터 모델을 사용하거나 사용하지 않고 적응형 양식을 생성하도록 선택할 수 있습니다.

이 문서에서는 데이터 소스를 선택하고 전환 서비스를 사용하여 적응형 양식을 생성한 후 필드 값 및 제출 옵션을 미리 채우는 권장 워크플로우에 대해 설명합니다.

<table> 
 <tbody> 
  <tr> 
   <th><strong>데이터 소스</strong></th> 
   <th><strong>권장 워크플로우</strong></th> 
  </tr> 
  <tr> 
   <td><p>양식 데이터 모델, OData 또는 기타 타사 서비스</p></td> 
   <td> 
    <p><strong>옵션 1</strong>:양식 데이터 모델, OData 또는 기타 타사 서비스를 데이터 소스로 선택합니다. <a href="#generate-adaptive-forms-with-no-data-binding">Automated forms conversion 서비스를 사용하여 데이터 바인딩 없이 적응형 양식을 생성합니다</a>. 적응형 양식 필드를 데이터 모델 엔티티에 수동으로 바인딩하고 양식 데이터 모델 미리 채우기 서비스 옵션을 사용하여 필드 값을 미리 채웁니다. 양식 데이터 모델을 사용하여 제출 옵션을 사용하여 적응형 양식을 제출합니다.</p></td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
   <p><strong>옵션 2</strong>:양식 데이터 모델, OData 또는 기타 타사 서비스를 데이터 소스로 선택합니다. <a href="#generate-adaptive-forms-with-no-data-binding">Automated forms conversion 서비스를 사용하여 데이터 바인딩 없이 적응형 양식을 생성합니다</a>. 규칙 편집기를 사용하여 적응형 양식 필드를 바인딩하여 필드 값을 미리 채웁니다. 필요한 경우 필드 값을 수정하고 crx-repository에 데이터를 제출합니다.</p>
    </td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
    <p>이러한 워크플로우를 실행하는 단계별 지침은 <a href="#sqldatasource">데이터베이스, OData 또는 데이터 소스로 타사 서비스를 사용합니다.</a></p> </td> 
  </tr>
  <tr>
  <td><p>JSON 스키마</p></td> 
   <td> 
    <p>JSON 스키마를 데이터 소스로 선택합니다. 선택한 데이터 소스에 따라</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>옵션 1</strong>:데이터  <a href="#generate-adaptive-forms-with-no-data-binding">바인딩 없이 적응형 양식을 </a> 생성하고 Automated forms conversion 서비스를 사용하여 JSON 스키마를 데이터 소스로 구성합니다. 적응형 양식 필드를 JSON 스키마에 수동으로 바인딩하고 지원되는 프로토콜</a> 중 하나를 사용하여 필드 값을 미리 채웁니다. <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank"> 필요한 경우 필드 값을 수정하고 crx-repository에 데이터를 제출합니다.</a></p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>워크플로우를 실행하는 단계별 지침은 <a href="#jsondatasource">데이터 소스로 JSON 스키마 사용 을 참조하십시오.</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>옵션 2</strong>:automated forms conversion  <a href="#generate-adaptive-forms-with-json-binding">서비스를 사용하여 JSON 데이터 바인딩이 있는 </a> 적응형 양식을 생성합니다. 미리 채우기 서비스 및 양식 제출은 원활하게 작동합니다. 구성 단계는 필요하지 않습니다.</p> </td> 
  </tr>
   <tr>
  <td></td> 
   <td> 
    <p>워크플로우를 실행하는 단계별 지침은 <a href="#jsonwithdatabinding">데이터 소스로 JSON 스키마 사용</a> 을 참조하십시오.</p> </td> 
  </tr>
  <tr>
  <td><p>XSD 스키마</p></td> 
   <td> 
    <p>XSD 스키마를 데이터 소스로 선택합니다. 선택한 데이터 소스를 기반으로 Automated forms conversion 서비스를 사용하여 <a href="#generate-adaptive-forms-with-no-data-binding">데이터 바인딩 없이 적응형 양식을 생성하고 XSD 스키마를 데이터 소스로 구성합니다. </a> 적응형 양식 필드를 XSD 스키마에 수동으로 바인딩하고 지원되는 프로토콜</a>을 사용하여 필드 값을 미리 채웁니다. <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank"> 필요한 경우 필드 값을 수정하고 crx-repository에 데이터를 제출합니다.</a></p>
    </td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>워크플로우를 실행하는 단계별 지침은 <a href="#xsddatasource">XSD 스키마를 데이터 소스로 사용</a>을 참조하십시오.</p>
    </td> 
  </tr>
 </tbody> 
</table>


automated forms conversion 서비스에 대한 자세한 내용은 다음 문서를 참조하십시오.

* [자동 양식 전환 서비스 소개](introduction.md)
* [자동 양식 전환 서비스 구성](configure-service.md)
* [인쇄 양식을 적응형 양식으로 전환](convert-existing-forms-to-adaptive-forms.md)
* [전환된 양식 검토 및 수정](review-correct-ui-edited.md)

이 문서에서 제공하는 정보는 읽는 사람이 적응형 양식 개념에 대한 기본 지식을 가지고 있다는 가정을 기반으로 합니다.

## 전제 조건 {#pre-requisites}

* [AEM 작성자 인스턴스 구성](https://helpx.adobe.com/kr/experience-manager/6-5/sites/deploying/using/deploy.html)
* AEM 작성자 인스턴스에서 [Automated forms conversion 서비스를 구성](configure-service.md)

## 샘플 적응형 양식 {#sample-adaptive-form}

사용 사례를 실행하여 적응형 양식의 필드 값을 미리 채우고 데이터 소스에 제출하려면 다음 샘플 PDF 파일을 다운로드하십시오.

샘플 대출 신청 양식

[파일 가져오기](assets/sample_loan_application_form.pdf)

PDF 파일은 Automated forms conversion 서비스에 대한 입력으로 사용됩니다. 이 서비스는 이 파일을 적응형 양식으로 변환합니다. 다음 이미지는 PDF 형식의 샘플 대출 애플리케이션을 나타냅니다.

![샘플 대출 신청 양식](assets/sample_form_new.png)

## 양식 모델 {#prepare-data-for-form-model} 데이터 준비

AEM Forms 데이터 통합을 사용하면 서로 다른 데이터 소스를 구성하고 연결할 수 있습니다. 변환 프로세스를 사용하여 적응형 양식을 생성한 후에는 양식 데이터 모델, XSD 또는 JSON 스키마를 기반으로 양식 모델을 정의할 수 있습니다. 데이터베이스, Microsoft Dynamics 또는 다른 타사 서비스를 사용하여 양식 데이터 모델을 만들 수 있습니다.

이 자습서에서는 MySQL 데이터베이스를 소스로 사용하여 양식 데이터 모델을 만듭니다. 데이터베이스에서 **응용 프로그램** 스키마를 만들고 적응형 양식의 필드를 기반으로 하여 **신청인** 테이블을 스키마에 추가합니다.

![샘플 데이터 mysql](assets/sample_data_mysql.png)

다음 DDL 문을 사용하여 데이터베이스에서 **신청인** 테이블을 생성할 수 있습니다.

```sql
CREATE TABLE `applicant` (
   `name` varchar(45) DEFAULT NULL,
   `address` varchar(45) DEFAULT NULL,
   `phonenumber` int(11) NOT NULL,
   `email` varchar(45) DEFAULT NULL,
   `occupation` varchar(45) DEFAULT NULL,
   `annualsalary` varchar(45) DEFAULT NULL,
   `familymembers` int(11) DEFAULT NULL,
   PRIMARY KEY (`phonenumber`)
 ) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

XSD 스키마를 양식 모델로 사용하여 사용 사례를 실행하는 경우 다음 텍스트가 포함된 XSD 파일을 만드십시오.

```xml
<?xml version="1.0" encoding="utf-8" ?>
    <xs:schema targetNamespace="http://adobe.com/sample.xsd"
                    xmlns="http://adobe.com/sample.xsd"
                    xmlns:xs="http://www.w3.org/2001/XMLSchema">

<xs:element name="sample" type="SampleType"/>

  <xs:complexType name="SampleType">
    <xs:sequence>
      <xs:element name="name" type="xs:string"/>
   <xs:element name="address" type="xs:string"/>
   <xs:element name="phonenumber" type="xs:int"/>
   <xs:element name="email" type="xs:string"/>
   <xs:element name="occupation" type="xs:string"/>
   <xs:element name="annualsalary" type="xs:string"/>
   <xs:element name="familymembers" type="xs:string"/>
 </xs:sequence>
  </xs:complexType>

  </xs:schema>
```

또는 XSD 스키마를 로컬 파일 시스템으로 다운로드합니다.

샘플 대출 응용 프로그램 XSD 스키마

[파일 가져오기](assets/loanapplication.xsd)

적응형 양식의 양식 모델로 XSD 스키마를 사용하는 방법에 대한 자세한 내용은 [XML 스키마를 사용하여 적응형 양식 만들기](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-xml-schema-form-model.html)를 참조하십시오.

사용 사례를 실행하는 양식 모델로 JSON 스키마를 사용하는 경우, 다음 텍스트가 있는 JSON 파일을 만드십시오.

```JSON
{
    "$schema": "http://json-schema.org/draft-04/schema#",
    "definitions": {
        "loanapplication": {
            "type": "object",
            "properties": {
                "name": {
                    "type": "string"
                },
                "address": {
                    "type": "string"
                },
    "phonenumber": {
                    "type": "number"
                },
    "email": {
                    "type": "string"
                },
    "occupation": {
                    "type": "string"
                },
    "annualsalary": {
                    "type": "string"
                },
    "familymembers": {
                    "type": "number"
                }
            }
        }
 },
 "type": "object",
    "properties": {
        "employee": {
            "$ref": "#/definitions/loanapplication"
        }
    }
}
```

또는 로컬 파일 시스템에 JSON 스키마를 다운로드합니다.

샘플 대출 애플리케이션 JSON 스키마

[파일 가져오기](assets/demo_schema.json)

적응형 양식의 양식 모델로 JSON 스키마를 사용하는 방법에 대한 자세한 내용은 [JSON 스키마를 사용하여 적응형 양식 만들기](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html)를 참조하십시오.

## 데이터 바인딩 없이 적응형 양식 생성 {#generate-adaptive-forms-with-no-data-binding}

[Automated forms conversion 서비스를 사용하여 ](convert-existing-forms-to-adaptive-forms.md)샘플 대출 응용 프로그램 양식](#sample-adaptive-form)을 데이터 바인딩이 없는 적응형 양식으로 변환합니다. [ 데이터 바인딩이 없는 적응형 양식을 생성하려면 **[!UICONTROL Generate adaptive form(s) without data bindings]** 확인란을 선택하십시오.

![데이터 바인딩이 없는 적응형 양식](assets/generate_af_without_binding.png)

데이터 바인딩이 없는 적응형 양식을 생성한 후 적응형 양식의 데이터 소스를 선택합니다.

* [데이터베이스, OData 또는 타사 서비스](#sqldatasource)
* [JSON 스키마](#jsondatasource)
* [XSD 스키마](#xsddatasource)

>[!NOTE]
> automated forms conversion 서비스를 사용하여 변환하는 적응형 양식에 동일한 이름의 필드가 여러 개 있는 경우 해당 필드가 데이터 소스 엔티티에 연결되어 제출 시 데이터 손실이 발생할 수 있는지 확인하십시오.


### 데이터베이스, OData 또는 타사 서비스를 데이터 소스로 사용 {#sqldatasource}

사용 사례:automated forms conversion 서비스를 사용하여 데이터 바인딩이 없는 적응형 양식을 생성하고 MYSQL 데이터베이스를 데이터 소스로 구성합니다. 적응형 양식 필드를 데이터 모델 엔티티에 수동으로 바인딩하고 **[!UICONTROL Form Data Model Prefill Service]** 옵션을 사용하여 필드 값을 미리 채웁니다. **[!UICONTROL Submit using Form Data Model]** 옵션을 사용하여 적응형 양식을 제출합니다.

사용 사례를 실행하기 전에:

* [MySQL 데이터베이스를 데이터 소스로 구성](https://helpx.adobe.com/experience-manager/6-5/forms/using/configure-data-sources.html#configurerelationaldatabase)
* [양식 데이터 모델 만들기](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html)

사용 사례에 따라 **응용 프로그램** 양식 데이터 모델을 만들고 읽기 서비스 인수를 **[!UICONTROL Literal]** 값에 바인딩합니다. 전화 번호 리터럴 값은 MySQL 데이터베이스의 **신청인** 스키마에 구성된 레코드 중 하나여야 합니다. 서비스는 값을 인수로 사용하여 데이터 소스에서 세부 정보를 가져옵니다. **[!UICONTROL Binding To]** 드롭다운 목록에서 [사용자 프로필 속성 또는 요청 속성](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html#bindargument)을 선택할 수도 있습니다

![양식 데이터 모델 구성](assets/configure_model_object.png)

>[!NOTE]
>
>사용 사례를 실행하기 전에 **get** 및 **insert** 서비스를 양식 데이터 모델에 추가하고, 구성하고, 테스트해야 합니다.

다음 단계를 실행합니다.

1. **[!UICONTROL output]** 폴더에서 사용할 수 있는 변환된 **샘플 대출 신청 양식**&#x200B;을 선택하고 **[!UICONTROL Properties]**&#x200B;을 탭합니다.
1. **[!UICONTROL Form Model]** 탭을 탭하고 **[!UICONTROL Select From]** 드롭다운 목록에서 **[!UICONTROL Form Data Model]** 를 선택한 다음, **[!UICONTROL Select Form Data Model]** 를 탭하여 **응용 프로그램** 양식 데이터 모델을 선택합니다. **[!UICONTROL Save & Close]** 을 눌러 양식을 저장합니다.
1. **샘플 대출 응용 프로그램 양식**&#x200B;을 선택하고 **[!UICONTROL Edit]**&#x200B;를 탭합니다.
1. **[!UICONTROL Content]** 탭에서 구성 아이콘을 탭합니다.

   ![양식 컨테이너 구성](assets/configure_form_container.png)

   1. **[!UICONTROL Basic]** 섹션의 **[!UICONTROL Prefill Service]** 드롭다운 목록에서 **[!UICONTROL Form Data Model Prefill service]** 을 선택합니다.

   1. **[!UICONTROL Submission]** 섹션의 **[!UICONTROL Submit Action]** 드롭다운 목록에서 **[!UICONTROL Submit using Form Data Model]** 을 선택합니다.

   1. **[!UICONTROL Data Model to submit]** 필드를 사용하여 데이터 모델을 선택합니다.
   1. ![완료 아이콘](assets/save_icon.svg)을 탭하여 속성을 저장합니다.

1. 지원자명 텍스트 상자를 탭하고 ![구성 아이콘](assets/configure_icon.svg)(구성)을 선택합니다.

   1. 참조 바인딩 필드에서 **지원자** > **이름**&#x200B;을 선택하고 ![완료 아이콘](assets/save_icon.svg)을 탭하여 속성을 저장합니다. 마찬가지로 **주소**, **전화 번호**, **전자 메일**, **직업**, **연간 급여(달러)** 및 **아니요. 종속 패밀리 멤버** 필드(양식 데이터 모델 엔티티가 있음).

   ![참조 바인딩](assets/bind_references.png)

1. 미리 입력된 적응형 양식 필드 값을 보려면 **[!UICONTROL Preview]** 을 누릅니다.
1. 필요한 경우 필드 값을 수정하고 적응형 양식을 제출합니다. 필드 값이 MySQL 데이터베이스에 제출됩니다. 데이터베이스의 **신청인** 테이블을 새로 고쳐 테이블에서 업데이트된 값을 볼 수 있습니다.

**사용 사례:**  Automated forms conversion 서비스를 사용하여 데이터 바인딩이 없는 적응형 양식을 생성하고 MYSQL 데이터베이스를 데이터 소스로 구성합니다. 규칙 편집기를 사용하여 적응형 양식 필드를 바인딩하여 필드 값을 미리 채웁니다. 필요한 경우 필드 값을 수정하고 crx-repository에 데이터를 제출합니다.

다음 단계를 실행하여 [규칙 편집기](https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html)를 사용하여 양식 데이터 모델 서비스를 호출하여 적응형 양식의 필드 및 미리 채우기 값을 바인딩합니다.

1. **[!UICONTROL output]** 폴더에서 **샘플 대출 신청 양식**&#x200B;을 선택하고 **[!UICONTROL Edit]**&#x200B;을 탭합니다.
1. **[!UICONTROL Content]** 탭에서 구성 아이콘을 탭합니다.

   ![양식 컨테이너 구성](assets/configure_form_container.png)

   **[!UICONTROL Basic]** 섹션의 **[!UICONTROL Prefill Service]** 드롭다운 목록에서 **[!UICONTROL Form Data Model Prefill service]** 을 선택합니다.

1. **[!UICONTROL Applicant Name]** 텍스트 상자를 탭하고 **[!UICONTROL Edit Rules]** 를 탭합니다.

   ![규칙을 편집하여 데이터 바인딩 만들기](assets/edit_rules_bind_reference.png)

1. 규칙 편집기 페이지에서 **[!UICONTROL Create]** 을 누릅니다.
1. **[!UICONTROL Rule Editor]** 페이지에서 다음을 수행합니다.

   1. 지원자명 텍스트 상자의 상태를 선택합니다. 예를 들어 **[!UICONTROL is initialized]** 은 **[!UICONTROL Preview]** 모드에서 양식을 렌더링할 때 **[!UICONTROL Then]** 조건이 실행됩니다.

   1. **[!UICONTROL Then]** 섹션의 **[!UICONTROL Select Action]** 드롭다운 목록에서 **[!UICONTROL Invoke Service]** 을 선택합니다. Forms 인스턴스의 모든 서비스가 드롭다운 목록에 표시됩니다.

   1. 양식 데이터 모델을 나열하는 섹션에서 **[!UICONTROL Get]** 서비스를 선택합니다. 입력 필드에는 **지원자** 데이터 모델에 정의된 기본 키인 **phonenumber**&#x200B;이 표시됩니다. 시스템은 이 필드를 기반으로 출력 섹션의 필드에 대한 적응형 양식의 값을 검색하고 미리 채웁니다.

   1. 출력 섹션을 사용하여 양식 데이터 모델 엔티티가 있는 적응형 양식 필드에 대한 바인딩을 만듭니다. 예를 들어 **[!UICONTROL Applicant Name]** 적응형 양식 필드를 **name** 엔터티에 바인딩합니다.

   1. 탭하기 **[!UICONTROL Done]**. 규칙 편집기 페이지에서 **[!UICONTROL Done]**&#x200B;을 다시 누릅니다.

   ![참조를 바인딩하는 규칙 편집기](assets/rule_editor_bind_references.png)

1. 미리 입력된 적응형 양식 필드 값을 보려면 **[!UICONTROL Preview]** 을 누릅니다.

   >[!NOTE]
   >
   >적응형 양식과 연결된 양식 데이터 모델에서 **get** 서비스 속성에 대해 **[!UICONTROL Return Array]** 속성이 OFF로 설정되어 있는지 확인하십시오.

1. 필요한 경우 필드 값을 수정하고 적응형 양식을 제출합니다. 제출된 데이터는 crx-repository의 다음 위치에서 사용할 수 있습니다.

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### 데이터 소스로 JSON 스키마 사용 {#jsondatasource}

**사용 사례:**  Automated forms conversion 서비스를 사용하여 데이터 바인딩이 없는 적응형 양식을 생성하고 JSON 스키마를 데이터 소스로 구성합니다. 적응형 양식 필드를 JSON 스키마에 수동으로 바인딩하고 **데이터를 사용하여 미리 보기** 옵션을 사용하여 필드 값을 미리 채웁니다. 필요한 경우 필드 값을 수정하고 crx-repository에 데이터를 제출합니다.

사용 사례를 실행하기 전에 다음 사항이 있는지 확인하십시오.

* [JSON 스키마 구조와 호환되는 유효한 JSON 스키마](#prepare-data-for-form-model)
* [데이터 바인딩이 없는 적응형 양식](#generate-adaptive-forms-with-no-data-binding)

다음 단계를 실행합니다.

1. **output** 폴더에서 사용할 수 있는 변환된 **샘플 융자 응용 프로그램 양식**&#x200B;을 선택하고 **[!UICONTROL Properties]**&#x200B;를 탭합니다.
1. **[!UICONTROL Form Model]** 탭을 탭하고 **[!UICONTROL Select From]** 드롭다운 목록에서 **[!UICONTROL Schema]** 를 선택한 다음, **[!UICONTROL Select Schema]** 를 탭하여 로컬 파일 시스템에 저장된 **demo.schema JSON** 스키마를 업로드합니다. **[!UICONTROL Save & Close]** 을 눌러 양식을 저장합니다.
1. **샘플 대출 응용 프로그램 양식**&#x200B;을 선택하고 **[!UICONTROL Edit]**&#x200B;를 탭합니다.
1. 지원자명 텍스트 상자를 탭하고 ![구성 아이콘](assets/configure_icon.svg)(구성)을 선택합니다.

   참조 바인딩 필드에서 **지원자** > **이름**&#x200B;을 선택하고 ![완료 아이콘](assets/save_icon.svg)을 탭하여 속성을 저장합니다. 마찬가지로 **주소**, **전화 번호**, **전자 메일**, **직업**, **연간 급여(달러)** 및 **아니요. JSON 스키마 엔티티가 있는 종속 패밀리 멤버** 필드

1. **[!UICONTROL output]** 폴더에서 사용할 수 있는 변환된 **샘플 대부 응용 프로그램 양식**&#x200B;을 다시 선택하고 **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**&#x200B;를 선택합니다.</br>

   샘플 데이터 파일 다운로드</br>

   [파일 가져오기](assets/json_data_file.txt)</br>

1. 필요한 경우 필드 값을 수정하고 적응형 양식을 제출합니다. 제출된 데이터는 crx-repository의 다음 위치에서 사용할 수 있습니다.

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### XSD 스키마를 데이터 소스로 사용 {#xsddatasource}

**사용 사례:**  Automated forms conversion 서비스를 사용하여 데이터 바인딩이 없는 적응형 양식을 생성하고 XSD 스키마를 데이터 소스로 구성합니다. 적응형 양식 필드를 XSD 스키마에 수동으로 바인딩하고 **데이터**&#x200B;로 미리 보기를 사용하여 필드 값을 미리 채웁니다. 필요한 경우 필드 값을 수정하고 crx-repository에 데이터를 제출합니다.

사용 사례를 실행하기 전에 다음 사항이 있는지 확인하십시오.

* [XML 스키마 구조와 호환되는 유효한 XSD 스키마](#prepare-data-for-form-model)
* [데이터 바인딩이 없는 적응형 양식](#generate-adaptive-forms-with-no-data-binding)

다음 단계를 실행합니다.

1. **[!UICONTROL output]** 폴더에서 사용할 수 있는 변환된 **샘플 대출 신청 양식**&#x200B;을 선택하고 **[!UICONTROL Properties]**&#x200B;을 탭합니다.
1. **[!UICONTROL Form Model]** 탭을 탭하고 **[!UICONTROL Select From]** 드롭다운 목록에서 **[!UICONTROL Schema]** 를 선택한 다음, **[!UICONTROL Select Schema]** 를 탭하여 로컬 파일 시스템에 저장된 **응용 프로그램** XSD 스키마를 업로드합니다. XSD 스키마의 루트 요소를 선택하고 **[!UICONTROL Save & Close]** 을 눌러 양식을 저장합니다.
1. **샘플 대출 응용 프로그램 양식**&#x200B;을 선택하고 **[!UICONTROL Edit]**&#x200B;를 탭합니다.
1. 지원자명 텍스트 상자를 탭하고 ![구성 아이콘](assets/configure_icon.svg)(구성)을 선택합니다.
참조 바인딩 필드에서 **지원자** > **이름**&#x200B;을 선택하고 ![완료 아이콘](assets/save_icon.svg)을 탭하여 속성을 저장합니다. 마찬가지로 **주소**, **전화 번호**, **전자 메일**, **직업**, **연간 급여(달러)** 및 **아니요. XSD 스키마 엔터티가 있는 종속 패밀리 멤버** 필드

1. **출력** 폴더에서 사용할 수 있는 변환된 **샘플 대부 응용 프로그램 양식**&#x200B;을 다시 선택하고 **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**&#x200B;를 선택합니다.</br>

   샘플 데이터 파일 다운로드</br>

   [파일 가져오기](assets/loan-application-data-xml-data.zip)</br>


1. 필요한 경우 필드 값을 수정하고 적응형 양식을 제출합니다. 제출된 데이터는 crx-repository의 다음 위치에서 사용할 수 있습니다.

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## JSON 바인딩 {#generate-adaptive-forms-with-json-binding}을 사용하여 적응형 양식 생성

[Automated forms conversion 서비스를 사용하여 ](convert-existing-forms-to-adaptive-forms.md)샘플 대출 응용 프로그램 양식](#sample-adaptive-form)을 데이터 바인딩이 있는 적응형 양식으로 변환합니다. [ 적응형 양식을 생성하는 동안 **[!UICONTROL Generate adaptive form(s) without data bindings]** 확인란을 선택하지 않아야 합니다.

![JSON 바인딩이 있는 적응형 양식](assets/generate_af_with_data_bindings.png)

### 데이터 소스로 JSON 스키마 사용 {#jsonwithdatabinding}

**사용 사례:** Automated forms conversion 서비스를 사용하여 JSON 데이터 바인딩이 있는 적응형 양식을 생성합니다. 미리 채우기 서비스 및 양식 제출은 원활하게 작동합니다. 구성 단계는 필요하지 않습니다.

사용 사례를 실행하기 전에 [데이터 바인딩이 있는 적응형 양식이 있는지 확인하십시오](#generate-adaptive-forms-with-json-binding).

다음 단계를 실행합니다.

1. **[!UICONTROL output]** 폴더에서 사용할 수 있는 변환된 **샘플 대부 응용 프로그램 양식**&#x200B;을 다시 선택하고 **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**&#x200B;를 선택합니다.</br>

   샘플 데이터 파일 다운로드</br>

   [파일 가져오기](assets/loan_application_data_source_json_data_binding.txt)</br>

1. 필요한 경우 필드 값을 수정하고 적응형 양식을 제출합니다. 제출된 데이터는 crx-repository의 다음 위치에서 사용할 수 있습니다.

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## 제출된 적응형 양식 JSON 데이터를 XML 형식 {#convert-submitted-adaptive-form-data-to-xml}으로 변환

적응형 양식 필드에 값을 입력하고 제출하면 crx-repository에서 데이터를 JSON 형식으로 사용할 수 있습니다. [org.apache.sling.commons.json.xml](https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString) API 또는 다음 샘플 코드를 사용하여 JSON 데이터의 형식을 XML로 변환할 수 있습니다.

```
import org.apache.sling.commons.json.JSONException;
import org.apache.sling.commons.json.JSONObject;
import org.apache.sling.commons.json.xml.XML;
 
public class ConversionUtils {
 
    public static String jsonToXML(String jsonString) throws JSONException {
        //https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString(java.lang.Object)
        //jar - http://maven.ibiblio.org/maven2/org/apache/sling/org.apache.sling.commons.json/2.0.18/
        //Note: Need to extract boundData part before converting to XML
        return XML.toString(new JSONObject(jsonString));
    }
}
```
