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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946349"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>'default' só pode aparecer em uma instrução 'switch'
Você tentou usar o **padrão** instrução mais de uma vez dentro de uma instrução switch. O caso padrão é sempre a última instrução case em uma instrução switch (ele é o caso fall-through).  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Remova todos os extras **padrão** caso, as instruções do seu `switch` instrução (use na maioria dos instrução case de um padrão em sua instrução switch).  
  
## <a name="see-also"></a>Consulte também  
 [Instrução switch](../../javascript/reference/switch-statement-javascript.md)   
 [Controlando o fluxo de programa](../../javascript/controlling-program-flow-javascript.md)   
 [Palavras reservadas de JavaScript](../../javascript/reference/javascript-reserved-words.md)