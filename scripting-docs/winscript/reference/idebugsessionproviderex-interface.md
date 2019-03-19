---
title: Interface IDebugSessionProviderEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9bf341adeaeb17c8986b1b30b12f58113aef562
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146767"
---
# <a name="idebugsessionproviderex-interface"></a>Interface IDebugSessionProviderEx
A interface primária fornecida por um IDE para habilitar a depuração e linguagem-iniciadas pelo host do depurador. Ele estabelece uma sessão de depuração para um aplicativo em execução. Essa interface é implementada pelo Gerenciador de depuração de máquina.  
  
 Além dos métodos herdados de `IUnknown`, o `IDebugSessionProviderEx` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Determina se a depuração Just In Time é possível com o aplicativo especificado.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Inicia uma sessão de depuração com o aplicativo especificado.|