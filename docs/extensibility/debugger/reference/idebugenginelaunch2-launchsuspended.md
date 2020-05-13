---
title: IDebugEngineLaunch2::Lançamento suspenso | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e802c17d0a93aabbe5c6c0a8573abc6a551944ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730548"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
Este método inicia um processo por meio do motor de depuração (DE).

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT LaunchSuspended ( 
   LPCOLESTR             pszMachine,
   IDebugPort2*          pPort,
   LPCOLESTR             pszExe,
   LPCOLESTR             pszArgs,
   LPCOLESTR             pszDir,
   BSTR                  bstrEnv,
   LPCOLESTR             pszOptions,
   LAUNCH_FLAGS          dwLaunchFlags,
   DWORD                 hStdInput,
   DWORD                 hStdOutput,
   DWORD                 hStdError,
   IDebugEventCallback2* pCallback,
   IDebugProcess2**      ppDebugProcess
);
```

```csharp
int LaunchSuspended(
   string               pszServer,
   IDebugPort2          pPort,
   string               pszExe,
   string               pszArgs,
   string               pszDir,
   string               bstrEnv,
   string               pszOptions,
   enum_LAUNCH_FLAGS    dwLaunchFlags,
   uint                 hStdInput,
   uint                 hStdOutput,
   uint                 hStdError,
   IDebugEventCallback2 pCallback,
   out IDebugProcess2   ppProcess
);
```

## <a name="parameters"></a>parâmetros
`pszMachine`\
[em] O nome da máquina para iniciar o processo. Use um valor nulo para especificar a máquina local.

`pPort`\
[em] A interface [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) representando a porta em que o programa será executado.

`pszExe`\
[em] O nome do executável a ser lançado.

`pszArgs`\
[em] Os argumentos para passar para o executável. Pode ser um valor nulo se não houver argumentos.

`pszDir`\
[em] O nome do diretório de trabalho usado pelo executável. Pode ser um valor nulo se nenhum diretório de trabalho for necessário.

`bstrEnv`\
[em] Bloco de ambiente de strings com término nula, seguido de um exterminador NULL adicional.

`pszOptions`\
[em] As opções para o executável.

`dwLaunchFlags`\
[em] Especifica o [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) para uma sessão.

`hStdInput`\
[em] Manuseie para um fluxo de entrada alternativo. Pode ser 0 se o redirecionamento não for necessário.

`hStdOutput`\
[em] Manuseie para um fluxo de saída alternativo. Pode ser 0 se o redirecionamento não for necessário.

`hStdError`\
[em] Manuseie para um fluxo de saída de erro alternativo. Pode ser 0 se o redirecionamento não for necessário.

`pCallback`\
[em] O objeto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que recebe eventos de depurador.

`ppDebugProcess`\
[fora] Retorna o objeto [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) resultante que representa o processo iniciado.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Normalmente, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] inicia um programa usando o método [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) e, em seguida, anexa o depurador ao programa suspenso. No entanto, existem circunstâncias em que o motor de depuração pode precisar iniciar um programa (por exemplo, se o mecanismo [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] de `IDebugEngineLaunch2::LaunchSuspended` depuração faz parte de um intérprete e o programa que está sendo depurado é uma linguagem interpretada), nesse caso usa o método.

 O método [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) é chamado para iniciar o processo depois que o processo foi iniciado com sucesso em um estado suspenso.

## <a name="see-also"></a>Confira também
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)
