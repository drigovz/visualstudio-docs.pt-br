---
title: 'IDebugClassField:: EnumInterfacesImplemented | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 45cdc4ea3d1dad911179ce7b2a4926248ee921fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191004"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cria um enumerador para as interfaces implementadas por essa classe.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT EnumInterfacesImplemented(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumInterfacesImplemented(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppEnum`  
 fora Retorna um objeto [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa a lista de interfaces implementadas. Retorna um valor nulo se não houver nenhuma interface.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará S_OK ou retornará S_FALSE se não houver interfaces implementadas nessa classe. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Cada elemento da enumeração é um objeto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que descreve uma interface. Observe que [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] o código não gerenciado não usa interfaces como uma entidade discreta, portanto, esse método sempre retorna um valor nulo para código não gerenciado [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)] .  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
