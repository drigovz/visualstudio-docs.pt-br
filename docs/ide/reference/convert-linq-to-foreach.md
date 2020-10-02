---
title: Refatorar código para converter uma consulta LINQ em uma instrução foreach
description: Converta qualquer consulta LINQ escrita em sintaxe de consulta em uma instrução foreach.
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
ms.openlocfilehash: 7abdebf36ab075dfd289069671cf3b6851a72b75
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659362"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refatorar para converter LINQ em uma instrução foreach

Use essa refatoração para converter a [sintaxe da consulta LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) em uma instrução [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

Esta refatoração aplica-se a:

- C#

- Visual Basic

## <a name="how-to-use-it"></a>Como usá-lo

1. Selecione toda a consulta LINQ começando com `from`.

   > [!NOTE]
   > Esta refatoração só pode ser usada para converter consultas LINQ expressas com a sintaxe de consulta e não a sintaxe do método.

1. Pressione **Ctrl** + **.** ou clique no ícone de chave de fenda ![ícone de chave de fenda](../media/screwdriver-icon.png) na margem do arquivo de código.

   ![Menu de ações rápidas para conversão de LINQ em foreach](media/convert-linq-to-foreach.png)

1. Selecione **Converter em 'foreach'**. Ou selecione **Visualizar alterações** para abrir a caixa de diálogo [Visualizar alterações](../../ide/preview-changes.md) e, em seguida, selecione **Aplicar**.

> [!NOTE]
> Para C#, o código gerado por essas refatorações usa um tipo de explícito ou [var](/dotnet/csharp/language-reference/keywords/var) para a variação de iteração do loop `foreach`. O tipo no código gerado, explícito ou implícito, depende das configurações de estilo de código em escopo. Essas configurações de estilo de código em particular são configuradas no nível do computador, em **ferramentas**  >  **Opções**  >  **Editor de texto**  >  **C#**  >  **Code Style**  >  **General**  >  ** \' var ' Preferências**gerais, ou no nível da solução em um arquivo [EditorConfig](/dotnet/fundamentals/code-analysis/style-rules/language-rules#implicit-and-explicit-types) . Se você alterar uma configuração de estilo do código em **Opções**, abra o arquivo de código para que as alterações entrem em vigor.

## <a name="see-also"></a>Consulte também

- [LINQ](/dotnet/standard/using-linq)
- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)
