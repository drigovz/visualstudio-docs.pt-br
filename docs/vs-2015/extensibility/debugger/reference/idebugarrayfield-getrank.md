---
title: 'IDebugArrayField:: getrank | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5d0396718482c9ce90527155a3612160612f66d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198725"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém a classificação ou o número de dimensões da matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwRank`  
 fora Retorna a classificação.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A classificação de uma matriz corresponde ao número de dimensões. Em C++ e C#, matrizes multidimensionais são realmente matrizes de matrizes e, portanto, podem ser consideradas apenas uma matriz unidimensional (e o `GetRank` método sempre retorna 1). Em [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] , por outro lado, as matrizes multidimensionais são tratadas de forma diferente e a classificação de tal matriz reflete o número de dimensões (e o `GetRank` método sempre retorna o número de dimensões).  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
