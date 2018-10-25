---
title: 'Idiaenumframedata:: item | Microsoft Docs'
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
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17c0663c20401840f9df899b87911f6a8afb9d43
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877199"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera um elemento de quadro de dados por meio de um índice.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Item (   
   DWORD           index,  
   IDiaFrameData** section  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 índice  
 [in] Índice do [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objeto a ser recuperado. O índice está no intervalo de 0 a `count`-1, onde `count` é retornado pelo [idiaenumframedata:: Get_count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) método.  
  
 section  
 [out] Retorna um [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objeto que representa o elemento de dados de quadros desejada.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)



