---
title: 'Idiaenumsourcefiles:: Skip | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Skip method
ms.assetid: 4821e6dd-d33f-403d-857d-e3ae81e4a9e3
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8154e8405f679a2bf0879c87e423a42b203cd884
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879591"
---
# <a name="idiaenumsourcefilesskip"></a>IDiaEnumSourceFiles::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ignora um número especificado de arquivos de origem em uma sequência de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 celt  
 [in] O número de arquivos de origem na sequência de enumeração para ignorar.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` se não houver nenhum arquivo de origem mais ignorar.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)



