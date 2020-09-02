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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: affc324418e3745f85fb0b91a0ef7abda0ab28b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699071"
---
# <a name="templategroupid-element-visual-studio-templates"></a>Elemento TemplateGroupID (modelos do Visual Studio)
Especifica que tipo de projeto um modelo de item será exibido. Esse elemento é significativo quando [ShowByDefault (modelos do Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) é definido como `false` . Quando [ShowByDefault (modelos do Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) é definido como `true` , um modelo de item está disponível em todos os tipos de projeto.

 \<VSTemplate> \<TemplateData>
 \<TemplateGroupID>

## <a name="syntax"></a>Sintaxe

```
<TemplateGroupID> ... </TemplateGroupID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Categoriza o modelo e define como ele é exibido no **novo projeto** ou na caixa de diálogo **Adicionar novo item** .|

## <a name="text-value"></a>Valor de texto
 Um valor de texto é obrigatório.

 O texto especifica um identificador para uma categoria de modelos de item.

## <a name="remarks"></a>Comentários
 `TemplateGroupID` é um elemento.

 O valor do `TemplateGroupID` elemento é usado junto com o registro do sistema de projeto (HKEY_LOCAL_MACHINE \Software\microsoft\visualstudio \\ *\<version number>* \projects \\ ) para filtrar os modelos que aparecem na caixa de diálogo **Adicionar novo item** .

|Valor Visual C++|Significado|
|------------------------|-------------|
|VC-nativo|Usado para projetos nativos. Também o padrão se um tipo de projeto não puder ser determinado.|
|Gerenciado por VC|Usado para projetos gerenciados (/CLR)|
|VC-Windows|Usado para todos os projetos destinados à plataforma Windows (nativo/gerenciado/de armazenamento)|
|WinRT-Native-UAP|Usado para projetos da Windows 10 Store|
|CodeSharing-nativo|Usado para projetos de item compartilhado|
|WinRT-nativo-6,3|Usado para projetos de Windows 8.1 Store|
|WinRT-nativo-telefone-6,3|Usado para projetos Windows Phone 8,1|
|WinRT-nativo|Usado para projetos da Windows 8,0 Store|
|VC-Android|Usado para projetos Android|

## <a name="see-also"></a>Confira também
- [Referência de esquema do modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
