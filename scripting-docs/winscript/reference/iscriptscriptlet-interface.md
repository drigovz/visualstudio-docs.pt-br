---
title: IScriptScriptlet Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptScriptlet interface
ms.assetid: b9981908-a337-4228-864c-c741f111ab2d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c11aada6b8c39c7dd5f0b2a6b30cdd837aa0edda
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151252"
---
# <a name="iscriptscriptlet-interface"></a>Interface IScriptScriptlet
Um objeto que implementa o `IScriptScriptlet` interface representa um script do manipulador de eventos.  
  
 Além dos métodos herdados de `IScriptEntry`, o `IScriptScriptlet` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|Retorna o nome do evento que está associado com o scriptlet.|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|Retorna o nome de evento simples que está associado com um scriptlet. Este é um nome de palavra única que não contenha nenhum espaço em branco.|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|Retorna o último identificador no nome totalmente qualificado do host do objeto do scriptlet.|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|Define o nome do evento que está associado com o scriptlet.|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|Define o nome de evento simples que está associado com um scriptlet. Este é um nome de palavra única que não contenha nenhum espaço em branco.|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|Define o último identificador no nome totalmente qualificado do host do objeto do scriptlet.|  
  
## <a name="see-also"></a>Consulte também  
 [Active Script Authoring Interfaces](../../winscript/reference/active-script-authoring-interfaces.md)