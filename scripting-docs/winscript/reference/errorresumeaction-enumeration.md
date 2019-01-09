---
title: Enumeração ERRORRESUMEACTION | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d78852a05226f5112447dd142c06a2ba55ddba5a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090929"
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