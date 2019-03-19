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
ms.openlocfilehash: 8befb3da4e4b6f060a5f58aedec3604afe70aefb
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159043"
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
 [in] Especifica qual estatística para retornar. Deve ser o valor:  
  
|Constante|Valor|Descrição|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Retorne o número de instruções executadas desde que o script iniciado ou que as estatísticas foram redefinidas.|  
  
 `pluHi`  
 [out] Os 32 bits altos de um inteiro sem sinal de 64 bits que representa a estatística.  
  
 `pluLo`  
 [out] Os 32 bits baixos de um inteiro sem sinal de 64 bits que representa a estatística.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os valores possíveis incluem, mas não são limitados aos valores na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna uma das estatísticas de script padrão.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [IActiveScriptStats Interface](../../winscript/reference/iactivescriptstats-interface.md)