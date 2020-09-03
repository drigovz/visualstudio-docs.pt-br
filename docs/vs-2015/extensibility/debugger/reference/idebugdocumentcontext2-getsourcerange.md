---
title: 'IDebugDocumentContext2:: GetSourceRange | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bcec6af2b8e7b1acfdc9c3cf38cb18654be78c53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145007"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém o intervalo de códigos-fonte deste contexto de documento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetSourceRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pBegPosition`  
 [entrada, saída] Uma estrutura de [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que é preenchida com a posição inicial. Defina esse argumento como um valor nulo se essas informações não forem necessárias.  
  
 `pEndPosition`  
 [entrada, saída] Uma estrutura de [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que é preenchida com a posição final. Defina esse argumento como um valor nulo se essas informações não forem necessárias.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Um intervalo de origem é o intervalo inteiro do código-fonte, da instrução atual de volta para logo após a instrução anterior que contribuiu com código. O intervalo de origem normalmente é usado para misturar instruções de origem, incluindo comentários, com código na janela de desmontagem.  
  
 Para obter o intervalo apenas para as instruções de código contidas nesse contexto de documento, chame o método [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) .  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
