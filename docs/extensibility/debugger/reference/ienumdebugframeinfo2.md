---
title: IEnumDebugFrameInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0aa67792ced94afd9c4439cbc6ea577e6b85f28b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716611"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Esta interface enumera as estruturas [frameinfo.](../../../extensibility/debugger/reference/frameinfo.md)

## <a name="syntax"></a>Sintaxe

```
IEnumDebugFrameInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) implementa essa interface para fornecer uma lista de estruturas que descrevem a pilha de chamadas atual.

## <a name="notes-for-callers"></a>Observações para chamadores
 O Visual Studio chama [o EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) para obter essa interface sempre que um ponto de interrupção, exceção ou parada ocorrer em um programa que está sendo depurado.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IEnumDebugFrameInfo2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[Avançar](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Recupera um número especificado de estruturas [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) em uma seqüência de enumeração.|
|[Ignorar](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Salta um número especificado de estruturas [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) em uma seqüência de enumeração.|
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Reinicia uma seqüência de enumeração para o início.|
|[Clonar](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Obtém o número de estruturas [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) em um enumerador.|

## <a name="remarks"></a>Comentários
 O Visual Studio obtém essa interface como o primeiro passo para lidar com um ponto de ruptura, exceção ou pausa gerada pelo usuário no programa que está sendo depurado. A lista de estruturas [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) representa a pilha de chamadas atual, com a chamada de função atual no início da lista e a chamada de função mais antiga no final da lista. Cada `FRAMEINFO` um representa um quadro de pilha, um contexto no qual as expressões podem ser avaliadas e variáveis locais analisadas.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
