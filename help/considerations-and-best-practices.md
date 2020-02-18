---
title: '[게시 안 함] 우수 사례 및 고려 사항 '
seo-title: '[게시 안 함] 우수 사례 및 고려 사항 '
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: c2821264-39e2-44f8-b234-835c46f33fd5
topic-tags: introduction
discoiquuid: b786e40a-202e-4e17-a2f5-1f77c46538c2
privatebeta: true
index: false
translation-type: tm+mt
source-git-commit: afe461baa5bcfc1106c16aae2d6a9c839ea675e8

---


# [우수 사례] 및 고려 사항 게시 안 함 {#do-not-publish-best-practices-and-considerations}

AEM Forms 자동 전환 서비스는 PDF 양식을 적응형 양식으로 변환합니다. 이 서비스는 인공 지능과 머신 러닝 알고리즘을 사용하여 소스 양식의 레이아웃과 필드를 파악합니다. 모든 머신 러닝 서비스는 소스 데이터를 지속적으로 학습하고 모든 이탈을 통해 향상된 출력을 생성합니다. 이러한 서비스는 인간처럼 경험에서 배운다.

자동화된 양식 변환 서비스는 다양한 양식을 기반으로 교육됩니다. 소스 양식의 필드를 손쉽게 식별하고 적응형 양식을 만듭니다. 그러나 PDF 양식에는 사람의 눈으로 쉽게 볼 수 있지만 서비스를 이해하기 어려운 일부 필드와 스타일이 있습니다. 서비스는 일부 필드 또는 스타일에 적용 가능한 필드 유형이나 패널과 다르게 지정할 수 있습니다. 이러한 모든 필드 및 스타일 패턴은 아래에 나열되어 있습니다.

서비스는 소스 데이터를 계속 학습할 때 이러한 패턴에 올바른 필드나 패널을 찾아 지정하기 시작합니다. 당분간은 검토 및 수정 [편집기를 사용하여](review-correct-ui-edited.md) 이러한 문제를 수정할 수 있습니다. 문제를 수정하거나 더 자세히 읽기 전에 [적응형 양식 구성 요소에](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html)익숙해지십시오.

## 일반 {#general}

<!--
Comment Type: draft

<ul>
<li>Service does not convert filled PDF forms to adaptive form. Use empty adaptive forms.Service does not convert colored PDF forms to adaptive form. Use black and white or grayscale adaptive forms. <br /> </li>
<li>Service does not convert filled PDF forms to adaptive form. Use empty adaptive forms.</li>
<li>Service does not support scanned forms. Do not use scanned forms. </li>
<li>Service can fail to recognize text and fields in a dense form. Increase the width between text and fields of a dense form before starting the conversion.</li>
<li>Service does not extract images. Manually add images to converted forms.</li>
<li>Service does not extract text present within an image. Manually add text to the adaptive form.</li>
</ul>
-->

<table border="1" cellpadding="1" cellspacing="0" style="border-collapse: separate; border-spacing: 0px;" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">알려진 패턴 및 해상도</td> 
   <td width="70%">예</td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>서비스는 컬러 PDF 양식을 적응형 양식으로 변환하지 않습니다.</p> <p> </p> <p><strong>해상도</strong></p> <p>흑백 또는 회색 음영 PDF 양식을 사용할 수 있습니다. </p> </td> 
   <td style="text-align: left;"> <img src="assets/coloured-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>작성된 PDF 양식을 적응형 양식으로 변환하지 않습니다.</p> <p> </p> <p><strong>해상도</strong></p> <p>빈 적응형 양식을 사용합니다.</p> </td> 
   <td style="text-align: left;"><img src="assets/pre-filled-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>서비스가 고밀도 양식의 텍스트와 필드를 인식하지 못할 수 있습니다.</p> <p> </p> <p><strong>해상도</strong></p> <p>변환을 시작하기 전에 덴스 양식의 텍스트와 필드 사이의 너비를 늘립니다.</p> </td> 
   <td style="text-align: left;"><img src="assets/dense%20form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>서비스가 스캔한 양식을 지원하지 않습니다.</p> <p> </p> <p><strong>해상도</strong></p> <p>스캔한 양식을 사용하지 마십시오. </p> </td> 
   <td><img src="assets/scanned-form.jpg" /></td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>서비스는 이미지 내에서 이미지와 텍스트를 추출하지 않습니다. </p> <p> </p> <p><strong>해상도</strong></p> <p>변환된 양식에 이미지 또는 텍스트를 수동으로 추가할 수 있습니다.</p> </td> 
   <td><img src="assets/image-in-adaptive-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>점선 또는 비투명 경계와 테두리가 있는 표는 변환되지 않습니다.</p> <p><strong>해상도</strong></p> <p>명확한 경계와 테두리가 있는 표를 사용합니다. 지원됨.</p> </td> 
   <td><img src="assets/border-less-tables.png" /></td> 
  </tr>
 </tbody>
</table>

## 선택 그룹 {#choice-group}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">패턴</td> 
   <td width="70%">예</td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>상자 또는 원이 아닌 모양이 있는 선택 그룹 옵션은 해당 적응형 양식 구성 요소로 변환되지 않습니다. </p> <p> </p> <p><strong>해상도</strong></p> <p>선택 옵션 모양을 상자 또는 원으로 변경하거나 검토 및 수정 편집기를 사용하여 모양을 식별합니다.</p> </td> 
   <td><img src="assets/shaded-box-patterns.png" /> </td> 
  </tr>
 </tbody>
</table>

## 양식 필드 {#form-fields}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">패턴</td> 
   <td width="70%">예</td> 
  </tr>
  <tr>
   <td width="25%"><p><strong>패턴</strong></p> <p>서비스는 테두리를 지우지 않고 필드를 식별하지 않습니다.</p> <p> </p> <p><strong>해상도</strong></p> <p>검토 및 수정 편집기를 사용하여 이러한 필드를 식별합니다.</p> <p> </p> <p> </p> </td> 
   <td width="50%"><br /> <img src="assets/fields-without-clear-borders.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>서비스는 캡션이 있는 일부 양식 필드를 맨 아래 또는 오른쪽 식별되지 않은 상태로 둡니다.</p> <p> </p> <p><strong>해상도</strong></p> <p>검토 및 수정 편집기를 사용하여 해당 필드 식별</p> </td> 
   <td><br /> <img src="assets/forms-with-clear-borders-scale.png" /><br /> </td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>서비스는 서로 매우 가깝게 배치되거나 테두리가 지워지지 않은 일부 양식 필드에 잘못된 유형을 병합하거나 할당합니다. </p> <p> </p> <p><strong>해상도</strong></p> <p>검토 및 수정 편집기를 사용하여 이러한 필드를 식별합니다.</p> </td> 
   <td><img src="assets/forms-with-fields-placed-nearby.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>서비스는 멀리 떨어져 있는 캡션이나 캡션과 입력 필드 사이에 있는 점선이 있는 필드를 인식하지 못할 수 있습니다.</p> <p> </p> <p><strong>해상도</strong></p> <p>경계가 분명한 양식 필드를 사용하거나 검토 및 수정 편집기를 사용하여 이러한 문제를 수정할 수 있습니다.</p> </td> 
   <td><img src="assets/form-fields-with-far-away-captions.png" /></td> 
  </tr>
 </tbody>
</table>

## 목록 {#lists}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">패턴</td> 
   <td width="70%">예</td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>양식 필드가 포함된 목록은 병합되거나 해당 적응형 양식 구성 요소로 변환되지 않습니다.</p> <p><strong>해상도</strong></p> <p>경계가 분명한 양식 필드를 사용하거나 검토 및 수정 편집기를 사용하여 이러한 문제를 수정할 수 있습니다.</p> </td> 
   <td><img src="assets/lists-with-fields.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>서비스에서 몇 개의 중첩된 목록을 식별할 수 없음</p> <p> </p> <p><strong>해상도</strong></p> <p>검토 및 수정 편집기를 사용하여 이러한 문제를 수정할 수 있습니다.</p> </td> 
   <td><img src="assets/nested-lists.png" /> </td> 
  </tr>
  <tr>
   <td><p><strong>패턴</strong></p> <p>서비스는 선택 그룹이 포함된 일부 목록을 서로 병합합니다.</p> <p><strong>해상도</strong></p> <p>검토 및 수정 편집기를 사용하여 이러한 문제를 수정할 수 있습니다.</p> </td> 
   <td><img src="assets/lists-containing-choice-groups.png" /> </td> 
  </tr>
 </tbody>
</table>

<!--
Comment Type: draft

<h3>Choice groups</h3>
-->

<!--
Comment Type: draft

<ul>
<li>Lists with form fields, nested lists, and nested choice groups are not supported.</li>
<li>Form fields with captions at bottom or right are not supported.</li>
<li>Form fiields without bordes are not supported.</li>
<li>Hidden form fields are not supported.</li>
<li>Button in PDF forms are not converted to adaptive form buttons.<br /> </li>
<li>Tables with clear explicit boundaries and borders are supported.</li>
<li>Fields with far away captions are not supported.<br /> </li>
<li>Choice groups with only box or circle shaped selectors are supported. </li>
</ul>
-->
