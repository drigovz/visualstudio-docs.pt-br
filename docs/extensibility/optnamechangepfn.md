---
title: OPTNAMECHANGEPFN | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6107f48f4680cef9cbb825f4d760f3f0bac1ec1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336236"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Essa é uma função de retorno de chamada especificada em uma chamada para o [SccSetOption](../extensibility/sccsetoption-function.md) (usando a opção `SCC_OPT_NAMECHANGEPFN`) e é usado para comunicar alterações de nome feitas pelo controle de fonte de plug-in voltar ao IDE.

## <a name="signature"></a>Assinatura

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>Parâmetros
 pvCallerData

[in] Valor de usuário especificado em uma chamada anterior para o [SccSetOption](../extensibility/sccsetoption-function.md) (usando a opção `SCC_OPT_USERDATA`).

 pszOldName

[in] O nome original do arquivo.

 pszNewName

[in] O nome do arquivo foi renomeado para.

## <a name="return-value"></a>Valor retornado
 nenhuma.

## <a name="remarks"></a>Comentários
 Se um arquivo é renomeado durante uma operação de controle do código-fonte, o plug-in de controle do código-fonte pode notificar o IDE sobre a alteração de nome por meio desse retorno de chamada.

 Se o IDE não dá suporte a esse retorno de chamada, ele não chamará o [SccSetOption](../extensibility/sccsetoption-function.md) especificá-lo. Se o plug-in não suporta esse retorno de chamada, ele retornará `SCC_E_OPNOTSUPPORTED` do `SccSetOption` quando o IDE tenta definir o retorno de chamada de função.

## <a name="see-also"></a>Consulte também
- [Funções de retorno de chamada implementadas pelo IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)