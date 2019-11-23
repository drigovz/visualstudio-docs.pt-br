---
title: O URI a ser decodificado não é uma codificação válida | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 99df8739137971e32c14f265460ff3f4a9c03816
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572260"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>O URI a ser decodificado não tem uma codificação válida
Você tentou decodificar um URI formado incorretamente (Uniform Resource Identifier). Os URIs têm uma sintaxe especial; a maioria dos caracteres não alfanuméricos deve ser codificada antes que possam ser usados em um URI. Você pode usar os métodos `encodeURI` e `encodeURIComponent` para criar um URI a partir de uma cadeia de caracteres de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] normal.  
  
 Um URI completo é composto de uma sequência de componentes e separadores. A forma geral é:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Os nomes entre colchetes angulares representam componentes e ":", "/", ";" e "?" são caracteres reservados usados como separadores.  
  
### <a name="to-correct-this-error"></a>Para corrigir esse erro  
  
- Verifique se você está tentando decodificar apenas URIs válidos. Você não pode decodificar cadeias de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] normais, pois elas podem conter caracteres inválidos.  
  
## <a name="see-also"></a>Consulte também  
 [função decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Função DecodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)