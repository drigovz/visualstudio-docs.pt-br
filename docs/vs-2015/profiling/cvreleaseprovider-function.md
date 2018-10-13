---
title: Função CvReleaseProvider | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f5b644dfdb469d84b90a1a0d7d59651fbad2460b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49300775"
---
# <a name="cvreleaseprovider-function"></a>Função CvReleaseProvider
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Libera o provedor de marcador. A liberação do provedor de marcador não afetará a série de marcador criada anteriormente desse provedor. A série de marcador deve ser liberada separadamente pela chamada CvReleaseMarkerSeries. A falha ao liberar o provedor causa uma perda de memória.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pProvider`  
 Contexto de provedor. Não pode ser NULL.  
  
## <a name="return-value"></a>Valor de retorno  
 S_OK quando o provedor é liberado com êxito ou código de erro no caso de erros. Use as macros SUCCEEDED/FAILED para verificar a condição de erro.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** cvmarkers.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência de biblioteca C++](../profiling/cpp-library-reference.md)



