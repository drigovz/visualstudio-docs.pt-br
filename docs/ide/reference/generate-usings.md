---
title: Gerar usos
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
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: 903b160bac0e8096062e09fd78ff4c92c46cf8ee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094317"
---
# <a name="add-missing-usings-in-visual-studio"></a>Adicionar usos ausentes no Visual Studio

Esta geração de código aplica-se a:

- C#

- Visual Basic

**O que é isso?** Permite adicionar imediatamente as importações necessárias ou [usar diretivas](/dotnet/csharp/language-reference/keywords/using-directive) para código de cópia e cola.

**Quando:** É prática comum copiar códigos de diferentes lugares do seu projeto ou outras fontes e colá-lo em novo código. Esta Ação Rápida encontra diretivas de importação ausentes para código de cópia e colado e, em seguida, solicita que você as adicione. Esta correção de código também pode adicionar referências de projeto para projeto.

**Por que:** Como o Quick Action adiciona automaticamente as importações necessárias, `using` você não precisa copiar manualmente as diretivas que seu código precisa.

## <a name="add-missing-usings-refactoring"></a>Adicionar a refatoração de usos ausentes

1. Copie o código de um arquivo e cole-o `using` em um novo sem incluir as diretivas necessárias. O erro resultante é acompanhado por uma correção de código que adiciona as diretivas faltantes. `using`

    > [!NOTE]
    > É necessário ativar essa sugestão em **Ferramentas > Opções > Editor de Texto > C# > Avançado > Diretivas Using**.

2. Selecione Ctrl+. para abrir o menu **Ações Rápidas e Refatorações**.

    ![Gerar usos](media/generate-using-codefix.png)

3. Selecione **using \<sua referência\>;** para adicionar a referência ausente.

    ![Gerar o resultado de instruções using](media/generate-using-result.png)

## <a name="see-also"></a>Confira também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)
- [Dicas para desenvolvedores .NET](../csharp-developer-productivity.md)
