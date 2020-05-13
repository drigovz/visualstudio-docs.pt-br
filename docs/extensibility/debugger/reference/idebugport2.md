---
title: IDebugPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62912be9fdfecc98a264a58c9713cc12ccaf28f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725235"
---
# <a name="idebugport2"></a>IDebugPort2
Esta interface representa uma porta de depuração em uma máquina.

## <a name="syntax"></a>Sintaxe

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Um fornecedor de porta personalizado implementa essa interface para representar uma porta de depuração em uma máquina.

 Se a porta suportar o envio de <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> eventos de <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> porta, ele também deve implementar a interface para suportar uma interface que, por sua vez, fornece a interface [IDebugPortEvents2.](../../../extensibility/debugger/reference/idebugportevents2.md)

## <a name="notes-for-callers"></a>Observações para chamadores
 Chamadas para [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) ou [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) retornam esta interface, representando a porta solicitada.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugPort2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Retorna o nome da porta.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Retorna o identificador de porta.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Retorna a solicitação usada para criar uma porta (se disponível).|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Devolve o fornecedor de porto para esta porta.|
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Retorna uma interface ao processo dado o identificador do processo.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Enumera todos os processos em execução em uma porta.|

## <a name="remarks"></a>Comentários
 A porta local fornece acesso a todos os processos e programas em execução na máquina local. Outras portas podem representar uma conexão de cabo serial a um dispositivo baseado no Windows CE ou uma conexão de rede a um computador não-DCOM. A `IDebugPort2` interface é usada para encontrar o nome e o identificador de uma porta e enumerar todos os processos em execução na porta. As facilidades para iniciar e encerrar processos `IDebugPortEx2` na porta são implementadas na interface.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
