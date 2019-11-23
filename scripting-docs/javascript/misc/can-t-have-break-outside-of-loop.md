---
title: Não é possível ter ' break ' fora do loop | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 356e7022f940e696030b0cda4f71a599c147dd5a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576013"
---
# <a name="cant-have-break-outside-of-loop"></a>Não é possível ter 'break' fora do loop
Você tentou usar a palavra-chave **Break** fora de um loop. A palavra-chave **Break** é usada para encerrar um loop ou `switch` instrução. Ele deve ser inserido no corpo de um loop ou `switch` instrução. No entanto, um **rótulo** pode seguir a palavra-chave break.  
  
```js
break labelname;  
```  
  
 Você só precisa da forma rotulada da palavra-chave **Break** quando estiver usando loops aninhados ou instruções `switch` e precisar interromper um loop que não seja o mais interno.  
  
### <a name="to-correct-this-error"></a>Para corrigir esse erro  
  
- Verifique se a palavra-chave **Break** aparece dentro de um loop delimitador ou instrução switch.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução break](../../javascript/reference/break-statement-javascript.md)   
 [Controlando o fluxo do programa](../../javascript/controlling-program-flow-javascript.md)   
 [Solucionar problemas com scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)