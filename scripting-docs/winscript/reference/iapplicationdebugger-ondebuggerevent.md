---
title: IApplicationDebugger::onDebuggerEvent | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 7dec2cea6cfcf11cc756ef730f98feee9ed9bb0e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092671"
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
 [in] O identificador de interface para o objeto.  
  
 `punk`  
 [in] O objeto de evento, que implementa a interface definida por `riid`.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_NOTIMPL`|O método não está implementado atualmente.|  
  
## <a name="remarks"></a>Comentários  
 A semântica do `IUnknown` é inteiramente definida pelo aplicativo/depurador.  
  
 Esse método permite extensões personalizadas do modelo de depurador. ele não está implementado atualmente.  
  
 Esse método é chamado quando `IDebugApplication::FireDebuggerEvent` é chamado.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)