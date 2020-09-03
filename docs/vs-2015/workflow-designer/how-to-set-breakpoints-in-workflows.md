---
title: Como definir pontos de interrupção em fluxos de trabalho | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d1bbb18a9015b52b3d65cb8f8fd02674693abc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659133"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Como: Definir pontos de interrupção em fluxos de trabalho
Quando você usa [!INCLUDE[wfd1](../includes/wfd1-md.md)], você pode definir pontos de interrupção nos fluxos de trabalho gráficos como você faria em Visual Basic ou no código em c. Como esperado, a execução de fluxo de trabalho que ele pare em cada ponto de interrupção esse definido.

 Um ponto de interrupção tem três Estados: *pendente*, *associado*e *erro*. Quando você definir um ponto de interrupção, ele está pendente, e ele é representado por um ícone vermelho contínuo. Quando o runtime carregado o tipo de fluxo de trabalho, transformações limite. Se você especificar um formato incorreto do ponto de interrupção, como um nome de atividade que não é válida, uma janela de erro aparece. O ponto de interrupção é adicionado ainda para a janela de ponto de interrupção, mas é marcado com um pequeno “x”.

> [!NOTE]
> Os pontos de interrupção em fluxos de trabalho chamados não são suportados.
>
> [!WARNING]
> Certifique-se de selecionar a opção **habilitar apenas meu código (somente gerenciado)** no menu **ferramentas**, **Opções**, **depuração** antes de depurar. Se você tiver duas sequências aninhadas em outra sequência e definir um ponto de interrupção na primeira sequência interna, pressionar **F11** não será depurado na segunda sequência interna se a opção <strong>habilitar apenas meu código (somente gerenciado)</strong>não estiver selecionada.
>
> [!WARNING]
> Os pontos de interrupção em um fluxo de trabalho não obterão a ocorrência se o caminho completo para a propriedade de arquivo XAML não é preciso. O caminho completo do arquivo XAML não é preciso após movido o projeto/solução para outra pasta ou a outro computador. Selecione Ctrl+S para salvar e atualiza a propriedade de caminho completo.

### <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Para definir um ponto de interrupção em uma atividade no modo design

1. Selecione a atividade que você deseja que o depurador para interromper novamente.

2. No menu **depurar** , selecione **alternar ponto de interrupção**. Um ícone vermelho aparecerá na borda superior esquerda da atividade.

     Como alternativa, você também pode pressionar a tecla de atalho **F9** depois de selecionar a atividade ou pode clicar com o botão direito do mouse na atividade e selecionar **ponto** de interrupção e, em seguida, **Inserir ponto de interrupção** no menu de contexto.

## <a name="see-also"></a>Consulte Também
 [Como invocar os fluxos de trabalho de depuração do depurador de fluxo de trabalho](../workflow-designer/how-to-invoke-the-workflow-debugger.md) [com o designer de fluxo de trabalho](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) [como: Depurar XAML com o designer de fluxo de trabalho](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)