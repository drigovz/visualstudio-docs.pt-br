---
title: Refatoração Extrair uma interface
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.extractinterface
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: bc315ed49e31e78bc549e446858a30979d7135b2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838210"
---
# <a name="extract-an-interface-refactoring"></a>Refatoração Extrair uma interface

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O quê:** Permite criar uma interface usando membros existentes de uma classe, um struct ou uma interface.

**Quando:** Você tem várias classes, structs ou interfaces com métodos que podem se tornar comuns e ser usados por outras classes, structs ou interfaces.

**Por que:** As interfaces são ótimos constructos para designs orientados a objeto. Imagine ter classes para vários animais (gato, cachorro, pássaro) que podem ter métodos comuns, como comer, beber, dormir. Usar uma interface como IAnimal permitiria que cachorro, gato e pássaro tivessem uma "assinatura" comum para esses métodos.

## <a name="how-to"></a>Como fazer

1. realce o nome da classe para executar a ação ou simplesmente coloque o cursor do texto em algum lugar no nome da classe.

   - C#:

       ![Código realçado – C#](media/extractinterface-highlight-cs.png)

   - Visual Basic:

       ![Código realçado – Visual Basic](media/extractinterface-highlight-vb.png)

2. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl+R**, em seguida, **Ctrl+I**. (Observe que o atalho de teclado pode ser diferente com base no perfil selecionado.)
      - Pressione **Ctrl**+**.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Extrair Interface** no pop-up da janela Visualização.
   - **Mouse**
      - Selecione **Editar > Refatorar > Extrair Interface**.
      - Clique com o botão direito do mouse no nome da classe, selecione o menu **Ações Rápidas e Refatorações** e selecione **Extrair Interface** no pop-up da janela Visualização.

3. Na caixa de diálogo **Extrair Interface** que é exibida, insira as informações solicitadas:

   ![Extrair Interface](media/extractinterface-dialog-cs.png)


   | Campo | Descrição |
   | - | - |
   | **Nome da nova interface** | O nome da interface a ser criada. O padrão é I*ClassName*, onde *ClassName* é o nome da classe selecionada acima. |
   | **Nome do novo arquivo** | O nome do arquivo que será gerado com a interface. Como acontece com o nome da interface, o padrão é I*ClassName*, onde *ClassName* é o nome da classe selecionada acima. |
   | **Selecionar membros públicos para formar a interface** | Os itens a serem extraídos para a interface. Você pode selecionar quantos desejar. |


4. Escolha **OK**.

   A interface foi criada no arquivo com o nome especificado. Além disso, a classe que você selecionou implementa essa interface.

   - C#:

      ![Classe resultante – C#](media/extractinterface-class-cs.png) ![Interface resultante – C#](media/extractinterface-interface-cs.png)

   - Visual Basic:

      ![Classe resultante – Visual Basic](media/extractinterface-class-vb.png) ![Interface resultante – Visual Basic](media/extractinterface-interface-vb.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)