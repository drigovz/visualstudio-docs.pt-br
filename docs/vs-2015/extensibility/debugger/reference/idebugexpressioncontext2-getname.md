---
title: IDebugExpressionContext2::GetName | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2c69b165e6a9e36d190a64b9d2e9ec41fcff2183
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922170"
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera o nome do contexto de avaliação.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName(   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrName`  
 [out] Retorna o nome do contexto de avaliação.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O nome é a descrição deste contexto de avaliação. Geralmente, é algo que pode ser analisado por um avaliador de expressão que se refere a este contexto de avaliação exato. Por exemplo, em C++ o nome é da seguinte maneira:  
  
```  
"{ function-name, source-file-name, module-file-name }"  
```  
  
## <a name="see-also"></a>Consulte também  
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
