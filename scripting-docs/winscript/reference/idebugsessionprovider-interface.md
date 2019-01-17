---
title: Interface IDebugSessionProvider | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSessionProvider interface
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6d17546d5461a1ad76b144bf2652672ab4aa675
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345137"
---
# <a name="idebugsessionprovider-interface"></a>Interface IDebugSessionProvider
A principal interface fornecida por um depurador IDE para habilitar o host e o idioma iniciou a depuração. Ele estabelece uma sessão de depuração para um aplicativo em execução. Essa interface é implementada pelo Gerenciador de depuração de máquina.  
  
 Além dos métodos herdados de `IUnknown`, o `IDebugSessionProvider` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Inicia uma sessão de depuração com o aplicativo especificado.|