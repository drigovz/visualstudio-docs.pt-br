---
title: IDebugPortEx2::LaunchSuspended | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94810761e546b0cae9eca32fc76bc0bfd396c7e7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311125"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
Um arquivo executável é iniciado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT LaunchSuspended( 
   LPCOLESTR        pszExe,
   LPCOLESTR        pszArgs,
   LPCOLESTR        pszDir,
   BSTR             bstrEnv,
   DWORD            hStdInput,
   DWORD            hStdOutput,
   DWORD            hStdError,
   IDebugProcess2** ppPortProcess
);
```

```csharp
int LaunchSuspended( 
   string             pszExe,
   string             pszArgs,
   string             pszDir,
   string             bstrEnv,
   uint               hStdInput,
   uint               hStdOutput,
   uint               hStdError,
   out IDebugProcess2 ppPortProcess
);
```

## <a name="parameters"></a>Parâmetros
`pszExe`\
[in] O nome do executável a ser iniciado. Isso pode ser um caminho completo ou relativo ao diretório de trabalho especificado no `pszDir` parâmetro.

`pszArgs`\
[in] Os argumentos a serem passados para o executável. Pode ser um valor nulo se não houver nenhum argumento.

`pszDir`\
[in] O nome do diretório de trabalho usado pelo executável. Pode ser um valor nulo se nenhum diretório de trabalho é necessário.

`bstrEnv`\
[in] Bloco de ambiente de cadeias de caracteres terminada em nulo, seguido por um terminador nulo adicional.

`hStdInput`\
[in] Identificador para um fluxo de entrada alternativo. Pode ser 0 se o redirecionamento não for necessário.

`hStdOutput`\
[in] Identificador para um fluxo de saída alternativos. Pode ser 0 se o redirecionamento não for necessário.

`hStdError`\
[in] Identificador para um fluxo de saída de erro alternativa. Pode ser 0 se o redirecionamento não for necessário.

`ppPortProcess`\
[out] Retorna um [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) objeto que representa o processo iniciado.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método deve iniciar o processo de forma que ele está suspenso e não executar qualquer código. O [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) método é chamado para retomar o processo.

 Um programa também pode ser iniciado de um mecanismo de depuração. Para obter detalhes, consulte [inicializando um programa](../../../extensibility/debugger/launching-a-program.md).

## <a name="see-also"></a>Consulte também
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Inicializando um programa](../../../extensibility/debugger/launching-a-program.md)