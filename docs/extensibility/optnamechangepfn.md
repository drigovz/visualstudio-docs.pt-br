---
title: OPTNAMECHANGEPFN | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 603bd08c1ec3832bf732e0b33101076738d009e3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702244"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Esta é uma função de retorno de chamada especificada em `SCC_OPT_NAMECHANGEPFN`uma chamada para o [SccSetOption](../extensibility/sccsetoption-function.md) (usando opção) e é usada para comunicar alterações de nome feitas pelo plug-in de controle de origem de volta ao IDE.

## <a name="signature"></a>Assinatura

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>parâmetros
 pvCallerData

[em] Valor do usuário especificado em uma chamada anterior `SCC_OPT_USERDATA`para o [SccSetOption](../extensibility/sccsetoption-function.md) (utilização da opção ).

 pszOldName

[em] O nome original do arquivo.

 pszNewName

[em] O nome para o nome do arquivo foi renomeado.

## <a name="return-value"></a>Valor retornado
 Nenhum.

## <a name="remarks"></a>Comentários
 Se um arquivo for renomeado durante uma operação de controle de origem, o plug-in de controle de origem poderá notificar o IDE sobre a alteração de nome através deste retorno de chamada.

 Se o IDE não suportar esse retorno de chamada, ele não chamará a [Opção SccSet](../extensibility/sccsetoption-function.md) para especificá-la. Se o plug-in não suportar esse retorno `SCC_E_OPNOTSUPPORTED` de `SccSetOption` chamada, ele retornará da função quando o IDE tentar definir a chamada de volta.

## <a name="see-also"></a>Confira também
- [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
