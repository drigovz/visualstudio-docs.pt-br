---
title: IScriptEntry Interface | Microsoft Docs
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
ms.openlocfilehash: 0dc50a6aa5cf032827feac6b483b141b79f60e77
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148120"
---
# <a name="iscriptentry-interface"></a>Interface IScriptEntry
Um objeto que implementa o `IScriptEntry` interface representa um bloco de script ou um objeto de função.  
  
 Além dos métodos herdados de `IScriptNode`, o `IScriptEntry` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)|Retorna o texto que corresponde ao corpo de um `IScriptEntry` bloco de script, o bloco de função ou o scriptlet.|  
|[IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)|Retorna o nome do item que identifica um `IScriptEntry` objeto.|  
|[IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)|Para entradas que representam um único objeto (como uma função), retorna o nome do objeto.|  
|[IScriptEntry::GetRange](../../winscript/reference/iscriptentry-getrange.md)|Retorna a posição inicial e o comprimento de uma entrada.|  
|[IScriptEntry::GetSignature](../../winscript/reference/iscriptentry-getsignature.md)|Retorna informações de tipo para um `IScriptEntry` objeto de função.|  
|[IScriptEntry::GetText](../../winscript/reference/iscriptentry-gettext.md)|Retorna o texto que corresponde a um `IScriptEntry` bloco de script ou o código-fonte que está contido em um `IScriptScriptlet` manipulador de eventos.|  
|[IScriptEntry::SetBody](../../winscript/reference/iscriptentry-setbody.md)|Define o texto que está no corpo de uma `IScriptEntry` bloco de script ou um `IScriptScriptlet` scriptlet.|  
|[IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md)|Define o nome do item que identifica um `IScriptEntry` objeto.|  
|[IScriptEntry::SetName](../../winscript/reference/iscriptentry-setname.md)|Para entradas que representam um único objeto (como uma função), define o nome do objeto.|  
|[IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md)|Conjuntos de informações de tipo para um `IScriptEntry` objeto de função.|  
|[IScriptEntry::SetText](../../winscript/reference/iscriptentry-settext.md)|Define o texto que corresponde a um `IScriptEntry` bloco de script ou o código-fonte que está contido em um `IScriptScriptlet` manipulador de eventos.|  
  
## <a name="see-also"></a>Consulte também  
 [Active Script Authoring Interfaces](../../winscript/reference/active-script-authoring-interfaces.md)