---
title: Elemento BuildProjectOnload (modelos do Visual Studio) | Microsoft Docs
description: Saiba mais sobre o elemento BuildProjectOnload e como ele cria apenas novos projetos conforme você cria e adiciona-os a uma solução.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: b07d3074-0fc9-45e1-baf5-da6bd4f3f1c0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8e2a1f542e89851cb430f8d80934933351e9349e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882265"
---
# <a name="buildprojectonload-element-visual-studio-templates"></a>Elemento BuildProjectOnload (modelos do Visual Studio)
O cria apenas novos projetos conforme você cria e adiciona-os a uma solução. A solução inteira não é criada.

Hierarquia de elementos:

```xml
<VSTemplate>
  <TemplateData>
    <BuildProjectOnLoad>
```

## <a name="syntax"></a>Sintaxe

```vb
<BuildProjectOnLoad> true/false </BuildProjectOnLoad>
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
|`TemplateData`|Categoriza o modelo e define como ele aparece nas caixas de diálogo **novo projeto** e **Adicionar novo item** .|

## <a name="text-value"></a>Valor de texto
 Um valor de texto é obrigatório.

 O texto deve ser `true` ou `false` para indicar se deseja Compilar apenas o novo projeto quando ele é criado a partir do modelo.

## <a name="remarks"></a>Comentários
 `BuildProjectOnLoad` é um elemento opcional. O valor padrão é `false`.

## <a name="example"></a>Exemplo
 O exemplo a seguir ilustra os metadados de um modelo do Visual C#.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <BuildProjectOnload>true</BuildProjectOnLoad>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Confira também

- [Elemento e atributo BuildOnLoad](buildonload-visual-studio-templates.md)
- [Criando modelos de projeto e item](../ide/creating-project-and-item-templates.md)
- [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
