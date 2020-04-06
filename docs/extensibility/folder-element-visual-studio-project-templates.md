---
title: Elemento de pasta (Modelos de Projeto Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb256b8be0dd9ce68f193750bf3ff5a383d5f073
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711461"
---
# <a name="folder-element-visual-studio-project-templates"></a>Elemento de pasta (modelos de projeto do Visual Studio)
Especifica uma pasta que será adicionada ao projeto.

 \<VSTemplate \<>Template> \<de \<> de> do projeto> de conteúdo

## <a name="syntax"></a>Sintaxe

```
<Folder Name="Project Folder">
    <Folder> ... </Folder>
    <ProjectItem> ... </ProjectItem>
</Folder>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`Name`|Atributo obrigatório.<br /><br /> O nome da pasta do projeto.|
|`TargetFolderName`|Atributo opcional.<br /><br /> Especifica o nome para dar a pasta quando um projeto é criado a partir do modelo. Este atributo é útil para usar a substituição de parâmetros para criar um nome de pasta ou nomear uma pasta com uma string internacional que não pode ser usada diretamente no arquivo *.zip.*|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|`Folder`|Especifica uma pasta para adicionar ao projeto. `Folder`elementos podem `Folder` conter elementos infantis.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Especifica um arquivo para adicionar ao projeto.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Project](../extensibility/project-element-visual-studio-templates.md)|Elemento filho opcional do [TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md).|

## <a name="remarks"></a>Comentários
 `Folder`é uma criança `Project`opcional de .

 Você pode usar qualquer um dos seguintes métodos para organizar itens de projeto em pastas em um modelo:

- Inclua as pastas no arquivo *.zip* e adicione-as ao projeto no arquivo *.vstemplate* especificando o caminho para o arquivo nos `ProjectItem` elementos, sem `Folder` elementos. Esse é o método recomendado. Por exemplo:

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Inclua as pastas no arquivo *.zip* e adicione-as ao projeto `Folder` no arquivo *.vstemplate* com elementos. Por exemplo:

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- Não inclua pastas no arquivo modelo *.zip,* mas `TargetFileName` adicione `ProjectItem` pastas usando o atributo do elemento. Por exemplo:

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>Exemplo
 O exemplo a seguir ilustra os metadados [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] de um modelo de projeto para um aplicativo Windows.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <Folder Name="Properties">
                <ProjectItem>AssemblyInfo.cs</ProjectItem>
                <ProjectItem>Resources.resx</ProjectItem>
                <ProjectItem>Resources.Designer.cs</ProjectItem>
                <ProjectItem>Settings.settings</ProjectItem>
                <ProjectItem>Settings.Designer.cs</ProjectItem>
            </Folder>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Confira também
- [Referência de esquema de modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Criando modelos de projetos e itens](../ide/creating-project-and-item-templates.md)
- [Elemento ProjectItem (modelos de itens do Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
