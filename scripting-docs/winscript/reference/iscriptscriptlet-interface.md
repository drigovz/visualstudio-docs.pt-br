---
title: Interface IScriptScriptlet | Microsoft Docs
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
ms.openlocfilehash: 7b7973aee209695592f022d0e05a770caa1e694c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571879"
---
# <a name="iscriptscriptlet-interface"></a>Interface IScriptScriptlet
Um objeto que implementa a interface `IScriptScriptlet` representa um script de manipulador de eventos.  
  
 Além dos métodos herdados de `IScriptEntry`, a interface `IScriptScriptlet` expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IScriptScriptlet::GetEventName](../../winscript/reference/iscriptscriptlet-geteventname.md)|Retorna o nome do evento associado ao scriptlet.|  
|[IScriptScriptlet:: GetSimpleEventName](../../winscript/reference/iscriptscriptlet-getsimpleeventname.md)|Retorna o nome do evento simples que está associado a um Scriptlet. Este é um nome de palavra única que não contém nenhum espaço em branco.|  
|[IScriptScriptlet::GetSubItemName](../../winscript/reference/iscriptscriptlet-getsubitemname.md)|Retorna o último identificador no nome totalmente qualificado do host de objeto de um Scriptlet.|  
|[IScriptScriptlet::SetEventName](../../winscript/reference/iscriptscriptlet-seteventname.md)|Define o nome do evento que está associado ao scriptlet.|  
|[IScriptScriptlet::SetSimpleEventName](../../winscript/reference/iscriptscriptlet-setsimpleeventname.md)|Define o nome do evento simples que está associado a um Scriptlet. Este é um nome de palavra única que não contém nenhum espaço em branco.|  
|[IScriptScriptlet::SetSubItemName](../../winscript/reference/iscriptscriptlet-setsubitemname.md)|Define o último identificador no nome totalmente qualificado do host de objeto de um Scriptlet.|  
  
## <a name="see-also"></a>Consulte também  
 [Active Script Authoring Interfaces](../../winscript/reference/active-script-authoring-interfaces.md)