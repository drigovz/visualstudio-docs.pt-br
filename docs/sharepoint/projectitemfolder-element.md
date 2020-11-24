---
title: Elemento ProjectItemFolder | Microsoft Docs
description: Obtenha informações de referência sobre o elemento ProjectItemFolder, que representa uma pasta mapeada na referência de esquema XML do item de projeto do SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 99a27f8e255aa17e8b9fa604b504109976c5d36a
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440786"
---
# <a name="projectitemfolder-element"></a>Elemento ProjectItemFolder
  Representa uma pasta mapeada.

## <a name="syntax"></a>Sintaxe

```xml
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"
    Type = "Type of deployment for the mapped folder" />
```

## <a name="type"></a>Type
 **ProjectItemFolderType**

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|**Target (destino)**|Atributo **xs: String** necessário.<br /><br /> O caminho da pasta na instalação do SharePoint à qual a pasta mapeada corresponde, em relação à pasta raiz da implantação. A pasta raiz de implantação é determinada pelo tipo de implantação especificado pelo atributo de **tipo** .<br /><br /> Para obter mais informações, consulte as descrições das propriedades **caminho de implantação** e raiz de **implantação** dos itens de projeto do SharePoint em [desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Tipo**|Atributo **xs: String** necessário.<br /><br /> O tipo de implantação para a pasta mapeada. Para obter mais informações sobre os valores possíveis, consulte a descrição para a propriedade **tipo de implantação** de itens de projeto do SharePoint em [desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Elementos filho
 Nenhum.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Representa um item de projeto do SharePoint. Esse é o elemento raiz necessário do arquivo *. COMDATA* .|

## <a name="remarks"></a>Comentários
 Para obter mais informações sobre pastas mapeadas, consulte [como adicionar e remover pastas mapeadas](../sharepoint/how-to-add-and-remove-mapped-folders.md).

## <a name="element-information"></a>Informações do elemento

|Propriedade|Valor|
|-|-|
|**Namespace**|http: \/ \/ schemas.Microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|
|**Nome do esquema**|Esquema de item de projeto do SharePoint|
|**Arquivo de validação**|ProjectItemModelSchema. xsd|
|**Pode estar vazio**|Não|

## <a name="see-also"></a>Confira também
- [Referência de esquema de item de projeto do SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Como: Adicionar e remover pastas mapeadas](../sharepoint/how-to-add-and-remove-mapped-folders.md)
