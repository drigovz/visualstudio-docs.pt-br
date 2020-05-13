---
title: ButtonText Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59308feea2002a18662a7c04b95a92a920f934c4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739911"
---
# <a name="buttontext-element"></a>Elemento ButtonText
Este campo permite especificar o texto que aparece em vários menus. Por padrão, `ButtonText` o elemento aparece nos controladores de menu. O `ButtonText` elemento também se torna padrão se os outros campos de texto estiverem em branco. O `ButtonText` elemento não pode estar em branco mesmo se os outros campos de texto forem especificados.

## <a name="syntax"></a>Sintaxe

```xml
<ButtonText>My Command</ButtonText>
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
|[Elemento cordas](../extensibility/strings-element.md)|Grupos de texto `ButtonText` elementos, tais como e `CommandName`.|

## <a name="text-value"></a>Valor de texto
 O valor do `ButtonText` texto do elemento fornece o texto exibido para itens de menu, combos e outros elementos de interface de usuário (UI) que têm texto visível.

## <a name="see-also"></a>Confira também
- [Arquivos da tabela de comando do Visual Studio (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
