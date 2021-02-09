---
title: BeginCapture | Microsoft Docs
description: Use o método BeginCapture da classe VsgDbg para iniciar um intervalo de captura que terminará com endcapture.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a9e002a66ec3ec121a4cdc20ffb9ce59c1ed9dc0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874568"
---
# <a name="begincapture"></a>BeginCapture
Inicia um intervalo de captura que terminará com `EndCapture` .

## <a name="syntax"></a>Sintaxe

```C++
void BeginCapture();
```

## <a name="remarks"></a>Comentários
 Um intervalo de captura normalmente abrange um subconjunto de um quadro, como quando você deseja capturar informações gráficas apenas sobre um determinado tipo de chamada de desenho. Se o intervalo de captura abranger uma chamada para presente, então dois quadros de informações gráficas serão capturados. O primeiro quadro abrange o intervalo entre a chamada e a `BeginCapture` chamada para Present; o segundo quadro abrange o intervalo entre o primeiro evento do Direct3D após a chamada para Present e a chamada para `EndCapture` .

 Para capturar um intervalo, você deve preparar seu aplicativo para capturar e gravar informações gráficas — ou seja, você deve ter chamado [init](init.md) por meio de uma instância da `VsgDbg` classe antes de chamar `BeginCapture` ou `EndCapture` .

## <a name="see-also"></a>Confira também
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)