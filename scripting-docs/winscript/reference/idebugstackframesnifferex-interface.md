---
title: Interface IDebugStackFrameSnifferEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSnifferEx interface
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dccd9210908922951c20378868c33b3389cbed4f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432244"
---
# <a name="idebugstackframesnifferex-interface"></a>Interface IDebugStackFrameSnifferEx
Fornece uma maneira para enumerar os registros de ativação lógicos conhecidos por um componente. Mecanismos de script geralmente implementam essa interface. O Gerenciador de depuração processo usa essa interface para localizar todos os quadros de pilha associado com um determinado thread.  
  
> [!NOTE]
> Essa interface é chamada de dentro do thread de interesse. A implementação da interface deve identificar o thread atual e retorna um enumerador apropriado.  
  
 Além dos métodos herdados de `IDebugStackFrameSniffer`, o `IDebugStackFrameSnifferEx` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Retorna um enumerador dos quadros de pilha do thread atual.|