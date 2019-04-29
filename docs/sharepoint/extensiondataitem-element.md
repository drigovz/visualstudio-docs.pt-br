---
title: Elemento ExtensionDataItem | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionDataItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 658fb63227f4c4532038d537bde7cc10ca2c4f5e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967377"
---
# <a name="extensiondataitem-element"></a>Elemento ExtensionDataItem
  Um item de dados personalizado que está associado com o item de projeto do SharePoint, no formato de chave/valor. A chave e o valor devem ser cadeias de caracteres.

## <a name="syntax"></a>Sintaxe

```xml
<ExtensionDataItem Key = "Key of the data item"
    Value = "Value of the data item" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|**Chave**|Exigido **xs: string** atributo.<br /><br /> A chave que é usada para armazenar e recuperar o item de dados.|
|**Valor**|Exigido **xs: string** atributo.<br /><br /> O valor do item de dados.|

### <a name="child-elements"></a>Elementos filho
 nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Representa uma coleção de itens de dados personalizados que estão associados com o item de projeto do SharePoint.|

## <a name="remarks"></a>Comentários
 Quando você associar dados personalizados com um item de projeto do SharePoint usando o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriedade de um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> do objeto, o Visual Studio salva os dados para uma nova **ExtensionDataItem** elemento no `.spdata` de arquivos para o item de projeto. Para obter mais informações, consulte [salvar os dados nas extensões do sistema de projeto do SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="element-information"></a>Informações sobre o elemento

|||
|-|-|
|**Namespace**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome do esquema**|Esquema de Item de projeto do SharePoint|
|**Arquivo de validação**|ProjectItemModelSchema.xsd|
|**Pode estar vazio**|Não|

## <a name="see-also"></a>Consulte também
- [Referência de esquema de item de projeto do SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
