---
title: Renomeação de refatoração
ms.date: 01/26/2018
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
ms.openlocfilehash: 4dbccd4732f56d671fd74f59916885ea338136f8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565455"
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

- A partir do Visual Studio 2019 versão 16.3, quando você renomear um tipo que corresponda ao nome do arquivo em que está, uma caixa de seleção aparece que permite que você renomeie o arquivo ao mesmo tempo. Essa opção aparece quando você renomeia uma classe, interface ou enumeração. Esta opção não é suportada para tipos parciais com múltiplas definições.

   ![Renomear animação com arquivo - C #](media/rename-with-file-animated-cs.gif)

- Se você escolher um nome que já exista, o que causaria um conflito, a caixa **Renomear** o avisará.

   ![Conflito de renomeação](media/rename-conflict-cs.png)

- Outra maneira de renomear um símbolo é alterar seu nome no editor. Em seguida, com o cursor no nome do símbolo, **pressione Ctrl**+**.** ou apenas expanda o menu do ícone da lâmpada que aparece e escolha **Renomear \<nome antigo> para \<nome novo>**.

## <a name="see-also"></a>Confira também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)
