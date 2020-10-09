---
title: Esperado ') ' na expressão regular (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29b25b5ab48ffe0a9a9dfafa9e60d66913c5e25e
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861885"
---
# <a name="expected--in-regular-expression-javascript"></a>')' esperado na expressão regular (JavaScript)
Você tentou criar uma captura de expressão regular, asserção ou grupo, mas não incluiu o parêntese de fechamento. Os parênteses têm várias finalidades em expressões regulares. Principalmente, eles são usados para capturar subexpressãos, para especificar asserções ou agrupar padrões para que os itens possam ser tratados como uma única unidade por *, +,? e assim por diante.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Adicione os parênteses de fechamento mais à direita.  
  
    > [!NOTE]
    > Se você quiser corresponder a um único parêntese, escape-o com uma barra invertida \\ (-para que ele não seja interpretado como um caractere especial [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Confira também  
 [Objeto de expressão regular](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Sintaxe de expressão regular (JavaScript)](/previous-versions/1400241x(v=vs.100))