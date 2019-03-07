---
title: ISimpleConnectionPoint::DescribeEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.DescribeEvents
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::DescribeEvents
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43a20a2d9580c80bc6aea5d22c6a0713f4843634
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088498"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Retorna o DISPID e o nome para cada evento em um intervalo especificado de eventos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `iEvent`  
 [in] Índice do primeiro evento a recuperar.  
  
 `cEvents`  
 [in] Número de eventos para recuperar.  
  
 `prgid`  
 [out] Matriz de valores DISPID do evento.  
  
 `prgbstr`  
 [out] Matriz de nomes de evento.  
  
 `pcEventsFetched`  
 [out] O número real de eventos buscada.  
  
## <a name="return-value"></a>Valor de retorno  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`S_FALSE`|Mais eventos foram solicitados que estavam disponíveis. Indisponíveis eventos são representados com DISPID_NULL e um BSTR nulo.|  
|`E_INVALIDARG`|Nenhum elemento pôde ser buscado.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o DISPID e o nome para cada evento em um intervalo especificado de eventos.  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)