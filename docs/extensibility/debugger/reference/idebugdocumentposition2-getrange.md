---
title: IDebugDocumentPosition2:GetRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a923691afdfe145931ab31d0e9bbc6142e7c8d1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731668"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Obtém o alcance para esta posição de documento.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>parâmetros
`pBegPosition`\
[dentro, fora] Uma [estrutura TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que é preenchida com a posição inicial. Defina esse argumento como um valor nulo se essas informações não forem necessárias.

`pEndPosition`\
[dentro, fora] Uma [estrutura TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que é preenchida com a posição final. Defina esse argumento como um valor nulo se essas informações não forem necessárias.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O intervalo especificado em uma posição de documento para um ponto de ruptura de localização é usado pelo mecanismo de depuração (DE) para procurar uma declaração que realmente contribua com o código. Por exemplo, considere o seguinte código:

```
Line 5: // comment
Line 6: x = 1;
```

 A linha 5 não contribui com nenhum código para o programa que está sendo depurado. Se o depurador que define o ponto de ruptura na linha 5 quiser que o DE pesquise uma certa quantidade para a primeira linha que contribui com o código, o depurador especificaria um intervalo que inclui linhas de candidatos adicionais onde um ponto de ruptura pode ser colocado corretamente. O DE então procuraria adiante através dessas linhas até encontrar uma linha que pudesse aceitar um ponto de ruptura.

## <a name="see-also"></a>Confira também
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
