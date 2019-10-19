---
title: 'IDebugApplication:: FireDebuggerEvent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FireDebuggerEvent
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FireDebuggerEvent
ms.assetid: fd1f602e-fc15-4158-a6e7-497ff5b4a509
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 00d895ed484e37f0ba38636a409876156ed97287
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575004"
---
# <a name="idebugapplicationfiredebuggerevent"></a>IDebugApplication::FireDebuggerEvent
Dispara um evento genérico para a interface de `IApplicationDebugger` do depurador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT FireDebuggerEvent(  
   REFGUID    riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `riid`  
 no Um GUID para o objeto.  
  
 `punk`  
 no Um objeto de evento a ser passado para o depurador.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_NOTIMPL`|O método não está implementado no momento.|  
  
## <a name="remarks"></a>Comentários  
 A semântica do GUID e a `IUnknown` são totalmente definidas para aplicativo/depurador.  
  
 Esse método permite extensões personalizadas do modelo do depurador; Ele não está implementado no momento.  
  
 Esse método faz com que `IApplicationDebugger::onDebuggerEvent` seja chamado.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 [IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)