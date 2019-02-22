---
title: Elemento FeatureProperties | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperties element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f9b893ce699dd86f309a05fad83560cc42439551
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619362"
---
# <a name="featureproperties-element"></a>Elemento FeatureProperties
  Uma coleção de valores de propriedade que são incluídos com um recurso quando ele é implantado no SharePoint. Depois que um recurso é implantado, você pode acessar os valores de propriedade em seu código.

## <a name="syntax"></a>Sintaxe

```xml
<FeatureProperties>
  <FeatureProperty.../>
</FeatureProperties>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos
 nenhuma.

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Elemento opcional.<br /><br /> Representa uma propriedade personalizada, no formato de chave/valor.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Representa um item de projeto do SharePoint. Esse elemento o elemento raiz necessário do `.spdata` arquivo.|

## <a name="remarks"></a>Comentários
 Para obter mais informações sobre as propriedades do recurso, consulte [fornecer informações de empacotamento e implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informações sobre o elemento

|Elemento|Descrição|
|-------------|-----------------|
|**Namespace**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome do esquema**|Esquema de Item de projeto do SharePoint|
|**Arquivo de validação**|ProjectItemModelSchema.xsd|
|**Pode estar vazio**|Não|

## <a name="see-also"></a>Consulte também
- [Referência de esquema de item de projeto do SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Fornecer informações de empacotamento e implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
