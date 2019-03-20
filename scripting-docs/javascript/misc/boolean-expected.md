---
title: Booliano esperado | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 261cf0ad93208c0eac09e42dcd68853352318e88
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149150"
---
# <a name="boolean-expected"></a>Booliano esperado
Você tentou invocar o **Boolean.prototype.toString** ou **Boolean.prototype.valueOf** método em um objeto de um tipo diferente de `Boolean`. O objeto desse tipo de invocação deve ser do tipo `Boolean`. Por exemplo:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Invoque apenas o **Boolean.prototype.toString** ou **Boolean.prototype.valueOf** métodos em objetos do tipo **booliano.**

## <a name="see-also"></a>Consulte também

- [Objeto Boolean](../../javascript/reference/boolean-object-javascript.md)
- [Tipos de Dados](../../javascript/data-types-javascript.md)
- [Controlar o fluxo de programas](../../javascript/controlling-program-flow-javascript.md)
- [Copiar, passar e comparar dados](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)