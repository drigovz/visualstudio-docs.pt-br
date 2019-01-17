---
title: IDebugThreadCall Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugThreadCall interface
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2167538f2251d961dfcad4a873658d9635a612e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346261"
---
# <a name="idebugthreadcall-interface"></a>Interface IDebugThreadCall
O `IDebugThreadCall` normalmente, a interface é implementada por um componente que faz chamadas entre threads com o `IDebugThread` marshalling de implementação fornecida pelo Gerenciador de depuração de processos (PDM).  
  
 O PDM chama o `IDebugThreadCall` interface em que o thread desejado e o `IDebugThreadCall` interface envia a chamada para a implementação desejada. O `IDebugThreadCall` interface converte as informações do parâmetro passadas nos parâmetros à parte superior apropriado.  
  
 O `IDebugThreadCall` interface é um objeto de thread livre.  
  
## <a name="methods"></a>Métodos  
 Além dos métodos herdados de `IUnknown`, o `IDebugThreadCall` interface expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Lida com chamadas para executar o código em outro thread.|