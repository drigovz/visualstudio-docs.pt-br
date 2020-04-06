---
title: IDebugProgram2::Anexar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d0b182ba7a873816e3a7aa32d39beb2c63cc5ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723142"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
Anexa ao programa.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback
);
```

## <a name="parameters"></a>parâmetros
`pCallback`\
[em] Um objeto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) a ser usado para depurar notificação de evento.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro. A tabela a seguir mostra alguns possíveis códigos de erro.

|Valor|Descrição|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|O programa especificado já está conectado ao depurador.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Uma violação de segurança ocorreu durante o procedimento de anexação.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Um programa de desktop não pode ser anexado ao depurador.|

## <a name="remarks"></a>Comentários
 Um mecanismo de depuração (DE) nunca chama esse método para anexar a um programa. Se o DE for executado no espaço de endereço do programa, o método [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) será chamado. Se o DE for executado no espaço de endereço do Gerenciador de depuração de sessão (SDM), o método [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md) será chamado.

## <a name="see-also"></a>Confira também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
