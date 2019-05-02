---
title: 'Designer de fluxo de trabalho - como: Depurar XAML com o Designer de Fluxo de Trabalho'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: cdbf5fa21c8fcf9069db9a7348d4ed576fc342c5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949586"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Como: Depurar XAML com o Designer de Fluxo de Trabalho

Fluxos de trabalho são definidos em termos de XAML. A representação de interface de usuário de fluxo de trabalho é construída sobre a árvore XAML que define o fluxo de trabalho. A experiência de depuração é semelhante à depuração de fluxos de trabalho no Designer de fluxo de trabalho. Por exemplo, durante a depuração XAML, os locais, inspeção e janelas de segmentos o funcionam da mesma forma como fazem no Designer de fluxo de trabalho de depuração. Além disso, a exibição da pilha de chamadas durante a depuração XAML é uma exibição hierárquica linha com base de fluxo de execução do fluxo de trabalho.

> [!NOTE]
> Se o XAML para um fluxo de trabalho está localizado no mesmo assembly que as atividades, a parte do assembly de nomes de classe não é incluído. Sem esta parte dos nomes de classe (atividade), o XAML não pode ser carregado no tempo de execução. Não é recomendável definir atividades no mesmo namespace que o projeto pai; caso contrário, o XAML deverá mão- ser editado após ser editado no designer.

## <a name="to-debug-workflow-xaml"></a>Para depurar o fluxo de trabalho XAML

1. Abra um projeto de fluxo de trabalho ou atividade no Visual Studio.

2. Definir um ponto de interrupção na atividade ou atividades que você deseja depurar, conforme descrito em [como: Definir pontos de interrupção em fluxos de trabalho](../workflow-designer/how-to-set-breakpoints-in-workflows.md).

3. Clique com botão direito no arquivo. XAML que contém a definição de fluxo de trabalho e selecione **Exibir código**. Você verá um ponto de interrupção exibido na mesma linha da declaração de elemento XAML de atividade que você definir o ponto de interrupção sobre no modo design.

4. Chamar o depurador, conforme descrito em [depurar fluxos de trabalho](debugging-workflows-with-the-workflow-designer.md).

5. Quando a execução de código atinge um de seus pontos de interrupção, o elemento XAML associado com esse ponto de interrupção será realçado. Para mover para o próximo ponto de interrupção, use o **F10** ou **F11** chave.

## <a name="see-also"></a>Consulte também

- [Como: definir pontos de interrupção em fluxos de trabalho](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Depurar fluxos de trabalho](debugging-workflows-with-the-workflow-designer.md)