---
title: IDebugProgram2::Execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f34ebea67ff95d1da6d777cdd828604f4a2f56e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722988"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
Continua executando este programa de um estado parado. Qualquer estado de execução anterior (como um passo) é liberado, e o programa começa a ser executado novamente.

> [!NOTE]
> Esse método é preterido. Use o método [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) em vez disso.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Execute(
   void
);
```

```csharp
int Execute();
```

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Quando o usuário inicia a execução a partir de um estado parado no segmento de algum outro programa, este método é chamado neste programa. Esse método também é chamado quando o usuário seleciona o comando **Iniciar** no menu **Depurar** no IDE. A implementação deste método pode ser tão simples quanto chamar o método [Retomar](../../../extensibility/debugger/reference/idebugthread2-resume.md) no segmento atual do programa.

> [!WARNING]
> Não envie um evento de parada ou um evento imediato (síncrono) para [o Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante o tratamento desta chamada; caso contrário, o depurador pode travar.

## <a name="see-also"></a>Confira também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Continuar](../../../extensibility/debugger/reference/idebugthread2-resume.md)
