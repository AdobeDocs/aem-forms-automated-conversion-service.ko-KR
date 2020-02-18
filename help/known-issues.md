---
title: 알려진 문제
seo-title: 알려진 문제
description: 자동화된 양식 변환 서비스의 알려진 문제 및 제한 사항
seo-description: AEM Forms Automated Forms Conversion 서비스를 사용하기 전에 서비스의 알려진 문제와 제한 사항에 대해 알아봅니다.
uuid: b1dc661b-ccd3-457f-acbb-4bd25db86e1e
topic-tags: introduction
discoiquuid: 9cd2363c-47a0-46e9-98cd-1fe088b9cd6e
translation-type: tm+mt
source-git-commit: 2fcceb45d9be4297fcd923f5a17c7b593294e855

---

# 알려진 문제 및 제한 사항 {#known-issues-limitations}

AEM Forms Automated Forms Conversion Service를 사용하기 전에 다음의 알려진 문제 및 제한 사항을 검토하십시오.

## 알려진 문제 {#known-issues}

* 변환할 양식이 들어 있는 폴더에는 총 15개 이상의 양식과 50개 페이지가 있으면 안 됩니다. 소스 폴더 크기는 10MB를 초과할 수 없습니다. 소스 폴더에 하위 폴더를 만들지 마십시오.
* 일부 양식 객체는 사람의 눈에 쉽게 보이기는 하지만 서비스에 [대해 식별하기](styles-and-pattern-considerations-and-best-practices.md)어렵습니다. 검토 [및 수정 편집기를](review-correct-ui-edited.md) 사용하여 이러한 양식 객체를 식별하고 변환합니다.
* 검토 및 수정 편집기:

   * 실행 취소 작업이 없습니다. [저장] 단추를 누르면 변경 사항이 영구적으로 저장됩니다.
   * XFA 기반 양식에 대해 반복 가능한 패널을 지원하지 않습니다.
   * 검토 및 수정 편집기를 사용하여 표의 목록을 수정하는 경우 행 너비가 자동으로 조정되지 않고 텍스트가 표의 다음 행으로 번질 수 있습니다.
   * 이 **[!UICONTROL Auto-detect multi-column layout from input forms]** 기능은 검토 및 수정 편집기와 양식 조각에서 작동하지 않습니다.

* XFA 기반 양식의 경우:
   * XFA 기반 양식에서 조각을 추출하는 것은 지원되지 않습니다.
   * XFA 스크립트는 지원되지 않습니다. 예를 들어 드롭다운 구성 요소에 대한 값을 자동으로 생성하기 위한 스크립트입니다.
   * 메타 모델은 선택 그룹에 대해 작동하지 않습니다.
   * 단일 문자가 있는 선택 그룹 옵션이 식별되지 않음
   * 소스 문서가 동적 XFA(.XDP)이고 적응형 형식으로 [XFA 속성의 동작을](https://helpx.adobe.com/experience-manager/6-5/forms/using/xfa-api-supported-in-adaptive-form.html#supportedxfaelementsandtheirmappinginadaptiveformsbr)정의하면 소스 문서의 존재 속성이 적용되지 않습니다. 예를 들어 소스 문서의 필드는 숨김으로 표시되고 스크립트에서는 필드를 표시한 다음 해당 필드는 출력 적응형 양식에 계속 표시됩니다.

* 생성된 적응형 **양식에** AcroForm을 기록 문서로 사용(DoR) 옵션을 사용하는 경우 다음을 고려하십시오.

<table>
    <tr>
        <td>복합 텍스트 필드에 대해 바인딩 및 데이터가 손실됩니다. 복합 텍스트 필드에는 여러 텍스트 상자가 서로 정렬되어 있습니다. 예를 들어 AcroForm에서는 신용 카드 번호가 여러 텍스트 상자에 분할되고 각 텍스트 상자에 별도의 바인딩이 있습니다. AcroForm이 응용 양식으로 변환되면 변환된 응용 양식에는 모든 텍스트 상자에 대한 단일 바인딩이 있습니다. 해결 방법으로 AcroForm을 응용 양식으로 변환하기 전에 AcroForm을 수정하여 단일 텍스트 상자를 사용하여 신용 카드 번호를 수락합니다.</td>
        <td><img  src="assets/creditCard_Composite.png"/>                                                            </td>
    </tr>
    <tr>
        <td>복합 날짜 필드에 대해 바인딩 및 데이터가 손실됩니다. 복합 날짜 필드는 세 개의 서로 다른 필드로 구성됩니다. 예를 들어 AcroForm의 생년월일 필드는 세 개의 개별 필드로 분할됩니다. 적응형 양식은 최신 피커 구성 요소를 제공합니다. AcroForm을 적응형 양식으로 변환하기 전에 적응형 양식의 날짜 선택기 구성 요소를 사용하려면 AcroForm을 수정하여 단일 날짜 필드를 사용하십시오.</td>
        <td><img  src="assets/CompositeDateField.png"/></td>
    </tr>
    <tr>
        <td>확인란 크기가 추가 텍스트보다 큰 경우 확인란이 검색되지 않고 AcroForm의 바인딩이 손실됩니다. AcroForm을 수정하여 확인란 크기를 추가 텍스트보다 작게 만듭니다.</td>
        <td><img  src="assets/large-text-box.png"/><br/><img  src="assets/small-text-box.png"/></td>
    </tr>
    <tr>
        <td>입력 필드가 해당 텍스트 필드에 정렬되지 않으면 입력 필드가 검색되지 않습니다.  </td>
        <td><img  src="assets/non-alingned-fields.png"/></td>
    </tr>
    <tr >
        <td>서비스는 AcroForm의 모든 확인란을 개별 선택 그룹으로 변환합니다. AcroForm을 사용하여 바인딩을 보존하기 위해 별도의 선택 그룹이 생성됩니다. 선택 그룹을 적응형 양식으로 병합하지 마십시오. 바인딩이 손실됩니다. 선택 그룹을 병합하는 경우 양식을 다시 변환하여 손실된 바인딩을 다시 검색합니다. </td>
        <td></td>
    </tr>
    <tr >
        <td>일부 표의 바운스 수는 자동으로 생성된 기록 문서(DoR)에서 페이지 밖으로 확장됩니다. </td>
        <td></td>
    </tr>
</table>

## 제한 사항 {#limitations}

* 복잡한 동적 레이아웃이 있는 PDF 양식, 점선 외곽선, 채워진 필드 또는 컬러 필드는 지원되지 않습니다.
* 이미지 내의 이미지와 텍스트는 식별되지 않습니다. 변환된 양식에 수동으로 이미지 추가
* 아트워크 XDP 문서는 지원되지 않습니다.
* 15페이지보다 큰 PDF 양식은 지원되지 않습니다.
* 암호화되고 암호로 보호되며 보안 문서는 변환되지 않습니다. 변환을 실행하기 전에 암호화 또는 암호를 제거합니다.
* 테두리 없는 표, 중첩된 표, 색상이 있는 표 및 자리 표시자 값이 있는 표와 같은 복잡한 표는 지원되지 않습니다. 적응형 양식 편집기를 사용하여 변환 후 복잡한 표를 추가하거나 수정할 수 있습니다. 빈 필드, 적절한 헤더 및 명확한 경계와 함께 단순 테이블만 지원됩니다.
* 이 서비스는 영어 양식만 응용 양식으로 변환합니다. AEM 번역 워크플로우를 [사용하여 변환된 적응형 양식을 다른 언어로 번역할 수](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)있습니다.
* AEM 6.4 양식은 입력 양식의 다중 열 레이아웃에 대한 자동 탐지를 지원하지 않습니다.
