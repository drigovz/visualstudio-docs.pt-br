---
title: Project Element (Modelos de Estúdio Visual) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 335a1e4efa62f07e10bb24b9971627d24bb13273
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701998"
---
# <a name="project-element-visual-studio-templates"></a>Elemento do projeto (modelos do Visual Studio)
Especifica os arquivos ou diretórios para adicionar ao projeto.

 \<VSTemplate \<> TemplateContent> \<Project>

## <a name="syntax"></a>Sintaxe

```
<Project
    File="MyProject.proj"
    TargetFileName="MyTargetProject.proj"
    ReplaceParameters="true/false">
    IgnoreProjectParameter="$myCustomParameter$"
        ...
</Project>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`File`|Atributo obrigatório.<br /><br /> Especifica o nome do arquivo do projeto no arquivo *modelo .zip.*|
|`ReplaceParameters`|Atributo opcional.<br /><br /> Um valor booleano que especifica se o arquivo do projeto tem valores de parâmetro que devem ser substituídos quando um projeto é criado a partir do modelo. O valor padrão é `false`.|
|`TargetFileName`|Atributo opcional.<br /><br /> Especifica o nome do arquivo do projeto quando um projeto é criado a partir do modelo.|
|`IgnoreProjectParameter`|Atributo opcional.<br /><br /> Especifica se o projeto deve ser adicionado à solução atual. Se o valor do parâmetro personalizado, "$*myCustomParameter*$" existir no arquivo de substituição de parâmetros, o projeto será criado, mas não adicionado como parte da solução atualmente aberta.|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[Pasta](../extensibility/folder-element-visual-studio-project-templates.md)|Elemento opcional.<br /><br /> Especifica uma pasta para adicionar ao projeto.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Elemento opcional.<br /><br /> Especifica um arquivo para adicionar a um projeto.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Elemento necessário.|

## <a name="remarks"></a>Comentários
 `Project`é um elemento `TemplateContent`infantil opcional de .

 O `Project` elemento é usado para especificar um projeto e, portanto, só é válido em modelos de projeto.

 `Project`elementos podem ter elementos de crianças [folder](../extensibility/folder-element-visual-studio-project-templates.md) ou `Folder` elementos infantis [ProjectItem,](../extensibility/projectitem-element-visual-studio-project-templates.md) mas não uma mistura de elementos tanto e `ProjectItem` crianças.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]renomeia automaticamente o nome do arquivo do projeto com base no nome inserido pelo usuário na caixa de diálogo **Projeto** Novo. Use `TargetFileName` o atributo se quiser fornecer um nome de arquivo alternativo para arquivos de projeto criados com o modelo.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra os metadados de um modelo de projeto para um [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicativo.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
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
- [Criando modelos de projetos e itens](../ide/creating-project-and-item-templates.md)
- [Elemento ProjectItem (modelos de projeto do Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)
- [Elemento de pasta (modelos de projeto do Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)
