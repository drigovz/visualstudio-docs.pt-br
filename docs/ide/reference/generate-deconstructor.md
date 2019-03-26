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
ms.openlocfilehash: 8887f4cd6b4dcd7f08e808f1271f5d546d6a224c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159173"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Gerar um desconstrutor no Visual Studio

Esta geração de código aplica-se a:

- C#

**O quê:** Permite gerar imediatamente o stub de método para um novo desconstrutor.

**Quando:** Você deseja desconstruir corretamente o tipo de forma automática.

**Por que:** Você pode digitar manualmente um desconstrutor; no entanto, essa funcionalidade gerará o stub para você com os parâmetros de saída corretos.

## <a name="generate-deconstructor"></a>Gerar desconstrutor

1. Declare um novo tipo com os parâmetros de saída desejados especificados. Essa declaração causará um erro quando nenhuma instância de desconstrução que corresponda à declaração puder ser encontrada.

   ![Erro de desconstrutor ausente](media/deconstruct.png)

2. Em seguida, escolha uma das seguintes opções no:

   - **Teclado**
      - Com o cursor na declaração, pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
      - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
      - Clique no ícone de ![chave de fenda](media/screwdriver.png) ícone que aparece na margem esquerda quando o cursor de texto já está na linha vazia na classe.

      ![Gerar uma correção de código de desconstrutor](media/deconstruct-codefix.png)

3. Selecione **Gerar método 'MyInternalClass.Deconstruct'** para gerar o desconstrutor.

   ![Código resultante do desconstrutor](media/deconstruct-result.png)


## <a name="see-also"></a>Consulte também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)
- [Dicas para desenvolvedores de .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)