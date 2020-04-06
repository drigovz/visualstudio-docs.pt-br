---
title: ProjectSubType Element (Modelos de Estúdio Visual) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 27396ad1bcc4e181b2b8cecd6ca863db2412630d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701825"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>Elemento ProjectSubType (modelos do Visual Studio)
Classifica o modelo em uma subcategoria do valor `ProjectType` especificado no elemento.

 \<VSTemplate \<> TemplateData> \<ProjectSubType>

## <a name="syntax"></a>Sintaxe

```xml
<ProjectSubType> SubType </ProjectSubType>
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

 Este valor especifica a subcategoria do modelo.

## <a name="remarks"></a>Comentários
 `ProjectSubType`é um elemento `TemplateData`infantil opcional de .

 O `ProjectSubType` elemento fornece uma subcategoria para o elemento [ProjectType.](../extensibility/projecttype-element-visual-studio-templates.md) Este valor pode incluir:

- `SmartDevice-NETCFv1`: Especifica que o modelo [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] tem como alvo a versão 1.0.

- `SmartDevice-NETCFv2`: Especifica que o modelo [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] tem como alvo a versão 2.0.

  Se um modelo `ProjectType` contiver um `Web`elemento `ProjectSubType` com um valor de , o elemento especificará a linguagem de programação do modelo. Este elemento pode ter os seguintes valores:

- `CSharp`: Especifica que o [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] modelo cria um projeto ou item da Web.

- `VisualBasic`: Especifica que o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] modelo cria um projeto ou item da Web.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra os metadados de um modelo de projeto para um [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicativo de dispositivo direcionado à [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] versão 2.0.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic device template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>
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
- [Criando modelos de projetos e itens](../ide/creating-project-and-item-templates.md)
- [Elemento ProjectType (modelos do Visual Studio)](../extensibility/projecttype-element-visual-studio-templates.md)
