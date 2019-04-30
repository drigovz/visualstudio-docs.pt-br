---
title: IActiveScriptGarbageCollector::CollectGarbage | Microsoft Docs
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
ms.openlocfilehash: db8683534e449b2cdd8fcdb344c245d93da8fafc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62954961"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
O host de Script ativo chama esse método para iniciar a coleta de lixo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `scriptgctype`  
 [in] O [enumeração SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md) que especifica se deve fazer a coleta de lixo completa ou normal.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna um HRESULT.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptGarbageCollector Interface](../../winscript/reference/iactivescriptgarbagecollector-interface.md)