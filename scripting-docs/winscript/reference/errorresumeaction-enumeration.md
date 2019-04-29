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
ms.openlocfilehash: d92b4b2e00b25a509d29511008876d781c8a577a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955166"
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
|ERRORRESUMEACTION_ReexecuteErrorStatement|Executa novamente a instrução que gerou o erro.|  
|ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller|Permite que o mecanismo de linguagem trate o erro.|  
|ERRORRESUMEACTION_SkipErrorStatement|Retoma a execução do código após a instrução que gerou o erro.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e estruturas de depurador do script ativo](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)