---
title: IDebugDefaultPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f560a3dabefb0a8dede6520dcd8fd47f609a7780
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732319"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Esta interface fornece vários métodos para acessar as instalações de servidor e notificação de uma porta.

## <a name="syntax"></a>Sintaxe

```
IDebugDefaultPort2 : IDebugPort2
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O Visual Studio implementa esta interface para representar a porta de depuração para acesso a programas. Um fornecedor de porta personalizado também pode implementar essa interface se lidar com a depuração remota.

## <a name="notes-for-callers"></a>Observações para chamadores
 Um argumento para métodos na interface [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) fornece essa interface. Chamar [queryInterface](/cpp/atl/queryinterface) em uma interface [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) também pode obter essa interface.

## <a name="methods-in-vtable-order"></a>Métodos em ordem Vtable
 Além dos métodos definidos no [IDebugPort2,](../../../extensibility/debugger/reference/idebugport2.md)esta interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Obtém a interface de notificação da porta a partir desta porta.|
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Obtém a interface para o servidor que hospeda esta porta.|
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Determina se esta porta está funcionando na máquina local.|

## <a name="remarks"></a>Comentários
 O nome`IDebugDefaultPort2`" " é um pouco de um equívoco, pois não representa uma porta padrão. Pode se chamar "IDebugPort3".

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
