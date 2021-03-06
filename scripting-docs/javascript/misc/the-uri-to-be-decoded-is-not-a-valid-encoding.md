---
title: O URI a ser decodificado não é uma codificação válida | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5025
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38ea642cece501804b6ee2efaac778c3b8d520fc
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861862"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>O URI a ser decodificado não tem uma codificação válida
Você tentou decodificar um URI formado incorretamente (Uniform Resource Identifier). Os URIs têm uma sintaxe especial; a maioria dos caracteres não alfanuméricos deve ser codificada antes que possam ser usados em um URI. Você pode usar os `encodeURI` `encodeURIComponent` métodos e para criar um URI a partir de uma [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] cadeia de caracteres normal.  
  
 Um URI completo é composto de uma sequência de componentes e separadores. A forma geral é:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Os nomes entre colchetes angulares representam componentes e ":", "/", ";" e "?" são caracteres reservados usados como separadores.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Verifique se você está tentando decodificar apenas URIs válidos. Não é possível decodificar [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] cadeias de caracteres normais, pois elas podem conter caractere inválido.  
  
## <a name="see-also"></a>Confira também  
 [Função decodeURI](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/decodeuri)   
 [Função DecodeURIComponent](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/decodeuricomponent)