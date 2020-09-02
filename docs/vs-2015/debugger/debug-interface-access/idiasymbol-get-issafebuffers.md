---
title: 'IDiaSymbol:: get_isSafeBuffers | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isSafeBuffers method
ms.assetid: f29e373d-e7bb-4181-ab9f-bf708d401d83
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 046744fda09f272ca80c2760e880dce23d45ae36
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65673752"
---
# <a name="idiasymbolget_issafebuffers"></a>IDiaSymbol::get_isSafeBuffers
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera um sinalizador que especifica se a diretiva de pré-processador para um buffer seguro é usada. Use quando a [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) for definida como `SymTagFunction` .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_isSafeBuffers(   
   BOOL* pRetVal)  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 fora Retorna `TRUE` se o ponteiro usa uma diretiva de pré-processador para um buffer seguro; caso contrário, retorna `FALSE` .  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
> [!NOTE]
> Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: dia2. h  
  
 Biblioteca: diaguids. lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [strict_gs_check](https://msdn.microsoft.com/library/decfec81-c916-42e0-a07f-8cc26df6a7ce)
