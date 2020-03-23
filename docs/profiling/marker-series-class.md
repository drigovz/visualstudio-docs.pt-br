---
title: Classe marker_series | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 155d47f6764e754a1093cbcf884368c80d709a2a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62575911"
---
# <a name="marker_series-class"></a>Classe marker_series
Representa um canal serial de eventos gerados por um único provedor.

## <a name="syntax"></a>Sintaxe

```cpp
class marker_series;
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[marker_series::marker_series construtor](../profiling/marker-series-marker-series-constructor.md)|Inicia uma nova instância da classe `marker_series`.|
|[marker_series:~marker_series destruidor](../profiling/marker-series-tilde-marker-series-destructor.md)|Destrói o objeto marker_series e libera todos os recursos alocados.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[marker_series::método is_enabled](../profiling/marker-series-is-enabled-method.md)|Determina se alguma sessão habilitou o provedor.|
|[marker_series:write_alert método](../profiling/marker-series-write-alert-method.md)|Grava um alerta para o arquivo de rastreamento da Visualização Simultânea.|
|[marker_series::método write_flag](../profiling/marker-series-write-flag-method.md)|Grava um sinalizador para o arquivo de rastreamento da Visualização Simultânea.|
|[marker_series::método write_message](../profiling/marker-series-write-message-method.md)|Grava uma mensagem para o arquivo de rastreamento da Visualização Simultânea.|

## <a name="inheritance-hierarchy"></a>Hierarquia de herança
 `marker_series`

## <a name="requirements"></a>Requisitos
 **Cabeçalho:** *cvmarkersobj.h*

 **Namespace:** Concurrency::diagnostic

## <a name="see-also"></a>Confira também
- [espaço de nome diagnóstico](../profiling/diagnostic-namespace.md)