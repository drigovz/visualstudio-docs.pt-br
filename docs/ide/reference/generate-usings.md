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
ms.openlocfilehash: f3b3435e10d6bb9a71fd16b9286759b136c167f4
ms.sourcegitcommit: ea5e02720d71185f8e27fbea205024371b0c7ceb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77544549"
---
# <a name="add-missing-usings-in-visual-studio"></a>Adicionar usos ausentes no Visual Studio

Esta geração de código aplica-se a:

- C#

**O que:** Permite adicionar imediatamente as importações necessárias ou o [uso de diretivas](/dotnet/csharp/language-reference/keywords/using-directive) para o código de cópia e colagem.

**Quando:** É uma prática comum copiar o código de locais diferentes em seu projeto ou outras fontes e colá-lo no novo código. Essa ação rápida localiza diretivas de importações ausentes para código de cópia e colagem e, em seguida, solicita que você as adicione. Essa correção de código também pode adicionar referências do projeto ao projeto.

**Por que:** Como a ação rápida adiciona automaticamente as importações necessárias, você não precisa copiar manualmente as diretivas de `using` que seu código precisa.

## <a name="add-missing-usings-refactoring"></a>Adicionar a refatoração de usos ausentes

1. Copie o código de um arquivo e cole-o em um novo sem incluir as diretivas de `using` necessárias. O erro resultante é acompanhado por uma correção de código que adiciona as diretivas de `using` ausentes.

    > [!NOTE]
    > É necessário ativar essa sugestão em **Ferramentas > Opções > Editor de Texto > C# > Avançado > Diretivas Using**.

2. Selecione Ctrl+. para abrir o menu **Ações Rápidas e Refatorações**.

    ![Gerar instruções using](media/generate-using-codefix.png)

3. Selecione **using \<sua referência\>;** para adicionar a referência ausente.

    ![Gerar o resultado de instruções using](media/generate-using-result.png)

## <a name="see-also"></a>Confira também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)
- [Dicas para desenvolvedores do .NET](../csharp-developer-productivity.md)
