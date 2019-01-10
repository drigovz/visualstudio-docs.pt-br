---
title: Renomear um nome de arquivo para que ele corresponda a um tipo
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 42e1d3cad1752649446a35abd863390166a57271
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834575"
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>Refatoração Sincronizar um tipo para um nome de arquivo ou um nome de arquivo para um tipo

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O quê:** Permite renomear um tipo para que ele corresponda ao nome de arquivo ou renomear um nome de arquivo para que ele corresponda ao tipo que ele contém.

**Quando:** Você renomeou um arquivo ou um tipo e ainda não atualizou o arquivo nem o tipo correspondente a ser correspondido.

**Por que:** Se você colocar um tipo em um arquivo com um nome diferente ou vice-versa, será difícil encontrar o que está procurando. Se você renomear o tipo ou nome de arquivo, o código se tornará mais legível e mais fácil de navegar.

## <a name="how-to"></a>Como fazer

1. realce ou coloque o cursor do texto dentro do nome do tipo para sincronizar:

   - C#:

       ![Código realçado – C#](media/synctype-highlight-cs.png)

   - Visual Basic:

       ![Código realçado – Visual Basic](media/synctype-highlight-vb.png)

2. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl**+**.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Renomear o arquivo para *TypeName*.cs** no pop-up da janela Visualização, onde *TypeName* é o nome do tipo selecionado.
      - Pressione **Ctrl**+**.** para disparar o menu **Ações Rápidas e Refatorações** e selecione **Renomear tipo para _Filename_** no pop-up da janela Visualização, onde *Filename* é o nome do arquivo atual.
   - **Mouse**
      - Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Renomear o arquivo para *TypeName*.cs** no pop-up da janela Visualização, onde *TypeName* é o nome do tipo selecionado.
      - Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Renomear o tipo para _Filename_** no pop-up da janela Visualização, onde *Filename* é o nome do arquivo atual.

   O tipo ou o arquivo foi renomeado.

   - C#: No exemplo a seguir, o arquivo **MyClass.cs** foi renomeado para **MyNewClass.cs** para corresponder ao nome do tipo.

       ![Resultado embutido em C#](media/synctype-result-cs.png)

   - Visual Basic: No exemplo a seguir, o arquivo **Employee.vb** foi renomeado para **Person.vb** para corresponder ao nome do tipo.

       ![Resultado embutido em Visual Basic](media/synctype-result-vb.png)

> ![NOTE] Esta refatoração ainda não está disponível para projetos .NET Core e .NET Standard.

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
