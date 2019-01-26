---
title: Mensagens de erro em Designer de Fluxo de Trabalho
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: a9d5604994476c4f87305d1a9495944809eb8b5f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54998606"
---
# <a name="error-messages-in-workflow-designer"></a>Mensagens de erro em Designer de Fluxo de Trabalho

Este tópico descreve os tipos de mensagens de erro que podem ser encontrados ao trabalhar com o Designer de fluxo de trabalho.

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Situações em que os erros no criador de Fluxo de Trabalho ocorrem

Erros no Designer de fluxo de trabalho ocorrem nas seguintes situações:

1.  Há um erro em uma expressão.

2.  As restrições de validação de uma atividade não foram satisfeitas.

3.  Há erros no arquivo XAML que fazem com que uma atividade a falha carregue.

4.  Há erros no arquivo XAML que fazem com que o fluxo de trabalho a falha carregue.

As expressões inválidos e restrições insatisfeitas de validação não fazem com que o fluxo de trabalho a falha compile. Compilar seu fluxo de trabalho é bem-sucedido, mas <xref:System.Activities.InvalidWorkflowException> é lançada pelo tempo de execução. Se há erros no arquivo XAML, a compilação falhará.

Dentro do Visual Studio, quando um fluxo de trabalho é carregado, os erros são exibidos na **Error List**. Para navegar até a atividade que é a origem do erro, clique duas vezes no erro na **Error List**.

### <a name="expression-errors"></a>Erros de expressão
 Uma expressão é inválido denotada por um círculo vermelho com um ponto de exclamação branco ao lado da expressão. Passa sobre este ícone exibe uma dica de ferramenta que descreve a fonte do erro. Dentro do Visual Studio, clique na expressão para exibir a linha que enfatiza a origem do erro. Passa sobre o texto alinhado exibe uma dica de ferramenta que descreve a fonte do erro.

### <a name="activity-validation-errors"></a>Erros de validação de atividades
 Quando as restrições de validação de uma atividade não forem atendidas, um círculo vermelho com um ponto de exclamação branco aparece no canto superior direito da atividade. Passa sobre este ícone exibe uma dica de ferramenta que descreve a fonte do erro.

### <a name="xaml-load-errors"></a>Erros de carregamento XAML
 Quando uma atividade não carrega, aparece uma caixa vermelha com o texto "atividade não pôde ser carregada devido a erros no XAML". Isso normalmente ocorre quando o tipo de atividade não puder ser resolvido. A atividade inválido pode ser excluído no designer selecionando a caixa vermelha e excluindo a.

### <a name="workflow-load-errors"></a>Erros de carregamento de fluxo de trabalho
 Quando um fluxo de trabalho não for carregado, o texto "Problemas com seu documento de Designer de fluxo de trabalho encontrado" aparece na superfície do designer, junto com as informações de exceção que causou a falha do fluxo de trabalho carregar. Isso geralmente ocorre quando o arquivo XAML não pode ser analisado.