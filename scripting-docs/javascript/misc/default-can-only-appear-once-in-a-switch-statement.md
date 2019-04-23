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
ms.openlocfilehash: 24162efcc720d9c0073f8a5799c6278b8d3c8c62
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60107821"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>'default' só pode aparecer em uma instrução 'switch'
Você tentou usar o **padrão** instrução mais de uma vez dentro de uma instrução switch. O caso padrão é sempre a última instrução case em uma instrução switch (ele é o caso fall-through).  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Remova todos os extras **padrão** caso, as instruções do seu `switch` instrução (use na maioria dos instrução case de um padrão em sua instrução switch).  
  
## <a name="see-also"></a>Consulte também  
 [Instrução switch](../../javascript/reference/switch-statement-javascript.md)   
 [Controlando o fluxo de programa](../../javascript/controlling-program-flow-javascript.md)   
 [Palavras reservadas de JavaScript](../../javascript/reference/javascript-reserved-words.md)