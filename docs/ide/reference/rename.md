---
title: Renomeação de refatoração
description: Saiba como usar o recurso refatorar renomeação para renomear identificadores para símbolos de código, como campos, variáveis locais, métodos, namespaces, propriedades e tipos.
ms.custom: SEO-VS-2020
ms.date: 05/04/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 43a6e93815732c4f9d2ec7f29d6d6bef4c1f3451
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616714"
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

2. Em seguida, use o teclado ou o mouse da seguinte maneira:

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

- A partir do Visual Studio 2019 versão 16,3, quando você renomeia um tipo que corresponde ao nome do arquivo no qual ele está, uma caixa de seleção é exibida, permitindo que você renomeie o arquivo ao mesmo tempo. Essa opção é exibida quando você renomeia uma classe, interface ou enumeração. Não há suporte para essa opção em tipos parciais com várias definições.

   ![Renomear animação com o arquivo-C #](media/rename-with-file-animated-cs.gif)

- Se você escolher um nome que já exista, o que causaria um conflito, a caixa **Renomear** o avisará.

   ![Conflito de renomeação](media/rename-conflict-cs.png)

- Outra maneira de renomear um símbolo é alterar seu nome no editor. Em seguida, com o cursor no nome do símbolo, pressione **Ctrl** + **.** ou simplesmente expanda o menu de ícone de lâmpada que aparece e escolha **renomear \<old name> como \<new name>**.

   ![Renomear no editor](media/rename-with-editor-cs.png)

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)
