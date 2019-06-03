---
title: Adicionar ou editar as marcas nos modelos de projeto
ms.date: 04/30/2019
author: minsa110
ms.author: somin
manager: jillfra
ms.topic: reference
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
- template tagging, updating
- template tags, updating
ms.openlocfilehash: 4a5113fa7f420d58892e2737ec9196422486490e
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2019
ms.locfileid: "66038622"
---
# <a name="add-tags-to-project-templates"></a>Adicionar marcas aos modelos de projeto

A partir do [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) versão 16.1 Preview 2, você poderá adicionar marcas de tipo de projeto, plataforma e linguagem aos seus modelos de projeto. As marcas são usadas em dois lugares na caixa de diálogo Novo projeto:

- As marcas aparecem sob a descrição do modelo

   ![Modelo de projeto com as marcas no diálogo do novo projeto](media/npd-item-with-template-tags.png)

- As marcas permitem que o modelo seja pesquisado e filtrado

   ![Pesquisar e filtrar na caixa de diálogo Novo projeto](media/npd-search-and-filter.png)

Você pode adicionar marcas ao atualizar o arquivo XML *.vstemplate* usando marcas de modelo criadas no Visual Studio ou com a criação de marcas de modelo personalizado. As marcas de modelo só aparecem no diálogo do novo projeto do Visual Studio 2019. Elas não afetam a renderização do modelo em versões anteriores do Visual Studio.

## <a name="add-or-edit-tags"></a>Adicionar ou editar marcas

Talvez você queira adicionar ou editar marcas no XML *.vstemplate* do modelo de projeto quando você:

* [Criar um novo modelo de projeto](/visualstudio/ide/how-to-create-project-templates) usando o Assistente para Exportar Modelo

* [Atualizar seu modelo de projeto existente](/visualstudio/ide/how-to-update-existing-templates)

* [Criar um novo modelo de projeto do VSIX](/visualstudio/extensibility/getting-started-with-the-vsix-project-template)

## <a name="syntax"></a>Sintaxe

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>Atributos

Os seguintes atributos são opcionais e para cenários de usuário avançado.

|Atributo|Descrição|
|---------------|-----------------|
|`Package`|Um GUID que especifica a ID do pacote do Visual Studio.|
|`ID`|Especifica a ID de recurso do Visual Studio.|

Sintaxe:

```xml
<LanguageTag Package="{PackageID}" ID="ResourceID" />
<PlatformTag Package="{PackageID}" ID="ResourceID" />
<ProjectTypeTag Package="{PackageID}" ID="ResourceID" />
```

## <a name="elements"></a>Elementos

### <a name="child-elements"></a>Elementos filho

nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|(Obrigatório) Classifica o modelo e define como ele é exibido na caixa de diálogo **Novo Projeto** ou **Adicionar Novo Item**.|

## <a name="text-value"></a>Valor de texto

É necessário um valor de texto, a menos que os atributos `Package` e `ID` sejam usados.

O texto fornece o nome do modelo.

## <a name="built-in-tags"></a>Marcas internas

O Visual Studio oferece uma lista de marcas internas que, quando adicionadas, renderizam um recurso localizado. Veja abaixo uma lista de marcas internas e seus valores correspondentes entre parênteses.

| Idioma | Plataforma | Tipo de Projeto |
| -- | -- | -- |
| C++ (`cpp`) | Android (`android`) | Nuvem (`cloud`) |
| C# (`csharp`) | Azure (`azure`) | Console (`console`) |
| F# (`fsharp`) | iOS (`ios`) | Área de trabalho (`desktop`) |
| Java (`java`) | Linux (`linux`) | Extensões (`extension`) |
| JavaScript (`javascript`) | macOS (`macos`) | Jogos (`games`) |
| Python (`python`) | tvOS (`tvos`) | IoT (`iot`) |
| Consulta de Idioma (`querylanguage`) | Windows (`windows`) | Biblioteca (`library`) |
| TypeScript (`typescript`) | Xbox (`xbox`) | Machine Learning (`machinelearning`) |
| Visual Basic (`visualbasic`) | | Dispositivo móvel (`mobile`) |
| | | Office (`office`) |
| | | Outros (`other`) |
| | | Serviço (`service`) |
| | | Teste (`test`) |
| | | UWP (`uwp`) |
| | | Web (`web`) |

## <a name="example"></a>Exemplo

O exemplo a seguir mostra os metadados para um modelo de projeto de um aplicativo do Visual C#.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <LanguageTag>C#</LanguageTag>
        <PlatformTag>windows</PlatformTag>
        <PlatformTag>linux</PlatformTag>
        <PlatformTag>My Platform</PlatformTag>
        <ProjectTypeTag>console</ProjectTypeTag>
        <ProjectTypeTag>desktop</ProjectTypeTag>
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

## <a name="see-also"></a>Consulte também

- [Referência de esquema de modelo do Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [Criando modelos de projeto e de item](/visualstudio/ide/creating-project-and-item-templates)
- [Personalizar modelos de item e projeto](/visualstudio/ide/customizing-project-and-item-templates)
- [Introdução ao modelo de projeto do VSIX](/visualstudio/extensibility/getting-started-with-the-vsix-project-template)