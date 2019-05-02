---
title: Dígito hexadecimal esperado | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82f020b5f3b82ab2ce3545102be83a5cd41c6069
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446517"
---
# <a name="expected-hexadecimal-digit"></a>Dígito hexadecimal esperado
Você criou uma sequência de escape Unicode incorreta. Sequências de escape Unicode começam com \u, seguido por exatamente quatro dígitos hexadecimais (nem mais, nem menos). Dígitos hexadecimais de Unicode podem conter apenas os números de 0 a 9, as letras maiusculas A-F e a letras minúsculas letras a-f. O exemplo a seguir demonstra uma sequência de escape Unicode está formada corretamente.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Certifique-se de que seu dígitos hexadecimais de Unicode começam com \u, contém apenas os números de 0 a 9, as letras maiusculas A-F, a minúscula letras a-f; e são agrupados em quatro dígitos.  
  
    > [!NOTE]
    > Se você quiser usar o \u texto literal em uma cadeia de caracteres e, em seguida, use duas barras invertidas - (\\\u)-um para a primeira barra invertida de escape.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Dados](../../javascript/data-types-javascript.md)