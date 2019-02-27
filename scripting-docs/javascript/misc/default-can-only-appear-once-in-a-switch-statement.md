---
title: "'default' só pode aparecer uma vez em uma instrução 'switch' | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a5d31a74900e8eee5daa97bb7f9af5146b237e04
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842176"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>'default' só pode aparecer em uma instrução 'switch'
Você tentou usar o **padrão** instrução mais de uma vez dentro de uma instrução switch. O caso padrão é sempre a última instrução case em uma instrução switch (ele é o caso fall-through).  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remova todos os extras **padrão** caso, as instruções do seu `switch` instrução (use na maioria dos instrução case de um padrão em sua instrução switch).  
  
## <a name="see-also"></a>Consulte também  
 [Instrução switch](../../javascript/reference/switch-statement-javascript.md)   
 [Controlando o fluxo de programa](../../javascript/controlling-program-flow-javascript.md)   
 [Palavras reservadas de JavaScript](../../javascript/reference/javascript-reserved-words.md)