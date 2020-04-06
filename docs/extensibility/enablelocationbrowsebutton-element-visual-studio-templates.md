---
title: HabilitarOElementodeBotãodeLocalização (Modelos de Estúdio Visual) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton
helpviewer_keywords:
- EnableLocationBrowseButton [Visual Studio project templates]
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 263157d5c6fefc208f28caa55475ba329a0d230f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711982"
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>HabilitarOelementoDeBotãoDeLocalização (Modelos do Visual Studio)
Especifica se o botão **Procurar** está disponível na caixa de diálogo **Novo Projeto,** para que os usuários possam facilmente modificar o diretório padrão onde um novo projeto é salvo.

 \<\<VSTemplate>TemplateData> \<Habilitar>debotão de navegação delocalização

## <a name="syntax"></a>Sintaxe

```
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>
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

 O texto deve `true` `false`ser ou , indicando se deve ou não exibir o botão **Procurar** na caixa de diálogo **Novo Projeto.**

## <a name="remarks"></a>Comentários
 `EnableLocationBrowseButton` é um elemento opcional. O valor `true`padrão é , que exibe o botão **Procurar** na caixa de diálogo **Novo Projeto.**

 Na caixa de diálogo **Novo projeto,** a caixa de texto **Local** especifica o diretório onde um novo projeto é salvo. O botão **Procurar** ajuda você a modificar este diretório exibindo a caixa de diálogo Local do **projeto,** que permite que você navegue facilmente para um diretório diferente disponível no seu computador e escolha-o como o diretório onde o novo projeto é salvo.

## <a name="example"></a>Exemplo
 O exemplo a seguir ilustra [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] os metadados de um aplicativo windows.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>
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
