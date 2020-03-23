---
title: Gerar uma ação rápida de desconstrutor
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5a3a89d15d05b44575fede98d3043d706b24c1d9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531891"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Gerar um desconstrutor no Visual Studio

Esta geração de código aplica-se a:

- C#

**O que é isso?** Permite que você gere imediatamente o stub de método para um novo desconstrutor.

**Quando:** Você deseja desconstruir corretamente seu tipo automaticamente.

**Por que:** Você pode digitar manualmente um desconstrutor, mas este recurso gera o stub para você com os parâmetros corretos de saída.

## <a name="generate-a-deconstructor"></a>Gerar um desconstrutor

1. Declare um novo tipo com os parâmetros de saída desejados especificados. Essa declaração causa um erro quando nenhuma instância de desconstrução correspondente à declaração for encontrada.

   ![Erro de desconstrutor ausente](media/deconstruct.png)

2. Siga uma destas etapas:

   - **Teclado**
      - Com o cursor na sua declaração, selecione Ctrl+. para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
      - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
      - Selecione o ícone ![chave de fenda](media/screwdriver.png) ícone que aparece na margem esquerda quando o cursor de texto já está na linha vazia na classe.

      ![Gerar uma correção de código de desconstrutor](media/deconstruct-codefix.png)

3. Selecione **Gerar método 'MyInternalClass.Deconstruct'** para gerar o desconstrutor.

   ![Código resultante do desconstrutor](media/deconstruct-result.png)

## <a name="see-also"></a>Confira também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)
- [Dicas para desenvolvedores .NET](../csharp-developer-productivity.md)