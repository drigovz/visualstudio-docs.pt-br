---
title: Método marker_series::write_alert | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert
helpviewer_keywords:
- Concurrency::diagnostic:marker_series::write_alert method
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 635f767f97ea3d237aeff843e99735eccae31efc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831378"
---
# <a name="markerserieswritealert-method"></a>Método marker_series::write_alert
Grava um alerta para o arquivo de rastreamento da Visualização Simultânea.

## <a name="syntax"></a>Sintaxe

```cpp
void write_alert(
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Parâmetros
 `_Format` Uma cadeia de caracteres de formato composto, que contém um texto intercalado com zero ou mais itens de formato correspondentes aos objetos na lista de argumentos.

## <a name="requirements"></a>Requisitos
 **Cabeçalho:** *cvmarkersobj.h*

 **Namespace:** Concurrency::diagnostic

## <a name="see-also"></a>Consulte também
- [Classe marker_series](../profiling/marker-series-class.md)