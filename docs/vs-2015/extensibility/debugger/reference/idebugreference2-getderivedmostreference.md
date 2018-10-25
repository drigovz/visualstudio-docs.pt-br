---
title: IDebugReference2::GetDerivedMostReference | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6baff17ba485b45a239d2acb0af2b765844fa35c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914002"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém a referência do mais derivado de uma referência. Reservado para uso futuro.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetDerivedMostReference(   
   IDebugReference2** ppDerivedMost  
);  
```  
  
```csharp  
int GetDerivedMostReference(   
   out IDebugReference2 ppDerivedMost  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppDerivedMost`  
 [out] Retorna um [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto que representa a propriedade mais derivado.  
  
## <a name="return-value"></a>Valor de retorno  
 Sempre retorna `E_NOTIMPL`.  
  
## <a name="remarks"></a>Comentários  
 Por exemplo, se esta propriedade descreve um objeto que implementa `ClassRoot` , mas o que é realmente uma instanciação de `ClassDerived` que é derivada de `ClassRoot`, em seguida, esse método retorna um [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto que representa uma referência para o `ClassDerived` objeto.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

