---
title: Não é possível ter ' break ' fora do loop | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee177c8070fc5af8123d7fd78e69b1f767a5b700
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862794"
---
# <a name="cant-have-break-outside-of-loop"></a>Não é possível ter 'break' fora do loop
Você tentou usar a palavra-chave **Break** fora de um loop. A palavra-chave **Break** é usada para encerrar um loop ou uma `switch` instrução. Ele deve ser inserido no corpo de um loop ou `switch` instrução. No entanto, um **rótulo** pode seguir a palavra-chave break.  
  
```js
break labelname;  
```  
  
 Você só precisa da forma rotulada da palavra-chave **Break** quando estiver usando loops aninhados ou `switch` instruções e precisar interromper um loop que não seja o mais interno.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Verifique se a palavra-chave **Break** aparece dentro de um loop delimitador ou instrução switch.  
  
## <a name="see-also"></a>Confira também  
 [Instrução break](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/break)   
 [Controlando o fluxo do programa](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)   
 [Solucionar problemas com scripts](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/What_went_wrong)