---
title: Arquivos de elemento | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1cf64fc8f70c0a3cf3ed5df1237603f490a703db
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639564"
---
# <a name="files-element"></a>Elemento de arquivos
  Especifica os arquivos para implantar com o item de projeto do SharePoint, como arquivos de recurso de elemento e a saída de projetos do SharePoint não dependentes.

## <a name="syntax"></a>Sintaxe

```xml
<Files>
  <ProjectItemFile.../>
  <ProjectOutputFile.../>
</Files>
```

## <a name="type"></a>Tipo
 **FileCollectionType**

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos
 nenhuma.

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Opcional **ProjectItemFileType** elemento.<br /><br /> Representa um arquivo do SharePoint, como o arquivo de elemento de recurso, para incluir com o item de projeto quando ele é implantado no SharePoint.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Opcional **ProjectOutputFileType** elemento.<br /><br /> Representa a saída de um projeto para incluir com o item de projeto quando ele é implantado no SharePoint.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Representa um item de projeto do SharePoint. Esse elemento o elemento raiz necessário do `.spdata` arquivo.|

## <a name="element-information"></a>Informações sobre o elemento

|||
|-|-|
|**Namespace**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome do esquema**|Esquema de Item de projeto do SharePoint|
|**Arquivo de validação**|ProjectItemModelSchema.xsd|
|**Pode estar vazio**|Não|

## <a name="see-also"></a>Consulte também
- [Referência de esquema de item de projeto do SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
