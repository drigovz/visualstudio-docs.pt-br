---
title: Mensagens de erro no Designer de Fluxo de Trabalho | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d89c0dcad23a91ec6057311b9afde7d6d4702772
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656765"
---
# <a name="error-messages-in-workflow-designer"></a>Mensagens de erro em Designer de Fluxo de Trabalho
Este tópico descreve os tipos de mensagens de erro que podem ser encontrados ao trabalhar com [!INCLUDE[wfd1](../includes/wfd1-md.md)].

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Situações em que os erros no criador de Fluxo de Trabalho ocorrem
 Erros em [!INCLUDE[wfd2](../includes/wfd2-md.md)] ocorrem nas seguintes situações:

1. Há um erro em uma expressão.

2. As restrições de validação de uma atividade não foram satisfeitas.

3. Há erros no arquivo XAML que fazem com que uma atividade a falha carregue.

4. Há erros no arquivo XAML que fazem com que o fluxo de trabalho a falha carregue.

   As expressões inválidos e restrições insatisfeitas de validação não fazem com que o fluxo de trabalho a falha compile. Compilar seu fluxo de trabalho é bem-sucedido, mas <xref:System.Activities.InvalidWorkflowException> é lançada pelo tempo de execução. Se há erros no arquivo XAML, a compilação falhará.

   Dentro de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], quando um fluxo de trabalho é carregado, seus erros são exibidos no **lista de erros**. Para navegar até a atividade que é a origem do erro, clique duas vezes no erro na **lista de erros**.

### <a name="expression-errors"></a>Erros de expressão
 Uma expressão é inválido denotada por um círculo vermelho com um ponto de exclamação branco ao lado da expressão. Passa sobre este ícone exibe uma dica de ferramenta que descreve a fonte do erro. Dentro de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], clique na expressão para exibir a linha que enfatiza a fonte do erro. Passa sobre o texto alinhado exibe uma dica de ferramenta que descreve a fonte do erro.

### <a name="activity-validation-errors"></a>Erros de validação de atividades
 Quando as restrições de validação de uma atividade não forem atendidas, um círculo vermelho com um ponto de exclamação branco aparece no canto superior direito da atividade. Passa sobre este ícone exibe uma dica de ferramenta que descreve a fonte do erro.

### <a name="xaml-load-errors"></a>Erros de carregamento XAML
 Quando uma atividade não carrega, uma caixa vermelha com o texto “atividade não pôde ser carregada devido a erros no XAML” aparece. Isso geralmente ocorre quando o tipo de atividade não pode ser resolvido. A atividade inválido pode ser excluído no designer selecionando a caixa vermelha e excluindo a.

### <a name="workflow-load-errors"></a>Erros de carregamento de fluxo de trabalho
 Quando um fluxo de trabalho não carrega, o texto “Designer de Fluxo de Trabalho após problemas com seu documento” aparece na superfície de designer, junto com as informações de exceção que causou a falha de fluxo de trabalho para carregar. Isso geralmente ocorre quando o arquivo XAML não pode ser analisado.