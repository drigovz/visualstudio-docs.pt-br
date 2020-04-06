---
title: TemplateGroupID Element (Modelos de Estúdio Visual) | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699071"
---
# <a name="templategroupid-element-visual-studio-templates"></a>Elemento TemplateGroupID (modelos do Visual Studio)
Especifica em que tipo de projeto aparecerá um modelo de item. Esse elemento é significativo quando [o ShowByDefault (Visual Studio Templates)](../extensibility/showbydefault-visual-studio-templates.md) é definido como `false`. Quando [o ShowByDefault (Visual Studio Templates)](../extensibility/showbydefault-visual-studio-templates.md) é definido como `true`, então um modelo de item está disponível em todos os tipos de projeto.

 \<VSTemplate \<> TemplateData> \<TemplateGroupID>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Categoriza o modelo e define como ele é exibido no **Novo Projeto** ou na caixa de diálogo Adicionar **novo item.**|

## <a name="text-value"></a>Valor de texto
 Um valor de texto é obrigatório.

 O texto especifica um identificador para uma categoria de modelos de itens.

## <a name="remarks"></a>Comentários
 `TemplateGroupID`é um elemento.

 O valor `TemplateGroupID` do elemento é usado juntamente com o registro\\do sistema de projeto (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio*\<número de versão>* \Projetos\\) para filtrar modelos que aparecem na caixa de diálogo Adicionar novo **item.**

|Valor Visual C++|Significado|
|------------------------|-------------|
|Nativo de VC|Usado para projetos nativos. Também o padrão se um tipo de projeto não puder ser determinado.|
|Vc-Gerenciado|Usado para projetos gerenciados (/clr)|
|VC-Windows|Usado para todos os projetos que visam a plataforma windows (nativo/gerenciado/armazenamento)|
|WinRT-Native-UAP|Usado para projetos de loja do Windows 10|
|Nativo do compartilhamento de código|Usado para projetos de itens compartilhados|
|WinRT-Native-6.3|Usado para projetos de loja do Windows 8.1|
|WinRT-Native-Phone-6.3|Usado para projetos do Windows Phone 8.1|
|Nativo de WinRT|Usado para projetos de loja do Windows 8.0|
|VC-Android|Usado para projetos Android|

## <a name="see-also"></a>Confira também
- [Referência de esquema do modelo do Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Criando modelos de projeto e de item](../ide/creating-project-and-item-templates.md)
