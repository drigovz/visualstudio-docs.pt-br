---
title: IDebugCustomAttribute | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5db7f060e630c0b4175ecf4708f14fc03869e431
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568924"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface representa um atributo personalizado e pode fornecer o nome, o pai e o tipo de classe do atributo.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCustomAttribute : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 Um provedor de símbolo implementa essa interface para dar suporte a atributos personalizados associados a um símbolo. Normalmente, ele é implementado em seu próprio objeto.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Uma chamada para [Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) retorna essa interface. Uma chamada para o método [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) retorna a interface [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) .  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 A tabela a seguir mostra os métodos de `IDebugCustomAttribute` .  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|Obtém o campo ao qual o atributo atual está anexado.|  
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|Obtém o tipo de classe de atributo personalizado.|  
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|Obtém o nome do atributo personalizado.|  
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|Obtém as informações de atributo como um blob de bytes.|  
  
## <a name="remarks"></a>Comentários  
 Um atributo personalizado é uma estrutura para C# que fornece metadados personalizados associados a uma classe ou um método específico.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Interfaces de provedor de símbolo](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
