---
title: Elemento LocationFieldMRUPrefix (modelos do Visual Studio)
titleSuffix: ''
description: Saiba mais sobre o elemento LocationFieldMRUPrefix e como ele especifica os caminhos usados mais recentemente (MRU) na caixa de diálogo novo projeto e adicionar novo item.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationFieldMRUPrefix
helpviewer_keywords:
- <LocationFieldMRUPrefix> element [Visual Studio Templates]
- LocationFieldMRUPrefix element [Visual Studio Templates]
ms.assetid: 03443691-9eb5-46f4-9169-cc2552a04bcb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 674773d25e4842aec649fc57daa4972530832f71
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924971"
---
# <a name="locationfieldmruprefix-element-visual-studio-templates"></a>Elemento LocationFieldMRUPrefix (modelos do Visual Studio)

Especifica os caminhos usados mais recentemente (MRU) na caixa de diálogo **novo projeto** e **Adicionar novo item** .

## <a name="syntax"></a>Sintaxe

```xml
<LocationFieldMRUPrefix> ... </LocationFieldMRUPrefix>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

 Nenhum.

### <a name="child-elements"></a>Elementos filho

 Nenhum.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Categoriza o modelo e define como ele é exibido no **novo projeto** ou na caixa de diálogo **Adicionar novo item** .|

## <a name="remarks"></a>Comentários

 Esse elemento só deve ser usado para modelos produzidos por meio do [!INCLUDE[vsipprvsip](../extensibility/includes/vsipprvsip_md.md)] .

## <a name="see-also"></a>Confira também

- [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Criando modelos de projeto e item](../ide/creating-project-and-item-templates.md)
