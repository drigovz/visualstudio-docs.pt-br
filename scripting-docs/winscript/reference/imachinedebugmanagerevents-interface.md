---
title: Interface IMachineDebugManagerEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerEvents interface
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9aab3d7abeecd22e830c68f174896df0e7df2da
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344014"
---
# <a name="imachinedebugmanagerevents-interface"></a>Interface IMachineDebugManagerEvents
Sinaliza as alterações na lista de aplicativos em execução mantida pelo gerenciador de depuração do computador. Essa interface pode ser usada pelo IDE do depurador para exibir uma lista dinâmica de aplicativos.  
  
 Além dos métodos herdados de `IUnknown`, o `IMachineDebugManagerEvents` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|Manipula o evento quando um aplicativo é adicionado à execução lista de aplicativos.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|Manipula o evento quando um aplicativo é removido a execução de lista de aplicativos.|