---
title: O tamanho da matriz deve ser um número inteiro finito e positivo | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 691f7aff61a8a2bfae6444540afe9a28a200278d
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840426"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>O tamanho da matriz deve ser um número inteiro finito e positivo
Você está chamando o **matriz** construtor com um argumento que não é um número inteiro (números inteiros consistem em zero e o conjunto de números inteiros positivos).  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Use números inteiros positivos apenas ao criar um novo `Array` objeto. Se você quiser criar uma matriz com um único elemento que não é um inteiro, você deve fazê-lo em um processo em duas etapas. Primeiro criar uma matriz com um elemento e, em seguida, coloque o valor no primeiro elemento (array[0]). O exemplo a seguir é um exemplo que gera esse erro.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     O exemplo a seguir demonstra a maneira correta de especificar uma matriz com um único elemento numérico.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Não há nenhum limite superior para o tamanho de uma matriz, que não seja o máximo valor inteiro (aproximadamente 4 bilhões).  
  
## <a name="see-also"></a>Consulte também  
 [Usando matrizes](../../javascript/advanced/using-arrays-javascript.md)