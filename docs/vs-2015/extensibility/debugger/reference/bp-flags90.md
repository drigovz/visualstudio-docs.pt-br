---
title: BP_FLAGS90 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9f7192eb7b2fa6d8bc886c0e601788ecba8eebcd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153501"
---
# <a name="bp_flags90"></a>BP_FLAGS90
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Enumera os valores válidos para sinalizadores opcionais. Os sinalizadores opcionais podem ser usados para especificar informações adicionais quando você define um ponto de interrupção. Essa enumeração estende a enumeração de [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE               = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION    = 0x0001,  
   BP90_FLAG_DONT_STOP          = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
typedef DWORD BP_FLAGS90;  
```  
  
```csharp  
public enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE                = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION     = 0x0001,  
   BP90_FLAG_DONT_STOP           = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 BP90_FLAG_NONE  
 Especifica um sinalizador de ponto de interrupção.  
  
 BP90_FLAG_MAP_DOCPOSITION  
 Especifica que o mecanismo de depuração (DE) deve mapear o ponto de interrupção usando a posição do documento. Isso é aplicável somente a pontos de interrupção definidos em arquivos de origem orientados por script, como páginas de Active Server (ASP).  
  
 BP90_FLAG_DONT_STOP  
 Especifica que o ponto de interrupção deve ser processado pelo mecanismo de depuração, mas que o mecanismo de depuração, por fim, não deve parar por aí; ou seja, um objeto de evento [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) não deve ser enviado. Esse sinalizador foi projetado para ser usado principalmente com pontos de rastreamento.  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 Usado pelo mecanismo de depuração nativo para determinar se o estado de depuração deve ser limpo. Ele é diferente de BP90_FLAG_DONT_STOP porque BP90_FLAG_DONT_STOP não será definido se o ponto de rastreamento executar uma macro.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg90. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
