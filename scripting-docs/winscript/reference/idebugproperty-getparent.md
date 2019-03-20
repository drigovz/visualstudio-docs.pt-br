---
title: IDebugProperty::GetParent | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetParent
ms.assetid: 673d625b-acca-45c4-88f4-b72275042f8f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2aeac5e23ec38aa79e5ff5057847429ac97dbb23
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152200"
---
# <a name="idebugpropertygetparent"></a>IDebugProperty::GetParent
Obtém a propriedade pai de uma propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetParent (  
   IDebugProperty** ppParent  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppParent`  
 [out] Retorna o `IDebugProperty` interface que representa o pai da propriedade.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um válidas `HRESULT`, normalmente `S_OK`.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)