---
title: '&lt;formRegion&gt; elemento (desenvolvimento do Office no Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 86aa6b715a99c962a2f0fd627dd6d3fb7618108a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987687"
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;formRegion&gt; elemento (desenvolvimento do Office no Visual Studio)
  O `formRegion` elemento o `vstov4` namespace identifica uma região de formulário do Outlook do Microsoft Office que está associada com um suplemento do VSTO.

## <a name="syntax"></a>Sintaxe

```xml
<formRegion
  name>
  <messageClass
    name/>
</formRegion>
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `formRegion` elemento o `vstov4` namespace identifica uma região de formulário que está associada com um suplemento do VSTO do Outlook. É necessária apenas para Outlook suplementos do VSTO que incluem regiões de formulário.

 Pode haver vários `formRegion` elementos definidos dentro de um `formRegions` elemento para um único suplemento VSTO.

 O `formRegion` elemento tem o seguinte atributo.

|Atributo|Descrição|
|---------------|-----------------|
|`name`|Necessário. Identifica o nome da região de formulário.|

 O `formRegion` elemento tem os seguintes elementos filho.

### <a name="messageclass"></a>messageClass
 O `messageClass` elemento identifica o formulário do Outlook que está associado com a região do formulário.

 O `messageClass` elemento tem o seguinte atributo.

|Atributo|Descrição|
|---------------|-----------------|
|`name`|Necessário. Identifica o formulário que está associado com a região do formulário.|

## <a name="example"></a>Exemplo
 O exemplo de código a seguir ilustra uma `formRegion` elemento em um manifesto de aplicativo para um Add-in do VSTO do Outlook implantado usando [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Há três classes de mensagem associadas a esta região do formulário de um. Este exemplo de código é parte de um exemplo maior fornecido no [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstov4:formRegion
    name="OutlookAddIn1.FormRegion1">
  <vstov4:messageClass name="IPM.Note" />
  <vstov4:messageClass name="IPM.Contact" />
  <vstov4:messageClass name="IPM.Appointment" />
</vstov4:formRegion>
```

## <a name="see-also"></a>Consulte também

- [Criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)
- [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)