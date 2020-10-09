---
title: Booliano esperado | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6d88815a33187e209bcba248d3c363afdd91227
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862659"
---
# <a name="boolean-expected"></a>Booliano esperado
Você tentou invocar o método **booliano. prototype. ToString** ou **booliano. prototype. valueOf** em um objeto de um tipo diferente de `Boolean` . O objeto deste tipo de invocação deve ser do tipo `Boolean` . Por exemplo:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Invocar apenas os métodos **Boolean. prototype. ToString** ou **Boolean. prototype. valueOf** em objetos do tipo **booliano.**

## <a name="see-also"></a>Confira também

- [Objeto Boolean](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
- [Data Types](https://developer.mozilla.org/docs/Web/JavaScript/Data_structures)
- [Controlar o fluxo de programas](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
- [Copiar, passar e comparar dados](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Functions)