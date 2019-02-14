---
title: IDiaEnumSymbolsByAddr::Prev | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::Prev method
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81700f73b7a1730a4f74f5340d5928b3662db3b1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933484"
---
# <a name="idiaenumsymbolsbyaddrprev"></a>IDiaEnumSymbolsByAddr::Prev
Recupera os símbolos anteriores na ordem pelo endereço.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 celt  
 [in] O número de símbolos no enumerador a ser recuperado.  
  
 rgelt  
 [out] Uma matriz que deve ser preenchida com [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objetos que representam os símbolos desejados.  
  
 pceltFetched  
 [out] Retorna o número de símbolos no enumerador buscado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não houver nenhum símbolo anterior. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método atualiza a posição de enumerador pelo número de elementos buscada.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)