---
title: Interface IDebugHelper | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: d1708b742a484a2e7d6d48cf759f15c08711e13d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979182"
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