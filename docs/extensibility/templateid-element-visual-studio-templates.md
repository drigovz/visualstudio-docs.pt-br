---
title: Elemento TemplateID (modelos do Visual Studio) | Microsoft Docs
description: Saiba mais sobre o elemento TemplateID e como ele especifica um identificador para um modelo de item que é categorizado em um grupo de modelos de item pelo elemento TemplateGroupID.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 26a0b3ef90eab7cef51e5ca65032f2f4f68acd42
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895317"
---
# <a name="templateid-element-visual-studio-templates"></a>Elemento TemplateID (modelos do Visual Studio)
Especifica um identificador para um modelo de item que é categorizado em um grupo de modelos de item pelo elemento [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) .

 \<VSTemplate> \<TemplateData>
 \<TemplateID>

## <a name="syntax"></a>Sintaxe

```
<TemplateID> ... </TemplateID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento necessário.<br /><br /> Categoriza o modelo e define como ele é exibido no **novo projeto** ou na caixa de diálogo **Adicionar novo item** .|

## <a name="text-value"></a>Valor de texto
 Um `string` que representa um identificador para um modelo de item que é categorizado em um grupo de modelos de item pelo `TemplateGroupID` elemento.

## <a name="remarks"></a>Comentários
 `TemplateID` é um elemento opcional.

 Se um arquivo. vstemplate omitir o `TemplateID` elemento, o elemento [Name](../extensibility/name-element-visual-studio-templates.md) será usado como o identificador para o modelo.

 O valor do `TemplateID` elemento é usado junto com o registro do sistema do projeto (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects\\ ) para filtrar os modelos que aparecem na caixa de diálogo **Adicionar novo item** .

## <a name="see-also"></a>Confira também
- [Referência de esquema do modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
