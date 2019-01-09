---
title: Não é possível ter 'break' fora do loop | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53f32da997b775e01959df5abc7e72fb55c1b194
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086691"
---
# <a name="cant-have-break-outside-of-loop"></a>Não é possível ter 'break' fora do loop
Você tentou usar o **quebra** palavra-chave fora de um loop. O **quebra** palavra-chave é usada para encerrar um loop ou `switch` instrução. Ele deve ser inserido no corpo de um loop ou `switch` instrução. No entanto, uma **rótulo** pode seguir a palavra-chave break.  
  
```js
break labelname;  
```  
  
 Você só precisa rotulada forma do **quebra** loops aninhados de palavra-chave quando você estiver usando ou `switch` instruções e a necessidade de interromper um loop não é o mais interno.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Verifique se o **quebra** palavra-chave aparece dentro de uma instrução de loop ou opção de circunscrição.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução break](../../javascript/reference/break-statement-javascript.md)   
 [Controlando o fluxo de programa](../../javascript/controlling-program-flow-javascript.md)   
 [Solucionar problemas com scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)