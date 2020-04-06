---
title: IDebugDocumentOffsetOffset2:GetRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd305b6506471a40de90fbd954e54461d2a139d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731632"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Recupera o intervalo para a posição atual do documento.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetRange(
   DWORD* pdwBegOffset,
   DWORD* pdwEndOffset
);
```

```csharp
public int GetRange(
   ref uint pdwBegOffset,
   ref uint pdwEndOffset
);
```

## <a name="parameters"></a>parâmetros
`pdwBegOffset`\
[dentro, fora] Deslocamento para a posição inicial do intervalo. Defina este parâmetro como um valor nulo se essas informações não forem necessárias.

`pdwEndOffset`\
[dentro, fora] Deslocamento para a posição final do intervalo. Defina este parâmetro como um valor nulo se essas informações não forem necessárias.

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
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
