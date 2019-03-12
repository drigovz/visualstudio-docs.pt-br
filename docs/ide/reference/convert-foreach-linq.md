---
title: Converter o loop foreach em LINQ
ms.date: 02/20/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: dc0f94d6aa9f13ac038f1af19a1ab1c78158ea14
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324951"
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

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)
- [Dicas para desenvolvedores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)