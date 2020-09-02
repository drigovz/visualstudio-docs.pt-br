---
title: IDebugActivateDocumentEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c2087cb8f1b9a4b89448f3bf07f869d16ed44dc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65673686"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

O mecanismo de depuração (DE) usa essa interface para solicitar que um documento seja carregado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugActivateDocumentEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 O DE implementa essa interface quando precisa de um arquivo de origem a ser aberto. Essa interface é implementada somente por mecanismos de depuração que funcionam com o ou fazem parte de intérpretes de script. A interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve ser implementada no mesmo objeto que essa interface (o SDM usa [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para acessar a `IDebugEvent2` interface).  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O DE cria e envia esse objeto DE evento quando ele precisa ter um arquivo de origem aberto. O evento é enviado usando a função de retorno de chamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornecida pelo SDM quando ele é anexado ao programa que está sendo depurado.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 A tabela a seguir mostra os métodos de `IDebugActivateDocumentEvent2` .  
  
|Métodos|Descrição|  
|-------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|Obtém o documento a ser ativado.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|Obtém o contexto do documento que descreve a posição dentro do documento.|  
  
## <a name="remarks"></a>Comentários  
 Um cenário típico em que essa interface é usada é quando um erro de análise ocorre no código de script em uma página HTML, o script DE envia essa interface para o SDM para que o documento com o erro de análise possa ser exibido.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
