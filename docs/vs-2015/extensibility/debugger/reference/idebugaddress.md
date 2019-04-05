---
title: IDebugAddress | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fb6344885e9e30c056982b15b8323eef3ef467b5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58928496"
---
# <a name="idebugaddress"></a>IDebugAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface representa o endereço de um item. Ele é retornado pelo manipulador de símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugAddress : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um provedor de símbolo implementa essa interface para representar um endereço de um objeto.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Muitos métodos em interfaces muitos retornam essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 Essa interface implementa o método a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Recupera uma [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estrutura que descreve um objeto e sua localização.|  
  
## <a name="remarks"></a>Comentários  
 O provedor de símbolo retorna essa interface para representar um objeto e sua localização dentro de um escopo específico (por exemplo, função, método ou classe). Essa interface é retornada do e passada para vários métodos do provedor de símbolo e expressão avaliador. Normalmente, o provedor de símbolo é a única entidade que precisa para interpretar o conteúdo desta interface.  
  
## <a name="requirements"></a>Requisitos  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
