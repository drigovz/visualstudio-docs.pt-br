---
title: 'IDebugExtendedProperty:: EnumExtendedMembers | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExtendedProperty.EnumExtendedMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExtendedProperty::EnumExtendedMembers
ms.assetid: 27cdb091-da4e-44d2-a631-31ae00468b98
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6fd225be9504254965eab77b912f50fb5c777e3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576398"
---
# <a name="idebugextendedpropertyenumextendedmembers"></a>IDebugExtendedProperty::EnumExtendedMembers
Enumera os membros de uma propriedade estendida.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT EnumExtendedMembers(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   IEnumDebugExtendedPropertyInfo**  ppeepi  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFieldSpec`  
 no Especifica as constantes EX_DBGPROP_INFO_FLAGS que determinam os campos nas estruturas de propriedade de depuração estendida enumeradas que devem ser preenchidas.  
  
 `nRadix`  
 no Base a ser usada na interpretação de qualquer informação numérica.  
  
 `ppeepi`  
 fora Retorna a interface `IEnumDebugExtendedPropertyInfo` que enumera as propriedades do membro.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um `HRESULT` válido, geralmente `S_OK`.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)  
 @No__t_1 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)  
 [Estrutura ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)