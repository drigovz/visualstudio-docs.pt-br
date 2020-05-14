---
title: IDebugProgramEx2::Anexar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fcb52a96074b783043af1e908cf454466df74c30
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722384"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
Anexar uma sessão a um programa.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason,
   IDebugSession2*       pSession
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   uint                 dwReason,
   IDebugSession2       pSession
);
```

## <a name="parameters"></a>parâmetros
`pCallback`\
[em] Um objeto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que representa a função de retorno de chamada para a a que o mecanismo de depuração anexado envia eventos.

`dwReason`\
[em] Um valor da [enumeração ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) que descreve o motivo da operação de anexação.

`pSession`\
[em] Um valor que identifica exclusivamente a sessão que está anexando ao programa.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro. Este método `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` deve retornar se o programa já estiver conectado.

## <a name="remarks"></a>Comentários
 A porta que contém o programa `pSession` pode usar o valor para determinar qual sessão está tentando anexar ao programa. Por exemplo, se uma porta permitir que apenas uma sessão de depuração seja anexada a um processo por vez, a porta poderá determinar se a mesma sessão já está anexada a outros programas no processo.

> [!NOTE]
> A interface `pSession` passada deve ser tratada apenas como um cookie, um valor que identifica exclusivamente o gerenciador de depuração de sessão anexado a este programa; nenhum dos métodos na interface fornecida é funcional.

## <a name="see-also"></a>Confira também
- [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
