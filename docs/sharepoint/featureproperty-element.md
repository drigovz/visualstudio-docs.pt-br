---
title: Elemento FeatureProperty | Microsoft Docs
description: Exiba informações de referência sobre o elemento FeatureProperty, que é um elemento no esquema do item de projeto do SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 070866b9dd14d974eb976b22bf7a79907e2c5d9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876661"
---
# <a name="featureproperty-element"></a>Elemento FeatureProperty
  Representa uma propriedade personalizada que é incluída com um recurso quando é implantada no SharePoint. Depois que um recurso é implantado, você pode acessar a propriedade em seu código.

## <a name="syntax"></a>Sintaxe

```xml
<FeatureProperty Key = "Key of the property value"
    Value = "Property value" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|**Chave**|Atributo **xs: String** necessário.<br /><br /> A chave usada para armazenar e recuperar o valor da propriedade. Cada propriedade deve ter uma chave que seja exclusiva dentro do recurso.|
|**Valor**|Atributo **xs: String** necessário.<br /><br /> O valor da propriedade.|

### <a name="child-elements"></a>Elementos filho
 Nenhum.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Recursoproperties](../sharepoint/featureproperties-element.md)|Representa uma coleção de valores de propriedade que são incluídos com um recurso quando ele é implantado no SharePoint.|

## <a name="remarks"></a>Comentários
 Para obter mais informações sobre as propriedades do recurso, consulte [fornecendo informações de pacote e de implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Informações do elemento

|Propriedade|Valor|
|-|-|
|**Namespace**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome do esquema**|Esquema de item de projeto do SharePoint|
|**Arquivo de validação**|ProjectItemModelSchema. xsd|
|**Pode estar vazio**|Não|

## <a name="see-also"></a>Confira também
- [Referência de esquema de item de projeto do SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Fornecer informações de empacotamento e implantação em itens de projeto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
