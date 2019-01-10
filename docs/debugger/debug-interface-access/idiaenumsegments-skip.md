---
title: 'Idiaenumsegments:: Skip | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Skip method
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e8fb7de90f43b6f8c4992366993c0c3d8409aba
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917573"
---
# <a name="idiaenumsegmentsskip"></a>IDiaEnumSegments::Skip
Ignora um número especificado de segmentos em uma sequência de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 celt  
 [in] O número de segmentos na sequência de enumeração para ignorar.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` se não houver nenhum mais segmentos para ignorar.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)