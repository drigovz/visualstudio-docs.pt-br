---
title: Elemento SortOrder (modelos do Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2875bcb4583c1d2ec47a935d1a8bb4f0de109a92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719921"
---
# <a name="sortorder-element-visual-studio-templates"></a>Elemento SortOrder (modelos do Visual Studio)
Especifica um valor que é usado para organizar o modelo, entre outros modelos na mesma categoria, como aparece na caixa de diálogo **novo projeto** ou **Adicionar novo item** .

 \<VSTemplate > \<TemplateData > \<SortOrder >

## <a name="syntax"></a>Sintaxe

```
<SortOrder> ... </SortOrder>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obrigatório.<br /><br /> Categoriza o modelo e define como ele é exibido no **novo projeto** ou na caixa de diálogo **Adicionar novo item** .|

## <a name="text-value"></a>Valor de texto
 Um valor de texto é obrigatório.

 Um `integer` que representa o valor da ordem de classificação.

## <a name="remarks"></a>Comentários
 `SortOrder` é um elemento opcional. O valor padrão é 100 e todos os valores devem ser múltiplos de 10.

 O elemento `SortOrder` é ignorado para modelos criados pelo usuário. Todos os modelos criados pelo usuário são classificados alfabeticamente.

 Os modelos que têm valores de ordem de classificação baixa aparecem na caixa de diálogo **novo projeto** ou **novo item de adição** , antes dos modelos que têm valores de ordem de classificação alta.

## <a name="example"></a>Exemplo
 O exemplo a seguir ilustra os metadados de um modelo de classe de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] padrão.

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

 Neste exemplo, o elemento `SortOrder` é relativamente alto. É provável que outros modelos de item de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] tenham um valor de `SortOrder` inferior a `290` e aparecerão antes desse modelo na caixa de diálogo **novo item** .

## <a name="see-also"></a>Consulte também
- [Referência de esquema do modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)