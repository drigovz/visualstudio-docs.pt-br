---
title: Converter um loop foreach em LINQ
descritpion: Convert any foreach loop that uses an IEnumerable to a LINQ query or a LINQ call form (also known as a LINQ method).
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 12c03830ccd37e0970e3c74bc78cdd9c8a8732b7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094221"
---
# <a name="convert-a-foreach-loop-to-linq"></a>Converter um loop foreach em LINQ

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que é isso?** Permite converter facilmente o loop *foreach* que usa um IEnumerable para uma consulta LINQ ou um formulário de chamada LINQ (também conhecido como método LINQ).

**Quando:** Você tem um loop foreach que usa um IEnumerable, e você quer que esse loop seja lido como uma consulta LINQ.

**Por que:** Você prefere usar a sintaxe LINQ em vez de um loop foreach. O [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) faz uma consulta em um constructo de linguagem de primeira classe no C#. O LINQ pode reduzir a quantidade de código em um arquivo, facilitar a leitura e permitir que diferentes fontes de dados tenham padrões de expressão de consulta semelhantes.

> [!NOTE]
> A sintaxe LINQ é normalmente menos eficiente do que um loop foreach. É bom estar ciente de que pode ocorrer alguma compensação de desempenho ao usar o LINQ para melhorar a legibilidade do código.

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>Converter um loop foreach em refatoração de LINQ

1. Coloque o cursor na palavra-chave `foreach`.

    ![Exemplo de foreach com IEnumerable](media/convert-foreach-to-LINQ.png)

2. Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.

   ![Converter em um exemplo de menu LINQ](media/convert-foreach-to-LINQ-codefix.png)

3. Selecione **Converter em LINQ** ou **Converter em Linq (formulário de chamada)**.

   ![Exemplo de resultado da consulta LINQ](media/convert-foreach-to-LINQ-result.png)

   ![Exemplo de resultado do formulário de chamada LINQ](media/convert-foreach-to-LINQ-callform-result.png)

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

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Janela Visualização de Alterações](../../ide/preview-changes.md)
- [Dicas para desenvolvedores do .NET](../csharp-developer-productivity.md)
