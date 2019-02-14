---
title: IDiaStackWalkFrame::searchForReturnAddressStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::searchForReturnAddressStart method
ms.assetid: 47660b9b-6e4f-4dfa-88ab-63dce28f7412
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a9c1e28c458ad863248235166df03cb2ae4f8a3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931226"
---
# <a name="idiastackwalkframesearchforreturnaddressstart"></a>IDiaStackWalkFrame::searchForReturnAddressStart
Pesquisa o quadro de pilha especificada para um endereço de retorno em ou próximo o endereço especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT searchForReturnAddressStart (   
   IDiaFrameData* frame,  
   ULONGLONG      startAddress,  
   ULONGLONG*     returnAddress  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `frame`  
 [in] Uma [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) objeto que representa o quadro de pilhas atual.  
  
 `startAddress`  
 [in] Um endereço de memória virtual da qual iniciar a pesquisa.  
  
 `returnAddress`  
 [out] Retorna a função mais próxima endereço do remetente a `startAddress`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)