---
title: IDebugDocumentPositionOffset2::GetRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7f780d5df2d111a371a4389cd29d4b724dfe3834
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855251"
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
  
#### <a name="parameters"></a>Parâmetros  
 `pdwBegOffset`  
 [no, out] Deslocamento da posição inicial do intervalo. Defina esse parâmetro como um valor nulo se essa informação não é necessária.  
  
 `pdwEndOffset`  
 [no, out] Deslocamento para a posição final do intervalo. Defina esse parâmetro como um valor nulo se essa informação não é necessária.  
  
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
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)