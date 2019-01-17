---
title: Interface IDebugHelper | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugHelper interface
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba760dc15cc0a3d3f2f0d80f3a16c5621582bc11
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347470"
---
# <a name="idebughelper-interface"></a>Interface IDebugHelper
Serve como uma fábrica para navegadores de objetos e pontos de conexão simples. O Gerenciador de depuração do processo (PDM) implementa essa interface, que é consumida pelos mecanismos de script.  
  
 Além dos métodos herdados de `IUnknown`, o `IDebugHelper` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Retorna um navegador de propriedade que encapsula uma VARIANTE.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Retorna um navegador de propriedade que envolve uma VARIANTE e permite a conversão personalizada de valores VARIANT ou tipos VARTYPE em cadeias de caracteres.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Retorna uma interface de eventos que encapsula um determinado `IDispatch` objeto.|