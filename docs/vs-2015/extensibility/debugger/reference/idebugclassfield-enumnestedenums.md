---
title: IDebugClassField::EnumNestedEnums | Microsoft Docs
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
- IDebugClassField::EnumNestedEnums
helpviewer_keywords:
- IDebugClassField::EnumNestedEnums method
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 88447e2006a6bb27cdd4fe92b9ace6389a95430e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867995"
---
# <a name="idebugclassfieldenumnestedenums"></a>IDebugClassField::EnumNestedEnums
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cria um enumerador para os enumeradores aninhados dessa classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT EnumNestedEnums(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumNestedEnums(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppEnum`  
 [out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa a lista de enumerações aninhadas. Retorna um valor nulo se não houver nenhum enumerações aninhadas.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, Retorna S_OK ou retornará S_FALSE se não houver nenhum enumeradores aninhados. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Cada elemento da enumeração é um [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) objeto que descreve uma enumeração aninhada.  
  
 Uma enumeração declarada dentro de uma classe é considerada uma enumeração aninhada. Por exemplo, com base em:  
  
```  
class RootClass {  
   enum NestedEnum { EnumValue = 0 }  
};  
```  
  
 O `EnumNestedEnums` método retornaria um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que contém um objeto [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) objeto que representa o `NestedEnum` enumeração.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)

