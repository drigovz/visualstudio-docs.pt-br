---
title: ISimpleConnectionPoint::D escribeEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: b5000689d588fe3f63ec5408893187bba8d13d63
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571814"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
Retorna o DISPID e o nome de cada evento em um intervalo de eventos especificado.  
  
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
 no Índice do primeiro evento a ser recuperado.  
  
 `cEvents`  
 no Número de eventos a serem recuperados.  
  
 `prgid`  
 fora Matriz de valores DISPID do evento.  
  
 `prgbstr`  
 fora Matriz de nomes de evento.  
  
 `pcEventsFetched`  
 fora O número real de eventos buscados.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna um `HRESULT`. Os possíveis valores incluem, mas sem limitação, aqueles na tabela a seguir.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`S_FALSE`|Foram solicitados mais eventos do que estavam disponíveis. Os eventos indisponíveis são representados com DISPID_NULL e um BSTR nulo.|  
|`E_INVALIDARG`|Nenhum elemento pôde ser buscado.|  
  
## <a name="remarks"></a>Comentários  
 Esse método retorna o DISPID e o nome de cada evento em um intervalo de eventos especificado.  
  
## <a name="see-also"></a>Consulte também  
 [Interface ISimpleConnectionPoint](../../winscript/reference/isimpleconnectionpoint-interface.md)