---
title: Elemento CustomParameter (modelos do Visual Studio) | Microsoft Docs
description: Saiba mais sobre o elemento CustomParameter e como ele contém um nome de parâmetro personalizado e um valor a ser usado quando um projeto ou item é criado a partir do modelo.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 61c118bbc85064beb10b99641f0803af7af12d56
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671943"
---
# <a name="customparameter-element-visual-studio-templates"></a>Elemento CustomParameter (modelos do Visual Studio)
Contém um nome de parâmetro personalizado e um valor a ser usado quando um projeto ou item é criado a partir do modelo.

## <a name="syntax"></a>Sintaxe

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`Name`|Obrigatórios. O nome do parâmetro. O formato dos parâmetros é $*Name*$.|
|`Value`|Obrigatórios. O valor de substituição para o parâmetro.|

### <a name="child-elements"></a>Elementos filho
 nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Agrupa os parâmetros personalizados que devem ser passados para o assistente de modelo quando o assistente faz substituições de parâmetro.|

## <a name="remarks"></a>Comentários
 Quando um modelo contém `CustomParameter` elementos, cada instância do `Name` atributo é substituída pelo `Value` atributo no projeto ou nos arquivos de item criados.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra como usar vários parâmetros personalizados em um modelo. Quando um projeto ou item é criado a partir de um modelo com os seguintes parâmetros personalizados, todas as instâncias de `$color1$` e `$color2$` nos arquivos de modelo serão substituídas por `Red` e `Blue` , respectivamente.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Veja também
- [Elemento CustomParameters (modelos do Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Parâmetros de modelo](../ide/template-parameters.md)
- [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
