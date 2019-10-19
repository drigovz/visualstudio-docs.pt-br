---
title: Estrutura ExtendedDebugPropertyInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ExtendedDebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 09f3c5a219fca9ec9b881e2ae8363aae4d48e03f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575829"
---
# <a name="extendeddebugpropertyinfo-structure"></a>Estrutura ExtendedDebugPropertyInfo
Estende a estrutura de `DebugPropertyInfo` com membros adicionais para caracterizar a propriedade estendida.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## <a name="members"></a>Membros  
 `dwValidFields`  
 Um tipo de dados enumerado usado para especificar quais campos são inicializados.  
  
 `bstrName`  
 O nome da propriedade dentro de um contexto.  
  
 `bstrType`  
 O tipo de propriedade como cadeia de caracteres formatada.  
  
 `bstrValue`  
 O valor da propriedade como uma cadeia de caracteres formatada.  
  
 `bstrFullName`  
 O nome completo da propriedade.  
  
 `dwAttrib`  
 Uma enumeração que especifica os sinalizadores para os atributos da propriedade de depuração.  
  
 `pDebugProp`  
 `IDebugProperty` objeto correspondente a este `ExtendedDebugPropertyInfo`.  
  
 `nDISPID`  
 A ID de expedição.  
  
 `nType`  
 O tipo de propriedade estendida.  
  
 `varValue`  
 O valor da propriedade estendida se ele puder caber em VARIANT.  
  
 `plbValue`  
 Os bytes de dados reais do valor da propriedade.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty` objeto correspondente a este `ExtendedDebugPropertyInfo`.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 [estrutura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)  
 @No__t_1 de [interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)  
 @No__t_1 de [interface IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)  
 @No__t_1 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)  
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)