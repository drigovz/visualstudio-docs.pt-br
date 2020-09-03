---
title: IDiaEnumSymbolsByAddr::Next | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Next method
ms.assetid: a1320587-7ce7-401f-9548-2f8bcece5cc3
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fc58c8da54380b8a835d64fcc5dc079bb8d8023e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189645"
---
# <a name="idiaenumsymbolsbyaddrnext"></a>IDiaEnumSymbolsByAddr::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera os próximos símbolos no endereço de ordenação.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT Next (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 celt  
 no O número de símbolos no enumerador a ser recuperado.  
  
 rgelt  
 fora Uma matriz que deve ser preenchida com o objeto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa os símbolos desejados.  
  
 pceltFetched  
 fora Retorna o número de símbolos no enumerador obtido.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não houver mais símbolos. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método atualiza a posição do enumerador pelo número de elementos buscados.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
