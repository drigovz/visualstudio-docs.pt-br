---
title: 'IEnumDebugCustomAttributes:: Reset | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Reset
helpviewer_keywords:
- IEnumDebugCustomAttributes::Reset
ms.assetid: e0db6518-5a71-4adb-a407-4d2ac7a3e369
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ff86808bfd33cf7112091b028140f538932dee28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551345"
---
# <a name="ienumdebugcustomattributesreset"></a>IEnumDebugCustomAttributes::Reset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Redefine a sequência de enumeração para o início.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Valor retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Depois que esse método é chamado, a próxima chamada para o [próximo](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) método retorna o primeiro elemento da enumeração.  
  
## <a name="see-also"></a>Consulte Também  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [Próximo](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)
