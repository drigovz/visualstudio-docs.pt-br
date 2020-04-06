---
title: Elemento ShowByDefault (Modelos do Estúdio Visual)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ShowByDefault
helpviewer_keywords:
- <ShowByDefault> element [Visual Studio Templates]
- ShowByDefault element [Visual Studio Templates]
ms.assetid: 7be783f6-0ef6-42bc-924a-df9a2eba7781
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 711cff06637957b796525543a02bfdd376e04284
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700102"
---
# <a name="showbydefault-element-visual-studio-templates"></a>Elemento ShowByDefault (Modelos do Estúdio Visual)
Se `false`, especificar que o modelo só será exibido sob o [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)especificado .

 \<VSTemplate \<> TemplateData> \<ShowByDefault>

## <a name="syntax"></a>Sintaxe

```
<ShowByDefault> true/false </ShowByDefault>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Categoriza o modelo e define como ele é exibido no **Novo Projeto** ou na caixa de diálogo Adicionar **novo item.**|

## <a name="text-value"></a>Valor de texto
 Um valor de texto é obrigatório.

 O texto deve `true` `false`ser ou . Se for verdade, especifica que o modelo será exibido para todos os tipos de projeto. Se for falso, o modelo só será `TemplateGroupID`exibido sob o especificado .

## <a name="remarks"></a>Comentários
 `ShowByDefault` é um elemento opcional. O valor padrão é `true`.

## <a name="example"></a>Exemplo
 O exemplo a seguir ilustra [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] os metadados de um modelo.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ShowByDefault>false</ShowByDefault>
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
- [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
- [Referência de esquema do modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Elemento TemplateGroupID (Modelos do Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md)
