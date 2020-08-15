---
title: Enumeração SCRIPTGCTYPE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f28e0ddd3764b3810d25bfbb9403c391c1bfd54
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238446"
---
# <a name="scriptgctype-enumeration"></a>Enumeração SCRIPTGCTYPE
O tipo de coleta de lixo a ser executado. Usado no método [IActiveScriptGarbageCollector:: CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {    SCRIPTGCTYPE_NORMAL           = 0,    SCRIPTGCTYPE_EXHAUSTIVE       = 1,} SCRIPTGCTYPE;  
```  
  
## <a name="enumeration-values"></a>Valores de enumeração  
  
|Valor|Tipo de coleta de lixo|  
|-|-|  
|SCRIPTGCTYPE_NORMAL|Faça a coleta de lixo normal. O valor inteiro é 0.|  
|SCRIPTGCTYPE_EXHAUSTIVE|Faça uma coleta de lixo exaustiva. O valor inteiro é 1.|  
  
## <a name="see-also"></a>Consulte também  
 [Constantes, enumerações e códigos de erro do script ativo](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)