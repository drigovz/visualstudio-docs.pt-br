---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Docs
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
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dbaa1a02d780acce0b3c818f9f90103cfed0e683
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183762"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método determina se o fornecedor de porta pode persistir portas (gravando-os em disco) entre as invocações do depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 nenhuma.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` Se as portas podem ser persistentes, ou `S_FALSE` para indicar que as portas não podem ser persistente.  
  
## <a name="remarks"></a>Comentários  
 Se o fornecedor de porta pode manter as portas, ele deverá fazê-lo quando ele é destruído e recarregá-los, em seguida, quando ela é instanciada novamente.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)

