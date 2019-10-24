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
ms.openlocfilehash: 9521288b27b1f9b11a2fdb8cbbd613f1a77f857d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736152"
---
# <a name="begincapture"></a>BeginCapture
Inicia um intervalo de captura que terminará com `EndCapture`.

## <a name="syntax"></a>Sintaxe

```C++
void BeginCapture();
```

## <a name="remarks"></a>Comentários
 Um intervalo de captura normalmente abrange um subconjunto de um quadro, como quando você deseja capturar informações gráficas apenas sobre um determinado tipo de chamada de desenho. Se o intervalo de captura abranger uma chamada para presente, então dois quadros de informações gráficas serão capturados. O primeiro quadro abrange o intervalo entre a chamada para `BeginCapture` e a chamada para presente; o segundo quadro abrange o intervalo entre o primeiro evento do Direct3D após a chamada para apresentar e a chamada para `EndCapture`.

 Para capturar um intervalo, você deve preparar seu aplicativo para capturar e gravar informações gráficas — ou seja, você deve ter chamado [init](init.md) por meio de uma instância da classe `VsgDbg` antes de chamar `BeginCapture` ou `EndCapture`.

## <a name="see-also"></a>Consulte também
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)