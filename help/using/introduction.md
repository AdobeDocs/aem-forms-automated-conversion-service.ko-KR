---
title: AFCS(automated forms conversion 서비스) 소개
description: 인쇄 양식을 적응형 양식으로 신속하게 전환
solution: Experience Manager Forms
feature: Adaptive Forms, Foundation Components
topic: Administration
topic-tags: forms
role: Admin, Developer
level: Beginner, Intermediate
exl-id: edabeac8-cd66-48ca-a99f-9643a1c184cf
source-git-commit: c2392932d1e29876f7a11bd856e770b8f7ce3181
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 58%

---

# Automated forms conversion 서비스(AFCS) {#introduction-to-automated-forms-conversion-service}

Automated forms conversion 서비스(AFCS)는 PDF forms을 적응형 양식으로 자동 전환하여 데이터 캡처 환경을 디지털화하고 현대화하는 데 도움이 됩니다. Adobe Sensei 기반의 이 서비스는 PDF 양식을 장치 친화적인 반응형 및 HTML5 기반의 적응형 양식으로 자동 전환합니다. PDF 양식 및 XFA에 대한 기존 투자를 활용하는 동시에 전환 중에 적절한 유효성 검사, 스타일 지정 및 레이아웃을 적응형 양식 필드에 적용합니다. 이 서비스는 다음과 같은 이점을 제공합니다.

* 인쇄 양식을 적응형 양식으로 전환하는 데 필요한 수작업 절감
* 전환 중 패턴 및 적절한 유효성 검사 적용
* 전환 중 기록 문서 생성
* 일반적으로 발생하는 필드를 재사용 가능한 양식 조각으로 그룹화
* 전환 중 Adobe Analytics 사용

![간단합니다. 소스 양식을 제공하고 모든 것을 우리에게 맡기십시오. 멋진 적응형 양식을 제공합니다. 언제든지 원하는 대로 결과물을 수정하실 수 있습니다. ](assets/pdf-to-adaptive-form-gitx50.gif)

## 온보딩 {#onboarding}

이 서비스는 AEM 6.4 Forms 및 AEM 6.5 Forms On-Premise 기간제 고객과 Adobe 관리 서비스 기업 고객에게 무료로 제공됩니다. Adobe 영업팀 또는 Adobe 담당자에게 문의하여 서비스 액세스를 요청할 수 있습니다. 이 서비스는 AEM Forms as a Cloud Service 고객도 무료로 이용할 수 있으며, 사전 활성화도 가능합니다.

Adobe는 조직에 대한 액세스 권한을 활성화하고 조직의 책임자로 지정된 사람에게 필요한 권한을 제공합니다. 책임자는 해당 서비스에 연결할 조직의 AEM Forms 개발자(사용자)에게 액세스 권한을 부여할 수 있습니다. 자세한 내용은 [자동 양식 전환 서비스 구성](configure-service.md)을 참조하십시오.

## 지원되는 PDF forms 및 언어 {#supported-languages-and-pdf-forms}

이 서비스는 비대화형 PDF 양식, AcroForms로 알려진 Adobe Acrobat으로 만든 양식, AEM Forms 또는 Adobe LiveCycle을 사용하여 만든 XFA 기반 양식을 지원합니다.

이 서비스는 Adobe Sign 지원 PDF forms도 지원합니다. 소스 PDF form에 Adobe Sign 텍스트 태그가 포함된 경우 서비스는 전환 중에 모든 Adobe Sign 관련 정보를 유지하고 소스 PDF의 서명자 정보를 해당 적응형 양식 필드와 연결합니다. 이 기능은 AcroForms에서만 사용할 수 있습니다.

이 서비스는 영어, 프랑스어, 독일어, 스페인어, 이탈리아어 및 포르투갈어 언어 양식을 적응형 양식으로 전환할 수 있습니다. [AEM 번역 워크플로](https://helpx.adobe.com/kr/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)를 사용하여 생성된 적응형 양식을 다른 언어로 번역할 수도 있습니다.

## 전환 워크플로우  {#conversion-workflow}

AFCS(automated forms conversion 서비스)는 Adobe 클라우드에서 실행됩니다. AEM 인스턴스를 서비스에 연결하고, 양식을 AEM 인스턴스에 업로드하고, 전환을 시작합니다. 전체 전환 프로세스는 다음과 같습니다.

![워크플로우](assets/conversion-workflow.png)

### 1. 환경 설정 {#set-up-the-environment}

AFCS(automated forms conversion 서비스)는 Adobe 클라우드에서 실행됩니다. [조직의 Adobe I/O 계정을 구성하고 로컬 AEM 인스턴스](configure-service.md)를 Adobe Cloud에서 실행되는 전환 서비스에 연결합니다.

### 2. PDF forms을 적응형 양식으로 전환 {#use-the-conversion-service}

AEM Forms 환경이 구성된 후 PDF 양식을 적응형 양식으로 전환하려면 [PDF 양식을 AEM 인스턴스로 업로드](convert-existing-forms-to-adaptive-forms.md)하고 [전환을 시작](convert-existing-forms-to-adaptive-forms.md#run-the-conversion)합니다. 양식을 업로드하기 전에 다음을 고려하십시오.

* 보안 양식을 업로드하지 마십시오. 이 서비스는 암호로 보호되거나 암호화된 양식을 전환하지 않습니다.
* 스캔, 컬러, 채워진 양식 및 영어, 프랑스어, 독일어, 스페인어, 이탈리아어 및 포르투갈어가 아닌 다른 언어로 양식을 업로드하지 마십시오. 이러한 양식은 지원되지 않습니다.
* 파일 이름에 공백이 있는 PDF 양식을 업로드하지 마십시오.
* [PDF 포트폴리오](https://helpx.adobe.com/kr/acrobat/using/overview-pdf-portfolios.html)를 업로드하지 마십시오. 이 서비스는 PDF Portfolio을 적응형 양식으로 전환하지 않습니다.
* [모범 사례 및 고려 사항](styles-and-pattern-considerations-and-best-practices.md) 문서에 설명된 제안 변경 사항을 PDF 양식에 적용하십시오.
* [알려진 문제](known-issues.md) 문서를 참조하여 문제를 방지하십시오.

### 3. 전환된 양식 검토 {#review-converted-forms}

실제 양식에는 AI/ML 기반 감지 로직에 의해 정확하게 캡처되지 않을 수 있는 필드 레이아웃, 이름 지정 또는 암시적 제안 측면에서 복잡한 데이터 캡처 요구 사항이 있을 수 있습니다. 자동 전환이 완료되면 [검토 및 수정 편집기](review-correct-ui-edited.md)를 사용하여 전환된 양식을 검토하고 필요한 업데이트를 수행하여 원하는 경험에 가까운 향상된 결과물을 생성할 수 있습니다. 필요한 변경 작업을 수행한 후 전환을 위해 양식을 다시 보냅니다.

자동 전환에 소요되는 시간은 입력 양식 크기, 양식의 복잡성, 서비스 처리 대기열 대출 등 다양한 요인에 따라 다릅니다. 사용자는 폴더/파일의 상태 표시기를 통해 정기적으로 진행 상황에 대한 알림을 받습니다. 전환이 완료되면 구성된 전자 메일 주소로도 전자 메일 알림을 보냅니다.
