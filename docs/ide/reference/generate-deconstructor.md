---
title: Gerar uma ação rápida de desconstrutor
description: Saiba como usar o menu ações rápidas e refatoração para gerar imediatamente o stub do método para um novo desconstrutor.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: ff2ac7682eff1c3da0597a95945a6a0b016d9213
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617247"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Gerar um desconstrutor no Visual Studio

Esta geração de código aplica-se a:

- C#

**O que:** Permite gerar imediatamente o stub do método para um novo desconstrutor.

**Quando:** Você deseja desconstruir corretamente seu tipo automaticamente.

**Por que:** Você pode digitar manualmente um desconstrutor, mas esse recurso gera o stub para você com os parâmetros de saída corretos.

## <a name="generate-a-deconstructor"></a>Gerar um desconstrutor

1. Declare um novo tipo com os parâmetros de saída desejados especificados. Essa declaração causa um erro quando nenhuma instância de desconstrução correspondente à declaração for encontrada.

   ![Erro de desconstrutor ausente](media/deconstruct.png)

2. Siga uma destas etapas:

   - **Teclado**
      - Com o cursor na sua declaração, selecione Ctrl+. para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
      - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
      - Selecione o :::image type="icon" source="media/screwdriver.png"::: ícone que aparece na margem esquerda se o cursor de texto já estiver na linha vazia da classe.

      ![Gerar uma correção de código de desconstrutor](media/deconstruct-codefix.png)

3. Selecione **Gerar método 'MyInternalClass.Deconstruct'** para gerar o desconstrutor.

   ![Código resultante do desconstrutor](media/deconstruct-result.png)

## <a name="see-also"></a>Confira também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)
- [Dicas para desenvolvedores do .NET](../csharp-developer-productivity.md)