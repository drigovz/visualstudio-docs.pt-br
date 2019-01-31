---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f94ea23c1a6afd16f57a2ffb9944cf8a7ded5c9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55019525"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
Retorna todos os valores de marca de ponteiro de acelerador que correspondem a uma função de stub do acelerador de C++ AMP.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cnt`  
 [in] O tamanho da matriz de saída `pPointerTags`.  
  
 `pcnt`  
 [out] A contagem de marcas de ponteiro accelerator na função de stub do acelerador de C++ AMP.  
  
 `pPointerTags`  
 [out] Um `DWORD` ponteiro de matriz é preenchido com os valores de marca de ponteiro accelerator na função de stub do acelerador de C++ AMP.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é chamado em um `IDiaSymbol` interface que corresponde a uma função de stub do acelerador de C++ AMP.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)