---
title: 새로운 기능 릴리스 정보 - 자동 양식 전환 서비스
description: 자동 양식 전환 서비스의 최신 기능 및 버그 수정에 대한 정보
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: forms
role: Admin, Developer
level: Beginner, Intermediate
exl-id: fccafbc9-28c1-4736-922c-24d675b25213
source-git-commit: e95b4ed35f27f920b26c05f3398529f825948f1f
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 63%

---

# 릴리스 정보

자동 양식 전환 서비스는 지속적으로 개선됩니다. 최신 개선 사항을 확인하려면 이 페이지를 정기적으로 방문하십시오. 이 페이지에서는 다음에 대한 정보를 제공합니다.

* 빠른 액세스
* 최신 릴리스
* 새로운 기능
* 개선 사항
* 버그 수정
* 사용하지 않는 기능
* 특별 지침
* 향후 변경 계획

## 2022년 2월 24일 (AFC-2022.02.0) {#feb-2022}

* [섹션을 조각으로 자동 변환](convert-existing-forms-to-adaptive-forms.md)하여 변환된 양식의 렌더링 속도를 개선하고 적응형 양식 편집기에서 보다 쉽게 대용량 양식을 로드할 수 있는 기능이 추가되었습니다.

## 2021년 8월 29일 (AFC-2021.08.0) {#aug-2021}

* 이탈리아어 및 포르투갈어 언어로 된 PDF forms을 적응형 양식으로 전환하는 기능이 추가되었습니다.

## 2021년 7월 29일 (AFC-2021.07.2) {#july-2021}

* 프랑스어, 독일어 및 스페인어로 된 PDF 양식을 적응형 양식으로 전환하는 기능이 추가되었습니다.

## 2021년 6월 24일 (AFC-2021.06.2) {#june-2021}

### 개선 사항 {#june-2021-improvements}

소스 양식에서 논리 섹션을 자동으로 감지하고 이를 해당 적응형 양식 패널로 변환하는 정확도가 개선되었습니다.

## 2021년 3월 3일 (AFC-2021.02.2) {#mar-2021}

### 개선 사항 {#march-2021-improvements}

소스 양식을 적응형 양식으로 전환하는 동안 양식 콘텐츠를 선택 그룹 및 필드로 구성하는 기능이 개선되었습니다.

## 2021년 2월 2일 (AFC-2021.01.2) {#feb-2021}

### 개선 사항 {#feb-2021-improvements}

소스 양식을 적응형 양식으로 전환하는 동안 양식 콘텐츠를 패널로 구성하고 패널의 제목을 생성하는 기능이 개선되었습니다.

## 2020년 7월 16일 (AFC-2020.07.2) {#jul-2020}

### 새로운 기능 {#whats-new-jul-2020-}

색상이 적용된 PDF forms를 적응형 양식으로 전환하는 기능이 추가되었습니다.

### 개선 사항 {#jul-2020-improvements}

텍스트, 양식 및 선택 그룹 필드를 해당 적응형 양식 구성 요소로 자동 변환하는 기능이 향상되었습니다.

## 2020년 3월 20일(AFC-2020.03.1) {#mar-2020}

### 빠른 액세스 {#early-access}

**양식에서 논리 섹션 자동 감지**

기본적으로 이 서비스를 통해 PDF 양식의 각 페이지마다 별도의 최상위 패널을 만들 수 있습니다. 이제 **[!UICONTROL Auto-detect logical sections]** 옵션을 사용하여 페이지 레벨 패널(페이지 번호 기반 패널)을 삭제하고 논리 패널만 만들 수 있습니다. 또한 이전 논리 섹션이 포함된 어떤 섹션에도 속하지 않는 필드와 두 장의 인접한 페이지에 걸쳐 있는 논리 섹션의 필드를 단일 논리 섹션으로 병합할 수 있습니다. 예를 들어, 논리 섹션의 일부 필드가 1페이지의 끝에 있고 일부는 2페이지의 시작에 있는 경우 그러한 모든 필드는 단일 논리 섹션으로 병합됩니다.

### 개선 사항 {#mar-2020-improvements}

**목록 검색 개선**

이제 보다 효과적으로 글머리 기호 및 번호 매기기 목록을 검색할 수 있습니다.

### 특별 지침 {#special-instructions}

**자동 양식 전환 서비스 커넥터 패키지 설치**

AFC-2020.03.1 릴리스에서 제공되는 최신 기능 및 개선 사항을 사용하려면 커넥터 패키지 1.1.38 이상이 필요합니다.

자동 양식 전환 서비스 환경을 이미 실행 중인 경우 전환 서비스의 최신 기능을 사용하려면 최신 서비스 팩, 최신 AEM Forms 추가 기능 패키지, 최신 커넥터 패키지를 차례대로 설치하십시오. 자세한 지침은 [자동 양식 전환 서비스 구성](configure-service.md) 문서를 참조하십시오.
