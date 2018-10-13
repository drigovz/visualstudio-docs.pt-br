---
title: IDebugProcess3::GetENCAvailableState | Microsoft Docs
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
- IDebugProcess3::GetENCAvailableState
helpviewer_keywords:
- IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6041df334b75dfd38387eca5e36b5773e2d82181
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306066"
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esse método obtém o estado atual de editar e continuar do processo. Um fornecedor de porta personalizado deve sempre retornar `E_NOTIMPL`.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetENCAvailableState(  
   EncUnavailableReason* pReason  
);  
```  
  
```csharp  
int GetENCAvailableState(  
   EncUnavailableReason[] pReason  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pReason`  
 [out] Um valor a partir de [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) enumeração.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará o código de erro.  
  
> [!NOTE]
>  Um fornecedor de porta personalizado deve sempre retornar `E_NOTIMPL`.  
  
## <a name="remarks"></a>Comentários  
 Esse estado pode ser afetado pelas [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md).  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)

