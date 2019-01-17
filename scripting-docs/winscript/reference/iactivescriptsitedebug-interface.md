---
title: Interface IActiveScriptSiteDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebug interface
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 339325686d2a98e34c6e9f96056612769a9e110e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348302"
---
# <a name="iactivescriptsitedebug-interface"></a>Interface IActiveScriptSiteDebug
Hosts inteligentes implementam o `IActiveScriptSiteDebug` interface para realizar o gerenciamento de documentos e participar de depuração. O `IActiveScriptSite` objeto geralmente fornece uma implementação do `IActiveScriptSiteDebug` interface. Se isso for feito, chame o `IActiveScriptSite::QueryInterface` método para obter o `IActiveScriptSiteDebug` interface.  
  
 Além dos métodos herdados de `IUnknown`, o `IActiveScriptSiteDebug` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|Usado pelo mecanismo de linguagem para delegar `IDebugCodeContext::GetSourceContext`.|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|Retorna o objeto de aplicativo de depuração associado a este site de script.|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|Obtém o nó de aplicativo sob a qual script documentos devem ser adicionados.|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|Permite que um host inteligente determinar como tratar erros de tempo de execução.|