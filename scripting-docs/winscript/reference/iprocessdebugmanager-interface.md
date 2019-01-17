---
title: Interface IProcessDebugManager | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProcessDebugManager interface
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5feb67b1a616eeaa855b27cb12ea9b3146545ebd
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345117"
---
# <a name="iprocessdebugmanager-interface"></a>Interface IProcessDebugManager
A interface primária para o gerenciador de depuração do processo. Essa interface pode criar, adicionar ou remover um aplicativo virtual de um processo. Ele pode enumerar os quadros de pilha e threads do aplicativo.  
  
 Além dos métodos herdados de `IUnknown`, o `IProcessDebugManager` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|Cria um novo objeto de aplicativo de depuração para este aplicativo.|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|Retorna um objeto de aplicativo padrão para o processo atual.|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|Adiciona um aplicativo à lista do Gerenciador de depuração de máquina dos aplicativos em execução.|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|Remove um aplicativo de execução de lista de aplicativos.|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|Cria um novo auxiliar de documento de depuração para este aplicativo.|