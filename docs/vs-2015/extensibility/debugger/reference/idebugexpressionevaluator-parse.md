---
title: IDebugExpressionEvaluator::P grosseira | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4039534b139eeeaf20f938c6d6c358c602f96227
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155351"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esse método converte uma cadeia de caracteres de expressão em uma expressão analisada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```csharp  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `upstrExpression`  
 no A cadeia de caracteres de expressão a ser analisada.  
  
 `dwFlags`  
 no Uma coleção de constantes [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) que determinam como a expressão deve ser analisada.  
  
 `nRadix`  
 no Base a ser usada para interpretar qualquer informação numérica.  
  
 `pbstrError`  
 fora Retorna o erro como texto legível.  
  
 `pichError`  
 fora Retorna a posição do caractere do início do erro na cadeia de caracteres da expressão.  
  
 `ppParsedExpression`  
 fora Retorna a expressão analisada em um objeto [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) .  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método produz uma expressão analisada, não um valor real. Uma expressão analisada está pronta para ser avaliada, ou seja, convertida em um valor.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
