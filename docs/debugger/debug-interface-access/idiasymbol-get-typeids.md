---
title: 'Idiasymbol:: Get_typeids | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d038c0be6f023206c6a96ec59389ec4063d975fd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53880082"
---
# <a name="idiasymbolgettypeids"></a>IDiaSymbol::get_typeIds
Recupera uma matriz de valores de identificador de tipo de compilador específicos para esse símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_typeIds (   
   DWORD  cTypeIds,  
   DWORD* pcTypeIds,  
   DWORD  typeIds[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cTypeIds`  
 [in] Tamanho do buffer para manter os dados.  
  
 `pcTypeIds`  
 [out] Retorna o número de `typeIds` escrita, ou, se `typeIds` é `NULL`, em seguida, o número total de identificadores de tipo disponíveis.  
  
 `typeIds[]`  
 [out] Uma matriz que deve ser preenchida com os identificadores de tipo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)