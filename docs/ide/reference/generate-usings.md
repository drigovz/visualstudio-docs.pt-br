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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094317"
---
# <a name="add-missing-usings-in-visual-studio"></a>Adicionar usos ausentes no Visual Studio

Esta geração de código aplica-se a:

- C#

- Visual Basic

**O que:** Permite adicionar imediatamente as importações necessárias ou o [uso de diretivas](/dotnet/csharp/language-reference/keywords/using-directive) para o código de cópia e colagem.

**Quando:** É uma prática comum copiar o código de locais diferentes em seu projeto ou outras fontes e colá-lo no novo código. Essa ação rápida localiza diretivas de importações ausentes para código de cópia e colagem e, em seguida, solicita que você as adicione. Essa correção de código também pode adicionar referências do projeto ao projeto.

**Por que:** Como a ação rápida adiciona automaticamente as importações necessárias, você não precisa copiar manualmente as `using` diretivas de que seu código precisa.

## <a name="add-missing-usings-refactoring"></a>Adicionar a refatoração de usos ausentes

1. Copie o código de um arquivo e cole-o em um novo sem incluir as `using` diretivas necessárias. O erro resultante é acompanhado por uma correção de código que adiciona as `using` diretivas ausentes.

    > [!NOTE]
    > É necessário ativar essa sugestão em **Ferramentas > Opções > Editor de Texto > C# > Avançado > Diretivas Using**.

2. Selecione Ctrl+. para abrir o menu **Ações Rápidas e Refatorações**.

    ![Gerar usos](media/generate-using-codefix.png)

3. Selecione **usando \<your reference\> ;** para adicionar a referência ausente.

    ![Gerar o resultado de instruções using](media/generate-using-result.png)

## <a name="see-also"></a>Confira também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)
- [Dicas para desenvolvedores do .NET](../csharp-developer-productivity.md)
