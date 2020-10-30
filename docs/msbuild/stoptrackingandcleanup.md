---
title: StopTrackingAndCleanup | Microsoft Docs
description: Saiba como o MSBuild usa StopTrackingAndCleanup para interromper todo o acompanhamento e liberar qualquer memória usada pela sessão de rastreamento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05aec8bc85ac392670469da8073da02888b2f063
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048106"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup

Interrompe o acompanhamento e libera a memória usada pela sessão de acompanhamento.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>Valor retornado

 Retorna um **HRESULT** com o conjunto de bits **SUCCEEDED** se o acompanhamento tiver sido interrompido.

## <a name="requirements"></a>Requisitos

 **Cabeçalho:** *FileTracker.h*

## <a name="see-also"></a>Veja também

- [StartTrackingContext](../msbuild/starttrackingcontext.md)