---
title: IDiaEnumSymbols::Skip | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e7a6a3f06572392cad2edbf125d0ff6491b508c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62563696"
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ignora um número especificado de símbolos em uma sequência de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 celt  
 no O número de símbolos na sequência de enumeração a serem ignorados.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará `S_OK` ; caso contrário, retornará `S_FALSE` se não houver mais símbolos a serem ignorados.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
