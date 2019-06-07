---
title: 'Designer de fluxo de trabalho - como: Usar o designer de argumento'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c333e78de17a3af5b4f7f0be46c19cf3120231d
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746906"
---
# <a name="how-to-use-the-argument-designer"></a>Como: Usar o designer de argumento

O designer do argumento facilita permitir que os dados e fluam fora de uma atividade. Acessar o designer clicando o **argumentos** botão no canto inferior esquerdo da tela de design. O designer contém uma lista de argumentos que aparecem em um formulário tabular e podem ser classificados por cada um dos cabeçalhos de coluna, exceto para o **valor padrão** coluna. Cada argumento contiver um nome, a direção de in/out/in-out/property, o tipo, e o valor padrão de expressão (se houver). O nome e o valor padrão de expressão são campos editáveis de texto, e o tipo e direção são gota- suspensa. Para obter mais informações, consulte [variáveis e argumentos (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>Para criar um novo argumento

1. Abra uma solução de fluxo de trabalho ou atividade no Visual Studio.

2. Abra o designer dos argumentos clicando o **argumentos** botão no canto inferior esquerdo da tela de design. O designer dos argumentos aparece.

3. Clique na linha vazia rotulada **argumento criar**. Isso adicionará uma nova linha com um novo argumento usando os seguintes valores padrão: argumentx para o **nome** onde x é um inteiro com um valor inicial de 1, que é incrementado automaticamente para criar nomes exclusivos de argumento, **em**  para o **direção**, e **cadeia de caracteres** para o **tipo de argumento**. Nenhum valor é adicionado para **valor padrão**. Você pode alterar esses valores a qualquer momento durante o processo de design de fluxo de trabalho.

    > [!NOTE]
    > Para excluir um argumento, selecione o argumento clicando nele e, em seguida, pressione a **excluir** chave.

## <a name="see-also"></a>Consulte também

- [Usando o Designer de Fluxo de Trabalho](developing-applications-with-the-workflow-designer.md)
- [Variables and Arguments](/dotnet/framework/windows-workflow-foundation/variables-and-arguments) (Variáveis e argumentos)