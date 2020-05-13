---
title: IDebugProcessSecurity | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36c81cda3a27cfe1ef0fecfefc9bbb790d4d5217
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723193"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity`é implementado por um fornecedor de porta para avisar o usuário que anexar ao processo é inseguro.

## <a name="syntax"></a>Sintaxe

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugProcessSecurity`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[Getusername](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Obtém o nome de usuário do fornecedor do porto.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Adverte um usuário que anexar ao processo de depuração é inseguro.|

## <a name="remarks"></a>Comentários
 Implemente esta interface para mostrar um aviso e permita que o usuário cancele se o processo ao qual você está anexando pode ser considerado inseguro.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Portas](../../../extensibility/debugger/ports.md)
- [Fornecedores de porta](../../../extensibility/debugger/port-suppliers.md)
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
