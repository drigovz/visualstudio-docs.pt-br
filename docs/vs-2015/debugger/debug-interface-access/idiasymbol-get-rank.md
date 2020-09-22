---
title: IDiaSymbol::get_rank | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf7c39213ae2eb233509d720b7e7c2eab0a17560
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838520"
---
# <a name="idiasymbolget_rank"></a>IDiaSymbol::get_rank
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera a classificação (número de dimensões) de uma matriz multidimensional FORTRAN.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pRetVal`  
 fora Retorna o número de dimensões em uma matriz multidimensional FORTRAN.  
  
## <a name="return-value"></a>Valor Retornado  
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
> [!NOTE]
> Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## <a name="remarks"></a>Comentários  
 Rank refere-se ao número de dimensões em uma matriz em que a matriz é declarada como `myarray[1,2,3]` . Este exemplo tem uma classificação de 3 e 3 dimensões. A classificação não se aplica ao C++ que usa o conceito de uma matriz de matrizes para cada dimensão (ou seja, `myarray[1][2][3]` ).  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
