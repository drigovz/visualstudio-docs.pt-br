---
title: 'Designer de Fluxo de Trabalho-como: usar o designer de argumentos'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c3f8216bb0dfe3813e4852151c351b865128d0c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650287"
---
# <a name="how-to-use-the-argument-designer"></a>Como: Use o designer do argumento

O designer de argumentos facilita a permissão de fluxo de dados para dentro e fora de uma atividade. Acesse o Designer clicando no botão **argumentos** no canto inferior esquerdo da tela de design. O designer contém uma lista de argumentos que aparecem em um formulário de tabela e podem ser classificados por cada um dos cabeçalhos de coluna, exceto para a coluna **valor padrão** . Cada argumento contiver um nome, a direção de in/out/in-out/property, o tipo, e o valor padrão de expressão (se houver). O nome e o valor padrão de expressão são campos editáveis de texto, e o tipo e direção são gota- suspensa. Para obter mais informações, consulte [Variables and Arguments (.net)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>Para criar um novo argumento

1. Abra uma solução de fluxo de trabalho ou atividade no Visual Studio.

2. Abra o designer de argumentos clicando no botão **argumentos** no canto inferior esquerdo da tela de design. O designer dos argumentos aparece.

3. Clique na linha vazia rotulada **criar argumento**. Isso adicionará uma nova linha com um novo argumento usando os seguintes valores padrão: argumentx para o **nome** em que x é um inteiro com um valor inicial de 1 que é incrementado automaticamente para criar nomes de argumentos exclusivos, **em** para a **direção**, e a **cadeia de caracteres** para o tipo de **argumento**. Nenhum valor é adicionado para o **valor padrão**. Você pode alterar esses valores a qualquer momento durante o processo de design de fluxo de trabalho.

    > [!NOTE]
    > Para excluir um argumento, selecione o argumento clicando nele e pressione a tecla **delete** .

## <a name="see-also"></a>Consulte também

- [Usando o Designer de Fluxo de Trabalho](developing-applications-with-the-workflow-designer.md)
- [Variables and Arguments](/dotnet/framework/windows-workflow-foundation/variables-and-arguments) (Variáveis e argumentos)