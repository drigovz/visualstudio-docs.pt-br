---
title: Gerar substituições de método Equals e GetHashCode em C#
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e70593bc04b576237a7f9f0f51ae6c3d37e40a88
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660035"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Gerar substituições dos métodos Equals e GetHashCode no Visual Studio

Esta geração de código aplica-se a:

- C#

**O quê:** Permite que você gere os métodos **Equals** e **GetHashCode**.

**Quando:** gere essas substituições quando houver um tipo que precise ser comparado por um ou mais campos e não pelo local do objeto na memória.

**Por que:**

- Se você estiver implementando um tipo de valor, considere substituir o método **Equals** para aumentar desempenho em relação à implementação padrão do método Equals em ValueType.

- Se você estiver implementando um tipo de referência, considere substituir o método **Equals** se o seu tipo parecer um tipo base, como Point, String, BigNumber e assim por diante.

- Substitua o método **GetHashCode** para permitir que um tipo funcione corretamente em uma tabela de hash. Leia mais orientação em [operadores de igualdade](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Como fazer

1. Coloque o cursor em algum lugar na linha de sua declaração de tipo.

   ![Código realçado](media/overrides-highlight-cs.png)

   > [!TIP]
   > Se você clicar duas vezes para selecionar o nome do tipo, a opção de menu não ficará disponível. Basta colocar o cursor em algum lugar na linha.

1. Depois, siga um destes procedimentos:

   - Pressione **Ctrl**+ **.** para acionar o menu **Ações e Refatorações Rápidas**.

   - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.

   - Clique no ícone de ![chave de fenda](../media/screwdriver-icon.png) ícone que aparece na margem esquerda.

   ![Visualização Gerar substituições](media/overrides-preview-cs.png)

1. Selecione **Gerar Equals(object)** ou **Gerar Equals e GetHashCode** no menu suspenso.

1. Na caixa de diálogo **Selecionar membros**, escolha os membros para os quais deseja gerar os métodos:

    ![Caixa de diálogo Gerar substituições](media/overrides-dialog-cs.png)

    > [!TIP]
    > Você também pode optar por gerar operadores nessa caixa de diálogo usando a caixa de seleção na parte inferior da caixa de diálogo.

   Os métodos `Equals` e `GetHashCode` são gerados com implementações padrão.

   ![Resultado da geração do método](media/overrides-result-cs.png)

## <a name="see-also"></a>Consulte também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)