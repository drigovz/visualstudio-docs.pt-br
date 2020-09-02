---
title: 'IEnumDebugThreads2:: clone | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Clone
helpviewer_keywords:
- IEnumDebugThreads2::Clone
ms.assetid: d774322c-e72d-4df3-b317-928da39dadc5
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cf9732942234f896216031d74acd5143832049bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147734"
---
# <a name="ienumdebugthreads2clone"></a>IEnumDebugThreads2::Clone
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Retorna uma cópia da enumeração atual como um objeto separado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppEnum`  
 fora Retorna uma cópia dessa enumeração como um objeto separado.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A cópia da enumeração tem o mesmo estado que o original no momento em que esse método é chamado. No entanto, os Estados da cópia e do original são separados e podem ser alterados individualmente.  
  
## <a name="see-also"></a>Consulte Também  
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
