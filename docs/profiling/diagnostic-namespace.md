---
title: Namespace diagnostic | Microsoft Docs
description: Use o namespace de diagnóstico para emitir marcadores de visualizador de simultaneidade. O namespace de diagnóstico é um membro do namespace de simultaneidade.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic
helpviewer_keywords:
- Concurrency, diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20b25e2974f4b0e4a6bbf6cf02c411fde3f3de1a
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686539"
---
# <a name="diagnostic-namespace"></a>Namespace de diagnóstico
O namespace `diagnostics` fornece funcionalidade para emitir marcadores de Visualização Simultânea.

## <a name="syntax"></a>Sintaxe

```cpp
namespace diagnostic;
```

## <a name="members"></a>Membros

### <a name="classes"></a>Classes

|Name|Descrição|
|----------|-----------------|
|[Classe marker_series](../profiling/marker-series-class.md)|Representa um canal serial de eventos gerados por um único provedor.|
|[Classe span](../profiling/span-class.md)|Define uma fase do aplicativo.|

### <a name="enumerations"></a>Enumerações

|Name|Descrição|
|----------|-----------------|
|[Enumeração marker_importance](../profiling/marker-importance-enumeration.md)|Representa o nível de importância de um marcador da Visualização Simultânea.|

## <a name="requirements"></a>Requisitos
 **Cabeçalho:** *cvmarkersobj.h*

 **Namespace:** Simultaneidade

## <a name="see-also"></a>Consulte também
- [Namespace de simultaneidade (Visualizador de simultaneidade)](../profiling/concurrency-namespace-concurrency-visualizer.md)