---
title: O URI a ser decodificado contém um caractere inválido | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a3c71b90d0711bf317d0ed72d51c0d5d45297c80
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841864"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>O URI a ser decodificado contém um caractere inválido
Você tentou codificar uma cadeia de caracteres como um URI (Uniform Resource Identifier), mas ele continha caracteres inválidos. Embora a maioria dos caracteres são válidos dentro de cadeias de caracteres a ser convertido em URIs, algumas sequências de caracteres Unicode são ilegais.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Verifique se a cadeia de caracteres a ser decodificado contém somente sequências de Unicode válidas. Um URI completo é composto de uma sequência de componentes e separadores. Os nomes entre colchetes angulares representam os componentes e o ":", "/", ";" e "?" são caracteres reservados usados como separadores. O formato geral é:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Função encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Função encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)