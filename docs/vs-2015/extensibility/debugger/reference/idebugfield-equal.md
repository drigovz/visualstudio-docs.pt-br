---
title: 'IDebugField:: equal | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547306"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esse método compara esse campo com o campo especificado para igualdade.  
  
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
 no O campo a ser comparado a este.  
  
## <a name="return-value"></a>Valor Retornado  
 Se os campos forem iguais, retorna `S_OK` . Se os campos forem diferentes, retorna de `S_FALSE.` outra forma, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
