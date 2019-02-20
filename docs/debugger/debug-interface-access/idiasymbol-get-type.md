---
title: IDiaSymbol::get_type | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_type method
ms.assetid: 1c6a4176-dd4e-4c22-8b8f-0e559fc078ba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5550ed7551e58140301f6a434d252a534b78228
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227188"
---
# <a name="idiasymbolgettype"></a>IDiaSymbol::get_type
Recupera o símbolo que representa o tipo para esse símbolo.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT get_type (
    IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parâmetros
`pRetVal`  
[out] Retorna um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto que representa o tipo desse símbolo.

## <a name="return-value"></a>Valor de retorno
Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.

> [!NOTE]
> Um valor de retorno `S_FALSE` significa que a propriedade não está disponível para o símbolo.

## <a name="remarks"></a>Comentários
Para determinar o tipo tem um símbolo, você deve chamar esse método e examinar resultante [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto. Observe que é possível que um símbolo não tenha um tipo. Por exemplo, o nome de uma estrutura não tem um tipo, mas pode ter símbolos filhos (usar o [idiasymbol:: Findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md) método a examinar os filhos).

## <a name="example"></a>Exemplo

```C++
IDiaSymbol*         pType;
CComPtr<IDiaSymbol> pBaseType;
if (SUCCEEDED(pType->get_type( &pBaseType ))) {
    BasicType btBaseType;
    if (SUCCEEDED(pBaseType->get_baseType((DWORD *)&btBaseType))) {
        // Do something with basic type.
    }
}
```

## <a name="see-also"></a>Consulte também
[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)  
[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
