---
title: CaptureCurrentFrame | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2718e800e2a31eb66319259ed1e43f2ab8b084c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161642"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Captura o restante do quadro atual para o arquivo de log de gráficos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Comentários  
 Se outra captura estiver em andamento, como uma captura que foi iniciada pela `BeginCapture` função, essa captura será concluída e gravada no log de gráficos como um quadro distinto. Imediatamente depois, o diagnóstico de gráficos começa a capturar o restante do quadro atual, que também é registrado como um quadro distinto. O fim do quadro atual é marcado por uma chamada para presente.  
  
 Para capturar um quadro, você deve preparar seu aplicativo para capturar e gravar informações gráficas — ou seja, você deve ter chamado [init](../debugger/init.md) por meio de uma instância da `VsgDbg` classe antes de chamar `CaptureCurrentFrame` .  
  
## <a name="see-also"></a>Consulte Também  
 [Iniciar](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)
