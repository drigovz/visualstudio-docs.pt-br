---
title: Gerar instruções using
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: d971bcdaca4efdf587c7e441f1b0b28d21388dee
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416470"
---
# <a name="add-missing-usings-in-visual-studio"></a>Adicionar usos ausentes no Visual Studio

Esta geração de código aplica-se a:

- C#

**O quê:** Permite adicionar imediatamente as importações necessárias ou as [instruções using](/dotnet/csharp/language-reference/keywords/using-statement) para um código copiado e colado.

**Quando:** É uma prática comum copiar o código de locais diferentes no projeto ou de outras fontes e colá-lo no novo código. Essa Ação rápida encontra as instruções de importações ausentes para o código copiado e colado e, em seguida, solicita a adição delas.

**Por que:** como a Ação rápida adiciona automaticamente as importações necessárias, você não precisa copiar manualmente as instruções `using` que seu código precisa.

## <a name="add-missing-usings-refactoring"></a>Adicionar a refatoração de usos ausentes

1. Copie o código de um arquivo diferente e cole-o em um novo código sem incluir as instruções `using` necessárias. O erro resultante é acompanhado por uma correção de código que adiciona as instruções `using` ausentes.

    > [!NOTE]
    > É necessário ativar essa sugestão em **Ferramentas > Opções > Editor de Texto > C# > Avançado > Diretivas Using**.

2. Selecione Ctrl+. para abrir o menu **Ações Rápidas e Refatorações**.

    ![Gerar instruções using](media/generate-using-codefix.png)

3. Selecione **using \<sua referência\>;** para adicionar a referência ausente.

    ![Gerar o resultado de instruções using](media/generate-using-result.png)

## <a name="see-also"></a>Consulte também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)
- [Dicas para desenvolvedores do .NET](../csharp-developer-productivity.md)
