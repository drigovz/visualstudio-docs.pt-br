---
title: SuportaLanguageDropDown Element (modelos de estúdio visual) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1230b493fe746a272cf4ca4cffe9d197afd8ba1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699462"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>Elemento SupportsLanguageDropDown (modelos do Visual Studio)
Especifica se o modelo de item da Web é idêntico para vários idiomas e se a opção **Idioma** está ativada na caixa de diálogo **Adicionar novo item.**

 \<VSTemplate \<> TemplateData> \<suportaidiomaDropDown>

## <a name="syntax"></a>Sintaxe

```
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>
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

 O texto deve `true` `false`ser ou , indicando se a opção **Idioma** está disponível ou não na caixa de diálogo **Adicionar novo item.**

## <a name="remarks"></a>Comentários
 `SupportsLanguageDropDown` é um elemento opcional. O valor padrão é `false`.

 O `SupportsLanguageDropDown` elemento está disponível apenas para modelos de itens da Web.

 Se o valor para este `true`elemento for definido como , então o modelo de item é idêntico para todas as linguagens de programação e a opção **Idioma** está habilitada na caixa de diálogo **Adicionar novo item.** Esta opção permite que você escolha a linguagem de programação do novo item que deseja criar a partir do modelo.

## <a name="example"></a>Exemplo
 O exemplo a seguir especifica para exibir a opção **'Down do Idioma'.**

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
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>
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
