---
title: Elemento ProjectItemfile | Microsoft Docs
description: Obtenha informações de referência sobre o elemento ProjectItemfile, que representa um arquivo de item de projeto na referência de esquema XML do item de projeto do SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a7c6dd7fc46dc8616eddc164bcf2ec801657cb00
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955132"
---
# <a name="projectitemfile-element"></a>Elemento ProjectItemFile
  Representa um arquivo do SharePoint, como um arquivo de elemento de recurso, a ser incluído com o item de projeto quando ele é implantado no SharePoint.

## <a name="syntax"></a>Sintaxe

```xml
<ProjectItemFile Source = "Name of the file"
    Target = "Deployment path of the file"
    Type = "Type of deployment for the file" />
```

## <a name="type"></a>Type
 **ProjectItemFileType**

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|**Origem**|Atributo **xs: String** necessário.<br /><br /> O nome do arquivo a ser implantado com o item de projeto.|
|**Target (destino)**|Atributo **xs: String** opcional.<br /><br /> O caminho em que o arquivo será implantado no SharePoint, em relação à pasta raiz da implantação. A pasta raiz de implantação é determinada pelo tipo de implantação especificado pelo atributo de **tipo** . Se o atributo de **destino** não for especificado, o arquivo será implantado em uma pasta com o nome especificado no atributo de **origem** .<br /><br /> Para obter mais informações, consulte as descrições das propriedades **caminho de implantação** e raiz de **implantação** dos itens de projeto do SharePoint em [desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md).|
|**Tipo**|Atributo **xs: String** necessário.<br /><br /> O tipo de implantação para o arquivo. Para obter mais informações sobre os valores possíveis, consulte a descrição para a propriedade **tipo de implantação** de itens de projeto do SharePoint em [desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Elementos filho
 Nenhum.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Arquivos](../sharepoint/files-element.md)|Especifica os arquivos a serem incluídos com o item de projeto do SharePoint quando ele é implantado no SharePoint.|

## <a name="remarks"></a>Comentários
 Os arquivos do SharePoint geralmente referenciados nos elementos **ProjectItemFile** incluem arquivos de elemento de recurso (*Elements.xml*), arquivos de esquema para definições de lista (*Schema.xml*) e arquivos de definição de Web Part para Web Parts (*. WebPart*).

## <a name="element-information"></a>Informações do elemento

|Propriedade|Valor|
|-|-|
|**Namespace**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome do esquema**|Esquema de item de projeto do SharePoint|
|**Arquivo de validação**|ProjectItemModelSchema. xsd|
|**Pode estar vazio**|Não|

## <a name="see-also"></a>Confira também
- [Referência de esquema de item de projeto do SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
