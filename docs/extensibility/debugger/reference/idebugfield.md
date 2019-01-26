---
title: IDebugField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e1b4b7f27bbecd71fa5a99e942d5f1b75e983c0d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55002472"
---
# <a name="idebugfield"></a>IDebugField
Essa interface representa um campo, ou seja, uma descrição de um tipo ou um símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um provedor de símbolo implementa essa interface como a classe base para todos os campos.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é a classe base para todos os campos. Com base no valor de retorno [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), essa interface pode retornar mais especializadas interfaces usando [QueryInterface](/cpp/atl/queryinterface). Além disso, várias interfaces de retorno `IDebugField` objetos de vários métodos.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugField`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Obtém as informações que pode ser exibidas sobre o símbolo ou um tipo.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Obtém o tipo de campo.|  
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Obtém o tipo de campo.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Obtém o contêiner do campo.|  
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Obtém o endereço do campo.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Obtém o tamanho de um campo, em bytes.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Obtém informações estendidas sobre um campo.|  
|[Igual](../../../extensibility/debugger/reference/idebugfield-equal.md)|Compara dois campos.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Obtém informações de tipo independente sobre o símbolo ou um tipo.|  
  
## <a name="remarks"></a>Comentários  
 Um tipo é equivalente a uma linguagem C `typedef`.  
  
 No exemplo a seguir language de C++, `weather` é um tipo de classe, e `sunny` e `stormy` são símbolos:  
  
```cpp  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Se um campo representa um símbolo ou tipo pode ser determinado chamando [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) e examinando a [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) resultado. Se o `FIELD_KIND_TYPE` bit estiver definido, o campo é um tipo e se o `FIELD_KIND_SYMBOL` bit estiver definido, ele é um símbolo.  
  
## <a name="requirements"></a>Requisitos  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de Provedor de Símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)