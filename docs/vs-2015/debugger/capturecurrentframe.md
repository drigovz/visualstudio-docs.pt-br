---
title: CaptureCurrentFrame | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b33cad0ad67d874ff5595eac7b634cc9810257f2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190676"
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



