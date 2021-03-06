---
title: Refatorar para converter um loop for em uma instrução foreach
description: Saiba como usar o menu ações rápidas e refatoração para converter entre loop for e uma instrução foreach.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 6a435824d3186cee7a32db9966cfde3db9b093bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919703"
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Refatoração para converter entre um loop for e uma instrução foreach

Este artigo descreve as refatorações de Ações Rápidas que convertem entre duas estruturas de loop. Ele inclui alguns motivos para você alternar entre um loop [for](/dotnet/csharp/language-reference/keywords/for) e uma instrução [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) em seu código.

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Converter um loop for em uma instrução foreach

Se você tiver um loop [for](/dotnet/csharp/language-reference/keywords/for) em seu código, será possível usar essa refatoração para convertê-lo em uma instrução [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

Esta refatoração aplica-se a:

- C#

- Visual Basic

> [!NOTE]
> A refatoração da Ação Rápida **Converter em foreach** só está disponível para loops [for](/dotnet/csharp/language-reference/keywords/for) que contêm todas as três partes: um inicializador, uma condição e um iterador.

### <a name="why-convert"></a>Por que converter

Os motivos pelos quais talvez você deseje converter um loop [for](/dotnet/csharp/language-reference/keywords/for) em uma instrução [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) incluem:

- Não use a variável loop local dentro do loop, exceto com um índice para acessar o item.

- Você deseja simplificar seu código e reduza a probabilidade de erros lógicos nas seções do inicializador, de condição e de iteração.

### <a name="how-to-use-it"></a>Como usá-lo

1. Coloque o cursor na palavra-chave `for`.

1. Pressione **Ctrl** + **.** ou clique no ícone de chave de fenda ![ícone de chave de fenda](../media/screwdriver-icon.png) na margem do arquivo de código.

   ![Converter em menu foreach](media/convert-to-foreach.png)

1. Selecione **Converter em 'foreach'**. Ou selecione **Visualizar alterações** para abrir a caixa de diálogo [Visualizar alterações](../../ide/preview-changes.md) e, em seguida, selecione **Aplicar**.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Converter uma instrução foreach em um loop for

Se você tiver uma instrução [foreach (C#)](/dotnet/csharp/language-reference/keywords/foreach-in) ou a instrução [Por Each...Next (Visual Basic)](/dotnet/csharp/language-reference/keywords/for) em seu código, use essa refatoração para convertê-la em um loop [for](/dotnet/visual-basic/language-reference/statements/for-each-next-statement).

Esta refatoração aplica-se a:

- C#

- Visual Basic

### <a name="why-convert"></a>Por que converter

Os motivos pelos quais talvez você deseje converter uma instrução [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) em um loop [for](/dotnet/csharp/language-reference/keywords/for) incluem:

- Você deseja usar a variável de loop local dentro do loop para outras funções além de apenas acessar o item.

- Você está [iterando por meio de uma matriz multidimensional](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) e deseja ter mais controle sobre os elementos da matriz.

### <a name="how-to-use-it"></a>Como usá-lo

1. Coloque o cursor na palavra-chave `foreach` ou `For Each`.

1. Pressione **Ctrl** + **.** ou clique no ícone de chave de fenda ![ícone de chave de fenda](../media/screwdriver-icon.png) na margem do arquivo de código.

   ![Converter em menu for](media/convert-to-for.png)

1. Selecione **Converter em 'for'**. Ou selecione **Visualizar alterações** para abrir a caixa de diálogo [Visualizar alterações](../../ide/preview-changes.md) e, em seguida, selecione **Aplicar**.

1. Como a refatoração introduz uma nova variável de contagem de iterações, a caixa **Renomear** é exibida no canto superior direito do editor. Se desejar escolher um nome diferente para a variável, digite-o e, em seguida, pressione **Enter** ou selecione **Aplicar** na caixa **Renomear**. Se você não deseja escolher um novo nome, pressione **Esc** ou selecione **Aplicar** para ignorar a caixa **Renomear**.

> [!NOTE]
> Para C#, o código gerado por essas refatorações usa um tipo de explícito ou [var](/dotnet/csharp/language-reference/keywords/var) para o tipo dos itens na coleção. O tipo no código gerado, explícito ou implícito, depende das configurações de estilo de código em escopo. Essas configurações de estilo de código em particular são configuradas no nível do computador, em **ferramentas**  >  **Opções**  >  **Editor de texto**  >  **C#**  >    >    >  **\' var ' Preferências** gerais, ou no nível da solução em um arquivo [EditorConfig](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types) . Se você alterar uma configuração de estilo do código em **Opções**, abra o arquivo de código para que as alterações entrem em vigor.

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)
