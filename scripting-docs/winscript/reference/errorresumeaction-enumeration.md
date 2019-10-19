---
title: Enumeração ERRORRESUMEACTION | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ERRORRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- ERRORRESUMEACTION enumeration
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad9b8598cb027c96f6fb6fad6f3d343e6058cfdb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575859"
---
# <a name="errorresumeaction-enumeration"></a>Enumeração ERRORRESUMEACTION
Descreve como continuar de um erro de execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|ERRORRESUMEACTION_ReexecuteErrorStatement|Executa novamente a instrução que produziu o erro.|  
|ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller|Permite que o mecanismo de linguagem manipule o erro.|  
|ERRORRESUMEACTION_SkipErrorStatement|Retoma a execução no código após a instrução que produziu o erro.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e estruturas de depurador do script ativo](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)