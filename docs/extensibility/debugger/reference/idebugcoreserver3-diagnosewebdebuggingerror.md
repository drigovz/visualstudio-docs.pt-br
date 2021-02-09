---
title: IDebugCoreServer3::D iagnoseWebDebuggingError | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
helpviewer_keywords:
- IDebugCoreServer3::DiagnoseWebDebuggingError
ms.assetid: 8c4570ca-ae55-42f2-bbaa-8d8e75d2fa19
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6c95c3953b70235daa739e48b5de50b4a815b13
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908054"
---
# <a name="idebugcoreserver3diagnosewebdebuggingerror"></a>IDebugCoreServer3::DiagnoseWebDebuggingError
Tenta determinar por que uma conexão automática falhou.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT DiagnoseWebDebuggingError(
   LPCWSTR pszUrl
);
```

```csharp
int DiagnoseWebDebuggingError(
   string pszUrl
);
```

## <a name="parameters"></a>Parâmetros
`pszUrl`\
no Não usado atualmente; deve sempre ser definido como um valor nulo.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro. A seguir estão outros códigos de retorno típicos:

|Código|Descrição|
|----------|-----------------|
|`S_WEBDBG_UNABLE_TO_DIAGNOSE`|Não é possível determinar por que o servidor remoto falhou ao iniciar a depuração.|
|`S_WEBDBG_DEBUG_VERB_BLOCKED`|Não é possível depurar no servidor remoto, possivelmente devido a permissões insuficientes ou porque o verbo de depuração não está habilitado.|
|`E_WEBDBG_DEBUG_VERB_BLOCKED`|O servidor Web foi bloqueado e está bloqueando o verbo DEBUG, que é necessário para habilitar a depuração.|

## <a name="see-also"></a>Confira também
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
