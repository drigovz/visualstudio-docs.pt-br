---
title: 'IDebugArrayObject:: GetDimensions | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09902c60f87cfb92d0f0778fcbd106ade4d8dac4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197783"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém as dimensões da matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```csharp  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwCount`  
 no O número de dimensões a serem recuperadas.  
  
 `dwDimensions`  
 [entrada, saída] Uma matriz que é preenchida com os tamanhos de cada dimensão. `dwCount` Especifica o tamanho máximo da `dwDimensions` matriz.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Uma matriz multidimensional pode ter tamanhos diferentes para cada dimensão. Por exemplo, considerando a matriz tridimensional `myarray[3][2][6]` , esse método retornaria 3, 2 e 6 no `dwDimensions` parâmetro nessa ordem.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
