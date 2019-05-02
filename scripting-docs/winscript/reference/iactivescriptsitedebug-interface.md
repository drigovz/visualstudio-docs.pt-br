---
title: Interface IActiveScriptSiteDebug | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 3cd8043648586ed3c614cbb137e51d992d7ae29b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992460"
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