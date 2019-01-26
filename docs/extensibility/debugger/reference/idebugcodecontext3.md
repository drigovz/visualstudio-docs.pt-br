---
title: IDebugCodeContext3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e9ff7ac48c745416dbbed799521048997fba5662
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54956435"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Estende o [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) interface para ativar a recuperação das interfaces do módulo e o processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Implementado por mecanismos de depuração e consumido pelo [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] pacote de depuração.  
  
## <a name="methods"></a>Métodos  
 Além dos métodos no `IDebugCodeContext2` interface, essa interface implementa os seguintes métodos:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Recupera uma referência à interface do módulo de depuração.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Recupera uma referência à interface do processo de depuração.|  
  
## <a name="remarks"></a>Comentários  
 Esta é uma interface opcional que geralmente não precisa ser implementado.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll