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
ms.openlocfilehash: 6e1b24cb8406ff29659eb79d1d9fa856db628b89
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094088"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refatorar para converter LINQ em uma instrução foreach

Use essa refatoração para converter a [sintaxe da consulta LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) em uma instrução [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

Esta refatoração aplica-se a:

- C#

- Visual Basic

## <a name="how-to-use-it"></a>Como usar

1. Selecione toda a consulta LINQ começando com `from`.

   > [!NOTE]
   > Esta refatoração só pode ser usada para converter consultas LINQ expressas com a sintaxe de consulta e não a sintaxe do método.

1. Pressione **Ctrl**+**.** ou clique no ícone de chave de fenda ![ícone de chave de fenda](../media/screwdriver-icon.png) na margem do arquivo de código.

   ![Menu de ações rápidas para conversão de LINQ em foreach](media/convert-linq-to-foreach.png)

1. Selecione **Converter em 'foreach'**. Ou selecione **Visualizar alterações** para abrir a caixa de diálogo [Visualizar alterações](../../ide/preview-changes.md) e, em seguida, selecione **Aplicar**.

> [!NOTE]
> Para C#, o código gerado por essas refatorações usa um tipo de explícito ou [var](/dotnet/csharp/language-reference/keywords/var) para a variação de iteração do loop `foreach`. O tipo no código gerado, explícito ou implícito, depende das configurações de estilo de código em escopo. Essas configurações específicas de estilo de código são configuradas no nível da máquina em **Ferramentas** > **Opções** > **Editor de** > texto**C#** > **Estilo de** > código**Preferências gerais** > **\'var,** ou no nível de solução em um arquivo [EditorConfig.](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types) Se você alterar uma configuração de estilo do código em **Opções**, abra o arquivo de código para que as alterações entrem em vigor.

## <a name="see-also"></a>Confira também

- [Linq](/dotnet/standard/using-linq)
- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)
