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
ms.openlocfilehash: 2ca2d3a0c174fa4c7d0f66d3abc440b8c9aa93cf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790284"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Gerar um desconstrutor no Visual Studio

Esta geração de código aplica-se a:

- C#

**O quê:** Permite gerar imediatamente o stub de método para um novo desconstrutor.

**Quando:** Você deseja desconstruir corretamente o tipo de forma automática.

**Por que:** você pode digitar manualmente um desconstrutor, mas essa funcionalidade gera o stub para você com os parâmetros de saída corretos.

## <a name="generate-a-deconstructor"></a>Gerar um desconstrutor

1. Declare um novo tipo com os parâmetros de saída desejados especificados. Essa declaração causa um erro quando nenhuma instância de desconstrução correspondente à declaração for encontrada.

   ![Erro de desconstrutor ausente](media/deconstruct.png)

2. Realize uma das seguintes etapas:

   - **Teclado**
      - Com o cursor na sua declaração, selecione Ctrl+. para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
      - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
      - Selecione o ícone ![chave de fenda](media/screwdriver.png) ícone que aparece na margem esquerda quando o cursor de texto já está na linha vazia na classe.

      ![Gerar uma correção de código de desconstrutor](media/deconstruct-codefix.png)

3. Selecione **Gerar método 'MyInternalClass.Deconstruct'** para gerar o desconstrutor.

   ![Código resultante do desconstrutor](media/deconstruct-result.png)

## <a name="see-also"></a>Consulte também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)
- [Dicas para desenvolvedores do .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)