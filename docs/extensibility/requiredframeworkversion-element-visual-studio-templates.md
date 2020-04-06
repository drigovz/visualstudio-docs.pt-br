---
title: RequiredFrameworkVersion Element (modelos de estúdio visual) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 060ebc0633de67d93257e24c2dff24d2aa0970da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701505"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>RequiredFrameworkVersion elemento (modelos do Visual Studio)

Especifica a versão mínima do .NET Framework que é exigido pelo modelo. Isso faz com que a versão **de destino seja** exibida na caixa de diálogo Novo **projeto.** O `RequiredFrameworkVersion` elemento também determina o menor valor disponível no dropdown.

> [!IMPORTANT]
> A partir da versão 15.6 do Visual Studio 2017, a versão **target framework versão** não é mais um filtro para modelos exibidos na seção **Modelos** da caixa de diálogo **Novo Projeto.** Em vez disso, o dropdown funciona como um seletor de estruturas para o modelo selecionado.

 \<VSTemplate \<> TemplateData> \<RequiredFrameworkVersion>

## <a name="syntax"></a>Sintaxe

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necessário.<br /><br /> Categoriza o modelo e define como ele é exibido no **Novo Projeto** ou na caixa de diálogo Adicionar **novo item.**|

## <a name="text-value"></a>Valor de texto
 Um valor de texto é obrigatório.

 O texto deve ser o número de versão mínimo do .NET Framework necessário para o modelo.

## <a name="remarks"></a>Comentários

`RequiredFrameworkVersion` é um elemento opcional. Use este elemento somente se o modelo suportar uma versão mínima específica (e versões posteriores, se houver) do .NET Framework. Se você `RequiredFrameworkVersion` especificar o elemento e seu modelo não suportar uma versão mínima específica do .NET Framework, a versão **de destino será** exibida quando não for aplicável.

## <a name="example"></a>Exemplo

O exemplo a seguir ilustra os [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] metadados de um modelo de classe padrão.

```xml
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>3.0</RequiredFrameworkVersion>
        <MaxFrameworkVersion>4.7.1</MaxFrameworkVersion>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

Neste exemplo, a versão mínima do .NET Framework que é `RequiredFrameworkVersion`exigido pelo modelo, representado por , é 3.0. Um projeto criado com este modelo pode segmentar versões .NET Framework a partir de 3.0.

## <a name="see-also"></a>Confira também

- [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Criar modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
- [Visão geral do direcionamento de estrutura](../ide/visual-studio-multi-targeting-overview.md)
