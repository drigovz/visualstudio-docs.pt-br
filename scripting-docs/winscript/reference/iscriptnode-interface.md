---
title: Interface IScriptNode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptNode interface
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38ab73ddb1bd924035cb6ba61d26e65f16f53eed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577510"
---
# <a name="iscriptnode-interface"></a>Interface IScriptNode
Um objeto que implementa a interface `IScriptNode` representa uma página da Web.  
  
 Além dos métodos herdados de `IUnknown`, a interface `IScriptNode` expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|Indica se um objeto ainda está ativo.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|Adiciona uma instância filho de `IScriptEntry`.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Adiciona um Scriptlet como uma instância filho de um `IScriptNode`.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|Exclui a árvore de objetos.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|Retorna o filho que está no índice especificado no nó.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Retorna um valor definido pelo aplicativo que é usado para associar um Scriptlet ao objeto de host.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|Retorna o índice de um objeto na lista filho do pai.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|Retorna a linguagem de script usada pelo nó de script atual.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|Retorna o número de nós filho do objeto `IScriptNode`.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|Retorna o objeto `IScriptNode` que é o pai de um objeto.|  
  
## <a name="see-also"></a>Consulte também  
 [Active Script Authoring Interfaces](../../winscript/reference/active-script-authoring-interfaces.md)