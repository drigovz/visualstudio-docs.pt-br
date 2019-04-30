---
title: IDebugProperty::GetPropertyInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetPropertyInfo
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51cf7fae597d95b0d9098d6b2dc6950c2d06bfa0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979143"
---
# <a name="idebugpropertygetpropertyinfo"></a>IDebugProperty::GetPropertyInfo
Obtém o valor de um `IDebugProperty` que descreve um método ou uma propriedade indexada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGSdwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFields`  
 [in] Especifica o `DBGPROP_INFO_FLAGS` constantes que determinam os campos a serem preenchidos no `DebugPropertyInfo` estrutura.  
  
 `nRadix`  
 [in] Base a ser usada na formatação de todas as informações numéricas.  
  
 `pPropertyInfo`  
 [out] Retorna o `DebugPropertyInfo` estrutura que descreve a propriedade.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um válidas `HRESULT`, normalmente `S_OK`.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [Estrutura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)