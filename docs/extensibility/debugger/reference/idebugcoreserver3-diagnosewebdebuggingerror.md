---
title: IDebugCoreServer3::DiagnoseWebDebuggingError | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 52b6d634da7cda9c7b90b8cd4f7d93e7accc033d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317791"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Falha nas tentativas de determinar o motivo pelo qual um auto-attach.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
);
```

## <a name="parameters"></a>Parâmetros
`pszUrl`\
[in] Não usado no momento; sempre deve ser definido como um valor nulo.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. Estes são os outros códigos de retorno típicos:

|Código|Descrição|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Não é possível determinar o motivo de falha de servidor remoto iniciar a depuração.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Não é possível depurar em um servidor remoto, possivelmente devido a permissões insuficientes ou porque o verbo DEBUG não está habilitado.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|O servidor web foi bloqueado e está bloqueando o verbo DEBUG, que é necessário para habilitar a depuração.|

## <a name="see-also"></a>Consulte também
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)