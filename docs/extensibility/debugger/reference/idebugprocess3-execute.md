---
title: 'IDebugProcess3:: execute | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4a697a4677b6bedef376e602c4327dff66ead53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915415"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Continua executando esse processo a partir de um estado parado. Qualquer estado de execução anterior (como uma etapa) é limpo e o processo começa a ser executado novamente.

> [!NOTE]
> Esse método deve ser usado em vez de [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md).

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Execute(
   IDebugThread2* pThread
);
```

```csharp
int Execute(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>Parâmetros
`pThread`\
no Um objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa o thread a ser executado.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna o código de erro.

## <a name="remarks"></a>Comentários
 Quando o usuário inicia a execução de um estado parado em algum outro thread do processo, esse método é chamado nesse processo. Esse método também é chamado quando o usuário seleciona o comando **Iniciar** no menu **depurar** no IDE. A implementação desse método pode ser tão simples quanto chamar o método [resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) no thread atual no processo.

> [!WARNING]
> Não enviar um evento de interrupção ou um evento imediato (síncrono) para [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ao lidar com essa chamada; caso contrário, o depurador pode parar de responder.

## <a name="see-also"></a>Confira também
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Retomar](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
