---
title: IDebugPropertyCreateEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1558aa8ca9cad93b00cf90f02f3af6d346b036b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698659"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface é enviada pelo mecanismo de depuração (DE) para o SDM (Gerenciador de depuração de sessão) quando cria uma propriedade associada a um documento específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 O DE implementa essa interface para relatar que uma propriedade foi criada. A interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve ser implementada no mesmo objeto que essa interface. O SDM usa [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para acessar a `IDebugEvent2` interface. Essa interface é implementada se a DE tiver criado uma propriedade associada a um script que foi carregado ou criado e se esse script precisar aparecer no IDE.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O DE cria e envia este objeto de evento para relatar que uma propriedade foi criada. O evento é enviado usando a função de retorno de chamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que é fornecida pelo SDM quando ele é anexado ao programa que está sendo depurado.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 A tabela a seguir mostra o método da `IDebugPropertyCreateEvent2` interface.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Obtém a nova propriedade.|  
  
## <a name="remarks"></a>Comentários  
 Se uma propriedade tiver um documento ou script específico associado a ela, a DE poderá enviar esse evento para o SDM a fim de atualizar a janela de **documentos de script** com o nome do documento. O SDM chamará [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) com o argumento `guidDocument` para recuperar um `VARIANT` contendo um ponteiro [IUnknown](https://msdn.microsoft.com/library/e6b85472-e54b-4b8c-b19f-4454d6c05a8f) . O SDM chamará [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) nesse ponteiro para recuperar a interface [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) que é usada para atualizar a janela de **documentos de script** .  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Interfaces principais](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
