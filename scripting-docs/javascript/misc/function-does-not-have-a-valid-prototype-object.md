---
title: Função não tem um objeto de protótipo válido | Microsoft Docs
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
ms.openlocfilehash: 413f73a53a6d4f698219139a87c449be4c155831
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007497"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>A função não tem um objeto de protótipo válido
Você tentou usar **instanceof** para determinar se um objeto foi derivado de uma classe de função específica, mas você redefiniu o objeto `prototype` propriedade como `null`, ou um tipo de objeto externo (os dois não é válido [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objetos). Um objeto externo pode ser um objeto do modelo de objeto host (por exemplo, o objeto de janela ou documento do Internet Explorer) ou um objeto COM externo.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Verifique se a função `prototype` propriedade se refere ao válido [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objeto.  
  
## <a name="see-also"></a>Consulte também  
 [Objeto de função](../../javascript/reference/function-object-javascript.md)   
 [Propriedade prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)