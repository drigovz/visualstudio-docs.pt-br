---
title: IDebugContainerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugContainerField
helpviewer_keywords:
- IDebugContainerField interface
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eb03d0adc7e7ff4eb02f29394afdd0f5c810c710
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988734"
---
# <a name="idebugcontainerfield"></a>IDebugContainerField
Essa interface representa um símbolo ou um tipo que é um contêiner para outros símbolos ou tipos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugContainerField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um provedor de símbolo implementa essa interface no mesmo objeto que implementa o [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface. Essa interface também é a classe base para todas as interfaces que representam contêineres.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Muitos métodos em interfaces muitos retornam essa interface. Como esta é uma classe base para todos os contêineres, as interfaces mais especializadas podem ser obtidos usando dessa interface [QueryInterface](/cpp/atl/queryinterface). Essas interfaces incluem [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), e [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 Além dos métodos na [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interface, essa interface implementa o método a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Cria um enumerador para os campos do contêiner.|  
  
## <a name="remarks"></a>Comentários  
 Matrizes (contêineres para variáveis), (contêineres para métodos e variáveis) de classes e métodos (contêineres para parâmetros e variáveis locais) são exemplos de contêineres.  
  
## <a name="requirements"></a>Requisitos  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)