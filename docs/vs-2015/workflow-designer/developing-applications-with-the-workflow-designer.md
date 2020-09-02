---
title: Desenvolvendo aplicativos com o Designer de Fluxo de Trabalho | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- DefaultWorkflowDesigner
- DefaultWorkflowDesigner.UI
helpviewer_keywords:
- Visual Studio 2010 Workflow Designer [WFD], overview
- Workflow Designer [WFD]
- Visual Studio 2010 Workflow Designer [WFD]
- Workflow Designer [WFD], overview
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 848300c54800e229ee1f487fc415bad45d982a6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656821"
---
# <a name="developing-applications-with-the-workflow-designer"></a>Desenvolvendo aplicativos com designers de Fluxo de Trabalho
ph x="1" /&gt; é um designer e um depurador visuais para a compilação e gráficos a depuração de aplicativos de [!INCLUDE[wf](../includes/wf-md.md)] em [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] que está hospedada no ambiente de desenvolvimento de [!INCLUDE[vs2010](../includes/vs2010-md.md)] . Permite que você escreve um aplicativo de fluxo de trabalho, uma biblioteca de atividade, ou um serviço composto de [!INCLUDE[indigo1](../includes/indigo1-md.md)] com o uso de modelos e os designers de atividade. [!INCLUDE[crabout](../includes/crabout-md.md)] fluxos de trabalho, consulte o [Windows Workflow Foundation &#91; .NET Framework 4&#93;](https://msdn.microsoft.com/library/9a23ea6b-d600-483e-89cd-8889cfec5f66).

 Os seguintes são vários novos recursos de design esse conjunto essa nova versão de [!INCLUDE[wfd2](../includes/wfd2-md.md)] independentemente das versões anteriores de [!INCLUDE[wfd2](../includes/wfd2-md.md)]:

- [!INCLUDE[wfd2](../includes/wfd2-md.md)] é compilado usando [!INCLUDE[avalon1](../includes/avalon1-md.md)]. Isso melhora a experiência do designer de atividade e melhora o desempenho para grandes e fluxos de trabalho complexos.

- As atividades personalizados são criadas agora com [!INCLUDE[avalon2](../includes/avalon2-md.md)], usando XAML e o modelo de programação para criar designer de atividade foi simplificado.

- Uma atividade do fluxograma era implementado, então você pode visualizar o fluxo de programa usando o fluxograma familiar que modela o estilo.

- [!INCLUDE[wfd2](../includes/wfd2-md.md)] tem um novo designer variável que permite que você declare e defina o escopo variáveis em seus fluxos de trabalho, associando os às atividades.

- Em [!INCLUDE[vs2010](../includes/vs2010-md.md)], [!INCLUDE[wfd2](../includes/wfd2-md.md)] fornece recursos do IntelliSense para criar expressões do Visual Basic dentro dos fluxos de trabalho [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] .

- A experiência de depuração estende agora em XAML, permitindo que você defina pontos de interrupção na definição de fluxo de trabalho XAML e entrar no seu código XAML em runtime, que fornece uma experiência semelhante ao código gerenciado.

- Rehosting [!INCLUDE[wfd2](../includes/wfd2-md.md)] fora de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] é simplificado extremamente em comparação com versões anteriores, que requer agora apenas algumas linhas de código.

- A nova <xref:System.Activities.Statements.Flowchart> atividade e seu [fluxograma](../workflow-designer/flowchart-activity-designer.md) permitem visualizar o fluxo do seu programa usando o estilo de modelagem de fluxograma familiar.

- As atividades de mensagem foram aprimoradas, permitindo que você escreva (nenhum código declarativo completa) serviços de [!INCLUDE[indigo1](../includes/indigo1-md.md)] .

- O **Adicionar referência de serviço...** a funcionalidade permite gerar atividades automaticamente que acessam os serviços Web.

## <a name="in-this-section"></a>Nesta seção
 [Usando o designer de fluxo de trabalho](../workflow-designer/using-the-workflow-designer.md) Mostra como criar novas atividades e projetos de fluxo de trabalho usando os designers internos e como usar outras ferramentas fornecidas pelo designer para manipular argumentos, variáveis, expressões, importações e navegação por trilha.

 [Usando os designers de atividade](../workflow-designer/using-the-activity-designers.md) Descreve as categorias de atividades e modelos e seus designers fornecidos pelo sistema.

 [Depurando fluxos de trabalho com o designer de fluxo de trabalho](../workflow-designer/debugging-workflows-with-the-workflow-designer.md) Descreva como executar procedimentos de depuração tradicionais, bem como depuração XAML e expressões.

 [Ajuda da interface do usuário designer de fluxo de trabalho](../workflow-designer/workflow-designer-ui-help.md) Contém tópicos de ajuda sensíveis ao contexto para caixas de diálogo fornecidas pelo [!INCLUDE[wfd1](../includes/wfd1-md.md)] , bem como orientações sobre recursos do Shell de designer, atalhos de teclado e mensagens de erro.

 [Desenvolvendo aplicativos de fluxo de trabalho direcionados à estrutura .net 3,0 ou .net 3,5](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md) Contém orientações sobre como usar o designer herdado que tem como alvo o [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 [Hospedagem do Designer &#91;amostras do WF&#93;](https://msdn.microsoft.com/library/b676ad31-5f64-4d84-9a36-b4d7113a2f4d) Este exemplo mostra como criar o layout do WPF para conter o designer.

 [Designers de atividades personalizadas](https://msdn.microsoft.com/library/dcf14dca-ce6d-4278-96ba-062f0a679075) Esta seção contém exemplos de atividade que usam designers personalizados para exibição no designer de fluxo de trabalho.