---
title: Interface IDebugApplicationNodeEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNodeEvents interface
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2f72290e331a51f1b33746b22a6526c9bfbac7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574711"
---
# <a name="idebugapplicationnodeevents-interface"></a>Interface IDebugApplicationNodeEvents
Fornece a interface de eventos para a interface `IDebugApplicationNode`.  
  
 Além dos métodos herdados de `IUnknown`, a interface `IDebugApplicationNodeEvents` expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|Manipula o evento quando um nó filho é adicionado a um objeto de nó de aplicativo de depuração.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|Manipula o evento quando um nó filho é removido de um objeto de nó de aplicativo de depuração.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|Manipula um evento que significa que o objeto depurar nó do aplicativo foi desanexado de um nó pai.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|Manipula um evento que significa que o objeto depurar nó do aplicativo foi anexado a um nó pai.|  
  
## <a name="see-also"></a>Consulte também  
 [IDebugApplicationNode Interface](../../winscript/reference/idebugapplicationnode-interface.md)