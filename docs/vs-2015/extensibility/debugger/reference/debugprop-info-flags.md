---
title: DEBUGPROP_INFO_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 764d28972575e8da9ef499e6d33a4a4a1deb3b07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143008"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica quais informações recuperar sobre um objeto de propriedade de depuração.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
typedef DWORD DEBUGPROP_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membros  
 DEBUGPROP_INFO_FULLNAME  
 Inicializar/usar o `bstrFullName` campo.  
  
 DEBUGPROP_INFO_NAME  
 Inicializar/usar o `bstrName` campo.  
  
 DEBUGPROP_INFO_TYPE  
 Inicializar/usar o `bstrType` campo.  
  
 DEBUGPROP_INFO_VALUE  
 Inicializar/usar o `bstrValue` campo.  
  
 DEBUGPROP_INFO_ATTRIB  
 Inicializar/usar o `dwAttrib` campo.  
  
 DEBUGPROP_INFO_PROP,  
 Inicializar/usar o `pProperty` campo que contém uma interface [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) .  
  
 DEBUGPROP_INFO_VALUE_AUTOEXPAND  
 Especifica que o campo de valor deve conter o valor expandido automaticamente, se disponível, para esse tipo de objeto.  
  
 DEBUGPROP_INFO_VALUE_NOFUNCEVAL  
 Preterido.  
  
 DEBUGPROP_INFO_VALUE_RAW  
 Não retornar nenhum valor ou membro de beautified (ou seja, não formatar os valores).  
  
 DEBUGPROP_INFO_VALUE_NO_TOSTRING  
 Não retornar nenhum valor especial sintetizado (por exemplo, não chame `ToString()` em um objeto para produzir um Value).  
  
 DEBUGPROP_INFO_NONE  
 Especifica que nenhum sinalizador está definido.  
  
 DEBUGPROP_INFO_STANDARD  
 Inicialize/use os `dwAttrib` `bstrName` campos,, e `bstrType` `bstrValue` .  
  
 DEBUGPROP_INFO_All  
 Indica uma máscara de todos os sinalizadores.  
  
## <a name="remarks"></a>Comentários  
 Esses valores são passados para os métodos [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)e [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) para indicar quais campos devem ser inicializados na estrutura de [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) .  
  
 Esses valores também são usados para o `dwFields` membro da `DEBUG_PROPERTY_INFO` estrutura para indicar quais campos da estrutura são usados e válidos quando a estrutura é retornada.  
  
 Esses valores podem ser combinados com um bit a bit `OR` .  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
