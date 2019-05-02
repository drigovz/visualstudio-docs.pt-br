---
title: IDebugDocumentPosition2::GetRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae9c160954ac7bfb6ff3d18d107a78366a19c96b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875549"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Obtém o intervalo para essa posição do documento.

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

#### <a name="parameters"></a>Parâmetros
 `pBegPosition`

 [no, out] Um [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estrutura será preenchida com a posição inicial. Defina este argumento como um valor nulo se essa informação não é necessária.

 `pEndPosition`

 [no, out] Um [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estrutura será preenchida com a posição final. Defina este argumento como um valor nulo se essa informação não é necessária.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O intervalo especificado em uma posição de documento para um ponto de interrupção de local é usado pelo mecanismo de depuração (DE) para procurar uma instrução que contribui, na verdade, o código com antecedência. Por exemplo, considere o seguinte código:

```
Line 5: // comment
Line 6: x = 1;
```

 Linha 5 contribui com nenhum código para o programa que está sendo depurado. Se quiser que o depurador que define o ponto de interrupção na linha 5 DE para pesquisar adiante uma certa quantidade para a primeira linha que contribui com o código, o depurador seria especificar um intervalo que inclui linhas de candidato adicional em que um ponto de interrupção pode ser colocado corretamente. O DE, em seguida, pesquisaria para frente por meio dessas linhas até que ela encontrou uma linha que poderia aceitar um ponto de interrupção.

## <a name="see-also"></a>Consulte também
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)