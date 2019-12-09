---
title: Refatoração Extrair uma interface
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 15da8bdf1a3df60a7ad4816ce578ec5672c85ecf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654425"
---
# <a name="extract-an-interface-refactoring"></a>Refatoração Extrair uma interface

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O que:** Permite criar uma interface usando membros existentes de uma classe, estrutura ou interface.

**Quando:** Você tem membros em uma classe, struct ou interface que podem ser herdados por outras classes, estruturas ou interfaces.

**Por quê:** as interfaces são ótimos constructos para designs orientados a objetos. Imagine ter classes para vários animais (gato, cachorro, pássaro) que podem ter métodos comuns, como comer, beber, dormir. Usar uma interface como IAnimal permitiria que cachorro, gato e pássaro tivessem uma "assinatura" comum para esses métodos.

## <a name="extract-an-interface-refactoring"></a>Refatoração Extrair uma interface

1. Coloque o cursor no nome da classe.

   - C#:

       ![Código realçado – C#](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Código realçado – Visual Basic](media/extractinterface-highlight-vb.png)

2. Em seguida, realize uma das seguintes ações:

   - **Teclado**
      - Pressione **Ctrl+R**, em seguida, **Ctrl+I**. (O atalho de teclado pode ser diferente de acordo com o perfil selecionado.)
      - Pressione **Ctrl**+ **.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Extrair Interface** no pop-up da janela Visualização.
   - **Mouse**
      - Selecione **Editar > Refatorar > Extrair Interface**.
      - Clique com o botão direito do mouse no nome da classe, selecione o menu **Ações Rápidas e Refatorações** e selecione **Extrair Interface** no pop-up da janela Visualização.

3. Na caixa de diálogo **Extrair Interface** que é exibida, insira as informações solicitadas:

   ![Extrair Interface](media/extractinterface-dialog-same-file.png)

   | Campo | Descrição |
   | - | - |
   | **Nome da nova interface** | O nome da interface a ser criada. O nome usará como padrão I*ClassName*, em que *ClassName* é o nome da classe selecionada acima. |
   | **Nome do novo arquivo** | O nome do arquivo gerado que conterá a interface. Assim como ocorre com o nome da interface, esse nome usará como padrão I*ClassName*, em que *ClassName* é o nome da classe selecionada acima. Selecione também a opção para **Adicionar ao arquivo atual**. |
   | **Selecionar membros públicos para formar a interface** | Os itens a serem extraídos para a interface. Você pode selecionar quantos desejar. |

4. Clique em **OK**.

   A interface foi criada no arquivo com o nome especificado. Além disso, a classe que você selecionou implementa essa interface.

   - C#:

      ![Classe resultante – C#](media/extractinterface-class-cs.png)

      ![Interface resultante – C#](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Classe resultante – Visual Basic](media/extractinterface-class-vb.png)

      ![Interface resultante – Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Dicas para desenvolvedores de .NET](../csharp-developer-productivity.md)
