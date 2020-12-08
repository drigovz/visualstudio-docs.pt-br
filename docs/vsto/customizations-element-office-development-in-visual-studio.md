---
title: '&lt;elemento personalizações &gt; (desenvolvimento do Office no Visual Studio)'
description: Saiba como o elemento personalizações do namespace vstov4 contém todas as informações sobre como instalar e carregar cada solução do Office.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <customizations> element
- customizations element
- application manifests [Office development in Visual Studio], <customizations> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cc1f33101346d334d08d2bd2d7795961ea33011e
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844030"
---
# <a name="ltcustomizationsgt-element-office-development-in-visual-studio"></a>&lt;elemento personalizações &gt; (desenvolvimento do Office no Visual Studio)
  O `customizations` elemento do `vstov4` namespace contém todas as informações sobre a instalação e o carregamento de cada solução do Office.

## <a name="syntax-for-document-level-customizations"></a>Sintaxe para personalizações em nível de documento

```xml
<customizations>
  <customization
    id
    <document
      solutionId
    />
  </customization>
</customizations>
```

## <a name="syntax-for-vsto-add-ins"></a>Sintaxe para suplementos do VSTO

```xml
<customizations>
  <customization
    id
    <appAddin
      application
      loadBehavior
      keyName>
    <friendlyName></friendlyName>
    <description></description>
    <formRegions></formRegions>
  </customization>
</customizations>
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `customizations` elemento contém informações específicas sobre cada solução do Office. Esse elemento deve estar no seguinte namespace: `vstov4=urn:schemas-microsoft-com:vsto.v4` . Os elementos filho do assembly também devem estar nesse namespace.

 O `customizations` elemento não tem atributos.

 O `customizations` elemento tem o seguinte elemento filho.

### <a name="customization"></a>Personalização
 Obrigatórios. O `customization` elemento no `vstov4` namespace é definido em [&#60;elemento&#62; de personalização &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).

## <a name="example-of-a-document-level-customization"></a>Exemplo de uma personalização no nível do documento

### <a name="description"></a>Descrição
 O exemplo de código a seguir ilustra o `customizations` elemento para uma personalização em nível de documento.

> [!NOTE]
> Este exemplo de código faz parte de um exemplo maior fornecido em [manifestos do aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
<vstov4:customizations
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
  <vstov4:customization>
    <vstov4:document
      solutionId="73e" />
  </vstov4:customization>
</vstov4:customizations>
```

## <a name="example-of-a-vsto-add-in"></a>Exemplo de um suplemento do VSTO

### <a name="description"></a>Descrição
 O exemplo de código a seguir ilustra o `customizations` elemento para um suplemento do VSTO. Este é um suplemento do VSTO do Outlook que inclui regiões de formulário. Este exemplo de código faz parte de um exemplo maior fornecido em [manifestos do aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
<vstov4:customizations
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
  <vstov4:customization>
    <vstov4:appAddIn
      application="Outlook"
      loadBehavior="3"
      keyName="ContosoOutlookAddIn">
      <vstov4:friendlyName>
        ContosoOutlookAddIn
      </vstov4:friendlyName>
      <vstov4:description>
        ContosoOutlookAddIn - Outlook VSTO Add-in
        created with Visual Studio Tools for Office
      </vstov4:description>
      <vstov4:formRegions>
        <vstov4:formRegion
            name="OutlookAddIn1.FormRegion1">
          <vstov4:messageClass name="IPM.Note" />
          <vstov4:messageClass name="IPM.Contact" />
          <vstov4:messageClass name="IPM.Appointment" />
        </vstov4:formRegion>
      </vstov4:formRegions>
    </vstov4:appAddIn>
  </vstov4:customization>
</vstov4:customizations>
```

## <a name="see-also"></a>Confira também

- [Manifestos do aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)