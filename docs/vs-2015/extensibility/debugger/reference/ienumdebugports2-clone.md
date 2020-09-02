---
title: 'IEnumDebugPorts2:: clone | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Clone
helpviewer_keywords:
- IEnumDebugPorts2::Clone
ms.assetid: d5ce77e8-bb99-409a-98fa-20fe5a0de25e
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8216882286bc1521043bfb8aafe3aa4ea588a8d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180455"
---
# <a name="ienumdebugports2clone"></a>IEnumDebugPorts2::Clone
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Retorna uma cópia da enumeração atual como um objeto separado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugPorts2 ppEnum  
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
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
