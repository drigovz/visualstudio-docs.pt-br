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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188570"
---
# <a name="idebugport2"></a>IDebugPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface representa uma porta de depuração em um computador.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 Um fornecedor de porta personalizado implementa essa interface para representar uma porta de depuração em um computador.  
  
 Se a porta der suporte ao envio de eventos de porta, ela também deverá implementar a <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface para dar suporte a uma <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface que, por sua vez, fornece a interface [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) .  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 As chamadas para [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) ou [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) retornam essa interface, representando a porta solicitada.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 A tabela a seguir mostra os métodos de `IDebugPort2` .  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Retorna o nome da porta.|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Retorna o identificador de porta.|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Retorna a solicitação usada para criar uma porta (se disponível).|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Retorna o fornecedor da porta para esta porta.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Retorna uma interface para o processo de acordo com o identificador do processo.|  
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Enumera todos os processos em execução em uma porta.|  
  
## <a name="remarks"></a>Comentários  
 A porta local fornece acesso a todos os processos e programas em execução no computador local. Outras portas podem representar uma conexão de cabo serial com um dispositivo baseado em Windows CE ou uma conexão de rede com um computador não DCOM. A `IDebugPort2` interface é usada para localizar o nome e o identificador de uma porta, enumerar todos os processos em execução na porta e fornecer recursos para iniciar e encerrar processos na porta.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Interfaces principais](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
