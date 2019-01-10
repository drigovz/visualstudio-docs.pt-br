---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e65def0ac8e94b2f113332981f57c051896f6bd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875453"
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