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
ms.openlocfilehash: 0ce1b620a6d8aba7e4aea767745891dff6d9f869
ms.sourcegitcommit: cd91a8a4f6086cda9ba6948be25864fc7d6b8e44
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59537498"
---
# <a name="generate-usings-in-visual-studio"></a>Gerar instruções using no Visual Studio

Esta geração de código aplica-se a:

- C#

**O quê:** Permite adicionar imediatamente as importações necessárias ou as [instruções using](/dotnet/csharp/language-reference/keywords/using-statement) para um código copiado e colado.

**Quando:** É uma prática comum copiar o código de locais diferentes no projeto ou de outras fontes e colá-lo no novo código. Essa Ação rápida encontra as instruções de importações ausentes para o código copiado e colado e, em seguida, solicita a adição delas.

**Por que:** como a Ação rápida adiciona automaticamente as importações necessárias, você não precisa copiar manualmente as instruções `using` que seu código precisa.

## <a name="generate-usings-refactoring"></a>Refatoração de gerar instruções using

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
- [Dicas para desenvolvedores do .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
