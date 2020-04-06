---
title: TemplateData Element (Modelos de Estúdio Visual) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3ce0226286e8cc4623b66c043eb7bd376597118
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699187"
---
# <a name="templatedata-element-visual-studio-templates"></a>Elemento TemplateData (modelos do Visual Studio)
Categoriza o modelo e define como ele é exibido no **Novo Projeto** ou na caixa de diálogo Adicionar **novo item.**

 \<VSTemplate \<> TemplateData>

## <a name="syntax"></a>Sintaxe

```
<TemplateData>
    <Name> ... </Name>
    <Description> ... </Description>
    <Icon> ... </Icon>
    <ProjectType> ... </ProjectType>
    ...
</TemplateData>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos
 Nenhum.

### <a name="child-elements"></a>Elementos filho

| Elemento | Descrição |
| - | - |
| [Nome](../extensibility/name-element-visual-studio-templates.md) | Elemento necessário.<br /><br /> Especifica o nome do modelo como ele aparece no **Novo Projeto** ou na caixa de diálogo Adicionar **novo item.** |
| [Descrição](../extensibility/description-element-visual-studio-templates.md) | Elemento necessário.<br /><br /> Especifica a descrição do modelo como ele aparece no **Novo Projeto** ou na caixa de diálogo Adicionar **novo item.** |
| [Ícone](../extensibility/icon-element-visual-studio-templates.md) | Elemento necessário.<br /><br /> Especifica o caminho e o nome do arquivo do arquivo de imagem que serve como ícone, que aparece no **Novo Projeto** ou na caixa de diálogo Adicionar **novo item,** para o modelo. |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | Elemento necessário.<br /><br /> Categoriza o modelo de projeto para que ele apareça sob o grupo especificado na caixa de diálogo **Projeto Novo.** |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Classifica o modelo do projeto para que ele apareça na subcategoria especificada na caixa de diálogo **Novo Projeto.** |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica o ID do modelo. |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica o ID do grupo de modelo. |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica um valor usado para organizar o modelo, entre outros modelos na mesma categoria, como aparece na caixa de diálogo **Novo Projeto** ou Adicionar **Novo Item.** |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica se uma pasta de contenção é criada na instanciação do projeto. |
| [Defaultname](../extensibility/defaultname-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica o nome que o sistema de projeto Visual Studio irá gerar para o projeto ou item quando for criado. |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica se o sistema de projeto Visual Studio gerará o nome padrão de um projeto ou item quando ele for criado. |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica se o projeto pode ser criado como um projeto temporário (somente visual studio 2017). |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica se o botão **Procurar** está disponível na caixa de diálogo **Novo Projeto,** para que os usuários possam facilmente modificar o diretório padrão onde um novo projeto é salvo. |
| [Escondidos](../extensibility/hidden-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica se o modelo é exibido na caixa de diálogo **Novo Projeto** ou Adicionar **novo item.** |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica o número de categorias-pai que exibirão o modelo na caixa de diálogo **Novo Projeto.** |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | Elemento opcional. |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | Elemento opcional.<br /><br /> Especifica se a caixa de texto **Local** na caixa de diálogo **Projeto novo** está ativada, desativada ou oculta para o modelo do projeto. |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Use este elemento se o modelo apenas suportar uma versão mínima específica e versões posteriores, se houver, do Quadro .NET. |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica se o modelo suporta uma página-mestre para projetos web. |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica se o modelo suporta a separação de código, ou o modelo de página de código atrás, para projetos web. |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica se o modelo é idêntico para vários idiomas e se a opção **Idioma** está disponível na caixa de diálogo **Novo Projeto.** |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | Elemento opcional.<br /><br /> Especifica a plataforma que o modelo de projeto tem como alvo. Esse elemento especifica que um modelo [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] de projeto é usado para criar aplicativos. |

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Elemento necessário.<br /><br /> Contém todos os metadados para o modelo do projeto, modelo de item ou kit inicial.|

## <a name="remarks"></a>Comentários
 `TemplateData`é um elemento necessário.

 Se você não incluir um elemento opcional, o valor padrão para esse elemento será usado.

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
- [Referência de esquema do modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
