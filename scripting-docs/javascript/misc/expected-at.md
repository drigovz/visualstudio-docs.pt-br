---
title: Esperado ' @' | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 73e7e8fb43bb45e4c97b6bb5ec6c739c16a4423a
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349849"
---
# <a name="expected-"></a>'@' esperado
Você tentou criar uma variável a ser usada com instruções de compilação condicional usando o `@set` instrução, mas não colocou um sinal de arroba "**@**" antes do nome da variável.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Adicionar um sinal de arroba "**@**" imediatamente antes do nome da variável. Por exemplo:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [@set Statement](../../javascript/reference/at-set-statement-javascript.md)   
 [Compilação condicional](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variáveis de compilação condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)