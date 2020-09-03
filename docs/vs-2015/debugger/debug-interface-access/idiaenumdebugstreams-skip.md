---
title: IDiaEnumDebugStreams::Skip | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Skip method
ms.assetid: 6ec7753c-d7af-4879-b107-1b3442e0b025
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1b052809a6fedb7f94bc973fa1115269f6590970
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182537"
---
# <a name="idiaenumdebugstreamsskip"></a>IDiaEnumDebugStreams::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ignora um número especificado de fluxos de depuração em uma sequência de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 no O número de fluxos de depuração na sequência de enumeração a serem ignorados.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará `S_OK` ; caso contrário, retornará `S_FALSE` se não houver mais registros a serem ignorados.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)
