---
title: Enumeração SCRIPT_DEBUGGER_OPTIONS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SCRIPT_DEBUGGER_OPTIONS Enumeration
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c69d419732786442cda275bf85c74ab2b9d3e870
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574559"
---
# <a name="script_debugger_options-enumeration"></a>Enumeração SCRIPT_DEBUGGER_OPTIONS
Indica um conjunto de opções e/ou recursos que se aplicam ao depurador anexado. Usado em [IDebugApplicationNode100:: GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) e [IDebugApplicationNode100:: SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
> Essas constantes são implementadas pelo PDM v 10.0 e posteriores. Localizado em. activdbg100.h.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Valor|Descrição|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|Não há nenhuma opção definida.|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|Indica que o tempo de execução de script deve gerar eventos BREAKREASON_ERROR quando uma exceção é lançada. Essa opção pode ser definida pelo depurador ou definida pelo código do usuário via `Debug.enableFirstChanceExceptions(<true&#124;false>)`.|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|Indica que o depurador anexado dá suporte a Web Workers.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e estruturas de depurador do script ativo](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)