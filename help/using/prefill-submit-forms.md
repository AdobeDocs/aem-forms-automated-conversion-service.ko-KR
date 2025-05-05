---
title: 적응형 양식을 위한 권장 데이터 소스 기반 미리 채우기 및 제출 워크플로우
description: AFCS(Automated forms conversion 서비스)를 사용하여 생성된 적응형 양식을 위한 데이터 소스 기반 미리 채우기 및 제출 워크플로우입니다.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: forms
role: Admin, Developer
level: Beginner, Intermediate
contentOwner: khsingh
exl-id: 5deef8f5-5098-47c1-b696-b2db59e92931
source-git-commit: c2392932d1e29876f7a11bd856e770b8f7ce3181
workflow-type: tm+mt
source-wordcount: '2397'
ht-degree: 1%

---

# 적응형 양식을 위한 권장 데이터 소스 기반 미리 채우기 및 제출 워크플로우 {#recommended-data-source-btased-prefill-and-submit-workflows-for-adaptive-forms}

AFCS(Automated forms conversion 서비스)를 사용하여 변환된 적응형 양식에 다음 데이터 소스를 사용할 수 있습니다.

* 양식 데이터 모델, OData 또는 기타 타사 서비스
* JSON 스키마
* XSD 스키마

데이터 소스를 기반으로 데이터 모델이 있거나 없는 적응형 양식을 생성하도록 선택할 수 있습니다.

이 문서에서는 데이터 소스를 선택하고 전환 서비스를 사용하여 적응형 양식을 생성한 후 필드 값과 제출 옵션을 미리 채우는 권장 워크플로우에 대해 설명합니다.

<table> 
 <tbody> 
  <tr> 
   <th><strong>데이터 소스</strong></th> 
   <th><strong>권장 워크플로우</strong></th> 
  </tr> 
  <tr> 
   <td><p>양식 데이터 모델, OData 또는 기타 타사 서비스</p></td> 
   <td> 
    <p><strong>옵션 1</strong>: 양식 데이터 모델, OData 또는 기타 타사 서비스를 데이터 소스로 선택합니다. AFCS(Automated forms conversion 서비스)를 사용하여 <a href="#generate-adaptive-forms-with-no-data-binding">데이터 바인딩이 없는 적응형 양식을 생성</a>합니다. 적응형 양식 필드를 양식 데이터 모델 엔티티에 수동으로 바인딩하고 양식 데이터 모델 미리 채우기 서비스 옵션을 사용하여 필드 값을 미리 채웁니다. 양식 데이터 모델을 사용하여 제출 옵션을 사용하여 적응형 양식을 제출합니다.</p></td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
   <p><strong>옵션 2</strong>: 양식 데이터 모델, OData 또는 기타 타사 서비스를 데이터 소스로 선택합니다. AFCS(Automated forms conversion 서비스)를 사용하여 <a href="#generate-adaptive-forms-with-no-data-binding">데이터 바인딩이 없는 적응형 양식을 생성</a>합니다. 규칙 편집기를 사용하여 적응형 양식 필드를 바인딩하여 필드 값을 미리 채웁니다. 필요한 경우 필드 값을 수정하고 crx-repository에 데이터를 전송합니다.</p>
    </td> 
  </tr>
  <tr> 
   <td></td> 
   <td> 
    <p>이러한 워크플로우를 실행하는 단계별 지침은 <a href="#sqldatasource">데이터베이스, OData 또는 서드파티 서비스를 데이터 소스로 사용</a>을 참조하십시오.</p> </td> 
  </tr>
  <tr>
  <td><p>JSON 스키마</p></td> 
   <td> 
    <p>JSON 스키마를 데이터 소스로 선택합니다. 선택한 데이터 소스 기반:</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>옵션 1</strong>: AFCS(Automated forms conversion 서비스)를 사용하여 <a href="#generate-adaptive-forms-with-no-data-binding">데이터 바인딩이 없는 적응형 양식을 생성</a>하고 JSON 스키마를 데이터 소스로 구성합니다. 적응형 양식 필드를 JSON 스키마에 수동으로 바인딩하고 <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">지원되는 프로토콜 중 하나를 사용</a>하여 필드 값을 미리 채웁니다. 필요한 경우 필드 값을 수정하고 crx-repository에 데이터를 전송합니다.</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p>워크플로우를 실행하는 단계별 지침은 <a href="#jsondatasource">JSON 스키마를 데이터 소스로 사용 을 참조하십시오.</p></td> 
  </tr>
  <tr>
  <td></td> 
   <td> 
    <p><strong>옵션 2</strong>: AFCS(Automated forms conversion 서비스)를 사용하여 <a href="#generate-adaptive-forms-with-json-binding">JSON 데이터 바인딩이 있는 적응형 양식을 생성</a>합니다. 미리 채우기 서비스와 양식 제출이 원활하게 작동합니다. 구성 단계는 필요하지 않습니다.</p> </td> 
  </tr>
   <tr>
  <td></td> 
   <td> 
    <p>워크플로우를 실행하는 단계별 지침은 <a href="#jsonwithdatabinding">JSON 스키마를 데이터 소스로 사용</a>을 참조하십시오.</p> </td> 
  </tr>
  <tr>
  <td><p>XSD 스키마</p></td> 
   <td> 
    <p>XSD 스키마를 데이터 소스로 선택합니다. 선택한 데이터 원본을 기반으로 AFCS(Automated forms conversion 서비스)를 사용하여 <a href="#generate-adaptive-forms-with-no-data-binding">데이터 바인딩이 없는 적응형 양식을 생성</a>하고 XSD 스키마를 데이터 원본으로 구성합니다. 적응형 양식 필드를 XSD 스키마에 수동으로 바인딩하고 <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/prepopulate-adaptive-form-fields.html#Supportedprotocolsforprefillinguserdata" target="_blank">지원되는 프로토콜 중 하나를 사용</a>하여 필드 값을 미리 채웁니다. 필요한 경우 필드 값을 수정하고 crx-repository에 데이터를 전송합니다.</p>
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


AFCS(Automated forms conversion 서비스)에 대한 자세한 내용은 다음 문서를 참조하십시오.

* [automated forms conversion 서비스 소개](introduction.md)
* [automated forms conversion 서비스 구성](configure-service.md)
* [인쇄 양식을 적응형 양식으로 전환](convert-existing-forms-to-adaptive-forms.md)
* [전환된 양식 검토 및 수정](review-correct-ui-edited.md)

이 글에서 제공하는 정보는 이를 읽는 누구나 적응형 양식 개념에 대한 기본 지식을 가지고 있다는 가정을 기반으로 한다.

## 전제 조건 {#pre-requisites}

* [AEM 작성자 인스턴스 구성](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html)
* AEM 작성자 인스턴스에서 [AFCS(Automated forms conversion 서비스) 구성](configure-service.md)

## 샘플 적응형 양식 {#sample-adaptive-form}

사용 사례를 실행하여 적응형 양식의 필드 값을 미리 채워 데이터 소스에 제출하려면 다음 샘플 PDF 파일을 다운로드하십시오.

샘플 대출 신청서 양식

[파일 가져오기](assets/sample_loan_application_form.pdf)

PDF 파일은 Automated forms conversion 서비스(AFCS)에 대한 입력 역할을 합니다. 이 서비스는 이 파일을 적응형 양식으로 전환합니다. 다음 이미지는 PDF 형식의 샘플 대출 신청을 보여 줍니다.

![샘플 대출 신청서 양식](assets/sample_form_new.png)

## 양식 모델을 위한 데이터 준비 {#prepare-data-for-form-model}

AEM Forms 데이터 통합을 사용하면 서로 다른 데이터 소스를 구성하고 연결할 수 있습니다. 전환 프로세스를 사용하여 적응형 양식을 생성한 후 양식 데이터 모델, XSD 또는 JSON 스키마를 기반으로 양식 모델을 정의할 수 있습니다. 데이터베이스, Microsoft Dynamics 또는 기타 서드파티 서비스를 사용하여 양식 데이터 모델을 만들 수 있습니다.

이 자습서에서는 MySQL 데이터베이스를 소스로 사용하여 양식 데이터 모델을 만듭니다. 데이터베이스에 **loanapplication** 스키마를 만들고 적응형 양식에서 사용할 수 있는 필드를 기반으로 스키마에 **applant** 테이블을 추가하십시오.

![샘플 데이터 mysql](assets/sample_data_mysql.png)

다음 DDL 문을 사용하여 데이터베이스에서 **plentor** 테이블을 만들 수 있습니다.

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

XSD 스키마를 양식 모델로 사용하여 사용 사례를 실행하는 경우 다음 텍스트가 포함된 XSD 파일을 생성합니다.

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

또는 XSD 스키마를 로컬 파일 시스템에 다운로드합니다.

샘플 대출 애플리케이션 XSD 스키마

[파일 가져오기](assets/loanapplication.xsd)

적응형 양식에서 XSD 스키마를 양식 모델로 사용하는 방법에 대한 자세한 내용은 [XML 스키마를 사용하여 적응형 양식 만들기](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-xml-schema-form-model.html)를 참조하십시오.

양식 모델로 JSON 스키마를 사용하여 사용 사례를 실행하는 경우 다음 텍스트가 포함된 JSON 파일을 만듭니다.

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

적응형 양식에서 JSON 스키마를 양식 모델로 사용하는 방법에 대한 자세한 내용은 [JSON 스키마를 사용하여 적응형 양식 만들기](https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html)를 참조하십시오.

## 데이터 바인딩 없이 적응형 양식 생성 {#generate-adaptive-forms-with-no-data-binding}

[&#128279;](convert-existing-forms-to-adaptive-forms.md)Automated forms conversion 서비스를 사용하여 [샘플 대출 응용 프로그램 양식](#sample-adaptive-form)을(를) 데이터 바인딩이 없는 적응형 양식으로 변환할 수 있습니다. 데이터 바인딩 없이 적응형 양식을 생성하려면 **[!UICONTROL Generate adaptive form(s) without data bindings]** 확인란을 선택해야 합니다.

![데이터 바인딩이 없는 적응형 양식](assets/generate_af_without_binding.png)

데이터 바인딩이 없는 적응형 양식을 생성한 후 적응형 양식에 대한 데이터 소스를 선택합니다.

* [데이터베이스, OData 또는 모든 타사 서비스](#sqldatasource)
* [JSON 스키마](#jsondatasource)
* [XSD 스키마](#xsddatasource)

>[!NOTE]
> AFCS(Automated forms conversion 서비스)를 사용하여 변환하는 적응형 양식에 같은 이름의 필드가 여러 개 포함되어 있는 경우, 제출 중에 발생할 수 있는 데이터 손실을 방지하기 위해 해당 필드가 데이터 소스 엔티티에 바인딩되어 있는지 확인하십시오.
>

### 데이터베이스, OData 또는 서드파티 서비스를 데이터 소스로 사용 {#sqldatasource}

사용 사례: Automated forms conversion 서비스(AFCS)를 사용하여 데이터 바인딩 없이 적응형 양식을 생성하고 MYSQL 데이터베이스를 데이터 소스로 구성합니다. 적응형 양식 필드를 양식 데이터 모델 엔터티에 수동으로 바인딩하고 **[!UICONTROL Form Data Model Prefill Service]** 옵션을 사용하여 필드 값을 미리 채웁니다. **[!UICONTROL Submit using Form Data Model]** 옵션을 사용하여 적응형 양식을 제출합니다.

사용 사례를 실행하기 전에:

* [MySQL 데이터베이스를 데이터 소스로 구성](https://helpx.adobe.com/experience-manager/6-5/forms/using/configure-data-sources.html#configurerelationaldatabase)
* [양식 데이터 모델 만들기](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html)

사용 사례에 따라 **loanapplication** 양식 데이터 모델을 만들고 읽기 서비스 인수를 **[!UICONTROL Literal]** 값에 바인딩합니다. 전화 번호 리터럴 값은 MySQL 데이터베이스의 **appeline** 스키마에 구성된 레코드 중 하나여야 합니다. 서비스는 값을 인수로 사용하여 데이터 소스에서 세부 정보를 가져옵니다. **[!UICONTROL Binding To]** 드롭다운 목록에서 [사용자 프로필 속성 또는 요청 속성](https://helpx.adobe.com/experience-manager/6-5/forms/using/work-with-form-data-model.html#bindargument)을 선택할 수도 있습니다

![양식 데이터 모델 구성](assets/configure_model_object.png)

>[!NOTE]
>
>사용 사례를 실행하기 전에 양식 데이터 모델에 **get** 및 **insert** 서비스를 추가하고 서비스를 구성하고 테스트하십시오.

다음 단계를 실행합니다.

1. **[!UICONTROL output]** 폴더에서 사용 가능한 전환된 **샘플 대출 신청 양식**&#x200B;을 선택하고 **[!UICONTROL Properties]**&#x200B;을(를) 누릅니다.
1. **[!UICONTROL Form Model]** 탭을 탭하고 **[!UICONTROL Select From]** 드롭다운 목록에서 **[!UICONTROL Form Data Model]**&#x200B;을(를) 선택한 다음 **[!UICONTROL Select Form Data Model]**&#x200B;을(를) 탭하여 **loanapplication** 양식 데이터 모델을 선택합니다. 양식을 저장하려면 **[!UICONTROL Save & Close]**&#x200B;을(를) 탭하세요.
1. **샘플 대출 신청서 양식**&#x200B;을 선택하고 **[!UICONTROL Edit]**&#x200B;을(를) 탭하세요.
1. **[!UICONTROL Content]** 탭에서 구성 아이콘을 탭합니다.

   ![양식 컨테이너 구성](assets/configure_form_container.png)

   1. **[!UICONTROL Basic]** 섹션의 **[!UICONTROL Prefill Service]** 드롭다운 목록에서 **[!UICONTROL Form Data Model Prefill service]**&#x200B;을(를) 선택합니다.

   1. **[!UICONTROL Submission]** 섹션의 **[!UICONTROL Submit Action]** 드롭다운 목록에서 **[!UICONTROL Submit using Form Data Model]**&#x200B;을(를) 선택합니다.

   1. **[!UICONTROL Data Model to submit]** 필드를 사용하여 데이터 모델을 선택하십시오.
   1. 속성을 저장하려면 ![완료 아이콘](assets/save_icon.svg)을 탭하세요.

1. 지원자 이름 텍스트 상자를 누르고 ![구성 아이콘](assets/configure_icon.svg)(구성)을 선택합니다.

   1. 바인드 참조 필드에서 **지원자** > **이름**&#x200B;을 선택하고 ![완료 아이콘](assets/save_icon.svg)을 눌러 속성을 저장합니다. 마찬가지로 **주소**, **전화 번호**, **전자 메일**, **직업**, **연봉(달러)** 및 **아니요&rbrace;에 대한 데이터 바인딩을 만듭니다. 양식 데이터 모델 엔터티가 있는 종속 패밀리 멤버**&#x200B;개 필드

   ![참조 바인딩](assets/bind_references.png)

1. 미리 채워진 적응형 양식 필드 값을 보려면 **[!UICONTROL Preview]**&#x200B;을(를) 탭하세요.
1. 필요한 경우 필드 값을 수정하고 적응형 양식을 제출합니다. 필드 값이 MySQL 데이터베이스에 제출됩니다. 데이터베이스의 **신청자** 테이블을 새로 고쳐 테이블에서 업데이트된 값을 볼 수 있습니다.

**사용 사례:** AFCS(Automated forms conversion 서비스)를 사용하여 데이터 바인딩이 없는 적응형 양식을 생성하고 MYSQL 데이터베이스를 데이터 소스로 구성합니다. 규칙 편집기를 사용하여 적응형 양식 필드를 바인딩하여 필드 값을 미리 채웁니다. 필요한 경우 필드 값을 수정하고 crx-repository에 데이터를 전송합니다.

다음 단계를 실행하여 [규칙 편집기](https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html)를 사용하여 양식 데이터 모델 서비스를 호출하여 적응형 양식의 필드를 바인딩하고 값을 미리 채우십시오.

1. **[!UICONTROL output]** 폴더에서 **샘플 대출 신청 양식**&#x200B;을 선택하고 **[!UICONTROL Edit]**&#x200B;을(를) 누릅니다.
1. **[!UICONTROL Content]** 탭에서 구성 아이콘을 탭합니다.

   ![양식 컨테이너 구성](assets/configure_form_container.png)

   **[!UICONTROL Basic]** 섹션의 **[!UICONTROL Prefill Service]** 드롭다운 목록에서 **[!UICONTROL Form Data Model Prefill service]**&#x200B;을(를) 선택합니다.

1. **[!UICONTROL Applicant Name]** 텍스트 상자를 누르고 **[!UICONTROL Edit Rules]**&#x200B;을 누릅니다.

   ![규칙을 편집하여 데이터 바인딩을 만듭니다](assets/edit_rules_bind_reference.png)

1. 규칙 편집기 페이지에서 **[!UICONTROL Create]**&#x200B;을(를) 탭합니다.
1. **[!UICONTROL Rule Editor]** 페이지에서:

   1. 지원자명 텍스트 상자의 상태를 선택합니다. 예를 들어 **[!UICONTROL is initialized]**&#x200B;이(가) **[!UICONTROL Preview]** 모드에서 양식을 렌더링할 때 **[!UICONTROL Then]** 조건이 실행됩니다.

   1. **[!UICONTROL Then]** 섹션의 **[!UICONTROL Select Action]** 드롭다운 목록에서 **[!UICONTROL Invoke Service]**&#x200B;을(를) 선택합니다. Forms 인스턴스의 모든 서비스가 드롭다운 목록에 표시됩니다.

   1. 양식 데이터 모델을 나열하는 섹션에서 **[!UICONTROL Get]** 서비스를 선택하십시오. 입력 필드에 **지원자** 데이터 모델에 대해 정의된 기본 키인 **phonenumber**&#x200B;이(가) 표시됩니다. 시스템은 이 필드를 기반으로 출력 섹션의 필드에 대한 적응형 양식의 값을 검색하고 미리 채웁니다.

   1. 출력 섹션을 사용하여 양식 데이터 모델 엔티티와 함께 적응형 양식 필드에 대한 바인딩을 만듭니다. 예를 들어 **[!UICONTROL Applicant Name]** 적응형 양식 필드를 **name** 엔터티로 바인딩하십시오.

   1. **[!UICONTROL Done]**&#x200B;을 누릅니다. 규칙 편집기 페이지에서 **[!UICONTROL Done]**&#x200B;을(를) 다시 탭합니다.

   ![참조를 바인딩할 규칙 편집기](assets/rule_editor_bind_references.png)

1. 미리 채워진 적응형 양식 필드 값을 보려면 **[!UICONTROL Preview]**&#x200B;을(를) 탭하세요.

   >[!NOTE]
   >
   >적응형 양식과 연결된 양식 데이터 모델에서 **get** 서비스 속성에 대해 **[!UICONTROL Return Array]** 속성이 OFF로 설정되어 있는지 확인하십시오.

1. 필요한 경우 필드 값을 수정하고 적응형 양식을 제출합니다. 제출된 데이터는 crx 저장소의 다음 위치에서 사용할 수 있습니다.

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### JSON 스키마를 데이터 소스로 사용 {#jsondatasource}

**사용 사례:** AFCS(Automated forms conversion 서비스)를 사용하여 데이터 바인딩이 없는 적응형 양식을 생성하고 JSON 스키마를 데이터 소스로 구성합니다. 적응형 양식 필드를 JSON 스키마에 수동으로 바인딩하고 **데이터로 미리 보기** 옵션을 사용하여 필드 값을 미리 채웁니다. 필요한 경우 필드 값을 수정하고 crx-repository에 데이터를 전송합니다.

사용 사례를 실행하기 전에 다음을 확인하십시오.

* [json 스키마 구조와 호환되는 유효한 JSON 스키마](#prepare-data-for-form-model)
* [데이터 바인딩이 없는 적응형 양식](#generate-adaptive-forms-with-no-data-binding)

다음 단계를 실행합니다.

1. **output** 폴더에서 사용할 수 있는 변환된 **샘플 대출 신청 양식**&#x200B;을 선택하고 **[!UICONTROL Properties]**&#x200B;을(를) 탭합니다.
1. **[!UICONTROL Form Model]** 탭을 탭하고 **[!UICONTROL Select From]** 드롭다운 목록에서 **[!UICONTROL Schema]**&#x200B;을(를) 선택한 다음 **[!UICONTROL Select Schema]**&#x200B;을(를) 탭하여 로컬 파일 시스템에 저장된 **demo.schema JSON** 스키마를 업로드합니다. 양식을 저장하려면 **[!UICONTROL Save & Close]**&#x200B;을(를) 탭하세요.
1. **샘플 대출 신청서 양식**&#x200B;을 선택하고 **[!UICONTROL Edit]**&#x200B;을(를) 탭하세요.
1. 지원자 이름 텍스트 상자를 누르고 ![구성 아이콘](assets/configure_icon.svg)(구성)을 선택합니다.

   바인드 참조 필드에서 **지원자** > **이름**&#x200B;을 선택하고 ![완료 아이콘](assets/save_icon.svg)을 눌러 속성을 저장합니다. 마찬가지로 **주소**, **전화 번호**, **전자 메일**, **직업**, **연봉(달러)** 및 **아니요&rbrace;에 대한 데이터 바인딩을 만듭니다. JSON 스키마 엔터티가 있는 종속 패밀리 멤버**&#x200B;개 필드 중

1. **[!UICONTROL output]** 폴더에서 사용 가능한 전환된 **샘플 대출 신청 양식**&#x200B;을 다시 선택하고 **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**&#x200B;을(를) 선택합니다.</br>

   샘플 데이터 파일 </br> 다운로드

   [파일 가져오기](assets/json_data_file.txt)</br>

1. 필요한 경우 필드 값을 수정하고 적응형 양식을 제출합니다. 제출된 데이터는 crx 저장소의 다음 위치에서 사용할 수 있습니다.

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

### XSD 스키마를 데이터 소스로 사용 {#xsddatasource}

**사용 사례:** AFCS(Automated forms conversion 서비스)를 사용하여 데이터 바인딩이 없는 적응형 양식을 생성하고 XSD 스키마를 데이터 소스로 구성합니다. 적응형 양식 필드를 XSD 스키마에 수동으로 바인딩하고 **데이터로 미리 보기**&#x200B;를 사용하여 필드 값을 미리 채웁니다. 필요한 경우 필드 값을 수정하고 crx-repository에 데이터를 전송합니다.

사용 사례를 실행하기 전에 다음을 확인하십시오.

* [xml 스키마 구조와 호환되는 유효한 XSD 스키마](#prepare-data-for-form-model)
* [데이터 바인딩이 없는 적응형 양식](#generate-adaptive-forms-with-no-data-binding)

다음 단계를 실행합니다.

1. **[!UICONTROL output]** 폴더에서 사용 가능한 전환된 **샘플 대출 신청 양식**&#x200B;을 선택하고 **[!UICONTROL Properties]**&#x200B;을(를) 누릅니다.
1. **[!UICONTROL Form Model]** 탭을 탭하고 **[!UICONTROL Select From]** 드롭다운 목록에서 **[!UICONTROL Schema]**&#x200B;을(를) 선택한 다음 **[!UICONTROL Select Schema]**&#x200B;을(를) 탭하여 로컬 파일 시스템에 저장된 **loanapplication** XSD 스키마를 업로드합니다. XSD 스키마에 대한 루트 요소를 선택하고 **[!UICONTROL Save & Close]**&#x200B;을(를) 탭하여 양식을 저장합니다.
1. **샘플 대출 신청서 양식**&#x200B;을 선택하고 **[!UICONTROL Edit]**&#x200B;을(를) 탭하세요.
1. 지원자 이름 텍스트 상자를 누르고 ![구성 아이콘](assets/configure_icon.svg)(구성)을 선택합니다.
바인드 참조 필드에서 **지원자** > **이름**&#x200B;을 선택하고 ![완료 아이콘](assets/save_icon.svg)을 눌러 속성을 저장합니다. 마찬가지로 **주소**, **전화 번호**, **전자 메일**, **직업**, **연봉(달러)** 및 **아니요&rbrace;에 대한 데이터 바인딩을 만듭니다. XSD 스키마 엔터티가 있는 종속 패밀리 멤버** 필드

1. **output** 폴더에서 사용할 수 있는 변환된 **샘플 대출 신청 양식**&#x200B;을 다시 선택하고 **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**&#x200B;을(를) 선택합니다.</br>

   샘플 데이터 파일 </br> 다운로드

   [파일 가져오기](assets/loan-application-data-xml-data.zip)</br>


1. 필요한 경우 필드 값을 수정하고 적응형 양식을 제출합니다. 제출된 데이터는 crx 저장소의 다음 위치에서 사용할 수 있습니다.

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## JSON 바인딩을 사용하여 적응형 양식 생성 {#generate-adaptive-forms-with-json-binding}

[&#128279;](convert-existing-forms-to-adaptive-forms.md)Automated forms conversion 서비스(AFCS)를 사용하여 [샘플 대출 응용 프로그램 양식](#sample-adaptive-form)을(를) 데이터 바인딩이 있는 적응형 양식으로 변환합니다. 적응형 양식을 생성하는 동안 **[!UICONTROL Generate adaptive form(s) without data bindings]** 확인란을 선택하지 마십시오.

![JSON 바인딩이 있는 적응형 양식](assets/generate_af_with_data_bindings.png)

### JSON 스키마를 데이터 소스로 사용 {#jsonwithdatabinding}

**사용 사례:** AFCS(Automated forms conversion 서비스)를 사용하여 JSON 데이터 바인딩이 있는 적응형 양식을 생성했습니다. 미리 채우기 서비스와 양식 제출이 원활하게 작동합니다. 구성 단계는 필요하지 않습니다.

사용 사례를 실행하기 전에 [데이터 바인딩이 있는 적응형 양식](#generate-adaptive-forms-with-json-binding)이 있는지 확인하십시오.

다음 단계를 실행합니다.

1. **[!UICONTROL output]** 폴더에서 사용 가능한 전환된 **샘플 대출 신청 양식**&#x200B;을 다시 선택하고 **[!UICONTROL Preview]** > **[!UICONTROL Preview with Data]**&#x200B;을(를) 선택합니다.</br>

   샘플 데이터 파일 </br> 다운로드

   [파일 가져오기](assets/loan_application_data_source_json_data_binding.txt)</br>

1. 필요한 경우 필드 값을 수정하고 적응형 양식을 제출합니다. 제출된 데이터는 crx 저장소의 다음 위치에서 사용할 수 있습니다.

   `http://host name:port/crx/de/index.jsp#/content/forms/fp/admin/submit/data/latest file available in the folder`

## 제출된 적응형 양식 JSON 데이터를 XML 형식으로 변환 {#convert-submitted-adaptive-form-data-to-xml}

적응형 양식 필드에 값을 입력하고 제출하면 crx-repository에서 JSON 형식으로 데이터를 사용할 수 있습니다. [org.apache.sling.commons.json.xml](https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString) API 또는 다음 샘플 코드를 사용하여 JSON 데이터 형식을 XML로 변환할 수 있습니다.

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
