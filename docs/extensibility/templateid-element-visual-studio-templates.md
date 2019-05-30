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
ms.openlocfilehash: e8207b72d7bb818a5d153abdd56914fd6b2a3f08
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316546"
---
# <a name="templateid-element-visual-studio-templates"></a>Elemento TemplateID (modelos do Visual Studio)
Especifica um identificador para um modelo de item é categorizado em um grupo de modelos de item, o [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) elemento.

 \<VSTemplate> \<TemplateData> \<TemplateID>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obrigatório.<br /><br /> Categoriza o modelo e define como ele é exibido em qualquer um de **novo projeto** ou o **Adicionar Novo Item** caixa de diálogo.|

## <a name="text-value"></a>Valor de texto
 Um `string` que representa um identificador para um modelo de item é categorizado em um grupo de modelos de item pelo `TemplateGroupID` elemento.

## <a name="remarks"></a>Comentários
 `TemplateID` é um elemento opcional.

 Se um arquivo. vstemplate omite a `TemplateID` elemento, em seguida, a [nome](../extensibility/name-element-visual-studio-templates.md) elemento é usado como o identificador para o modelo.

 O valor da `TemplateID` elemento é usado junto com o registro do sistema de projeto (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects\\) para modelos de filtro que aparecem na **Adicionar Novo Item** caixa de diálogo.

## <a name="see-also"></a>Consulte também
- [Referência de esquema do modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)