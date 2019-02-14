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
ms.openlocfilehash: 536fac55c68a7736a37961ccab2741d6b8aedd41
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993176"
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
 [EndCapture](endcapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)