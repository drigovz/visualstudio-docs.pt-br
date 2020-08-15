---
title: Simplificar expressão LINQ
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 04485d6ce67c822fd0620bd63f3557851db6dbb9
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88251279"
---
# <a name="simplify-linq-expression"></a>Simplificar expressão LINQ

Esta refatoração aplica-se a:

- C#

**O que:** Refactores instâncias de `SomeEnumerableType.Where(<LambdaExpression>).Single()` para `SomeEnumerable.Single(<LambdaExpression>)` , `Enumerable.Single()` bem como os seguintes métodos enumeráveis:,,,,, `SingleOrDefault()` `Last()` `LastOrDefault()` `Any()` `Count()` `First()` e `FirstOrDefault()` .

**Quando:**  Todas as instâncias em que o método chama `Single()` , `SingleOrDefault()` e assim por diante, não têm nenhum argumento e são precedidas por uma `Where()` expressão. A entrada para a `Where()` expressão não pode ser construída como uma árvore de expressão.

**Por que:** Remover a chamada desnecessária para o Enumerable para o `.Where()` método melhora o desempenho e a legibilidade.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor dentro da `SomeEnumerableType.Where(<LambdaExpression>).Single()` instância no Visual Studio.
2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.
3. Selecione **simplificar expressão LINQ**

   ![Converter typeof em nameof](media/simplify-linq-expression.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
