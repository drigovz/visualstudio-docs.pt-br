---
title: Enumeração BREAKREASON | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKREASON
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 939d9f36c9838f02e58bc433d1a7bb9bef43c28d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955402"
---
# <a name="breakreason-enumeration"></a>Enumeração BREAKREASON
Indica o que causou a interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|BREAKREASON_STEP|O mecanismo de linguagem está no modo passo a passo.|  
|BREAKREASON_BREAKPOINT|O mecanismo de linguagem encontrou um ponto de interrupção explícito.|  
|BREAKREASON_DEBUGGER_BLOCK|O mecanismo de linguagem encontrou um bloco de depurador em outro thread.|  
|BREAKREASON_HOST_INITIATED|O host solicitou uma quebra.|  
|BREAKREASON_LANGUAGE_INITIATED|O mecanismo de linguagem solicitou uma quebra.|  
|BREAKREASON_DEBUGGER_HALT|O IDE do depurador solicitou uma quebra.|  
|BREAKREASON_ERROR|Erro de execução causou a interrupção.|  
|BREAKREASON_JIT|Causadas pela inicialização de depuração JIT.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e estruturas de depurador do script ativo](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)