---
title: Elemento TemplateGroupID (modelos do Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9219b764125727509807cc6f2b9fdf6400e97f2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685242"
---
# <a name="templategroupid-element-visual-studio-templates"></a>Elemento TemplateGroupID (modelos do Visual Studio)
Especifica o tipo de projeto um modelos de item aparecerá no. Esse elemento é significativo quando [ShowByDefault (modelos do Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) é definido como `false`. Quando [ShowByDefault (modelos do Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) é definido como `true`, em seguida, um modelo de item está disponível em todos os tipos de projeto.

 \<VSTemplate> \<TemplateData> \<TemplateGroupID>

## <a name="syntax"></a>Sintaxe

```
<TemplateGroupID> ... </TemplateGroupID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Categoriza o modelo e define como ele é exibido em qualquer um de **novo projeto** ou o **Adicionar Novo Item** caixa de diálogo.|

## <a name="text-value"></a>Valor de texto
 Um valor de texto é obrigatório.

 O texto Especifica um identificador para uma categoria de modelos de item.

## <a name="remarks"></a>Comentários
 `TemplateGroupID` é um elemento.

 O valor de `TemplateGroupID` elemento é usado junto com o registro do sistema de projeto (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<número de versão >* \Projects\\) para modelos de filtro que aparecem na **Adicionar Novo Item** caixa de diálogo.

|Valor do Visual C++|Significado|
|------------------------|-------------|
|VC nativo|Usado para projetos nativos. Também o padrão se um tipo de projeto não pode ser determinado.|
|VC gerenciados|Usado para gerenciados (/ clr) projetos|
|VC-Windows|Usado para todos os projetos que usam a plataforma do windows (nativo/gerenciado/store)|
|WinRT-Native-UAP|Usado para projetos de armazenamento do Windows 10|
|CodeSharing-Native|Usado para projetos de item compartilhado|
|WinRT-Native-6.3|Usado para projetos do Windows 8.1 Store|
|WinRT-Native-Phone-6.3|Usado para projetos do Windows Phone 8.1|
|WinRT-Native|Usado para projetos do Windows 8.0 Store|
|VC-Android|Usado para projetos do Android|

## <a name="see-also"></a>Consulte também
- [Referência de esquema do modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)