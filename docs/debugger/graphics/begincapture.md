---
title: BeginCapture | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e714245ff2585f9de0b998160ce08f04c88b097
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62896430"
---
# <a name="begincapture"></a>BeginCapture
Inicia um intervalo de captura que terminará com `EndCapture`.

## <a name="syntax"></a>Sintaxe

```C++
void BeginCapture();
```

## <a name="remarks"></a>Comentários
 Normalmente, um intervalo de captura abrange um subconjunto de um quadro, como quando você deseja capturar informações gráficas trata apenas de um determinado tipo de chamada de desenho. Se o intervalo de captura abrange uma chamada para apresentar, dois quadros de informações de gráficos são capturados. O primeiro quadro abrange o intervalo entre a chamada para `BeginCapture` e a chamada para apresentar; o segundo quadro abrange o intervalo entre o primeiro evento do Direct3D após a chamada para apresentar e a chamada para `EndCapture`.

 Para capturar um intervalo, você deve preparar seu aplicativo para capturar e registrar informações de gráficos — ou seja, você deve ter chamado [Init](init.md) por meio de uma instância das `VsgDbg` classe antes de chamar `BeginCapture` ou `EndCapture`.

## <a name="see-also"></a>Consulte também
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)