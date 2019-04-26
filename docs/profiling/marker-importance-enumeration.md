---
title: Enumeração de marker_importance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3f5cfb583ec4fceb9fb7428b08c00f6ca8e26b6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62999966"
---
# <a name="markerimportance-enumeration"></a>Enumeração marker_importance
Representa o nível de importância de um marcador da Visualização Simultânea.

## <a name="syntax"></a>Sintaxe

```cpp
enum marker_importance;
```

## <a name="members"></a>Membros

### <a name="values"></a>Valores

|Nome|Descrição|
|----------|-----------------|
|`critical_importance`|Especifica que o marcador tem importância crítica.|
|`high_importance`|Especifica que o marcador tem alta importância.|
|`low_importance`|Especifica que o marcador tem baixa importância.|
|`normal_importance`|Especifica que o marcador tem importância normal.|

## <a name="requirements"></a>Requisitos
 **Cabeçalho:** *cvmarkersobj.h*

 **Namespace:** Concurrency::diagnostic

## <a name="see-also"></a>Consulte também
- [namespace de diagnóstico](../profiling/diagnostic-namespace.md)