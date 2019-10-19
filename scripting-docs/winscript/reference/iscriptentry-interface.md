---
title: Interface IScriptEntry | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptEntry interface
ms.assetid: 86da3bc1-58b7-4d73-87ab-bc3ce34e3f41
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 868322358908a32c8f14b56846cf3237f8531b4c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575393"
---
# <a name="iscriptentry-interface"></a>Interface IScriptEntry
Um objeto que implementa a interface `IScriptEntry` representa um bloco de script ou um objeto de função.  
  
 Além dos métodos herdados de `IScriptNode`, a interface `IScriptEntry` expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Retorna o texto que corresponde ao corpo de um bloco de script `IScriptEntry`, bloco de função ou scriptlet.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Retorna o nome do item que identifica um objeto de `IScriptEntry`.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Para entradas que representam um único objeto (como uma função), retorna o nome do objeto.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Retorna a posição inicial e o comprimento de uma entrada.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Retorna informações de tipo para um objeto de função `IScriptEntry`.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Retorna o texto que corresponde a um bloco de script `IScriptEntry` ou o código-fonte contido em um manipulador de eventos `IScriptScriptlet`.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Define o texto que está no corpo de um bloco de script `IScriptEntry` ou um Scriptlet `IScriptScriptlet`.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Define o nome do item que identifica um objeto de `IScriptEntry`.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Para entradas que representam um único objeto (como uma função), define o nome do objeto.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Define informações de tipo para um objeto de função `IScriptEntry`.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Define o texto que corresponde a um bloco de script `IScriptEntry` ou o código-fonte contido em um manipulador de eventos `IScriptScriptlet`.|  
  
## <a name="see-also"></a>Consulte também  
 [Active Script Authoring Interfaces](../../winscript/reference/active-script-authoring-interfaces.md)