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
ms.openlocfilehash: 467a6ec6ca45f2ea0411e0266163ca23a9e3d594
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572513"
---
# <a name="vbarray-expected"></a>VBArray esperado
Você forneceu um objeto que não era um Visual Basic safeArray, quando um era esperado.  
  
```js
new VBArray(safeArray);  
```  
  
 VBArrays são somente leitura e não podem ser criados diretamente. O argumento safeArray é um valor VBArray e deve ter obtido um valor VBArray antes de ser passado para o Construtor `VBArray`. Isso só pode ser feito recuperando o valor de um ActiveX existente ou outro objeto.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Certifique-se de que você passe somente objetos **VBArray** para o construtor **VBArray** .  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [objeto VBArray](../../javascript/reference/vbarray-object-javascript.md)  
 [Usando matrizes](../../javascript/advanced/using-arrays-javascript.md)