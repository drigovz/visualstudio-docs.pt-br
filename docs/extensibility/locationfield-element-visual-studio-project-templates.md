---
title: LocationField Element (Modelos de Projetos do Estúdio Visual) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d993e84bec41486ef4dce6ad98c61f23ab2a46bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702881"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>Elemento LocationField (modelos de projeto do Visual Studio)
Especifica se a caixa de texto **Local** na caixa de diálogo **Projeto novo** está ativada, desativada ou oculta para o modelo do projeto.

 \<VSTemplate>> \<de \<campo de> de localização

## <a name="syntax"></a>Sintaxe

```
<LocationField> Enabled/Disabled/Hidden </LocationField>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necessário.<br /><br /> Categoriza o modelo e define como ele é exibido no **Novo Projeto**.|

## <a name="text-value"></a>Valor de texto
 Um valor de texto é obrigatório.

 Os valores de texto válidos são:

- `Enabled`, que especifica que a caixa **Localização** da caixa de diálogo **Novo Projeto** está ativada.

- `Disabled`, que especifica que a caixa **Localização** da caixa de diálogo **Novo Projeto** está desativada.

- `Hidden`, que especifica que a caixa **Localização** da caixa de diálogo **Novo Projeto** está oculta.

## <a name="remarks"></a>Comentários
 O valor padrão é `Enabled`.

 A caixa de texto **Localização** na caixa de diálogo **Projeto Novo** permite que os usuários alterem o diretório padrão no qual novos projetos são salvos.

 O valor especificado `Location` no elemento só é honrado pela caixa de diálogo se o sistema de projeto subjacente o suportar.

## <a name="example"></a>Exemplo
 O exemplo a seguir ilustra [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] os metadados de um modelo.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <LocationField>Disabled</LocationField>
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
