---
title: IDebugProperty::GetParent | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 34e4d38a4a04134535925d130b0660e52a0c0b19
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097650"
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