---
title: CaptureCurrentFrame | Microsoft Docs
description: Use o método CaptureCurrentFrame da classe VsgDbg para capturar o restante do quadro atual para o arquivo de log de gráficos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 94c55a34ee71f8002d31613d64ff978f0a546b72
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874542"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Captura o restante do quadro atual para o arquivo de log de gráficos.

## <a name="syntax"></a>Sintaxe

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Comentários
 Se outra captura estiver em andamento, como uma captura que foi iniciada pela `BeginCapture` função, essa captura será concluída e gravada no log de gráficos como um quadro distinto. Imediatamente depois, o diagnóstico de gráficos começa a capturar o restante do quadro atual, que também é registrado como um quadro distinto. O fim do quadro atual é marcado por uma chamada para presente.

 Para capturar um quadro, você deve preparar seu aplicativo para capturar e gravar informações gráficas — ou seja, você deve ter chamado [init](init.md) por meio de uma instância da `VsgDbg` classe antes de chamar `CaptureCurrentFrame` .

## <a name="see-also"></a>Confira também
- [Init](init.md)
- [BeginCapture](begincapture.md)