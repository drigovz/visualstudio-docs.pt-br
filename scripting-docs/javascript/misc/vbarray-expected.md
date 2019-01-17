---
title: VBArray esperado | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5013
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4b5416c6e37e59a60206bd21606b5214f05a269
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347447"
---
# <a name="vbarray-expected"></a>VBArray esperado
Você forneceu um objeto que não era um safeArray de Visual Basic, quando apenas um era esperado.  
  
```js
new VBArray(safeArray);  
```  
  
 VBArrays são somente leitura e não pode ser criados diretamente. O argumento de safeArray é um valor de VBArray e deve ter obtido um valor de VBArray antes de ser passado para o `VBArray` construtor. Isso pode ser feito apenas recuperando o valor de um controle ActiveX existente ou em outro objeto.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Verifique se você passar somente **VBArray** objetos para o **VBArray** construtor.  
  
## <a name="see-also"></a>Consulte também  
 [Objeto VBArray](../../javascript/reference/vbarray-object-javascript.md)   
 [Usando matrizes](../../javascript/advanced/using-arrays-javascript.md)