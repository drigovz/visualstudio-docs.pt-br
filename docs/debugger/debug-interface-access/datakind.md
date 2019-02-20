---
title: DataKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf8e59bf79355b4e610091ac8662b8d2a01af322
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318674"
---
# <a name="datakind"></a>DataKind
Indica o escopo específico de um valor de dados.

## <a name="syntax"></a>Sintaxe

```C++
enum DataKind {
    DataIsUnknown,
    DataIsLocal,
    DataIsStaticLocal,
    DataIsParam,
    DataIsObjectPtr,
    DataIsFileStatic,
    DataIsGlobal,
    DataIsMember,
    DataIsStaticMember,
    DataIsConstant
};
```

## <a name="elements"></a>Elementos
DataIsUnknown  
Símbolo de dados não pode ser determinado.

DataIsLocal  
Item de dados é uma variável local.

DataIsStaticLocal  
Item de dados é uma variável local estática.

DataIsParam  
Item de dados é um parâmetro formal.

DataIsObjectPtr  
Item de dados é um ponteiro de objeto (`this`).

DataIsFileStatic  
Item de dados é uma variável no escopo do arquivo.

DataIsGlobal  
Item de dados é uma variável global.

DataIsMember  
Item de dados é uma variável de membro de objeto.

DataIsStaticMember  
Item de dados é uma variável de classe estática.

DataIsConstant  
Item de dados é um valor constante.

## <a name="remarks"></a>Comentários
Os valores nesta enumeração são retornados pelo [idiasymbol:: Get_datakind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) método.

## <a name="requirements"></a>Requisitos
Cabeçalho: cvconst.h

## <a name="see-also"></a>Consulte também
[Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
