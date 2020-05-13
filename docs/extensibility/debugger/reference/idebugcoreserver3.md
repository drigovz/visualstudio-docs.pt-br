---
title: IDebugCoreServer3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d110e66e937249fdee34f424d4f68a9b914113d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732812"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Esta interface dá acesso a informações sobre o servidor em que o processo está sendo executado.

## <a name="syntax"></a>Sintaxe

```
IDebugCoreServer3 : IDebugCoreServer2
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O Visual Studio implementa essa interface.

## <a name="notes-for-callers"></a>Observações para chamadores
 Use [queryInterface](/cpp/atl/queryinterface) para obter esta interface a partir de uma interface [IDebugCoreServer2.](../../../extensibility/debugger/reference/idebugcoreserver2.md) Uma chamada para [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) também pode retornar esta interface. Essa interface é usada mais frequentemente por um fornecedor de porta personalizado para lançar programas em um servidor (local ou remoto).

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 Além dos métodos na interface [IDebugCoreServer2,](../../../extensibility/debugger/reference/idebugcoreserver2.md) esta interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[Obternome de servidor](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Recupera o nome do servidor.|
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Recupera uma versão amigável do nome do servidor|
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Informa os mecanismos específicos de depuração para se conectar automaticamente aos processos quando esses processos começarem.|
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Recupera um código de erro específico quando o attach automático falha.|
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Cria uma instância de um mecanismo de depuração no servidor.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Recupera um sinalizador indicando se o servidor está na mesma máquina que o chamador.|
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Recupera um valor que indica o protocolo que está sendo usado para se comunicar com o servidor.|
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Desativa todas as configurações de conexão automática para todos os motores de depuração que este servidor conhece.|

## <a name="remarks"></a>Comentários
 Um fornecedor de porta personalizado recebe a interface [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) em uma chamada para [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md). A `IDebugCoreServer3` interface pode ser obtida a partir dessa interface.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
