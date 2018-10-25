---
title: IEnumDebugObjects::GetCount | Microsoft Docs
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
- IEnumDebugObjects::GetCount
helpviewer_keywords:
- IEnumDebugObjects::GetCount method
ms.assetid: 9cbc5db4-03ae-479f-a664-13cad66ad210
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0949266dde27252bf132764540b2e4a3a481fd35
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880676"
---
# <a name="ienumdebugobjectsgetcount"></a>IEnumDebugObjects::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esse método retorna o número de elementos na enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetCount(  
   [out] ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pcelt`  
 [out] Retorna o número de elementos na enumeração.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método não é parte da interface habitual do enumeração COM qual especifica que somente Avançar, Clone, Skip e redefinição precisam ser implementados.  
  
## <a name="see-also"></a>Consulte também  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)

