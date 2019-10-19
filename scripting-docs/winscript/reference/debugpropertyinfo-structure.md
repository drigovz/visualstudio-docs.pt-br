---
title: Estrutura DebugPropertyInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugPropertyInfo structure
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 793c83b467460f0744abffe3f161f7510f56257a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575062"
---
# <a name="debugpropertyinfo-structure"></a>Estrutura DebugPropertyInfo
Descreve um objeto de uma natureza hierárquica que tem nome, tipo e valor. Ele é usado para descrever as propriedades de depuração de variáveis locais, parâmetros, variáveis de inspeção e expressões e registros.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## <a name="members"></a>Membros  
 dwValidFields  
 Um tipo de dados enumerado usado para especificar quais campos são inicializados.  
  
 bstrName  
 O nome da propriedade dentro de um contexto.  
  
 bstrtype  
 O tipo de propriedade, como cadeia de caracteres formatada.  
  
 bstrvalue  
 O valor da propriedade, como cadeia de caracteres formatada.  
  
 bstrFullName  
 O nome completo da propriedade.  
  
 dwAttrib  
 Uma enumeração que especifica os sinalizadores para os atributos da propriedade de depuração.  
  
 pDebugProp  
 O `IDebugProperty` descrito pelas informações nesta estrutura de `DebugPropertyInfo`.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)  
 @No__t_1 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)  
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)