---
title: Interface IDebugStackFrameSniffer | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41fff384bc9075d94fcfa84d94350fec72ebc64a
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348874"
---
# <a name="idebugstackframesniffer-interface"></a>Interface IDebugStackFrameSniffer
Fornece uma maneira para enumerar os registros de ativação lógicos conhecidos por um componente. Mecanismos de script geralmente implementam essa interface. O Gerenciador de depuração processo usa essa interface para localizar todos os quadros de pilha associado com um determinado thread.  
  
> [!NOTE]
>  O depurador chama essa interface de dentro do thread de interesse. O mecanismo de script deve identificar o thread atual e retorna um enumerador apropriado.  
  
## <a name="methods"></a>Métodos  
 Além dos métodos herdados de `IUnknown`, o `IDebugStackFrameSniffer` interface expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Retorna um enumerador dos quadros de pilha do thread atual.|