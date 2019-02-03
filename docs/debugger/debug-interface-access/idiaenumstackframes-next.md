---
title: IDiaEnumStackFrames::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00be37ffa1724cb6ced2423ea388b2a24dae42f3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919962"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
Recupera um número especificado de elementos de quadro de pilha da sequência de enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT Next(   
   ULONG             celt,  
   IDiaStackFrame**  rgelt,  
   ULONG*            pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 celt  
 [in] O número de elementos de stackframe no enumerador a ser recuperado.  
  
 rgelt  
 [out] Uma matriz que deve ser preenchido com os solicitados [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) objetos.  
  
 pceltFetched  
 [out] Retorna o número da pilha de elementos de quadro no enumerador buscado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se não houver nenhum mais quadros de pilha. Caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)