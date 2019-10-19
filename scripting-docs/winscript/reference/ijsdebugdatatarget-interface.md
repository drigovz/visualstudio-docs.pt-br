---
title: Interface IJsDebugDataTarget | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 85c77209230abfe261c9ec0b884ad0a677cfbf07
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572455"
---
# <a name="ijsdebugdatatarget-interface"></a>Interface IJsDebugDataTarget
Implementado pelo depurador para fornecer funcionalidade para acessar e alterar o estado do processo do depurador de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
IJsDebugDataTarget : public IUnknown;  
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-methods"></a>Métodos Públicos  
  
|Name|Descrição|  
|----------|-----------------|  
|[Método IJsDebugDataTarget::AllocateVirtualMemory](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|Reserva e/ou confirma uma região de memória dentro do espaço de endereço virtual do processo de destino.|  
|[Método IJsDebugDataTarget::CreateStackFrameEnumerator](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|Cria um enumerador para os quadros de pilha.|  
|[Método IJsDebugDataTarget::FreeVirtualMemory](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|Libera e/ou desconfirma uma região de memória dentro do espaço de endereço virtual do processo de destino.|  
|[Método IJsDebugDataTarget::GetThreadContext](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|Recupera o contexto para determinado thread.|  
|[Método IJsDebugDataTarget::GetTlsValue](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|Para o thread que está sendo depurado, o recupera o valor no slot de armazenamento local do thread (TLS) para o índice TLS especificado.|  
|[Método IJsDebugDataTarget::ReadBSTR](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|Lê um BSTR a partir do destino de depuração.|  
|[Método IJsDebugDataTarget::ReadMemory](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|Lê a memória do processo de destino.|  
|[Método IJsDebugDataTarget::ReadNullTerminatedString](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|Lê o número especificado de caracteres do destino.|  
|[Método IJsDebugDataTarget::WriteMemory](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|Lê a memória do processo de destino.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de interfaces de script do Windows](../../winscript/reference/windows-script-interfaces-reference.md)