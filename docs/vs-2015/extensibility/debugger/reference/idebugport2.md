---
title: IDebugPort2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c9227e2e05499feac628a5b90fc6e3d2a4399992
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922968"
---
# <a name="idebugport2"></a>IDebugPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface representa uma porta de depuração em um computador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um fornecedor de porta personalizada implementa essa interface para representar uma porta de depuração em um computador.  
  
 Se a porta dá suporte ao envio de eventos de porta, ele também deverá implementar o <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface para oferecer suporte a uma <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface que por sua vez fornece a [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamadas para [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) ou [adicionar porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) retornar essa interface, que representa a porta solicitada.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugPort2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Retorna o nome da porta.|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Retorna o identificador de porta.|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Retorna a solicitação usada para criar uma porta (se disponível).|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Retorna o fornecedor de porta para essa porta.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Retorna uma interface para o processo que recebe o identificador do processo.|  
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Enumera todos os processos em execução em uma porta.|  
  
## <a name="remarks"></a>Comentários  
 A porta local fornece acesso a todos os processos e programas em execução no computador local. Outras portas podem representar uma conexão de cabo serial para um dispositivo baseado em Windows CE ou uma conexão de rede em um computador não-DCOM. O `IDebugPort2` interface é usada para localizar o nome e identificador de uma porta, enumerar todos os processos em execução na porta e fornecer recursos para iniciar e encerrar processos na porta.  
  
## <a name="requirements"></a>Requisitos  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Principais Interfaces](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
