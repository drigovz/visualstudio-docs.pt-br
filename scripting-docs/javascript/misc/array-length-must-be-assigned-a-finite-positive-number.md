---
title: O tamanho da matriz deve ser atribuído um número finito e positivo | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c6e536047aaebb9bd3a06e38574330937817748
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840786"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>O tamanho da matriz deve receber um número finito e positivo
Ao definir a **comprimento** propriedade de existente **matriz** objeto, que você especificou um tamanho da matriz que não era um número positivo ou zero. Esse erro ocorre quando você atribui um valor para o **comprimento** propriedade de um `Array` objeto que é negativo ou não é um número (`NaN`). Observe que [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] automaticamente converte números fracionários em inteiros.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Atribua um número inteiro positivo para a propriedade de comprimento. Não há nenhum limite superior para o tamanho de uma matriz, que não seja o máximo valor inteiro (aproximadamente 4 bilhões). O exemplo a seguir demonstra a maneira correta para definir a **comprimento** propriedade de um **matriz** objeto.  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Usando matrizes](../../javascript/advanced/using-arrays-javascript.md)