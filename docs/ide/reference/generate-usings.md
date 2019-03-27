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
ms.openlocfilehash: afd4b758332d9357dc20dd84e726d72da4d2db74
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355171"
---
# <a name="generate-usings-in-visual-studio"></a>Gerar instruções using no Visual Studio

Esta geração de código aplica-se a:

- C#

**O quê:** Permite adicionar imediatamente as importações necessárias ou as [instruções using](/dotnet/csharp/language-reference/keywords/using-statement) de um código copiado e colado.

**Quando:** É uma prática comum copiar e colar o código de locais diferentes no projeto ou de outras fontes de código. Essa ação rápida analisa as importações ausentes para o código copiado e colado e, em seguida, solicita a adição delas.

**Por que:** Com a adição automática das importações necessárias, o usuário não precisa copiar manualmente as instruções `using` necessárias.

## <a name="generate-usings-refactoring"></a>Refatoração de gerar instruções using

1. Copie e cole o código de um arquivo diferente sem incluir as instruções `using` necessárias. Agora, o erro é acompanhado por uma correção de código que adiciona as instruções `using` ausentes.

    > [!NOTE] 
    > Essa sugestão precisa ser ativada em **Ferramentas > Opções > Editor de Texto > C# > Avançado > Diretivas Using**.

2. Pressione **Ctrl**+**.** para abrir o menu **Ações Rápidas e Refatorações**. 

    ![Gerar instruções using](media/generate-using-codefix.png)

3. Selecione **using \<sua referência\>;** para adicionar a referência ausente.

    ![Gerar o resultado de instruções using](media/generate-using-result.png)

## <a name="see-also"></a>Consulte também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)
- [Dicas para desenvolvedores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
