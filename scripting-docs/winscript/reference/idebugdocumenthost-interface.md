---
title: Interface IDebugDocumentHost | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHost interface
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 226e2700b471cd34496682d233e57946e124ff3b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155661"
---
# <a name="idebugdocumenthost-interface"></a>Interface IDebugDocumentHost
Expõe a funcionalidade específica de host, como coloração de sintaxe, o depurador. O `IDebugDocumentHelper::SetDebugDocumentHost` método usa essa interface como um argumento.  
  
 Além dos métodos herdados de `IUnknown`, o `IDebugDocumentHost` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|Retorna um intervalo de caracteres que foram adicionados usando `IDebugDocumentHelper::AddDeferredText`, no documento de host original.|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|Retorna os atributos de texto de um bloco de texto do documento.|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|Notifica o host que está sendo criado um novo contexto de documento e permite que o host, opcionalmente, retornar um objeto que controla o novo contexto.|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|Retorna o caminho completo (incluindo o nome do arquivo) do arquivo de origem do documento.|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|Retorna o nome do documento, sem informações de caminho.|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|Notifica o host que o arquivo de origem do documento foi salvo e que seu conteúdo deve ser atualizado.|