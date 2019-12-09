---
title: 'IDiaTable:: item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d402f5ad54d5c0f487cebb3a8c53f68d17828ed4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738723"
---
# <a name="idiatableitem"></a>IDiaTable::Item
Recupera uma referência à entrada especificada na tabela.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT Item ( 
   DWORD      index,
   IUnknown** element
);
```

#### <a name="parameters"></a>Parâmetros
 `index`

no O índice da entrada da tabela no intervalo de 0 a `count`-1, em que `count` é retornado pelo método [IDiaTable:: get_Count](../../debugger/debug-interface-access/idiatable-get-count.md).

 `element`

fora Retorna um objeto `IUnknown` que representa a entrada da tabela especificada.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Uma tabela representa uma coleção de objetos. Dependendo desses objetos, o parâmetro do elemento pode ser convertido na interface apropriada. Por exemplo, se uma tabela contiver objetos [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) , o parâmetro do elemento poderá ser convertido na interface `IDiaSegment`.

 É uma abordagem mais comum para chamar o método `QueryInterface` na interface [IDiaTable](../../debugger/debug-interface-access/idiatable.md) para a interface do enumerador apropriada e usar os métodos específicos do enumerador para acessar o conteúdo da tabela. Consulte a interface [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) para obter um exemplo.

## <a name="see-also"></a>Consulte também
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)