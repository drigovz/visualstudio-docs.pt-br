---
title: Refatorar código para converter uma consulta LINQ em uma instrução foreach
description: Converta qualquer consulta LINQ escrita em sintaxe de consulta em uma instrução foreach.
ms.date: 05/15/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: bb2cdf96d7f7829ff6a6d1394160548da2adae7f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595742"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refatorar para converter LINQ em uma instrução foreach

Use essa refatoração para converter a [sintaxe da consulta LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) em uma instrução [foreach](/dotnet/csharp/language-reference/keywords/foreach-in).

Esta refatoração aplica-se a:

- C#

## <a name="how-to-use-it"></a>Como usá-lo

1. Selecione toda a consulta LINQ começando com `from`.

   > [!NOTE]
   > Esta refatoração só pode ser usada para converter consultas LINQ expressas com a sintaxe de consulta e não a sintaxe do método.

1. Pressione **Ctrl**+ **.** ou clique no ícone de chave de fenda ![ícone de chave de fenda](../media/screwdriver-icon.png) na margem do arquivo de código.

   ![Menu de ações rápidas para conversão de LINQ em foreach](media/convert-linq-to-foreach.png)

1. Selecione **Converter em 'foreach'** . Ou selecione **Visualizar alterações** para abrir a caixa de diálogo [Visualizar alterações](../../ide/preview-changes.md) e, em seguida, selecione **Aplicar**.

> [!NOTE]
> Para C#, o código gerado por essas refatorações usa um tipo de explícito ou [var](/dotnet/csharp/language-reference/keywords/var) para a variação de iteração do loop `foreach`. O tipo no código gerado, explícito ou implícito, depende das configurações de estilo de código em escopo. Essas configurações de estilo de código específicas são configuradas no nível do computador em **Ferramentas** > **Opções** > **Editor de Texto** > **C#**  > **Estilo de Código** > **Geral** >  **\'preferências de var**, ou no nível da solução em um arquivo [EditorConfig](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types). Se você alterar uma configuração de estilo do código em **Opções**, abra o arquivo de código para que as alterações entrem em vigor.

## <a name="see-also"></a>Veja também

- [LINQ](/dotnet/standard/using-linq)
- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)
