---
title: IDebugModule2::ReloadSymbols_Deprecated | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc5651a85ccc89a8a084c608e3fc698aa326e07c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56721297"
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
OBSOLETO. NÃO USE. Recarrega os símbolos para esse módulo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT ReloadSymbols( 
   LPCOLESTR pszUrlToSymbols,
   BSTR*     pbstrDebugMessage
);
```

```csharp
int ReloadSymbols( 
   string     pszUrlToSymbols,
   out string pbstrDebugMessage
);
```

#### <a name="parameters"></a>Parâmetros
 `pszUrlToSymbols`

 [in] O caminho para o repositório de símbolos.

 `pbstrDebugMessage`

 [out] Retorna uma mensagem informativa, como uma mensagem de status ou erro, que é exibida à direita do nome do módulo na janela de módulos.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. Um mecanismo de depuração deve retornar sempre `E_FAIL`.

## <a name="remarks"></a>Comentários
 Esse método não é mais suportado. Implemente a [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) método em vez disso.

## <a name="see-also"></a>Consulte também
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)