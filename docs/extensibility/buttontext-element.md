---
title: Elemento ButtonText | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe2440258e95ad0d61998b24dae54b731a998c47
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321221"
---
# <a name="buttontext-element"></a>Elemento ButtonText
Este campo permite especificar o texto que aparece em vários menus. Por padrão, o `ButtonText` elemento aparece em controladores de menu. O `ButtonText` elemento também se tornará o padrão se campos de texto estiverem em branco. O `ButtonText` elemento não pode ficar em branco, mesmo se os outros campos de texto forem especificados.

## <a name="syntax"></a>Sintaxe

```xml
<ButtonText>My Command</ButtonText>
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
|[Elemento Strings](../extensibility/strings-element.md)|Agrupa os elementos de texto, como `ButtonText` e `CommandName`.|

## <a name="text-value"></a>Valor de texto
 O valor de texto o `ButtonText` elemento fornece o texto que é exibido para itens de menu, combos e outros elementos de (UI) de interface de usuário que tenham texto visível.

## <a name="see-also"></a>Consulte também
- [Arquivos de tabela (. VSCT) de comando do Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)