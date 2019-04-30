---
title: IActiveScriptSiteDebug32 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: e7937311e01274570e34bd639a0dc5f68206a3aa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992441"
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32 Interface
Hosts inteligentes implementam o `IActiveScriptSiteDebug32` interface para realizar o gerenciamento de documentos e participar de depuração. O `IActiveScriptSite` objeto geralmente fornece uma implementação do `IActiveScriptSiteDebug32` interface. Se isso for feito, chame o `IActiveScriptSite::QueryInterface` método para obter o `IActiveScriptSiteDebug32` interface.  
  
 Além dos métodos herdados de `IUnknown`, o `IActiveScriptSiteDebug32` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Retorna o objeto de aplicativo de depuração associado a este site de script.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Usado pelo mecanismo de linguagem para delegar `IDebugCodeContext::GetSourceContext`.|