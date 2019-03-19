---
title: Interface IProcessDebugManager | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: d68c044cdc3d523841cc56814b8ca34bcd8aa037
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157224"
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