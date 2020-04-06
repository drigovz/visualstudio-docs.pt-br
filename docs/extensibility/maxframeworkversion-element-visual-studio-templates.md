---
title: MaxFrameworkVersion Element (modelos de estúdio visual) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c3acf9c40499417fe180ce470224824cc89a113
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702629"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>Elemento MaxFrameworkVersion (modelos do Visual Studio)

Especifica a versão máxima do .NET Framework que é exigido pelo modelo. Ele determina o valor mais alto disponível na versão **de destino da** versão de destino da caixa de diálogo Novo **Projeto.** Para que os usuários possam selecionar uma versão de framework, você também deve especificar [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) como a versão mínima .NET Framework para o modelo.

> [!IMPORTANT]
> A partir da versão 15.6 do Visual Studio 2017, a versão **target framework versão** não é mais um filtro para modelos exibidos na seção **Modelos** da caixa de diálogo **Novo Projeto.** Em vez disso, a versão **de destino é** a função como um seletor de estruturas para o modelo selecionado.

 \<VSTemplate \<> TemplateData> \<MaxFrameworkVersion>

## <a name="syntax"></a>Sintaxe

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
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

 O texto deve ser o número de versão mais alto do .NET Framework que é permitido pelo modelo.

## <a name="remarks"></a>Comentários

`MaxFrameworkVersion` é um elemento opcional. O `MaxFrameworkVersion` elemento deve ser omitido a menos que seja necessário, de modo a não limitar inadvertidamente o intervalo suportado de versões .NET Framework para o modelo. Também deve ser omitido se o .NET Framework não for aplicável ao modelo.

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

Neste exemplo, a versão máxima do .NET Framework que é `MaxFrameworkVersion`exigido pelo modelo, representado por , é 4.7.1. Um projeto criado com este modelo pode segmentar versões do .NET Framework até 4.7.1.

## <a name="see-also"></a>Confira também

- [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Criando modelos de projetos e itens](../ide/creating-project-and-item-templates.md)
