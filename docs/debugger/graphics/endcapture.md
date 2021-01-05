---
title: EndCapture | Microsoft Docs
description: Use o método endcapture da classe VsgDbg para finalizar um intervalo de captura que foi iniciado com BeginCapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bbdc8f2dc4fa3ad25be8674b9a46bf02179aa1d
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727825"
---
# <a name="endcapture"></a>EndCapture
Encerra um intervalo de captura que foi iniciado com `BeginCapture` .

## <a name="syntax"></a>Sintaxe

```C++
void EndCapture();
```

## <a name="remarks"></a>Comentários
 Um intervalo de captura normalmente abrange um subconjunto de um quadro, como quando você deseja capturar informações gráficas apenas sobre um determinado tipo de chamada de desenho. Se o intervalo de captura abranger uma chamada para presente, então dois quadros de informações gráficas serão capturados. O primeiro quadro abrange o intervalo entre a chamada e a `BeginCapture` chamada para Present; o segundo quadro abrange o intervalo entre o primeiro evento do Direct3D após a chamada para Present e a chamada para `EndCapture` .

 Para capturar um intervalo, você deve preparar seu aplicativo para capturar e gravar informações gráficas — ou seja, você deve ter chamado [init](init.md) por meio de uma instância da `VsgDbg` classe antes de chamar `BeginCapture` ou `EndCapture` .

## <a name="see-also"></a>Consulte também
- [BeginCapture](begincapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)