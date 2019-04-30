---
title: Enumeração APPLICATION_NODE_EVENT_FILTER | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- APPLICATION_NODE_EVENT_FILTER Constants
ms.assetid: dccb2cf7-0598-46f8-b3eb-16b752815e96
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c1727c8d1526199d179fe137c9bf899959bc2ba
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422210"
---
# <a name="applicationnodeeventfilter-enumeration"></a>Enumeração APPLICATION_NODE_EVENT_FILTER
Especifica os tipos de nós serem excluídos ao filtrar documentos de código. Usado na [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) e [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
> Essas constantes são implementadas pelo PDM v10.0 e maior. Localizado em. activdbg100.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum tagAPPLICATION_NODE_EVENT_FILTER {    FILTER_EXCLUDE_NOTHING = 0,    FILTER_EXCLUDE_ANONYMOUS_CODE = 0x1,    FILTER_EXCLUDE_EVAL_CODE = 0x2} APPLICATION_NODE_EVENT_FILTER;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Valor|Descrição|  
|------------|-----------|-----------------|  
|FILTER_EXCLUDE_NOTHING|0x00000000|Envie todos os eventos.|  
|FILTER_EXCLUDE_ANONYMOUS_CODE|0x00000001|Exclua nós de código anônimo. Esses nós são usados no tempo de execução do JScript para `new Function([args,] <code>)'`.|  
|FILTER_EXCLUDE_EVAL_CODE|0x00000002|Exclua nós de avaliação de código. Esses nós são usados pelo tempo de execução do JScript para suporte eval.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e estruturas de depurador do script ativo](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)