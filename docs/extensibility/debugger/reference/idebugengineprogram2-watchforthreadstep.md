---
title: idebugEngineProgram2::WatchForThreadstep | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf0474d527b7c6f1d180201a463f52a0b17d18fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730356"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Observa para que a execução (ou pare de observar a execução) ocorra no segmento dado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT WatchForThreadStep( 
   IDebugProgram2* pOriginatingProgram,
   DWORD           dwTid,
   BOOL            fWatch,
   DWORD           dwFrame
);
```

```csharp
int WatchForThreadStep( 
   IDebugProgram2 pOriginatingProgram,
   uint           dwTid,
   int            fWatch,
   uint           dwFrame
);
```

## <a name="parameters"></a>parâmetros
`pOriginatingProgram`\
[em] Um objeto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) representando o programa sendo pisado.

`dwTid`\
[em] Especifica o identificador do segmento para assistir.

`fWatch`\
[em] Não-zero`TRUE`( ) significa começar a observar `dwTid`a execução no segmento identificado por ; caso contrário,`FALSE`zero ( ) significa `dwTid`parar de assistir para execução em .

`dwFrame`\
[em] Especifica um índice de quadro que controla o tipo de passo. Quando este valor é zero (0), o tipo de passo é "passo `dwTid` a passo" e o programa deve parar sempre que o segmento identificado por executá-lo. Quando `dwFrame` não é zero, o tipo de passo é "passo a passo" e o programa deve parar apenas se o segmento identificado por `dwTid` estiver sendo executado em um quadro cujo índice é igual ou maior na pilha do que `dwFrame`.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Quando o Gerenciador de depuração de sessão (SDM) etapa um programa, identificado pelo `pOriginatingProgram` parâmetro, ele notifica todos os outros programas anexados chamando esse método.

 Este método é aplicável apenas à revisão do mesmo segmento.

## <a name="see-also"></a>Confira também
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
