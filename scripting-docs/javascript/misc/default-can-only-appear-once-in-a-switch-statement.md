---
title: "'default' só pode aparecer uma vez em uma instrução 'switch' | Microsoft Docs"
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
- VS.WebClient.Help.SCRIPT1027
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a94100f4-6ee5-4759-b635-9d309e47111e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4f254825e27793999932b772ac4bc2512908fae
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347301"
---
# <a name="default-can-only-appear-once-in-a-switch-statement"></a>'default' só pode aparecer em uma instrução 'switch'
Você tentou usar o **padrão** instrução mais de uma vez dentro de uma instrução switch. O caso padrão é sempre a última instrução case em uma instrução switch (ele é o caso fall-through).  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remova todos os extras **padrão** caso, as instruções do seu `switch` instrução (use na maioria dos instrução case de um padrão em sua instrução switch).  
  
## <a name="see-also"></a>Consulte também  
 [Instrução switch](../../javascript/reference/switch-statement-javascript.md)   
 [Controlando o fluxo de programa](../../javascript/controlling-program-flow-javascript.md)   
 [Palavras reservadas de JavaScript](../../javascript/reference/javascript-reserved-words.md)