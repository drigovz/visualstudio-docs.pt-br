---
title: Elemento costumes (modelos de estúdio visual) | Microsoft Docs
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
ms.openlocfilehash: f524996c226f001c68ddc7ac9aa8cb3b99857fc5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739413"
---
# <a name="customparameters-element-visual-studio-templates"></a>Elemento CustomParameters (modelos do Visual Studio)
Agrupa os parâmetros personalizados que devem ser passados para o assistente de modelo quando o assistente fizer substituições de parâmetros.

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
 Nenhum.

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Elemento opcional.<br /><br /> Contém um nome e valor de parâmetro personalizado para usar quando um projeto ou item é criado a partir do modelo. Pode ser que não haja nenhum ou mais de um elemento `CustomParameter` em um elemento `CustomParameters`.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Especifica o conteúdo do modelo.|

## <a name="remarks"></a>Comentários

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra como usar vários parâmetros personalizados em um modelo. Quando um projeto ou item é criado a partir de `$color1$` um `$color2$` modelo com os seguintes `Red` `Blue`parâmetros personalizados, todas as instâncias e nos arquivos de modelo serão substituídas e, respectivamente.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Confira também
- [Elemento Personalizado Parâmetro (modelos do Visual Studio)](../extensibility/customparameter-element-visual-studio-templates.md)
- [Parâmetros de modelo](../ide/template-parameters.md)
- [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
