---
title: 'IDebugFunctionObject2:: Evaluate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d87d7d3531d198a1478b4aaa55b354c3ac101302
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728438"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
Chama a função e retorna o valor resultante como um objeto.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Evaluate (
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwEvalFlags,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate (
   IDebugObject     ppParams,
   uint             dwParams,
   uint             dwEvalFlags,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Parâmetros
`ppParams`\
no Uma matriz de objetos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa os parâmetros de entrada. Cada um desses parâmetros foi criado usando um dos métodos Create nesta interface.

`dwParams`\
no O número de parâmetros na `ppParams` matriz.

`dwEvalFlags`\
no Uma combinação de sinalizadores da enumeração [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) que especificam como a avaliação deve ser executada.

`dwTimeout`\
no Especifica o tempo máximo, em milissegundos, a aguardar antes de retornar desse método. Use **infinito** para aguardar indefinidamente.

`ppResult`\
fora Retorna um **IDebugObject** que representa o valor da função como um objeto.

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
