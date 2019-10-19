---
title: 'IApplicationDebugger:: onDebuggerEvent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onDebuggerEvent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onDebuggerEvent
ms.assetid: 82a5faaa-1222-4bf1-8569-10439dbdf16d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f8edb2a3c39d639b5b6722707d7b6c0b57a5c19
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577864"
---
# <a name="iapplicationdebuggerondebuggerevent"></a>IApplicationDebugger::onDebuggerEvent
Manipula um evento de aplicativo personalizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `riid`  
 no O identificador de interface do objeto.  
  
 `punk`  
 no O objeto Event, que implementa a interface definida por `riid`.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_NOTIMPL`|O método não está implementado no momento.|  
  
## <a name="remarks"></a>Comentários  
 A semântica da `IUnknown` é totalmente definida por aplicativo/depurador.  
  
 Esse método permite extensões personalizadas do modelo do depurador; Ele não está implementado no momento.  
  
 Esse método é chamado quando `IDebugApplication::FireDebuggerEvent` é chamado.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)  
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)