---
title: A função não tem um objeto de protótipo válido | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb3cffa4bffd616560aa95ace4ad82a4368ebbd5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574596"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>A função não tem um objeto de protótipo válido
Você tentou usar o **instanceof** para determinar se um objeto foi derivado de uma classe de função específica, mas você redefiniu a propriedade de `prototype` do objeto como `null` ou um tipo de objeto externo (ambos os objetos [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] não válidos). Um objeto externo pode ser um objeto do modelo de objeto de host (por exemplo, o documento ou o objeto de janela do Internet Explorer) ou um objeto COM externo.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Certifique-se de que a propriedade `prototype` da função se refere a um objeto [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] válido.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [objeto de função](../../javascript/reference/function-object-javascript.md)  
 [Propriedade prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)