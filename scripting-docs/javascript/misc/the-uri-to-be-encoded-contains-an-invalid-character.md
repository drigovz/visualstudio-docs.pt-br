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
ms.openlocfilehash: f2f9111acf656bf882a3d506fe95b8361f3693ff
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053387"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>O URI a ser decodificado contém um caractere inválido
Você tentou codificar uma cadeia de caracteres como um URI (Uniform Resource Identifier), mas ele continha caracteres inválidos. Embora a maioria dos caracteres são válidos dentro de cadeias de caracteres a ser convertido em URIs, algumas sequências de caracteres Unicode são ilegais.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Verifique se a cadeia de caracteres a ser decodificado contém somente sequências de Unicode válidas. Um URI completo é composto de uma sequência de componentes e separadores. Os nomes entre colchetes angulares representam os componentes e o ":", "/", ";" e "?" são caracteres reservados usados como separadores. O formato geral é:  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Função encodeURI](../../javascript/reference/encodeuri-function-javascript.md)   
 [Função encodeURIComponent](../../javascript/reference/encodeuricomponent-function-javascript.md)