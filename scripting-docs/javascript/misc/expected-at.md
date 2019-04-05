---
title: Esperado '@' | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da8eb2f21cbe7ef611aaba863e853a2fe7a71753
ms.sourcegitcommit: b6177ce198c7c5a00030604c9d4faa735405d5df
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/04/2019
ms.locfileid: "59018305"
---
# <a name="expected-"></a>Esperado '\@'
Você tentou criar uma variável a ser usada com instruções de compilação condicional usando o `@set` instrução, mas não colocou um sinal de arroba "**@**" antes do nome da variável.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Adicionar um sinal de arroba "**@**" imediatamente antes do nome da variável. Por exemplo:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [@set Instrução](../../javascript/reference/at-set-statement-javascript.md)   
 [Compilação condicional](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variáveis de compilação condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)
