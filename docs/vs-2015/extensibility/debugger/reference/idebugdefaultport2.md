---
title: IDebugDefaultPort2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8178adfc1a54d74d758bcfae8272353d5a0c7bd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58929709"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface fornece vários métodos para acessar o servidor de uma porta e instalações de notificação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Visual Studio implementa essa interface para representar a porta de depuração para acessar os programas. Um fornecedor de porta personalizado também pode implementar essa interface se ele trata a depuração remota.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Um argumento para métodos na [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interface fornece essa interface. Chamando [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) em um [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interface também pode obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 Além dos métodos definidos no [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), essa interface implementa os métodos a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Obtém a interface de notificação de porta desta porta.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Obtém a interface para o servidor que hospeda essa porta.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Determina se essa porta está em execução no computador local.|  
  
## <a name="remarks"></a>Comentários  
 O nome "`IDebugDefaultPort2`" é um pouco de um nome inapropriado, pois ele não representa uma porta padrão. Ele poderia ser chamado "IDebugPort3".  
  
## <a name="requirements"></a>Requisitos  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
