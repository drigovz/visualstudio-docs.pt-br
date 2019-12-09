---
title: Interface ISimpleConnectionPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 549d7f38b01937f992b240cb6f1d651bc848236c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571796"
---
# <a name="isimpleconnectionpoint-interface"></a>Interface ISimpleConnectionPoint
Fornece uma maneira simples para descrever e enumerar os eventos acionados em um determinado ponto de conexão. Essa interface também facilita a conexão de um objeto `IDispatch` a esses eventos. Essa interface é implementada pelo PDM (Gerenciador de depuração de processos) e consumida por mecanismos de script.  
  
 Essa interface está disponível em `IDebugHelper::CreateSimpleConnectionPoint`.  
  
 Além dos métodos herdados de `IUnknown`, a interface `ISimpleConnectionPoint` expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Estabelece uma conexão entre o objeto do ponto de conexão simples e o coletor do cliente.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Retorna o DISPID e o nome de cada evento em um intervalo de eventos especificado.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Retorna o número de eventos expostos nesta interface.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Encerra uma conexão de consultoria estabelecida anteriormente por meio de `ISimpleConnectionPoint::Advise`.|  
  
## <a name="see-also"></a>Consulte também  
 [Interface IDebugProperty](../../winscript/reference/idebugproperty-interface.md)