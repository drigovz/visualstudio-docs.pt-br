---
title: 'IDebugPortSupplier3:: CanPersistPorts | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: edc989771b41cc4a5cc5b4710de4cbb5632873e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188191"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esse método determina se o fornecedor da porta pode persistir portas (gravando-as no disco) entre invocações do depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Nenhum.  
  
## <a name="return-value"></a>Valor Retornado  
 `S_OK` Se as portas puderem ser persistidas ou `S_FALSE` para indicar que as portas não podem ser persistentes.  
  
## <a name="remarks"></a>Comentários  
 Se o fornecedor da porta persistir portas, ele deverá fazer isso quando for destruído e, em seguida, recarregá-las quando ela for instanciada novamente.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
