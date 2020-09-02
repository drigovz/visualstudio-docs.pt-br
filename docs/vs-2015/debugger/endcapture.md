---
title: EndCapture | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a451746cae978f141b30fb7295a82310e04367c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197105"
---
# <a name="endcapture"></a>EndCapture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Encerra um intervalo de captura que foi iniciado com `BeginCapture` .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void EndCapture();  
```  
  
## <a name="remarks"></a>Comentários  
 Um intervalo de captura normalmente abrange um subconjunto de um quadro, como quando você deseja capturar informações gráficas apenas sobre um determinado tipo de chamada de desenho. Se o intervalo de captura abranger uma chamada para presente, então dois quadros de informações gráficas serão capturados. O primeiro quadro abrange o intervalo entre a chamada e a `BeginCapture` chamada para Present; o segundo quadro abrange o intervalo entre o primeiro evento do Direct3D após a chamada para Present e a chamada para `EndCapture` .  
  
 Para capturar um intervalo, você deve preparar seu aplicativo para capturar e gravar informações gráficas — ou seja, você deve ter chamado [init](../debugger/init.md) por meio de uma instância da `VsgDbg` classe antes de chamar `BeginCapture` ou `EndCapture` .  
  
## <a name="see-also"></a>Consulte Também  
 [BeginCapture](../debugger/begincapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)
