---
title: 기본 메타 모델 확장
description: 기본 메타 모델을 확장하여 조직 고유의 패턴, 유효성 검사 및 엔티티를 추가하고, Automated forms conversion 서비스를 실행하는 동안 구성을 적응형 양식 필드에 적용합니다.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: forms
role: Admin, Developer
level: Beginner, Intermediate
exl-id: f679059c-18aa-4cb5-8368-ed27e96c20de
source-git-commit: e95b4ed35f27f920b26c05f3398529f825948f1f
workflow-type: tm+mt
source-wordcount: '2565'
ht-degree: 1%

---

# 기본 메타 모델 확장 {#extend-the-default-meta-model}

Automated forms conversion 서비스는 소스 양식에서 양식 개체를 식별하고 추출합니다. 시맨틱 매퍼는 추출된 객체가 적응형 양식으로 표현되는 방식을 서비스가 결정할 수 있도록 도와줍니다. 예를 들어 소스 양식에는 날짜에 대한 다양한 표현 유형이 있을 수 있습니다. 시맨틱 매퍼는 소스 양식의 모든 날짜 양식 개체 표현을 적응형 양식의 날짜 구성 요소와 매핑하는 데 도움이 됩니다. 또한 Semantic Mapper를 사용하여 변환 중에 서비스가 유효성 검사, 규칙, 데이터 패턴, 도움말 텍스트 및 접근성 속성을 미리 구성하고 적응형 양식 구성 요소에 적용할 수 있습니다.

![](assets/meta-model.gif)

메타 모델은 JSON 스키마입니다. 메타 모델을 시작하기 전에 JSON에 대해 잘 알고 있는지 확인하십시오. JSON 형식으로 저장된 데이터를 작성, 편집 및 읽은 경험이 있어야 합니다.

## 기본 메타 모델 {#default-meta-model}

Automated forms conversion 서비스에는 기본 메타 모델이 있습니다. JSON 스키마이며 Automated forms conversion 서비스의 다른 구성 요소와 함께 Adobe 클라우드에 있습니다. 로컬 AEM 서버에서 http://으로 메타 모델의 복사본을 찾을 수 있습니다.&lt;server>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/metamodel/`global.schema.json`. 다음을 수행할 수도 있습니다. [여기를 클릭하십시오](assets/en.globalschema.json) 를 클릭하여 영어 스키마에 액세스하거나 다운로드합니다. 의 메타 모델 [프랑스어](assets/fr.globalschema.json), [독일어](assets/de.globalschema.json) [스페인어](assets/es.globalschema.json), [이탈리아어](assets/it.globalschema.json), 및 [포르투갈어](assets/pt_br.globalschema.json) 언어를 다운로드할 수도 있습니다.

메타 모델의 스키마는 https://schema.org/docs/schemas.html의 스키마 엔티티에서 파생됩니다. 여기에는 Person, PostalAddress, LocalBusiness 및 https://schema.org에 정의된 더 많은 엔티티가 있습니다. 메타 모델의 모든 엔티티는 JSON 스키마 오브젝트 유형을 준수합니다. 다음 코드는 샘플 메타 모델 구조를 나타냅니다.

```
   "Entity": {
      "id": "Entity",
      "properties": {
        "name": {
          "type": "string"
        },

        "description": {
          "type": "string",
          "description": "Description of the item"
        }
      }
    }
```

## 기본 메타 모델 다운로드 {#download-the-default-meta-model}

기본 메타 모델을 로컬 파일 시스템에 다운로드하려면 다음 단계를 수행하십시오.

1. AEM Forms 인스턴스에 로그인.
1. 다음 위치로 이동 **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** **>** **[!UICONTROL Meta Model]** 폴더를 삭제합니다.
1. 다음 항목 선택 **[!UICONTROL global.schema.json]** 파일 및 탭 **[!UICONTROL Download]**. 다운로드 대화 상자가 나타납니다. 다음 항목 선택 **[!UICONTROL Download asset(s) as binary files]** 옵션을 선택합니다. **[!UICONTROL Download]**&#x200B;을 누릅니다. 아카이브가 다운로드됩니다.

   <!--
   Comment Type: draft

   <li><p>Extract the archive and open the global.schema.json file for editing. </p> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

## 메타 모델 이해 {#understanding-the-meta-model}

메타 모델은 엔티티가 포함된 JSON 스키마 파일을 참조합니다. JSON 스키마 파일의 모든 엔티티에는 이름과 ID가 포함됩니다. 각 엔티티는 여러 속성을 포함할 수 있습니다. 엔티티와 해당 속성은 도메인에 따라 다를 수 있습니다. 키워드 및 필드 구성으로 스키마 파일을 늘려 스키마 속성을 적응형 양식 구성 요소에 매핑할 수 있습니다.

```
"Event": {
      "id": "Eventid",
      "allOf": [
        {
          "$ref": "#Entity"
        },
        {
          "properties": {
            "startDate": {
              "type": "string",
              "format": "date",
              "description": "Specify the start date and time of the event in ISO 8601 date format."
            },
            "endDate": {
              "type": "string",
              "format": "date",
              "description": "Specify the end date and time of the event in ISO 8601 date format."
            },
            "location": {
              "$ref": "#PostalAddress",
              "description": "Specify the location of the event."
            }
          }
        }
      ]
    }
```

이 예에서는 **이벤트** 값이 있는 엔티티의 이름을 나타냅니다. **id** 다음으로: **Eventid**. 이벤트 엔티티에는 여러 속성이 포함됩니다.

* startDate
* endDate
* 위치

다음 **allOf** 메타 모델에서 를 만들면 엔티티 간에 상속이 가능합니다.

각 속성에는 다음이 더 포함될 수 있습니다.

* [JSON 스키마 속성](#jsonschemaproperties)
* [생성된 적응형 양식 필드에 속성을 적용하는 키워드 기반 검색](#keywordsearch)
* [추가 속성](#additionalproperties)

![메타 모델 속성](assets/meta_model_elements.gif)

를 사용하여 참조된 키워드를 기반으로 합니다. **aem:affKeyword**, 변환 서비스는 소스 양식 필드에 대한 검색 작업을 수행합니다. 전환 서비스는 검색 기준을 충족하는 필드에 JSON 스키마 속성 및 추가 속성을 적용합니다.

이 예에서 전환 서비스는 소스 양식에서 전화, 전화, 휴대폰, 회사 전화, 집 전화, 전화 번호, 전화 번호 및 전화 번호 키워드를 검색합니다. 전환 서비스는 이러한 키워드를 포함하는 필드를 기반으로 전환 후 type, pattern 및 aem:afProperties를 적응형 양식 필드에 적용합니다.

### 생성된 적응형 양식 필드에 대한 JSON 스키마 속성 {#jsonschemaproperties}

메타 모델은 Automated forms conversion 서비스를 사용하여 생성된 적응형 양식 필드에 대한 다음의 JSON 스키마 공통 속성을 지원합니다.

<table> 
 <tbody> 
  <tr> 
   <th><strong>속성 이름</strong></th> 
   <th><strong>설명</strong></th> 
  </tr> 
  <tr> 
   <td><p>제목</p></td> 
   <td> 
    <p>메타 모델의 제목 속성 내에 언급된 텍스트는 생성된 적응형 양식 필드에 작업을 수행하는 검색 키워드 역할을 합니다. 예를 들어 적응형 양식 필드의 레이블 수정 자세한 내용은 <strong>양식 필드의 레이블 수정</strong> 위치: <a href="#custommetamodelexamples">사용자 지정 메타 모델 예</a></p> </td> 
  </tr>
  <td><p>설명</p></td> 
   <td> 
    <p>description 속성은 생성된 적응형 양식 필드에 대한 도움말 텍스트를 설정합니다. 자세한 내용은 <strong>양식 필드에 도움말 텍스트 추가</strong> 위치: <a href="#custommetamodelexamples">사용자 지정 메타 모델 예</a></p> </td> 
  </tr>
  <td><p>유형</p></td> 
   <td> 
    <p>type 속성은 생성된 적응형 양식 필드에 대한 데이터 유형을 정의합니다. 제목 속성에 사용할 수 있는 값은 다음과 같습니다.</p>
    <ul> 
     <li>string: 텍스트 데이터 유형의 적응형 양식 필드를 생성합니다.</li> 
     <li>number: 숫자 데이터 유형의 적응형 양식 필드를 생성합니다.</li>
     <li>정수: 하위 유형이 정수로 설정된 숫자 데이터 유형의 적응형 양식 필드를 생성합니다.</li>
     <li>부울: 스위치 적응형 양식 구성 요소를 생성합니다.</li>
     </ul><p>메타 모델에서 유형 속성을 사용하는 방법에 대한 자세한 내용은 <strong>양식 필드 유형 수정</strong> 위치: <a href="#custommetamodelexamples">사용자 지정 메타 모델 예</a></p></td> 
  </tr>
  <td><p>패턴</p></td> 
   <td> 
    <p>pattern 속성은 정규 표현식에 따라 생성된 적응형 양식 필드의 값을 제한합니다. 예를 들어 메타 모델의 다음 코드는 생성된 적응형 양식 필드에 대한 값을 10자리로 제한합니다.<br>"pattern": "/\\d{10}/"<br>마찬가지로 메타 모델의 다음 코드는 필드 값을 특정 날짜 형식으로 제한합니다.<br> "pattern": "date{DD MMMM, YYYY}"</p> </td> 
  </tr>
  <td><p>형식</p></td> 
   <td> 
    <p>format 속성은 정규 표현식 대신 명명된 패턴을 기반으로 생성된 적응형 양식 필드의 값을 제한합니다. 형식 속성에 사용할 수 있는 값은 다음과 같습니다.<ul><li>이메일: 이메일 적응형 양식 구성 요소를 생성합니다.</li><li>호스트 이름: 텍스트 상자 적응형 양식 구성 요소를 생성합니다.</li></ul>메타 모델에서 format 속성을 사용하는 방법에 대한 자세한 내용은 <strong>양식 필드 형식 수정</strong> 위치: <a href="#custommetamodelexamples">사용자 지정 메타 모델 예</a></p> </td> 
  </tr>
  <td><p>enum 및 enumNames</p></td> 
   <td> 
    <p>enum 및 enumNames 속성은 드롭다운, 확인란 또는 라디오 단추 필드의 값을 고정된 세트로 제한합니다. enumNames에 나열된 값은 사용자 인터페이스에 표시됩니다. 열거형 속성을 사용하여 나열된 값은 계산에 사용됩니다.<br>자세한 내용은 <strong>적응형 양식에서 양식 필드를 다중 선택 확인란으로 변환</strong>, <strong>텍스트 필드를 적응형 양식의 드롭다운 목록으로 변환</strong>, 및 <strong>드롭다운 목록에 추가 옵션 추가</strong> 위치: <a href="#custommetamodelexamples">사용자 지정 메타 모델 예</a></p> </td> 
  </tr>
 </tbody> 
</table>

### 생성된 적응형 양식 필드에 속성을 적용하는 키워드 기반 검색 {#keywordsearch}

Automated forms conversion 서비스는 변환 중에 소스 양식에서 키워드 검색을 수행합니다. 검색 기준을 충족하는 필드를 필터링한 후 전환 서비스는 메타 모델의 해당 필드에 대해 정의된 속성을 생성된 적응형 양식 필드에 적용합니다.

키워드는 를 사용하여 참조됩니다 **aem:affKeyword** 속성.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"]
 }
}
```

이 예제에서 전환 서비스는 다음 내에서 텍스트를 사용합니다 **aem:affKeyword** 를 검색 키워드로 사용하십시오. 검색 후 **은행 계좌 번호** 양식의 텍스트, 변환 서비스는 필드를 로 변환합니다. **숫자** 을 사용하여 입력 **유형** 속성.

### 생성된 적응형 양식 필드에 대한 추가 속성 {#additionalproperties}

다음을 사용할 수 있습니다. **aem:afProperties** automated forms conversion 서비스를 사용하여 생성된 적응형 양식 필드에 대한 다음 추가 속성을 정의하는 메타 모델의 속성:

<table> 
 <tbody> 
  <tr> 
   <th><strong>속성 이름</strong></th> 
   <th><strong>설명</strong></th> 
  </tr> 
  <tr> 
   <td><p>다중 라인</p></td> 
   <td> 
    <p>multiLine 속성은 변환 후 소스 양식 필드를 적응형 양식의 여러 줄 필드로 변환합니다. 자세한 내용은 <strong>문자열 필드를 여러 줄 필드로 변환</strong> 위치: <a href="#custommetamodelexamples">사용자 지정 메타 모델 예</a></p> </td> 
  </tr>
  <td><p>필수</p></td> 
   <td> 
    <p>필수 속성은 변환 후 적응형 양식 필드에 대한 입력을 필수로 설정합니다.<br>자세한 내용은 <strong>적응형 양식 필드에 유효성 검사 추가</strong> 위치: <a href="#custommetamodelexamples">사용자 지정 메타 모델 예</a></p>
    </td> 
  </tr>
  <td><p>jcr:title</p></td> 
   <td> 
    <p>제목 JSON 스키마 속성이 있는 jcr:title 속성을 사용하면 전환 후 적응형 양식 필드의 레이블을 수정할 수 있습니다.<br>자세한 내용은 <strong>양식 필드의 레이블 수정</strong> 위치: <a href="#custommetamodelexamples">사용자 지정 메타 모델 예</a><br>다음을 참조하십시오 <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/adaptive-form-json-schema-form-model.html" target="_blank">JSON 스키마를 사용하여 적응형 양식 만들기</a> json 스키마를 사용하여 적응형 양식 필드에 적용할 수 있는 추가 속성에 대한 정보입니다.</p>
    <p></p></td> 
  </tr>
  <td><p>sling:resourceType 및 guideNodeClass</p></td> 
   <td> 
    <p>sling:resourceType 및 guideNodeClass 속성을 사용하면 양식 필드를 해당 적응형 양식 구성 요소에 매핑할 수 있습니다.<br>자세한 내용은 <strong>적응형 양식에서 양식 필드를 다중 선택 확인란으로 변환</strong> 및 <strong>텍스트 필드를 적응형 양식의 드롭다운 목록으로 변환</strong> 위치: <a href="#custommetamodelexamples">사용자 지정 메타 모델 예</a></p> </td> 
  </tr>
  <td><p>validatePictureSection</p></td> 
   <td> 
    <p>validatePictureClause 속성은 변환 후 적응형 양식 필드에 허용되는 형식에 대한 유효성 검사를 설정합니다.<br>자세한 내용은 <strong>적응형 양식 필드에 유효성 검사 추가</strong> 위치: <a href="#custommetamodelexamples">사용자 지정 메타 모델 예</p> </td> 
  </tr>
 </tbody> 
</table>

## 자국어로 사용자 지정 메타모델 만들기{#language-specific-meta-model}

언어별 메타 모델을 만들 수 있습니다. 이러한 메타 모델은 원하는 언어로 매핑 규칙을 만드는 데 도움이 됩니다. Automated forms conversion 서비스를 사용하면 다음 언어로 메타 모델을 만들 수 있습니다.

* 영어(en)
* 프랑스어(fr)
* 독일어(de)
* 스페인어(es)
* 이탈리아어(it)
* 포르투갈어(pt-br)

추가 *aem:Language* 메타 태그는 상위 메타 모델로 태그를 지정하여 해당 언어를 지정합니다. 예를 들어

```JSON
"metaTags": {
        "aem:Language": "fr"
    }
```

언어가 지정되지 않은 경우 서비스는 메타 모델이 영어로 된 것으로 간주합니다.

### 언어별 메타 모델 만들기 고려 사항

* 모든 키의 이름이 영어로 되어 있는지 확인합니다. 예를 들어 emailAddress입니다.
* 모든 엔티티 참조와 모든 ID 키의 사전 정의된 값이 ASCII 문자로만 구성되는지 확인합니다. 예를 들어 &quot;id&quot;: &quot;ContactPoint&quot; / &quot;$ref&quot;: &quot;#ContactPoint&quot;입니다.
* 다음 키에 해당하는 모든 값이 지정된 메타 모델 언어로 되어 있는지 확인합니다.
   * aem:affKeyword
   * 제목
   * 설명
   * enumNames
   * 간단한 설명
   * validatePictureSectionMessage

  예를 들어 메타 모델의 언어가 프랑스어(&quot;aem:Language&quot;: &quot;fr&quot;)인 경우 모든 설명 및 메시지가 프랑스어로 되어 있는지 확인합니다.

* 모두 확인 [JSON 스키마 속성](#jsonschemaproperties) 지원되는 값만 사용하십시오. 예를 들어, 유형 속성은 String, Number, Integer 및 Boolean의 선택된 값만 포괄할 수 있습니다.

다음 이미지에는 영어 메타 모델 및 해당 프랑스어 메타 모델의 예가 표시됩니다.

![](assets/language-specific-meta-model-comparison.png)

## 사용자 지정 메타 모델을 사용하여 적응형 양식 필드 수정 {#modify-adaptive-form-fields-using-custom-meta-model}

조직에는 기본 메타 모델에 나열된 패턴 및 유효성 검사 외에도 패턴 및 유효성 검사가 있을 수 있습니다. 기본 메타 모델을 확장하여 조직 고유의 패턴, 검증 및 엔티티를 추가할 수 있습니다. Automated forms conversion 서비스는 전환 중에 사용자 지정 메타 모델을 양식 필드에 적용합니다. 조직에 관련된 새 패턴, 유효성 검사 및 엔티티가 검색되면 메타 모델을 계속 업데이트할 수 있습니다.

Automated forms conversion 서비스는 다음 위치에 저장된 기본 메타 모델을 사용하여 변환 중 소스 양식 필드를 적응형 양식 필드에 매핑합니다.

http://&lt;server>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/metamodel/global.schema.json

하지만 폴더에 사용자 지정 메타 모델을 저장하고 전환 중에 사용자 지정 메타 모델을 사용하도록 전환 서비스 속성을 수정할 수 있습니다.

### 전환 중 사용자 지정 메타 모델 사용 {#use-custom-meta-model-during-conversion}

전환 중에 사용자 지정 메타 모델을 사용하려면 다음 단계를 수행하십시오.

1. 다음 위치에 폴더 만들기 **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** 폴더에 사용자 지정 메타 모델 JSON 스키마 파일을 업로드합니다.
1. 다음을 사용하여 전환 서비스 속성을 엽니다.

   **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion Configuration]** > **&lt;properties of=&quot;&quot; selected=&quot;&quot; configuration=&quot;&quot;>**

1. 다음에서 **[!UICONTROL Basic]** 탭에서 사용자 지정 메타 모델의 위치를 **[!UICONTROL Custom Meta-model]** 필드 및 탭 **[!UICONTROL Save & Close]**.
1. [전환 실행](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process) 변환 프로세스에 사용자 지정 메타 모델 적용

### 맞춤형 메타 모델 예제 {#custommetamodelexamples}

사용자 지정 메타 모델을 사용하여 적응형 양식 필드 속성을 수정하는 몇 가지 일반적인 예는 다음과 같습니다.

* 양식 필드의 레이블 수정
* 양식 필드 유형 수정
* 양식 필드에 도움말 텍스트 추가
* 양식 필드를 적응형 양식의 다중 선택 라디오 단추로 변환
* 양식 필드 형식 수정
* 적응형 양식 필드에 유효성 검사 추가
* 적응형 양식의 양식 필드를 드롭다운 목록 옵션으로 변환
* 드롭다운 목록에 추가 옵션 추가
* 문자열 필드를 여러 줄 필드로 변환

#### 양식 필드의 레이블 수정 {#modify-the-label-of-a-form-field}

**예:** 전환 후 양식의 은행 계좌 번호 레이블을 적응형 양식의 사용자 정의 계좌 번호로 수정합니다.

이 사용자 지정 메타 모델에서 전환 서비스는 **제목** 속성을 검색 키워드로 사용합니다. 검색 후 **은행 계좌 번호** 양식의 텍스트 변환 서비스는 텍스트를 **고객 계정 번호** 이(가) 포함된 문자열 **jcr:title** 의 속성 **aem:afProperties** 섹션.

```
{
  "numberfields": {
      "type": "number",
   "title": "Bank account number",
   "aem:afProperties" : {
    "jcr:title" : "Customer account number"
   }
   }
}
```

#### 양식 필드 유형 수정 {#modify-the-type-of-a-form-field}

**예**: 를 수정합니다. **은행 계좌 번호** 변환 전 양식의 텍스트 유형 필드 변환 후 적응형 양식의 숫자 유형 필드로 변환

이 사용자 지정 메타 모델에서 전환 서비스는 다음 내에서 텍스트를 사용합니다. **aem:affKeyword** 를 검색 키워드로 사용하십시오. 검색 후 **은행 계좌 번호** 양식의 텍스트에서 전환 서비스는 다음을 사용하여 필드를 숫자 유형으로 전환합니다. **유형** 속성.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"]
 }
}
```

#### 양식 필드에 도움말 텍스트 추가 {#add-help-text-to-a-form-field}

**예**: 도움말 텍스트를 다음에 추가 **은행 계좌 번호** 적응형 양식의 필드.

이 사용자 지정 메타 모델에서 전환 서비스는 다음 내에서 텍스트를 사용합니다. **aem:affKeyword** 를 검색 키워드로 사용하십시오. 검색 후 **은행 계좌 번호** 양식의 텍스트 전환 서비스는 다음을 사용하여 도움말 텍스트를 적응형 양식 필드에 추가합니다. **설명** 속성.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"],
   "description": "Specify your bank account number."
 }
}
```

#### 적응형 양식에서 양식 필드를 다중 선택 확인란으로 변환 {#convert-a-form-field-to-multiple-choice-check-boxes-in-the-adaptive-form}

**예**: 변환 **국가** 변환 전 양식의 문자열 유형 필드를 변환 후 적응형 양식의 확인란

이 사용자 지정 메타 모델에서 전환 서비스는 다음 내에서 텍스트를 사용합니다. **aem:affKeyword** 를 검색 키워드로 사용하십시오. 검색 후 **국가** 양식의 텍스트에서 변환 서비스는 다음을 사용하여 필드를 다음 확인란으로 변환합니다. **enum** 속성:

* 인도
* 잉글랜드
* 오스트레일리아
* 뉴질랜드

**sling:resourceType** 및 **guideNodeClass** 속성은 양식 필드를 확인란 적응형 양식 구성 요소에 매핑합니다.

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidecheckbox",
      "guideNodeClass": "guidecheckbox"
    }
  }
}
```

#### 양식 필드 형식 수정 {#modify-the-format-of-a-form-field}

**예**: 의 형식 수정 **이메일 주소** 필드를 전자 메일 형식으로 변환.

이 사용자 지정 메타 모델에서 전환 서비스는 다음 내에서 텍스트를 사용합니다. **aem:affKeyword** 를 검색 키워드로 사용하십시오. 검색 후 **이메일 주소** 양식의 텍스트 변환 서비스는 다음을 사용하여 필드를 이메일 형식으로 변환합니다. **형식** 속성.

```
{
   "additionalDetails" : {
      "aem:affKeyword": ["E-mail Address"],
       "type" : "string",
       "format" : "email"
  } 
}
```

#### 적응형 양식 필드에 유효성 검사 추가 {#add-validations-to-adaptive-form-fields}

**예 1:** 에 유효성 검사 추가 **우편 번호** 적응형 양식의 필드.

이 사용자 지정 메타 모델에서 전환 서비스는 다음 내에서 텍스트를 사용합니다. **aem:affKeyword** 를 검색 키워드로 사용하십시오. 검색 후 **우편 번호** 양식의 텍스트에서 전환 서비스는 다음을 사용하여 필드에 유효성 검사를 추가합니다. **validatePictureSection** 에 정의된 속성 **aem:afProperties** 섹션. 유효성 검사를 기반으로 **우편 번호** 변환 후 적응형 양식의 필드에는 6자가 포함되어야 합니다.

```
{
   "postalCode" : {
      "aem:affKeyword": ["Postal Code"],
      "type" : "string",
      "aem:afProperties" : {
        "validatePictureClause" : "\\d{6}"
      } 
   }
}
```

**예제 2:** 에 유효성 검사 추가 **은행 계좌 번호** 적응형 양식의 필드.

이 사용자 지정 메타 모델에서 전환 서비스는 다음 내에서 텍스트를 사용합니다. **aem:affKeyword** 를 검색 키워드로 사용하십시오. 검색 후 **은행 계좌 번호** 양식의 텍스트에서 전환 서비스는 다음을 사용하여 필드에 유효성 검사를 추가합니다. **필수** 에 정의된 속성 **aem:afProperties** 섹션. 유효성 검사를 기반으로 **은행 계좌 번호** 전환 후 양식을 제출하기 전의 필드입니다.

```
{
  "numberfields": {
      "type": "number",
      "aem:affKeyword": ["Bank account number"],
   "aem:afProperties" : {
        "mandatory": "true"
      }   
   }
}
```

#### 텍스트 필드를 적응형 양식의 드롭다운 목록으로 변환 {#convert-a-text-field-to-drop-down-list-in-the-adaptive-form}

**예**: 변환 **국가** 전환 전 양식의 문자열 유형 필드입니다. 전환 후 적응형 양식의 드롭다운 옵션입니다.

이 사용자 지정 메타 모델에서 전환 서비스는 다음 내에서 텍스트를 사용합니다. **aem:affKeyword** 를 검색 키워드로 사용하십시오. 검색 후 **국가** 양식의 텍스트에서 전환 서비스는 다음을 사용하여 필드를 다음과 같은 드롭다운 목록 옵션으로 전환합니다. **enum** 속성:

* 인도
* 잉글랜드
* 오스트레일리아
* 뉴질랜드

**sling:resourceType** 및 **guideNodeClass** 속성은 양식 필드를 드롭다운 적응형 양식 구성 요소에 매핑합니다.

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidedropdownlist",
      "guideNodeClass": "guideDropDownlist"
    }
  }
}
```

#### 드롭다운 목록에 추가 옵션 추가 {#add-additional-options-to-the-drop-down-list}

**예:** 추가 **스리랑카** 사용자 지정 메타 모델을 사용하여 기존 드롭다운 목록에 대한 추가 옵션으로

추가 옵션을 추가하려면 **enum** 속성을 새 옵션과 함께 사용합니다. 이 예에서 **enum** 속성 포함 **스리랑카** 추가 옵션입니다. 다음에 나열된 값: **enum** 드롭다운 목록에 속성이 표시됩니다.

```
{
"title": {
    "aem:affKeyword": [
      "country"
    ],
    "type" : "string",
    "enum": [
      "India",
      "England",
      "Australia",
      "New Zealand",
   "Sri Lanka"
    ],
    "aem:afProperties": {
      "sling:resourceType": "fd/af/components/guidecheckbox",
      "guideNodeClass": "guidecheckbox"
    }
  }
}
```

#### 문자열 필드를 여러 줄 필드로 변환 {#convert-a-string-field-to-a-multi-line-field}

**예:** 변환 **주소** 변환 후 양식의 여러 줄 필드에 대한 문자열 유형의 필드입니다.

이 사용자 지정 메타 모델에서 전환 서비스는 다음 내에서 텍스트를 사용합니다. **aem:affKeyword** 를 검색 키워드로 사용하십시오. 검색 후 **주소** 양식의 텍스트에서 이 서비스는 다음을 사용하여 텍스트 필드를 여러 줄 필드로 변환합니다. **다중 라인** 에 정의된 속성 **aem:afProperties** 섹션.

```
{
 "multiLine" : {
   "aem:affKeyword": [
      "Address"
    ],
    "type" : "string",
    "aem:afProperties": {
      "multiLine": "true"
    }
  }
}
```