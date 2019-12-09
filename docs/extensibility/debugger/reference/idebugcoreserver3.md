---
title: IDebugCoreServer3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f9a8e6e16aa9279bb7324f5d08f0da3035f2b85
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343991"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Essa interface fornece acesso às informações sobre o processo está em execução no servidor.

## <a name="syntax"></a>Sintaxe

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Visual Studio implementa essa interface.

## <a name="notes-for-callers"></a>Observações para chamadores
 Use [QueryInterface](/cpp/atl/queryinterface) para obter essa interface de um [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interface. Uma chamada para [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) também pode retornar a esta interface. Essa interface é usada com mais frequência por um fornecedor de porta personalizado para iniciar programas em um servidor (local ou remoto).

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 Além dos métodos na [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interface, essa interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Recupera o nome do servidor.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Recupera uma versão amigável do nome do servidor|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Informa os mecanismos de depuração específicas para anexar automaticamente a processos quando iniciar esses processos.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Recupera um código de erro específico ao Falha ao anexar automático.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Cria uma instância de um mecanismo de depuração no servidor.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Recupera um sinalizador que indica se o servidor está no mesmo computador que o chamador.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Recupera um valor que indica o protocolo usado para se comunicar com o servidor.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Desabilita todos os a anexação automática as configurações para todos os mecanismos de depuração, que esse servidor sabe sobre.|

## <a name="remarks"></a>Comentários
 Um fornecedor de porta personalizada recebe o [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interface em uma chamada para [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md). O `IDebugCoreServer3` interface pode ser obtido da interface.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)