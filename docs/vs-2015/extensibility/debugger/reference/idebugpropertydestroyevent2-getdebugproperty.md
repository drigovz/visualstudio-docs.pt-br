---
title: IDebugPropertyDestroyEvent2::GetDebugProperty | Microsoft Docs
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
- IDebugPropertyDestroyEvent2::GetDebugProperty
helpviewer_keywords:
- IDebugPropertyDestroyEvent2::GetDebugProperty
ms.assetid: c96ae785-0ac8-4df4-8df3-15a8d7e13687
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: da5cc29c179f8dbefc519b1eaf1aaffdad4bb2f5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949481"
---
# <a name="idebugpropertydestroyevent2getdebugproperty"></a>IDebugPropertyDestroyEvent2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Obtém a propriedade a ser destruído.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetDebugProperty (   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty (   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppProperty`  
 [out] Retorna um [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa a propriedade a ser destruído.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

