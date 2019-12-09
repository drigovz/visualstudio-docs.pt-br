---
title: 'IDiaEnumTables:: item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf2d6b14f17d42a128e59446e27bfc251de40d17
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743748"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
Recupera uma tabela por meio de um índice ou nome.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Item ( 
   VARIANT     index,
   IDiaTable** table
);
```

#### <a name="parameters"></a>Parâmetros
 `index`

no Índice ou nome do [IDiaTable](../../debugger/debug-interface-access/idiatable.md) a ser recuperado. Se for usada uma variante de inteiro, ela deverá estar no intervalo de 0 a `count`-1, em que `count` é retornado pelo método [IDiaEnumTables:: get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) .

 `table`

fora Retorna um objeto [IDiaTable](../../debugger/debug-interface-access/idiatable.md) que representa a tabela desejada.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Se uma variante de cadeia de caracteres for especificada, a cadeia de caracteres nomeia uma tabela específica. O nome deve ser um dos nomes de tabela, conforme definido em [constantes (debug interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).

## <a name="example"></a>Exemplo

```C++
VARIANT var;
var.vt = VT_BSTR;
var.bstrVal = SysAllocString(DiaTable_Symbols );
IDiaTable* pTable;
pEnumTables->Item( var, &pTable );
```

## <a name="see-also"></a>Consulte também
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)
- [Constantes (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)