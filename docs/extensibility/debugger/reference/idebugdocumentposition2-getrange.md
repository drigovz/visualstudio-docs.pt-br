---
title: 'IDebugDocumentPosition2:: GetRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd0a08889507c03ec1a8c5c72a615edfb195e7d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946846"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Obtém o intervalo para esta posição do documento.

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

## <a name="parameters"></a>Parâmetros
`pBegPosition`\
[entrada, saída] Uma estrutura de [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que é preenchida com a posição inicial. Defina esse argumento como um valor nulo se essas informações não forem necessárias.

`pEndPosition`\
[entrada, saída] Uma estrutura de [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que é preenchida com a posição final. Defina esse argumento como um valor nulo se essas informações não forem necessárias.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O intervalo especificado em uma posição de documento para um ponto de interrupção de local é usado pelo mecanismo de depuração (DE) para pesquisar antecipadamente por uma instrução que realmente contribui com código. Por exemplo, considere o seguinte código:

```
Line 5: // comment
Line 6: x = 1;
```

 A linha 5 contribui com nenhum código para o programa que está sendo depurado. Se o depurador que define o ponto de interrupção na linha 5 desejar que o DE Pesquisar em um determinado valor para a primeira linha que contribui com o código, o depurador especificaria um intervalo que inclui linhas candidatas adicionais em que um ponto de interrupção pode ser colocado corretamente. Em seguida, a pesquisa avançará essas linhas até encontrar uma linha que poderia aceitar um ponto de interrupção.

## <a name="see-also"></a>Confira também
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
