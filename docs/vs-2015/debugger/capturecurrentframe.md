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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922250"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Captura o restante do quadro atual para o arquivo de log de gráficos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Comentários  
 Se outra captura está atualmente em andamento — como uma captura que foi iniciada pelo `BeginCapture` função — de captura será concluída e registrada no log de gráficos como um quadro distinto. Logo depois disso, o diagnóstico de gráficos começa capturando o restante do quadro atual, que também é registrado como um quadro distinto. Final do quadro atual é marcado por uma chamada para apresentar.  
  
 Para capturar um quadro, você deve preparar seu aplicativo para capturar e registrar informações de gráficos — ou seja, você deve ter chamado [Init](../debugger/init.md) por meio de uma instância das `VsgDbg` classe antes de chamar `CaptureCurrentFrame`.  
  
## <a name="see-also"></a>Consulte também  
 [Init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)
