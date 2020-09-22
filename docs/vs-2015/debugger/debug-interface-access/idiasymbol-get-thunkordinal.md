---
title: IDiaSymbol::get_thunkOrdinal | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 540eb49b215d06127a47df1defc436a0a307aa6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838307"
---
# <a name="idiasymbolget_thunkordinal"></a>IDiaSymbol::get_thunkOrdinal
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera o tipo de conversão de uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 fora Retorna um valor da enumeração de [enumeração THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md) que especifica o tipo de conversão de uma função.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
> [!NOTE]
> Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="remarks"></a>Comentários  
 Essa propriedade será válida somente se o símbolo como um valor de [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) de `SymTagThunk` .  
  
 Uma "conversão" é um trecho de código que converte entre um espaço de endereço de memória de 32 bits (também conhecido como espaço de endereço simples) e um espaço de endereço de 16 bits (conhecido como um espaço de endereço segmentado).  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração de THUNK_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
