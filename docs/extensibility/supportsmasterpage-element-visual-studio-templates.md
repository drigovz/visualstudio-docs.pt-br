---
title: SuportesMasterPage Element (Modelos de Estúdio Visual) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsMasterPage
helpviewer_keywords:
- <SupportsMasterPage> element [Visual Studio Templates]
- SupportsMasterPage element [Visual Studio Templates]
ms.assetid: ce877a6a-9bba-4fd9-92fb-0a8dfec9e75b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 384672303d00b72431820b98fa02d09e440a1de5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699449"
---
# <a name="supportsmasterpage-element-visual-studio-templates"></a>Elemento SupportsMasterPage (modelos do Visual Studio)
Especifica se a caixa de seleção **Selecionar página-mestre** está ativada na caixa de diálogo **Adicionar novo item.**

 \<VSTemplate \< \<>Template>Suporte de>demasterPage>

## <a name="syntax"></a>Sintaxe

```
<SupportsMasterPage> true/false </SupportsMasterPage>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Especifica dados que categorizam o modelo e define como ele é exibido na caixa de diálogo **Novo Projeto** ou **Novo Item.**|

## <a name="text-value"></a>Valor de texto
 Um valor de texto é obrigatório.

 O texto deve `true` `false`ser ou , indicando se a caixa de seleção **Selecionar página mestre** está ativada na caixa de diálogo Adicionar novo **item.**

## <a name="remarks"></a>Comentários
 `SupportsMasterPage` é um elemento opcional. O valor padrão é `false`.

 O `SupportsMasterPage` elemento está disponível apenas para modelos de itens da Web.

## <a name="example"></a>Exemplo
 O exemplo a seguir ilustra os metadados de um projeto web que inclui suporte para uma página-mestre.

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

## <a name="see-also"></a>Confira também
- [Referência de esquema do modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
