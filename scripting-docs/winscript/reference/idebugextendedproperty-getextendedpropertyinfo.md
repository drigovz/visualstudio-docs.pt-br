---
title: 'IDebugExtendedProperty:: GetExtendedPropertyInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExtendedProperty.GetExtendedPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExtendedProperty::GetExtendedPropertyInfo
ms.assetid: 56edf538-5082-4653-82b6-e6640d6f61ba
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77167c46e02bcf2bf5d3ce5836ad5de103176e93
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576387"
---
# <a name="idebugextendedpropertygetextendedpropertyinfo"></a>IDebugExtendedProperty::GetExtendedPropertyInfo
Busca informações estendidas para uma propriedade estendida, que é mais informações do que as `IDebugProperty` mais simples.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetExtendedPropertyInfo(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   ExtendedDebugPropertyInfo*  pExtendedPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFieldSpec`  
 no Especifica as constantes EX_DBGPROP_INFO_FLAGS que determinam os campos a serem preenchidos na estrutura de `ExtendedDebugPropertyInfo`.  
  
 `nRadix`  
 no Base a ser usada na interpretação de qualquer informação numérica.  
  
 `pExtendedPropertyInfo`  
 fora Retorna a estrutura de `ExtendedDebugPropertyInfo` que descreve a propriedade.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um `HRESULT` válido, geralmente `S_OK`.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)  
 @No__t_1 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)  
 [Estrutura ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)