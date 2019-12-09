---
title: IDebugField::Equal | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa630a6f2084f7ff79a9c89b685658cf694fcab9
ms.sourcegitcommit: 0cd282a7584b9bfd4df7882f8fdf3ad8a270e219
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2019
ms.locfileid: "62547306"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esse método compara esse campo com o campo especificado quanto à igualdade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```csharp  
int Equal(  
   IDebugField pField  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pField`  
 [in] O campo a ser comparado a esta.  
  
## <a name="return-value"></a>Valor de retorno  
 Se os campos são os mesmos, retornará `S_OK`. Retorna se os campos forem diferentes, `S_FALSE.` caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
