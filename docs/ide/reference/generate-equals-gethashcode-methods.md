---
title: Gerar substituições de método Equals e GetHashCode em C#
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f9b1a639dd655f4f75b21555396866858b144010
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569277"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Gerar substituições dos métodos Equals e GetHashCode no Visual Studio

Esta geração de código aplica-se a:

- C#

**O quê:** Permite que você gere os métodos **Equals** e **GetHashCode**.

**Quando:** gere essas substituições quando houver um tipo que precise ser comparado por um ou mais campos e não pelo local do objeto na memória.

**Porque:**

- Se você estiver implementando um tipo de valor, considere substituir o método **Equals** para aumentar desempenho em relação à implementação padrão do método Equals em ValueType.

- Se você estiver implementando um tipo de referência, considere substituir o método **Equals** se o seu tipo parecer um tipo base, como Point, String, BigNumber e assim por diante.

- Substitua o método **GetHashCode** para permitir que um tipo funcione corretamente em uma tabela de hash. Leia mais orientação em [operadores de igualdade](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Como fazer

1. Coloque o cursor em algum lugar na linha de sua declaração de tipo.

   ![Código realçado](media/overrides-highlight-cs.png)

   > [!TIP]
   > Se você clicar duas vezes para selecionar o nome do tipo, a opção de menu não ficará disponível. Basta colocar o cursor em algum lugar na linha.

1. Depois, siga um destes procedimentos:

   - Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.

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

## <a name="see-also"></a>Confira também

- [Geração de Código](../code-generation-in-visual-studio.md)
- [Visualizar Alterações](../../ide/preview-changes.md)
