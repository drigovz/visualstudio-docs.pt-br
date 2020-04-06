---
title: IDebugStackFrame3::InterceptCurrentException | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7debd5323e753c6c5fd1476eac3c062fb63393b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719486"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
Chamado pelo depurador no quadro de pilha atual quando ele quer interceptar a exceção atual.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT InterceptCurrentException(
   INTERCEPT_EXCEPTION_ACTION dwFlags,
   UINT64*                    pqwCookie
);
```

```csharp
int InterceptCurrentException(
   uint dwFlags,
   out  ulong pqwCookie
);
```

## <a name="parameters"></a>parâmetros
`dwFlags`\
[em] Especifica diferentes ações. Atualmente, apenas [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) o `IEA_INTERCEPT` valor INTERCEPT_EXCEPTION_ACTION é suportado e deve ser especificado.

`pqwCookie`\
[fora] Valor único identificando uma exceção específica.

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK; caso contrário, retorna um código de erro.

 A seguir estão os retornos de erro mais comuns.

|Erro|Descrição|
|-----------|-----------------|
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|A exceção atual não pode ser interceptada.|
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|O quadro de execução atual ainda não foi procurado por um manipulador.|
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Este método não é suportado para este quadro.|

## <a name="remarks"></a>Comentários
 Quando uma exceção é lançada, o depurador ganha o controle do tempo de execução em pontos-chave durante o processo de manipulação de exceções. Durante esses momentos-chave, o depurador pode perguntar ao quadro de pilha atual se o quadro deseja interceptar a exceção. Desta forma, uma exceção interceptada é essencialmente um manipulador de exceção em tempo real para um quadro de pilha, mesmo que esse quadro de pilha não tenha um manipulador de exceção (por exemplo, um bloco de tentativa/captura no código do programa).

 Quando o depurador quer saber se a exceção deve ser interceptada, ele chama esse método no objeto do quadro de pilha atual. Este método é responsável por lidar com todos os detalhes da exceção. Se a interface [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) não `InterceptStackException` for implementada ou o método retornar qualquer erro, o depurador continuará processando a exceção normalmente.

> [!NOTE]
> As exceções só podem ser interceptadas em código gerenciado, ou seja, quando o programa que está sendo depurado estiver sendo executado sob o tempo de execução .NET. É claro que os implementadores `InterceptStackException` de idiomas de terceiros podem implementar em seus próprios mecanismos de depuração, se assim desejarem.

 Depois que a interceptação estiver concluída, um [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) é sinalizado.

## <a name="see-also"></a>Confira também
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)
- [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
