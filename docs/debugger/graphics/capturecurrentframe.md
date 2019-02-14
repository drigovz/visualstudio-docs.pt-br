---
title: CaptureCurrentFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05d93e4cee3fb4969b928caa3ae76112708469f1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997228"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Captura o restante do quadro atual para o arquivo de log de gráficos.  
  
## <a name="syntax"></a>Sintaxe  
  
```C++  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>Comentários  
 Se outra captura está atualmente em andamento — como uma captura que foi iniciada pelo `BeginCapture` função — de captura será concluída e registrada no log de gráficos como um quadro distinto. Logo depois disso, o diagnóstico de gráficos começa capturando o restante do quadro atual, que também é registrado como um quadro distinto. Final do quadro atual é marcado por uma chamada para apresentar.  
  
 Para capturar um quadro, você deve preparar seu aplicativo para capturar e registrar informações de gráficos — ou seja, você deve ter chamado [Init](init.md) por meio de uma instância das `VsgDbg` classe antes de chamar `CaptureCurrentFrame`.  
  
## <a name="see-also"></a>Consulte também  
 [Init](init.md)   
 [BeginCapture](begincapture.md)