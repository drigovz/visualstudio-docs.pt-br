---
title: IDebugCoreServer2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c0bca6ccd3738518df339084b0f6463be181e52d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192911"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface é usada para representar e obter informações de um servidor em um computador na rede.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Visual Studio implementa essa interface para representar um servidor. Cada instância do Visual Studio cria uma instância dessa interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Um fornecedor de porta personalizada recebe essa interface em uma chamada para [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Um mecanismo de depuração pode obter essa interface indiretamente por meio de uma chamada para [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (que retorna [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), uma interface que é derivada de `IDebugCoreServer2`).  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugCoreServer2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Obtém o nome e os atributos de uma máquina.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Obtém o nome de uma máquina.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Obtém um fornecedor de porta que existe em um computador.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Obtém uma porta que já existe em um computador.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Cria um enumerador para todas as portas em um computador.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Cria um enumerador para todos os fornecedores de porta em um computador.|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Obtém os utilitários de máquina para uma máquina.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface também é usada pelo Visual Studio para navegar os processos em execução em computadores na rede.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
