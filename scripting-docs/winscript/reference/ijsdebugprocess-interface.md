---
title: Interface IJsDebugProcess | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ecdec77a8bcb3c1fb8a1dc64c63b363b4f001fde
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086652"
---
# <a name="ijsdebugprocess-interface"></a>Interface IJsDebugProcess
Fornece rotinas para inspecionar e controlar o processo de destino.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
IJsDebugProcess : public IUnknown;  
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-methods"></a>Métodos Públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Método IJsDebugProcess::CreateBreakPoint](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|Define o ponto de interrupção na posição do documento especificado.|  
|[Método IJsDebugProcess::CreateStackWalker](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|Método de fábrica para movimentador de pilhas.|  
|[Método IJsDebugProcess::PerformAsyncBreak](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|Coloca o mecanismo de script no modo de interrupção, fazendo com que ele quebrar na próxima instrução de script.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de interfaces de script do Windows](../../winscript/reference/windows-script-interfaces-reference.md)