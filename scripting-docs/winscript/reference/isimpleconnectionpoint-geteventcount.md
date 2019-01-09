---
title: ISimpleConnectionPoint::GetEventCount | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.GetEventCount
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::GetEventCount
ms.assetid: f1527d5b-6076-4536-8e59-e55da741ef39
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce53089b3dc468043648378d80e54cc2d3188358
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089798"
---
# <a name="isimpleconnectionpointgeteventcount"></a>ISimpleConnectionPoint::GetEventCount
Retorna o número de eventos expostos nesta interface.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT GetEventCount(  
   ULONG*  pulCount  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pulCount`  
 [out] Número de eventos expostos na contagem interface.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o número de eventos expostos nesta interface.  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)