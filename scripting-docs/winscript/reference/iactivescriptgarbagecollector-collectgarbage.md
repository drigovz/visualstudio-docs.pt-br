---
title: 'IActiveScriptGarbageCollector:: CollectGarbage | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0539ed2cb3540cf33ceaaa15827c3ca08c156698
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573591"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
O host de script ativo chama esse método para iniciar a coleta de lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `scriptgctype`  
 no A [Enumeração SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md) que especifica se a coleta de lixo normal ou exaustiva será feita.  
  
## <a name="return-value"></a>Valor retornado  
 Retorna um HRESULT.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptGarbageCollector Interface](../../winscript/reference/iactivescriptgarbagecollector-interface.md)