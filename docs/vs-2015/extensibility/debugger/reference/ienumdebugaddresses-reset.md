---
title: 'IEnumDebugAddresses:: Reset | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Reset
helpviewer_keywords:
- IEnumDebugAddresses::Reset method
ms.assetid: 3a9d7f20-5bc6-4e13-8e91-5af4092e092f
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 866c96f81edd5406f36790b932b057f6279f7e67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191942"
---
# <a name="ienumdebugaddressesreset"></a>IEnumDebugAddresses::Reset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esse método redefine a enumeração para o primeiro elemento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Nenhum  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Depois que esse método é chamado, a próxima chamada para [Next](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md) retorna o primeiro elemento da enumeração.  
  
## <a name="see-also"></a>Consulte Também  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)   
 [Próximo](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)
