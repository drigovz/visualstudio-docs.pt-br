---
title: 'IDebugProperty:: EnumMembers | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.EnumMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::EnumMembers
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f8c5f2cbb107d55e9ffe602cb7d3492701de10c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562429"
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
Enumera os membros de uma propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGSdwFieldSpec,  
   UINTnRadix,  
   REFIIDrefiid,  
   IEnumDebugPropertyInfo**ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFieldSpec`  
 no Especifica as constantes de `DBGPROP_INFO_FLAGS` que determinam quais campos nas estruturas de propriedade de depuração enumeradas devem ser preenchidos.  
  
 `nRadix`  
 no Base a ser usada na interpretação de qualquer informação numérica.  
  
 `refiid`  
 no Esse IID é passado para filtrar o enumerador. O IID é uma das interfaces `IDebugPropertyEnumType` que herdam de `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 fora Retorna a interface `IEnumDebugPropertyInfo` que enumera as propriedades do membro.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um `HRESULT` válido, geralmente `S_OK`.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)  
 @No__t_1 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)  
 @No__t_1 de [interface IDebugPropertyEnumType_All](../../winscript/reference/idebugpropertyenumtype-all-interface.md)  
 [Interface IEnumDebugPropertyInfo](../../winscript/reference/ienumdebugpropertyinfo-interface.md)