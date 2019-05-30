---
title: Elemento SupportsMasterPage (modelos do Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsMasterPage
helpviewer_keywords:
- <SupportsMasterPage> element [Visual Studio Templates]
- SupportsMasterPage element [Visual Studio Templates]
ms.assetid: ce877a6a-9bba-4fd9-92fb-0a8dfec9e75b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba409c831dd508dae796bca1ea2837674459690d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316689"
---
# <a name="supportsmasterpage-element-visual-studio-templates"></a>Elemento SupportsMasterPage (modelos do Visual Studio)
Especifica se a ou não a **selecionar a página mestra** caixa de seleção está habilitada no **Adicionar Novo Item** caixa de diálogo.

 \<VSTemplate > \<TemplateData > \<SupportsMasterPage >

## <a name="syntax"></a>Sintaxe

```
<SupportsMasterPage> true/false </SupportsMasterPage>
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos
 nenhuma.

### <a name="child-elements"></a>Elementos filho
 nenhuma.

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Especifica os dados que categoriza o modelo e a define como ele é exibido na **novo projeto** ou **Novo Item** caixa de diálogo.|

## <a name="text-value"></a>Valor de texto
 Um valor de texto é obrigatório.

 O texto deve ser `true` ou `false`, indicando se ou não o **selecionar a página mestra** caixa de seleção está habilitada no **Add New Item** caixa de diálogo.

## <a name="remarks"></a>Comentários
 `SupportsMasterPage` é um elemento opcional. O valor padrão é `false`.

 O `SupportsMasterPage` elemento só está disponível para modelos de item da Web.

## <a name="example"></a>Exemplo
 O exemplo a seguir ilustra os metadados para um projeto Web que inclui suporte para uma página mestra.

```
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsMasterPage>true</SupportsMasterPage>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Consulte também
- [Referência de esquema do modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)