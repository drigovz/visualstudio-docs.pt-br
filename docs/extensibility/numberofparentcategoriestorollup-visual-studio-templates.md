---
title: NúmeroOfParentCategoriesToRollUp (modelos)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp
helpviewer_keywords:
- NumberOfParentCategoriesToRollUp element [Visual Studio Templates]
- <NumberOfParentCategoriesToRollUp> element [Visual Studio Templates]
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b903b9d0bdab2c17dd2e489de01badad82c15473
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702363"
---
# <a name="numberofparentcategoriestorollup-element-visual-studio-templates"></a>NúmeroOfParentCategoriesToRollUp element (modelos do Visual Studio)
Especifica o número de categorias-pai que exibirão o modelo na caixa de diálogo **Novo Projeto.**

 \<VSTemplate \<>>TemplateData>NúmeroDeSérieDosPaisCategoriasToRolar>> \<

## <a name="syntax"></a>Sintaxe

```xml
<NumberOfParentCategoriesToRollUp>
1
</NumberOfParentCategoriesToRollUp>
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
 Um `integer` valor é necessário.

 Esse valor especifica o número de categorias-pai que exibirão o modelo na caixa de diálogo **Novo Projeto.**

## <a name="remarks"></a>Comentários
 `NumberOfParentCategoriesToRollUp` é um elemento opcional.

## <a name="example"></a>Exemplo
 Este exemplo ilustra os metadados de um [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplicativo do Windows. Se um modelo com esses metadados for colocado [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] dois níveis de pasta abaixo do nó de nível superior, o modelo aparecerá no nó de nível superior na caixa de diálogo **Novo Projeto.** Se `NumberOfParentCategoriesToRollUp` o modelo não estiver definido, o modelo só aparecerá no nó em que está fisicamente localizado.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>
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
