---
title: IDebugDocumentText2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e81aaccd3af692f4a7e0f708685dbea4a44d5c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200162"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface representa um documento de texto.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 Um mecanismo DE depuração (DE) implementa essa interface quando o código-fonte que ele precisa fornecer está na forma de texto. Como esse é o caso mais comum, se um DE implementa a interface [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) , ele também deve implementar a `IDebugDocumentText2` interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Use o `QueryInterface` método para obter essa interface de uma `IDebugDocument2` interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 Além dos métodos na `IDebugDocument2` interface, essa interface implementa os seguintes métodos:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Recupera o tamanho do texto nesta posição no documento.|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Recupera o texto da posição especificada no documento.|  
  
## <a name="remarks"></a>Comentários  
 Um objeto que implementa essa interface também deve implementar a <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface, que fornece a <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface para um objeto [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) .  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
