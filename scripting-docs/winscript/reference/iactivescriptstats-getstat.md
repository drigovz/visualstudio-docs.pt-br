---
title: IActiveScriptStats::GetStat | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStat
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStat
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 096f1cf5b9bf8b5533bd5c36d33f014c747ff9aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574345"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Retorna uma das estatísticas de script padrão.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `stid`  
 no Especifica qual estatística retornar. Deve ser o valor:  
  
|Constante|Valor|Descrição|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Retorna o número de instruções executadas desde que o script foi iniciado ou as estatísticas foram redefinidas.|  
  
 `pluHi`  
 fora Os bits de 32 altos de um inteiro sem sinal de 64 bits que representa a estatística.  
  
 `pluLo`  
 fora Os bits de 32 baixos de um inteiro sem sinal de 64 bits que representa a estatística.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os valores possíveis incluem, mas não se limitam aos valores na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna uma das estatísticas de script padrão.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [IActiveScriptStats Interface](../../winscript/reference/iactivescriptstats-interface.md)