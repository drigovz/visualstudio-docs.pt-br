---
title: 'IApplicationDebugger:: fechamento | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onClose
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onClose
ms.assetid: f3d6ca9f-6697-4d02-9d1a-16e3859bf282
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e31b2a77effc729f0e7df1e36116ee554446093
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577880"
---
# <a name="iapplicationdebuggeronclose"></a>IApplicationDebugger::onClose
Manipula um evento de fechamento de aplicativo de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT onClose();  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Esse método não usa parâmetros.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método é chamado quando `IDebugApplication::Close` é chamado.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IApplicationDebugger](../../winscript/reference/iapplicationdebugger-interface.md)  
 [IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)