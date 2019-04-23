---
title: VBArray esperado | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d1fabd8da6f825a266614a4a5c7fabd5c307130
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60064937"
---
# <a name="vbarray-expected"></a>VBArray esperado
Você forneceu um objeto que não era um safeArray de Visual Basic, quando apenas um era esperado.  
  
```js
new VBArray(safeArray);  
```  
  
 VBArrays são somente leitura e não pode ser criados diretamente. O argumento de safeArray é um valor de VBArray e deve ter obtido um valor de VBArray antes de ser passado para o `VBArray` construtor. Isso pode ser feito apenas recuperando o valor de um controle ActiveX existente ou em outro objeto.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Verifique se você passar somente **VBArray** objetos para o **VBArray** construtor.  
  
## <a name="see-also"></a>Consulte também  
 [Objeto VBArray](../../javascript/reference/vbarray-object-javascript.md)   
 [Usando matrizes](../../javascript/advanced/using-arrays-javascript.md)