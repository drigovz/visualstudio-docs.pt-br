---
title: O URI a ser decodificado não tem uma codificação válida | Microsoft Docs
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
ms.openlocfilehash: 792403a9a53f11431e87115d7a95345e316dc2ac
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56844289"
---
# <a name="the-uri-to-be-decoded-is-not-a-valid-encoding"></a>O URI a ser decodificado não tem uma codificação válida
Tentativa de decodificar um formada incorretamente URI (Uniform Resource Identifier). URIs têm uma sintaxe especial; a maioria dos caracteres não alfanuméricos devem ser codificados antes que possam ser usados em um URI. Você pode usar o `encodeURI` e `encodeURIComponent` métodos para criar um URI de um normal [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] cadeia de caracteres.  
  
 Um URI completo é composto de uma sequência de componentes e separadores. O formato geral é:  
  
```JavaScript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Os nomes entre colchetes angulares representam os componentes e o ":", "/", ";" e "?" são caracteres reservados usados como separadores.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Certifique-se de que você está tentando decodificar apenas URIs válidos. Você não consegue decodificar normal [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] cadeias de caracteres, como eles podem conter caracteres inválidos.  
  
## <a name="see-also"></a>Consulte também  
 [Função decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [Função DecodeURIComponent](../../javascript/reference/decodeuricomponent-function-javascript.md)