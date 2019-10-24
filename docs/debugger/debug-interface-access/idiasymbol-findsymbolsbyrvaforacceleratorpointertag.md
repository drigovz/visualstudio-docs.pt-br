---
title: IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0d05946db816e6bd209e364e11d5091163941a4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741148"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
Dado um valor de marca correspondente, esse método retorna uma enumeração de símbolos que estão contidos nessa função de stub em um endereço virtual relativo especificado.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag (
   DWORD             tagValue,
   DWORD             rva,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>Parâmetros
 `tagValue`

no O valor da marca do ponteiro para o qual os registros de símbolo do ponto são encontrados.

 `rva`

no O RVA usado para filtrar os símbolos que correspondem à variável de ponto com o valor de marca especificado.

 `ppResult`

fora Um ponteiro para um ponteiro de interface `IDiaEnumSymbols` que é inicializado com o resultado.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.

## <a name="remarks"></a>Comentários
 Chame esse método somente em uma interface `IDiaSymbol` que corresponda a uma função de stub de acelerador.

## <a name="see-also"></a>Consulte também
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)