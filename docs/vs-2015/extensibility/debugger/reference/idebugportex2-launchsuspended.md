---
title: 'IDebugPortEx2:: LaunchSuspended | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3c5e57c003257650f5ca60d4a7c3d9becea3e776
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188454"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Inicia um arquivo executável.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parâmetros  
 `pszExe`  
 no O nome do executável a ser iniciado. Isso pode ser um caminho completo ou relativo ao diretório de trabalho especificado no `pszDir` parâmetro.  
  
 `pszArgs`  
 no Os argumentos a serem passados para o executável. Pode ser um valor nulo se não houver argumentos.  
  
 `pszDir`  
 no O nome do diretório de trabalho usado pelo executável. Pode ser um valor nulo se nenhum diretório de trabalho for necessário.  
  
 `bstrEnv`  
 no Bloco de ambiente de cadeias de caracteres terminadas em nulo, seguido por um terminador nulo adicional.  
  
 `hStdInput`  
 no Identificador para um fluxo de entrada alternativo. Pode ser 0 se o redirecionamento não for necessário.  
  
 `hStdOutput`  
 no Identificador para um fluxo de saída alternativo. Pode ser 0 se o redirecionamento não for necessário.  
  
 `hStdError`  
 no Identificador para um fluxo de saída de erro alternativo. Pode ser 0 se o redirecionamento não for necessário.  
  
 `ppPortProcess`  
 fora Retorna um objeto [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) que representa o processo iniciado.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método deve iniciar o processo para que ele seja suspenso e não execute nenhum código. O método [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) é chamado para retomar o processo.  
  
 Um programa também pode ser iniciado por meio de um mecanismo de depuração. Para obter detalhes, consulte [iniciando um programa](../../../extensibility/debugger/launching-a-program.md).  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)   
 [Inicializando um programa](../../../extensibility/debugger/launching-a-program.md)
