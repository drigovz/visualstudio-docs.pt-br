---
title: SortOrder Element (Modelos de Estúdio Visual) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 935d00335a21d3e129e79ce351e554ea93787447
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699964"
---
# <a name="sortorder-element-visual-studio-templates"></a>Elemento SortOrder (modelos do Visual Studio)
Especifica um valor usado para organizar o modelo, entre outros modelos na mesma categoria, como aparece na caixa de diálogo **Novo Projeto** ou Adicionar **Novo Item.**

 \<VSTemplate \<> TemplateDataData> \<SortOrder>

## <a name="syntax"></a>Sintaxe

```
<SortOrder> ... </SortOrder>
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

 Um `integer` que representa o valor da ordem de classificação.

## <a name="remarks"></a>Comentários
 `SortOrder` é um elemento opcional. O valor padrão é 100, e todos os valores devem ser múltiplos de 10.

 O `SortOrder` elemento é ignorado para modelos criados pelo usuário. Todos os modelos criados pelo usuário são ordenados alfabeticamente.

 Modelos que têm valores de ordem de classificação baixos aparecem na caixa de diálogo **Novo Projeto** ou **Novo Item de Adicionar** antes de modelos que têm valores de ordem de classificação elevados.

## <a name="example"></a>Exemplo
 O exemplo a seguir ilustra os [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] metadados de um modelo de classe padrão.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>290</SortOrder>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

 Neste exemplo, `SortOrder` o elemento é relativamente alto. É provável que [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] outros modelos de `SortOrder` itens `290` tenham um valor menor do que e aparecerão antes deste modelo na caixa de diálogo **Novo item.**

## <a name="see-also"></a>Confira também
- [Referência de esquema do modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
