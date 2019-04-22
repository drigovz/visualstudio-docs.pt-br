---
title: Converter o loop foreach em LINQ
ms.date: 02/20/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 18c5b01aed925bf458e1c8779a2f41ea1a2d98a4
ms.sourcegitcommit: 7eb85d296146186e7a39a17f628866817858ffb0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59504062"
---
# <a name="convert-foreach-loop-to-linq"></a>Converter o loop foreach em LINQ

Esta refatoração aplica-se a:

- C#

**O quê:** Permite converter com facilidade os loops foreach usando IEnumerables em uma consulta LINQ ou em um formulário de chamada LINQ (também conhecido como método LINQ).

**Quando:** Quando você tem um loop foreach que usa um IEnumerable que prefere ler como uma consulta LINQ.

**Por que:** Às vezes, os usuários podem preferir usar a sintaxe LINQ em vez de um loop foreach. O [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) faz uma consulta de um constructo de linguagem de primeira classe no C#. O LINQ pode reduzir a quantidade de código em um arquivo, facilitar sua leitura e permitir que diferentes fontes de dados tenham padrões de expressão de consulta semelhantes.

> [!NOTE]
> A sintaxe LINQ é normalmente menos eficaz do que os loops foreach. É recomendável estar ciente de qualquer compensação de desempenho que possa ser causada ao melhorar a legibilidade do código com o LINQ.

## <a name="convert-foreach-loop-to-linq-refactoring"></a>Refatoração de converter o loop foreach em LINQ

1. Coloque o cursor na palavra-chave `foreach`.

    ![Foreach com IEnumerable](media/convert-foreach-to-LINQ.png)

2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.

   ![Converter em um menu LINQ](media/convert-foreach-to-LINQ-codefix.png)

3. Selecione **Converter em LINQ** ou **Converter em LINQ (formulário de chamada)**

   ![Resultado da consulta LINQ](media/convert-foreach-to-LINQ-result.png)
   
   ![Resultado do formulário de chamada LINQ](media/convert-foreach-to-LINQ-callform-result.png)
   
### <a name="sample-code"></a>Código de exemplo

```csharp
using System.Collections.Generic;

public class Class1
{
    public void MyMethod()
    {
        var greetings = new List<string>()
            { "hi", "yo", "hello", "howdy" };

        IEnumerable<string> enumerable()
        {
            foreach (var greet in greetings)
            {
                if (greet.Length < 3)
                {
                    yield return greet;
                }
            }

            yield break;
        }
    }
}
```

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)
- [Dicas para desenvolvedores do .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
