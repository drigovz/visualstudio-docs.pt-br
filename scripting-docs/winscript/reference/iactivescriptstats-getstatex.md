---
title: IActiveScriptStats::GetStatEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStatEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e5f25887d8fdd5b5fb774cc2e8619c1a93432c1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442772"
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
Retorna uma estatística de script personalizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `guid`  
 [in] Especifica qual estatística para retornar. A semântica de qual estatística corresponde a um determinado GUID é totalmente o mecanismo definido.  
  
 `pluHi`  
 [out] Os 32 bits altos de um inteiro sem sinal de 64 bits que representa a estatística.  
  
 `pluLo`  
 [out] Os 32 bits baixos de um inteiro sem sinal de 64 bits que representa a estatística.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`E_NOTIMPL`|O método não está implementado.|  
  
## <a name="remarks"></a>Comentários  
 Esse método permite que um mecanismo de script personalizado retornar estatísticas significativas para um host personalizado.  
  
> [!NOTE]
> Esse método não está implementado atualmente.  
  
## <a name="see-also"></a>Consulte também  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [IActiveScriptStats Interface](../../winscript/reference/iactivescriptstats-interface.md)