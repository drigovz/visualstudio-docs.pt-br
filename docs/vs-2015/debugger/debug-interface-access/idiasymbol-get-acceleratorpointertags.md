---
title: IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 829c7a0193ce2742959f677e95dd4a499997cf5b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58923507"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Retorna todos os valores de marca de ponteiro de acelerador que correspondem a uma função de stub do acelerador de C++ AMP.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
