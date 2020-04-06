---
title: IDebugPortEx2::Lançamento suspenso | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28ff6065bbe83852b5acc3ffe253a0bdabcc67ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725102"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
Lança um arquivo executável.

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

## <a name="parameters"></a>parâmetros
`pszExe`\
[em] O nome do executável a ser lançado. Este pode ser um caminho completo ou relativo `pszDir` ao diretório de trabalho especificado no parâmetro.

`pszArgs`\
[em] Os argumentos para passar para o executável. Pode ser um valor nulo se não houver argumentos.

`pszDir`\
[em] O nome do diretório de trabalho usado pelo executável. Pode ser um valor nulo se nenhum diretório de trabalho for necessário.

`bstrEnv`\
[em] Bloco de ambiente de strings com término nulo, seguido de um exterminador NULL adicional.

`hStdInput`\
[em] Manuseie para um fluxo de entrada alternativo. Pode ser 0 se o redirecionamento não for necessário.

`hStdOutput`\
[em] Manuseie para um fluxo de saída alternativo. Pode ser 0 se o redirecionamento não for necessário.

`hStdError`\
[em] Manuseie para um fluxo de saída de erro alternativo. Pode ser 0 se o redirecionamento não for necessário.

`ppPortProcess`\
[fora] Retorna um objeto [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) que representa o processo iniciado.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Este método deve iniciar o processo para que ele seja suspenso e não executando nenhum código. O método [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) é chamado para retomar o processo.

 Um programa também pode ser lançado a partir de um motor de depuração. Para obter detalhes, consulte [O Lançamento de um Programa](../../../extensibility/debugger/launching-a-program.md).

## <a name="see-also"></a>Confira também
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Inicializando um programa](../../../extensibility/debugger/launching-a-program.md)
