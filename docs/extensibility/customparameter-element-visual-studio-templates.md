---
title: Elemento de parâmetro personalizado (modelos de estúdio visual) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9063a354f03b896e189566e8d84a18caf7509db8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739423"
---
# <a name="customparameter-element-visual-studio-templates"></a>Elemento Personalizado Parâmetro (modelos do Visual Studio)
Contém um nome e valor de parâmetro personalizado para usar quando um projeto ou item é criado a partir do modelo.

## <a name="syntax"></a>Sintaxe

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`Name`|Obrigatórios. O nome do parâmetro. O formato para parâmetros é *$name*$.|
|`Value`|Obrigatórios. O valor de substituição do parâmetro.|

### <a name="child-elements"></a>Elementos filho
 Nenhum.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Agrupa os parâmetros personalizados que devem ser passados para o assistente de modelo quando o assistente fizer substituições de parâmetros.|

## <a name="remarks"></a>Comentários
 Quando um `CustomParameter` modelo contém elementos, cada instância o `Name` atributo é substituído pelo atributo `Value` nos arquivos de projeto ou item criados.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra como usar vários parâmetros personalizados em um modelo. Quando um projeto ou item é criado a partir de `$color1$` um `$color2$` modelo com os seguintes `Red` `Blue`parâmetros personalizados, todas as instâncias e nos arquivos de modelo serão substituídas e, respectivamente.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Confira também
- [Elemento CustomParameters (modelos do Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Parâmetros de modelo](../ide/template-parameters.md)
- [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
