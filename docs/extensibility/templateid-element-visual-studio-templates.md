---
title: Elemento TemplateID (modelos do Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0e404921d1ed74db2a1f23117242f49a07206c2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718733"
---
# <a name="templateid-element-visual-studio-templates"></a>Elemento TemplateID (modelos do Visual Studio)
Especifica um identificador para um modelo de item que é categorizado em um grupo de modelos de item pelo elemento [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) .

 \<VSTemplate > \<TemplateData > \<TemplateID >

## <a name="syntax"></a>Sintaxe

```
<TemplateID> ... </TemplateID>
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
 Um `string` que representa um identificador para um modelo de item que é categorizado em um grupo de modelos de item pelo elemento `TemplateGroupID`.

## <a name="remarks"></a>Comentários
 `TemplateID` é um elemento opcional.

 Se um arquivo. vstemplate omitir o elemento `TemplateID`, o elemento [Name](../extensibility/name-element-visual-studio-templates.md) será usado como o identificador para o modelo.

 O valor do elemento `TemplateID` é usado junto com o registro do sistema de projeto (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects \\) para filtrar os modelos que aparecem na caixa de diálogo **Adicionar novo item** .

## <a name="see-also"></a>Consulte também
- [Referência de esquema do modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)