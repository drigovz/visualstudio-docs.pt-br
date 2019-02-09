---
title: 'Designer de fluxo de trabalho - como: Definir pontos de interrupção em fluxos de trabalho'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7503d0b0bee201a9617e90966c9f75ac6333f228
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55908433"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Como: Definir pontos de interrupção em fluxos de trabalho

Quando você usar o Designer de fluxo de trabalho, você pode definir pontos de interrupção em fluxos de trabalho gráficos como você faria no código do Visual Basic ou c#. Como esperado, a execução de fluxo de trabalho que ele pare em cada ponto de interrupção esse definido.

Um ponto de interrupção tem três estados: *Pendente*, *ligado*, e *erro*. Quando você definir um ponto de interrupção, ele está pendente, e ele é representado por um ícone vermelho contínuo. Quando o tempo de execução carregado o tipo de fluxo de trabalho, transformações limite. Se você especificar um formato incorreto do ponto de interrupção, como um nome de atividade que não é válida, uma janela de erro aparece. O ponto de interrupção é adicionado ainda para a janela de ponto de interrupção, mas é marcado com um pequeno “x”.

> [!NOTE]
> Os pontos de interrupção em fluxos de trabalho chamados não são suportados.

> [!NOTE]
> Certifique-se de que você selecione a opção **Habilitar Just My Code (somente gerenciado)** da **ferramentas** > **opções** > **depuração**  menu Depurar. Se a opção não estiver selecionada, você tem duas sequências aninhadas dentro de outra sequência e você definir um ponto de interrupção na primeira sequência interna, pressionando **F11** não depurará na segunda sequência interna.

> [!NOTE]
> Pontos de interrupção em um fluxo de trabalho não são atingidos, se o caminho completo para a propriedade do arquivo XAML não é preciso. O caminho completo para o arquivo XAML não é preciso depois de mover o projeto ou solução para outra pasta ou em outro computador. Selecione **Ctrl**+**S** para salvar e atualizar a propriedade de caminho completo.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Para definir um ponto de interrupção em uma atividade no modo design

1. Selecione a atividade que você deseja que o depurador para interromper novamente.

2. Sobre o **Debug** menu, selecione **alternar ponto de interrupção**. Um ícone vermelho aparecerá na borda superior esquerda da atividade.

   Como alternativa, você pode pressionar **F9** depois que a atividade, ou você pode a atividade com o botão direito e selecione **ponto de interrupção** > **Inserir ponto de interrupção** no menu de atalho.

## <a name="see-also"></a>Consulte também

- [Fluxos de trabalho de depuração com o Designer de Fluxo de Trabalho](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Como: Depurar XAML com o Designer de fluxo de trabalho](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)