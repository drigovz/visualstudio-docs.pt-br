---
title: IEnumRemoteDebugApplications::Skip | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumRemoteDebugApplications.Skip
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumRemoteDebugApplications::Skip
ms.assetid: 9f6578d9-8de5-419c-b1b5-7cb07b6367fb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 492c02df40c767ea54e78f6951c1d02c4a69bb32
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088524"
---
# <a name="ienumremotedebugapplicationsskip"></a>IEnumRemoteDebugApplications::Skip
Ignora um número especificado de segmentos em uma sequência de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] Número de segmentos na sequência de enumeração para ignorar.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Este método ignora um número especificado de segmentos em uma sequência de enumeração.  
  
## <a name="see-also"></a>Consulte também  
 [Interface IEnumRemoteDebugApplications](../../winscript/reference/ienumremotedebugapplications-interface.md)