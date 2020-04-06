---
title: IDebugProcess3::Execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 444eadcce38adbd8ecd8655e8e0dc3f36f446848
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723687"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
Continua executando este processo a partir de um estado parado. Qualquer estado de execução anterior (como uma etapa) é limpo e o processo começa a ser executado novamente.

> [!NOTE]
> Este método deve ser usado em vez de [Executar](../../../extensibility/debugger/reference/idebugprogram2-execute.md).

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Execute(
   IDebugThread2* pThread
);
```

```csharp
int Execute(
   IDebugThread2 pThread
);
```

## <a name="parameters"></a>parâmetros
`pThread`\
[em] Um objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) representando o segmento a ser executado.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna código de erro.

## <a name="remarks"></a>Comentários
 Quando o usuário inicia a execução a partir de um estado parado no segmento de algum outro processo, esse método é chamado sobre esse processo. Esse método também é chamado quando o usuário seleciona o comando **Iniciar** no menu **Depurar** no IDE. A implementação deste método pode ser tão simples quanto chamar o método [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) no segmento atual no processo.

> [!WARNING]
> Não envie um evento de parada ou um evento imediato (síncrono) para [o Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante o tratamento desta chamada; caso contrário, o depurador pode travar.

## <a name="see-also"></a>Confira também
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Continuar](../../../extensibility/debugger/reference/idebugthread2-resume.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
