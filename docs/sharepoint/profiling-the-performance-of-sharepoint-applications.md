---
title: Criação de perfil do desempenho de aplicativos do SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Profiling.SilverlightWebPartOnly
- VS.SharePointTools.Profiling.DotNetTrustLevel
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 72739cd1063298a2dafc71976fd45360bc2d6ec2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "73189210"
---
# <a name="profile-the-performance-of-sharepoint-applications"></a>Criar perfil do desempenho de aplicativos do SharePoint

Se seus aplicativos do SharePoint estiverem com lentidão ou ineficiente, você poderá usar os recursos de criação de perfil no Visual Studio para identificar o código problemático e outros elementos. Usando o recurso de teste de carga, você pode determinar como um aplicativo do SharePoint é executado sob estresse, como quando muitos usuários acessam o aplicativo simultaneamente. Ao executar testes de desempenho da Web, você pode medir como o aplicativo é executado na Web. Usando testes de IU codificados, você pode verificar se todo o aplicativo do SharePoint, incluindo sua interface do usuário, funciona corretamente. Quando você usa esses testes juntos, eles podem ajudá-lo a identificar problemas de desempenho antes de implantar seu aplicativo.

## <a name="profile-tools-overview"></a>Visão geral das ferramentas de perfil

A criação de perfil refere-se ao processo de observar e registrar o comportamento de desempenho do seu aplicativo à medida que ele é executado. Por meio da criação de perfil de seu aplicativo, você pode descobrir problemas como afunilamentos, código ineficiente e problemas de alocação de memória, o que faz com que os aplicativos sejam executados lentamente ou usem muita memória. Por exemplo, você pode usar a criação de perfil para identificar pontos de HotSpot em seu código, que são segmentos de código que são chamados com frequência e podem retardar o desempenho geral do seu aplicativo. Depois de identificar pontos de hotspot, muitas vezes você pode otimizá-los ou eliminá-los.

Você pode usar várias ferramentas de criação de perfil no ambiente de desenvolvimento integrado (IDE) para identificar e localizar esses tipos de problemas de desempenho. Essas ferramentas funcionam da mesma maneira para projetos do SharePoint como as fazem para outros tipos de projetos do Visual Studio. O assistente de desempenho de Ferramentas de Criação de Perfil orienta você pela criação de uma sessão de desempenho que usa os testes que você especificar. Uma sessão de desempenho é um conjunto de dados de configuração que é usado para coletar informações de desempenho de um aplicativo, juntamente com os resultados de uma ou mais execuções de criação de perfil. As sessões de desempenho são armazenadas na pasta do projeto e você pode exibi-las em **Gerenciador de desempenho**. Para obter mais informações, consulte [Noções Básicas sobre Métodos de Coleta de Desempenho](../profiling/understanding-performance-collection-methods.md).

Depois de criar e executar uma análise de perfil em seu aplicativo, um relatório fornece detalhes sobre seu desempenho. Este relatório pode incluir itens como um grafo de uso da CPU ao longo do tempo, uma pilha de chamadas de função hierárquica ou uma árvore de chamada. O conteúdo exato do relatório pode variar, dependendo do tipo de teste que você executa, como amostragem ou instrumentação. Para obter mais informações, consulte [visão geral do relatório de ferramentas de criação de perfil](../profiling/performance-report-overview.md).

## <a name="performance-session-process"></a>Processo de sessão de desempenho

Para criar o perfil de um aplicativo, você começa usando o assistente de desempenho de Ferramentas de Criação de Perfil para a criação de uma sessão de desempenho. Na barra de menus, escolha **analisar**, **iniciar o assistente de desempenho**. Ao concluir o assistente, você insere as informações necessárias para sua sessão de desempenho, como o método de perfil que você deseja e o aplicativo para o qual deseja criar o perfil. Para obter mais informações, consulte [como criar o perfil de um site ou aplicativo Web usando o assistente de desempenho](../profiling/how-to-collect-performance-data-for-a-web-site.md). Como alternativa, você pode usar opções de linha de comando para configurar e executar uma sessão de desempenho. Para obter mais informações, consulte [usando o ferramentas de criação de perfil da linha de comando](../profiling/using-the-profiling-tools-from-the-command-line.md). Se você quiser configurar todos os aspectos de uma sessão de desempenho manualmente, consulte [como criar manualmente sessões de desempenho com o ferramentas de criação de perfil](../profiling/how-to-manually-create-performance-sessions.md). Você também pode criar uma sessão de desempenho de um teste de unidade pelo, na janela **resultados de teste** , abrindo o menu de atalho para o teste de unidade e escolhendo **criar sessão de desempenho**.

Depois de configurar uma sessão de desempenho, a configuração da sessão é salva, o servidor é configurado para fornecer dados de criação de perfil e o aplicativo é executado. Conforme você usa o aplicativo, os dados de desempenho são gravados em um arquivo de log. As sessões de desempenho são listadas em **Gerenciador de desempenho** na pasta **destinos** . Após a conclusão de uma sessão de desempenho, seu relatório aparecerá na pasta **relatórios** em **Gerenciador de desempenho**. Para exibir o relatório, abra-o no **Gerenciador de desempenho**. Para exibir ou configurar as propriedades de uma sessão de desempenho, abra o menu de atalho no **Gerenciador de desempenho**e escolha **Propriedades**. Para obter mais informações sobre propriedades específicas de uma sessão de desempenho, consulte [Configuring performance Sessions for ferramentas de criação de perfil](../profiling/configuring-performance-sessions.md). Para obter informações sobre como interpretar os resultados de uma sessão de desempenho, consulte [analisando ferramentas de criação de perfil dados](../profiling/analyzing-performance-tools-data.md).

## <a name="stress-test"></a>Teste de estresse

Você pode analisar o desempenho de estresse de seus aplicativos criando testes de carga e testes de desempenho na Web no Visual Studio. Ao criar um teste de carga no Visual Studio, você especifica uma combinação de fatores, chamada de cenário, para testar seu aplicativo. Esses fatores incluem o padrão de carga, o modelo de combinação de teste, a combinação de teste, a combinação de rede e o navegador da Web Mix. Os cenários de teste de carga podem incluir testes de unidade e testes de desempenho na Web.

Figura 1: exemplo de resultados de testes de carga

![Executando a exibição de gráficos de teste de carga](../sharepoint/media/load-webgraphs.png "Executando a exibição de gráficos de teste de carga")

Testes de desempenho na Web simulam como um usuário final pode interagir com um aplicativo do SharePoint. Você pode criar testes de desempenho na Web gravando solicitações HTTP em uma sessão de navegador ou usando o **gravador de teste de desempenho da Web**. As solicitações da Web aparecem no **Editor de testes de desempenho Web** depois que a sessão do navegador é concluída. Em seguida, você pode depurar os resultados no **Visualizador de resultados de teste de desempenho da Web**. Você também pode criar manualmente testes de desempenho da Web usando o **Editor de testes de desempenho Web**.

## <a name="test-user-interfaces"></a>Testar interfaces do usuário

Testes de IU codificados direcionam automaticamente seu aplicativo do SharePoint por meio de sua interface do usuário. Esses testes abordam os controles da interface do usuário, como botões e menus, para verificar se eles funcionam corretamente. Esse tipo de teste é particularmente útil se a validação ou outra lógica for executada na interface do usuário, como em uma página da Web. Você também pode usar testes de interface do usuário codificados para automatizar testes manuais. Você cria testes de interface do usuário codificados para seus aplicativos do SharePoint da mesma maneira que cria testes para outros tipos de aplicativos. Para obter mais informações, consulte [testando aplicativos do SharePoint 2010 com testes de interface do usuário codificados](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests?view=vs-2015).

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Walkthrough: criar perfil de um aplicativo do SharePoint](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Demonstra como executar uma análise de perfil de amostragem em um aplicativo do SharePoint.|
|[Realizar um teste de desempenho no aplicativo antes do lançamento](/azure/devops/test/load-test/run-performance-tests-app-before-release?view=vsts)|Descreve como criar testes de carga, que ajudam você a enfatizar aplicativos do SharePoint de teste.|
|[Teste de unidade de código](../test/unit-test-your-code.md)|Descreve como encontrar erros lógicos em seu código usando testes de unidade.|
|[Testando aplicativos do SharePoint 2010 com testes de IU codificados](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests?view=vs-2015)|Descreve como testar a interface do usuário de seus aplicativos do SharePoint.|

## <a name="see-also"></a>Confira também

- [Compilar e depurar soluções do SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Melhorar a qualidade do código](../test/improve-code-quality.md)