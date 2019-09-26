---
title: Mensagens de erro em Designer de Fluxo de Trabalho
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3f2d4d86f80bc7c2966d5156267352154b1279f
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254806"
---
# <a name="error-messages-in-workflow-designer"></a>Mensagens de erro em Designer de Fluxo de Trabalho

Este tópico descreve os tipos de mensagens de erro que podem ser encontrados ao trabalhar com Designer de Fluxo de Trabalho.

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Situações em que os erros no criador de Fluxo de Trabalho ocorrem

Erros em Designer de Fluxo de Trabalho ocorrem nas seguintes situações:

1. Há um erro em uma expressão.

2. As restrições de validação de uma atividade não foram satisfeitas.

3. Há erros no arquivo XAML que fazem com que uma atividade a falha carregue.

4. Há erros no arquivo XAML que fazem com que o fluxo de trabalho a falha carregue.

As expressões inválidos e restrições insatisfeitas de validação não fazem com que o fluxo de trabalho a falha compile. A criação do fluxo de trabalho é realizada <xref:System.Activities.InvalidWorkflowException> com sucesso, mas um é lançado em tempo de execução. Se há erros no arquivo XAML, a compilação falhará.

Dentro do Visual Studio, quando um fluxo de trabalho é carregado, seus erros são exibidos no **lista de erros**. Para navegar até a atividade que é a origem do erro, clique duas vezes no erro na **lista de erros**.

### <a name="expression-errors"></a>Erros de expressão
 Uma expressão é inválido denotada por um círculo vermelho com um ponto de exclamação branco ao lado da expressão. Passa sobre este ícone exibe uma dica de ferramenta que descreve a fonte do erro. Dentro do Visual Studio, clique na expressão para exibir a linha que sublinha a origem do erro. Passa sobre o texto alinhado exibe uma dica de ferramenta que descreve a fonte do erro.

### <a name="activity-validation-errors"></a>Erros de validação de atividades
 Quando as restrições de validação de uma atividade não forem atendidas, um círculo vermelho com um ponto de exclamação branco aparece no canto superior direito da atividade. Passa sobre este ícone exibe uma dica de ferramenta que descreve a fonte do erro.

### <a name="xaml-load-errors"></a>Erros de carregamento XAML
 Quando uma atividade não é carregada, uma caixa vermelha com o texto "a atividade não pôde ser carregada devido a erros no XAML" é exibida. Isso normalmente ocorre quando o tipo da atividade não pode ser resolvido. A atividade inválido pode ser excluído no designer selecionando a caixa vermelha e excluindo a.

### <a name="workflow-load-errors"></a>Erros de carregamento de fluxo de trabalho
 Quando um fluxo de trabalho falha ao carregar, o texto "Designer de Fluxo de Trabalho encontrou problemas com seu documento" aparece na superfície do designer, juntamente com as informações de exceção que causaram a falha do fluxo de trabalho. Isso geralmente ocorre quando o arquivo XAML não pode ser analisado.