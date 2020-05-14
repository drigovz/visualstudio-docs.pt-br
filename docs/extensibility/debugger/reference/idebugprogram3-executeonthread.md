---
title: IDebugProgram3::ExecuteOnThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 201c08352bc5b616298349c52197529ef3f1a7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722651"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
Executa o programa de depurador. O segmento é retornado para dar ao depurador informações sobre qual segmento o usuário está visualizando ao executar o programa.

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

## <a name="parameters"></a>parâmetros
`pThread`\
[em] Um objeto [IDebugThread2.](../../../extensibility/debugger/reference/idebugthread2.md)

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Existem três maneiras diferentes que um depurador pode retomar a execução depois de parar:

- Execute: Cancele qualquer etapa anterior e execute até o próximo ponto de ruptura e assim por diante.

- Passo: Cancele qualquer passo antigo e execute até que a nova etapa seja concluída.

- Continue: Corra novamente e deixe qualquer passo antigo ativo.

  O segmento `ExecuteOnThread` passado é útil ao decidir qual passo cancelar. Se você não conhece o segmento, a execução de execute cancela todas as etapas. Com o conhecimento do segmento, você só precisa cancelar o passo no segmento ativo.

## <a name="see-also"></a>Confira também
- [Executar](../../../extensibility/debugger/reference/idebugprogram2-execute.md)
- [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)
