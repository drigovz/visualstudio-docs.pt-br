---
title: Gerar usos
description: Saiba como usar o menu ações rápidas e refatoração para adicionar imediatamente as importações necessárias ou o uso de diretivas para código de cópia e colagem.
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
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: 0f73b50dc34e95161c4c85cd559abcf5c9bac60b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967989"
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

## <a name="see-also"></a>Consulte também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)
- [Dicas para desenvolvedores do .NET](../csharp-developer-productivity.md)
