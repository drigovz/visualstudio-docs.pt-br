---
title: Refatorar código para converter uma consulta LINQ em uma instrução foreach
ms.date: 05/15/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e8d19f86578e2aebda4e6c497d0c2d89c4826d8f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960146"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refatorar para converter LINQ em uma instrução foreach

Use essa refatoração para converter a [sintaxe da consulta LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) em uma instrução [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

Esta refatoração aplica-se a:

- C#

## <a name="how-to-use-it"></a>Como usá-lo

1. Selecione toda a consulta LINQ começando com `from`.

   > [!NOTE]
   > Esta refatoração só pode ser usada para converter consultas LINQ expressas com a sintaxe de consulta e não a sintaxe do método.

1. Pressione **Ctrl**+**.** ou clique no ícone de chave de fenda ![ícone de chave de fenda](../media/screwdriver-icon.png) na margem do arquivo de código.

   ![Menu de ações rápidas para conversão de LINQ em foreach](media/convert-linq-to-foreach.png)

1. Selecione **Converter em 'foreach'**. Ou selecione **Visualizar alterações** para abrir a caixa de diálogo [Visualizar alterações](../../ide/preview-changes.md) e, em seguida, selecione **Aplicar**.

> [!NOTE]
> Para C#, o código gerado por essas refatorações usa um tipo de explícito ou [var](/dotnet/csharp/language-reference/keywords/var) para a variação de iteração do loop `foreach`. O tipo no código gerado, explícito ou implícito, depende das configurações de estilo de código em escopo. Essas configurações de estilo de código específicas são configuradas no nível do computador em **Ferramentas** > **Opções** > **Editor de Texto** > **C#** > **Estilo de Código** > **Geral** > **\'preferências de var**, ou no nível da solução em um arquivo [EditorConfig](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types). Se você alterar uma configuração de estilo do código em **Opções**, abra o arquivo de código para que as alterações entrem em vigor.

## <a name="see-also"></a>Consulte também

- [LINQ](/dotnet/standard/using-linq)
- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)