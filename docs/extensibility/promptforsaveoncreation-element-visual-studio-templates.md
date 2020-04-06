---
title: PromptForSaveOnCreation Element (modelos de estúdio visual) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#PromptForSaveOnCreation
helpviewer_keywords:
- PromptForSaveOnCreation element [Visual Studio project templates]
ms.assetid: 75174674-0c3c-4b57-b2fd-6ea8e817b67d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 2e6bbd62120da59da1fb26e671c1aa02f33949f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701775"
---
# <a name="promptforsaveoncreation-element-visual-studio-templates"></a>Elemento PromptForSaveOnCreation (modelos do Visual Studio)

Especifica se o usuário é solicitado para um local de salvamento de projeto através da caixa de diálogo **Novo Projeto** ao criar um projeto. Se esse elemento `true`estiver definido como , então o usuário será solicitado para um local de salvamento. Se `false`, então eles não são solicitados (isto é, um projeto temporário é criado).

```xml
\<VSTemplate>
\<TemplateData>
\<PromptForSaveOnCreation>
```

## <a name="syntax"></a>Sintaxe

```xml
<PromptForSaveOnCreation> true/false </PromptForSaveOnCreation>
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

 O texto deve `true` `false`ser `true` ou , indicando que o usuário será solicitado para um local de salvamento ao criar um novo projeto.

## <a name="remarks"></a>Comentários
 `PromptForSaveOnCreation` é um elemento opcional. O valor padrão é `false`.

 Projetos temporários são projetos que você pode criar e modificar sem salvar o conteúdo desse projeto em disco.

## <a name="example"></a>Exemplo
 O exemplo a seguir `PromptForSaveOnCreation` define `false`o valor igual a , que especifica para permitir que o projeto seja criado como um projeto temporário.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <PromptForSaveOnCreation>false</PromptForSaveOnCreation>
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

- [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Criar modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
