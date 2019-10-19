---
title: 'IJsDebugProcess: método erformAsyncBreak de:P | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.PerformAsyncBreak
apilocation:
- jscript9diag.dll
ms.assetid: 2a6ee369-ea99-4332-8521-a1741ccb6292
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3320c59097dec5229030a3f15252d907562c67e6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577330"
---
# <a name="ijsdebugprocessperformasyncbreak-method"></a>Método IJsDebugProcess::PerformAsyncBreak
Coloca o mecanismo de script no modo de interrupção, fazendo com que ele seja interrompido na próxima instrução de script.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT PerformAsyncBreak(  
   DWORD threadId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `threadId`  
 no A ID do thread.  
  
## <a name="return-value"></a>Valor retornado  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jscript9diag. h  
  
## <a name="see-also"></a>Consulte também  
 [Interface IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)