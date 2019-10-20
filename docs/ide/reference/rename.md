---
title: Renomeação de refatoração
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2991227b3c8d742da360465e6c506e7123259e2c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655615"
---
# <a name="rename-a-code-symbol-refactoring"></a>Refatoração Renomear um símbolo de código

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O quê:** permite renomear identificadores para símbolos de código, como campos, variáveis locais, métodos, namespaces, propriedades e tipos.

**Quando:** você deseja renomear algo com segurança sem a necessidade de localizar todas as instâncias e copiar/colar o novo nome.

**Por quê:** copiar e colar o novo nome em um projeto inteiro provavelmente resultaria em erros. Essa ferramenta de refatoração realizará com precisão a ação de renomeação.

## <a name="how-to"></a>Como fazer

1. realce ou coloque o cursor do texto dentro do item a ser renomeado:

   - C#:

       ![Código realçado – C#](media/rename-highlight-cs.png)

   - Visual Basic:

       ![Código realçado – Visual Basic](media/rename-highlight-vb.png)

2. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl+R**, em seguida, **Ctrl+R**. (Observe que o atalho de teclado pode ser diferente com base no perfil selecionado.)
   - **Mouse**
      - Selecione **Editar > Refatorar > Renomear**.
      - Clique com o botão direito do mouse no código e selecione **Renomear**.

3. Renomeie o item digitando o novo nome.

   - C#:

      ![Renomear animação – C#](media/rename-animated-cs.gif)

   - Visual Basic:

      ![Renomear – VB](media/rename-rename-vb.png)

   > [!TIP]
   > Também é possível atualizar os comentários e outras cadeias de caracteres para usar esse novo nome, bem como [visualizar as alterações](../../ide/preview-changes.md) antes de salvar usando as caixas de seleção na caixa **Renomear** que aparece na parte superior direita do editor.

4. Quando estiver satisfeito com a alteração, escolha **Aplicar** ou pressione **Enter** e as alterações serão confirmadas.

## <a name="remarks"></a>Comentários

- A partir do Visual Studio 2019 versão 16,3, quando você renomeia um tipo que corresponde ao nome do arquivo no qual ele está, uma caixa de seleção é exibida para permitir que você renomeie o arquivo ao mesmo tempo. Essa opção é exibida quando você renomeia uma classe, interface ou enumeração. Não há suporte para essa opção em tipos parciais com várias definições.

   ![Renomear animação com arquivo-C#](media/rename-with-file-animated-cs.gif)

- Se você escolher um nome que já exista, o que causaria um conflito, a caixa **Renomear** o avisará.

   ![Conflito de renomeação](media/rename-conflict-cs.png)

- Outra maneira de renomear um símbolo é alterar seu nome no editor. Depois, com o cursor no nome do símbolo, pressione **Ctrl**+ **.** ou apenas expanda o menu do ícone da lâmpada que aparece e escolha **Renomear \<nome antigo> para \<nome novo>** .

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)
