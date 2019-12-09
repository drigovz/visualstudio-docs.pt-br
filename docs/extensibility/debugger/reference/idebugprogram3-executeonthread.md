---
title: IDebugProgram3::ExecuteOnThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 798a0caca394a21d6ee12a99efeacb2f27f6969c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343599"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Executa o programa do depurador. O thread é retornado para fornecer as informações do depurador em qual thread o usuário está exibindo ao executar o programa.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT ExecuteOnThread(
   [in] IDebugThread2* pThread)
```

```csharp
int ExecuteOnThread(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parâmetros
`pThread`\
[in] Uma [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Há três maneiras diferentes que um depurador pode retomar a execução após a interrupção:

- Execute: Cancele qualquer etapa anterior e seja executada até que o próximo ponto de interrupção e assim por diante.

- Etapa: Cancelar qualquer etapa antiga e executar até que a nova etapa seja concluída.

- Continue: Execute novamente e deixar qualquer etapa antiga ativa.

  O thread é passado para `ExecuteOnThread` é útil ao decidir qual etapa para cancelar. Se você não souber o thread em execução executar cancela todas as etapas. Com conhecimento do thread, você só precisará cancelar a etapa no thread ativo.

## <a name="see-also"></a>Consulte também
- [Executar](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)