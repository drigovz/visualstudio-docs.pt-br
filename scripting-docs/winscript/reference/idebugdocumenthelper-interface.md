---
title: IDebugDocumentHelper Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHelper interface
ms.assetid: b652a31e-b87b-45f1-b586-94f2b6e822db
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7322ea5e2026ff3f4491ed1106dceb97a5f11c73
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000905"
---
# <a name="idebugdocumenthelper-interface"></a>Interface IDebugDocumentHelper
Forneça implementações de várias interfaces necessárias para hospedagem inteligente, como o `IDebugDocument`, `IDebugDocumentContext`, `IDebugDocumentProvider`, `IDebugDocumentText`, e `IDebugDocumentTextEvents` interfaces.  
  
 Além dos métodos herdados de `IUnknown`, o `IDebugDocumentHelper` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugDocumentHelper::Init](../../winscript/reference/idebugdocumenthelper-init.md)|Inicializa um auxiliar de documentos de depuração com um nome e atributos inicias.|  
|[IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)|Adiciona este documento na árvore do documento.|  
|[IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)|Remove este documento da árvore do documento.|  
|[IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)|Acrescenta uma cadeia de caracteres de Unicode ao fim deste documento.|  
|[IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)|Acrescenta uma cadeia de caracteres DBCS ao fim deste documento.|  
|[IDebugDocumentHelper::SetDebugDocumentHost](../../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md)|Conjuntos de `IDebugDocumentHost` para este documento.|  
|[IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)|Notifica o auxiliar que o texto especificado está disponível, mas ele não fornece os caracteres.|  
|[IDebugDocumentHelper::DefineScriptBlock](../../winscript/reference/idebugdocumenthelper-definescriptblock.md)|Significa para o auxiliar que um determinado intervalo de caracteres é um bloco de script tratado pelo mecanismo de script específico.|  
|[IDebugDocumentHelper::SetDefaultTextAttr](../../winscript/reference/idebugdocumenthelper-setdefaulttextattr.md)|Define os atributos padrão a ser usado para texto que não está em um bloco de script.|  
|[IDebugDocumentHelper::SetTextAttributes](../../winscript/reference/idebugdocumenthelper-settextattributes.md)|Define os atributos em um intervalo de texto.|  
|[IDebugDocumentHelper::SetLongName](../../winscript/reference/idebugdocumenthelper-setlongname.md)|Define o nome longo para o documento.|  
|[IDebugDocumentHelper::SetShortName](../../winscript/reference/idebugdocumenthelper-setshortname.md)|Define o nome curto para o documento.|  
|[IDebugDocumentHelper::SetDocumentAttr](../../winscript/reference/idebugdocumenthelper-setdocumentattr.md)|Define os atributos para este documento.|  
|[IDebugDocumentHelper::GetDebugApplicationNode](../../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)|Retorna o nó de aplicativo de depuração correspondente a este documento.|  
|[IDebugDocumentHelper::GetScriptBlockInfo](../../winscript/reference/idebugdocumenthelper-getscriptblockinfo.md)|Recupera o intervalo de caracteres e o mecanismo de script correspondente a um bloco de script.|  
|[IDebugDocumentHelper::CreateDebugDocumentContext](../../winscript/reference/idebugdocumenthelper-createdebugdocumentcontext.md)|Cria um novo contexto de documento de depuração.|  
|[IDebugDocumentHelper::BringDocumentToTop](../../winscript/reference/idebugdocumenthelper-bringdocumenttotop.md)|Traz este documento na parte superior no depurador de interface do usuário.|  
|[IDebugDocumentHelper::BringDocumentContextToTop](../../winscript/reference/idebugdocumenthelper-bringdocumentcontexttotop.md)|Traz um contexto deste documento para a parte superior da interface de usuário do depurador.|