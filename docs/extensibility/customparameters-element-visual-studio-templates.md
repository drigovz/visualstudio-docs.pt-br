---
title: Elemento CustomParameters (modelos do Visual Studio) | Microsoft Docs
description: Saiba mais sobre o elemento CustomParameters e como ele agrupa os parâmetros personalizados que devem ser passados para o assistente de modelo quando o assistente faz substituições de parâmetro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c78c8a038df33d9b548229966402d0058f53144
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671473"
---
# <a name="customparameters-element-visual-studio-templates"></a>Elemento CustomParameters (modelos do Visual Studio)
Agrupa os parâmetros personalizados que devem ser passados para o assistente de modelo quando o assistente faz substituições de parâmetro.

## <a name="syntax"></a>Sintaxe

```
<CustomParameters>
    <CustomParameter/>
    <CustomParameter/>
</CustomParameters>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos
 nenhuma.

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Contém um nome de parâmetro personalizado e um valor a ser usado quando um projeto ou item é criado a partir do modelo. Pode ser que não haja nenhum ou mais de um elemento `CustomParameter` em um elemento `CustomParameters`.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Especifica o conteúdo do modelo.|

## <a name="remarks"></a>Comentários

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra como usar vários parâmetros personalizados em um modelo. Quando um projeto ou item é criado a partir de um modelo com os seguintes parâmetros personalizados, todas as instâncias de `$color1$` e `$color2$` nos arquivos de modelo serão substituídas por `Red` e `Blue` , respectivamente.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Veja também
- [Elemento CustomParameter (modelos do Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)
- [Parâmetros de modelo](../ide/template-parameters.md)
- [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
