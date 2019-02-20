---
title: IDiaEnumSegments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments interface
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39ac47f107c7365e2932d36084b2fc114934daba
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227349"
---
# <a name="idiaenumsegments"></a>IDiaEnumSegments
Enumera os vários segmentos contidos na fonte de dados.

## <a name="syntax"></a>Sintaxe

```
IDiaEnumSegments : IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
A tabela a seguir mostra os métodos de `IDiaEnumSegments`.

|Método|Descrição|
|------------|-----------------|
|[IDiaEnumSegments::get__NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|Recupera o [IEnumVARIANT Interface](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) versão este enumerador.|
|[IDiaEnumSegments::get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|Recupera o número de segmentos.|
|[IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)|Recupera um segmento por meio de um índice.|
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|Recupera um número especificado de segmentos na sequência de enumeração.|
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|Ignora um número especificado de segmentos em uma sequência de enumeração.|
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|Redefine uma sequência de enumeração para o início.|
|[IDiaEnumSegments::Clone](../../debugger/debug-interface-access/idiaenumsegments-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|

## <a name="remarks"></a>Comentários

## <a name="notes-for-callers"></a>Observações para chamadores
Obtenha essa interface por meio da chamada a `QueryInterface` método em um [IDiaTable](../../debugger/debug-interface-access/idiatable.md) objeto. Consulte o exemplo para obter detalhes.

## <a name="example"></a>Exemplo
Este exemplo mostra como obter o `IDiaEnumSections` interface de uma tabela. Para obter um exemplo mais completo de como usar segmentos, consulte o [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) interface.

```C++
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pSegments;
    if ( SUCCEEDED( pTable->QueryInterface(
                                __uuidof( IDiaEnumSegments ),
                                (void**)&pSegments )
                  )
       )
    {
        // Do something with this enumeration
    }
}
```

## <a name="requirements"></a>Requisitos
Cabeçalho: Dia2.h

Biblioteca: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Consulte também
[Interfaces (SDK de Acesso à Interface de Depuração)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)  
[IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
