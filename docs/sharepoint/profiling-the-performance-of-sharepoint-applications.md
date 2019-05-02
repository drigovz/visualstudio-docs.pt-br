---
title: Perfil do desempenho de aplicativos do SharePoint | Microsoft Docs
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
ms.openlocfilehash: 8b59a3de88403300a46b7992a2dad72e3d6b59e0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62563303"
---
# <a name="profile-the-performance-of-sharepoint-applications"></a>Perfil do desempenho de aplicativos do SharePoint

Se seus aplicativos do SharePoint são desempenho lento ou ineficiente, você pode usar os recursos de criação de perfil no Visual Studio para identificar código problemático e outros elementos. Ao usar o recurso de teste de carga, você pode determinar como um aplicativo do SharePoint é executado sob estresse, como quando vários usuários acessam o aplicativo simultaneamente. Executando testes de desempenho na web, você pode medir como o aplicativo é executado na web. Usando testes de IU codificados, você pode verificar se o aplicativo do SharePoint inteiro, inclusive sua interface do usuário, funciona corretamente. Quando você usa esses testes juntos, eles podem ajudá-lo a identificar problemas de desempenho antes de implantar seu aplicativo.

## <a name="profile-tools-overview"></a>Visão geral das ferramentas de perfil

Criação de perfil é o processo de observar e registrar o comportamento de desempenho do seu aplicativo enquanto ele é executado. Ao perfilar seu aplicativo, você pode descobrir problemas como afunilamentos, código ineficiente e problemas de alocação de memória, o que fazer com que aplicativos sejam executados lentamente ou usar muita memória. Por exemplo, você pode usar a criação de perfil para identificar hotspots em seu código, que são segmentos de código frequentemente chamados e que podem reduzir o desempenho geral do seu aplicativo. Depois de identificar pontos de acesso, muitas vezes você pode otimizar ou eliminá-los.

Você pode usar várias ferramentas de criação de perfil no ambiente de desenvolvimento integrado (IDE) para identificar e localizar esses tipos de problemas de desempenho. Essas ferramentas funcionam da mesma maneira para projetos do SharePoint que funcionam para outros tipos de projetos do Visual Studio. O Assistente de desempenho das ferramentas de criação de perfil orienta você sobre a criação de uma sessão de desempenho que usa os testes que você especificar. Uma sessão de desempenho é um conjunto de dados de configuração que são usados para coletar informações de desempenho de um aplicativo, juntamente com os resultados de uma ou mais execuções de criação de perfil. Sessões de desempenho são armazenadas na pasta do projeto, e você pode exibi-los no **Performance Explorer**. Para obter mais informações, consulte [Noções Básicas sobre Métodos de Coleta de Desempenho](../profiling/understanding-performance-collection-methods.md).

Depois de criar e executar uma análise de perfil em seu aplicativo, um relatório fornece detalhes sobre o desempenho. Este relatório pode incluir itens, como um gráfico de uso da CPU ao longo do tempo, uma pilha de chamadas de função hierárquica ou uma árvore de chamadas. O conteúdo exato do relatório pode variar, dependendo do tipo de teste que são executados, como amostragem ou instrumentação. Para obter mais informações, consulte [visão geral do relatório de ferramentas de criação de perfil](http://go.microsoft.com/fwlink/?LinkId=224689).

## <a name="performance-session-process"></a>Processo de sessão de desempenho

Para criar o perfil de um aplicativo, você deve começar usando o Assistente de criação de perfil de desempenho de ferramentas para criar uma sessão de desempenho. Na barra de menus, escolha **Analyze**, **Launch Performance Wizard**. Ao concluir o assistente, você pode inserir as informações necessárias para sua sessão de desempenho, como o método de perfil que você deseja e o aplicativo que você deseja analisar. Para obter mais informações, confira [Como: Criar o perfil de um Site ou aplicativo Web usando o Assistente de desempenho](http://go.microsoft.com/fwlink/?LinkId=224692). Como alternativa, você pode usar opções de linha de comando para configurar e executar uma sessão de desempenho. Para obter mais informações, consulte [usando a criação de perfil de ferramentas da linha de comando](http://go.microsoft.com/fwlink/?LinkId=224703). Se você deseja configurar todos os aspectos de uma sessão de desempenho manualmente, consulte [como: Criar manualmente sessões de desempenho com as ferramentas de criação de perfil](http://go.microsoft.com/fwlink/?LinkId=224691). Você também pode criar uma sessão de desempenho de um teste de unidade, além de **Test Results** janela, abrindo o menu de atalho para o teste de unidade e, em seguida, escolhendo **criar sessão de desempenho**.

Depois de configurar uma sessão de desempenho, a configuração de sessão é salva, o servidor está configurado para fornecer dados de criação de perfil e o aplicativo é executado. Como você usa o aplicativo, os dados de desempenho são gravados em um arquivo de log. Sessões de desempenho são listadas na **Gerenciador de desempenho** sob o **destinos** pasta. Após a conclusão de uma sessão de desempenho, o relatório aparece na **relatórios** pasta nos **Performance Explorer**. Para exibir o relatório, abra-o na **Performance Explorer**. Para exibir ou configurar as propriedades de uma sessão de desempenho, abra o menu de atalho em **Gerenciador de desempenho**e, em seguida, escolha **propriedades**. Para obter mais informações sobre propriedades específicas de uma sessão de desempenho, consulte [Configurando sessões de desempenho para as ferramentas de criação de perfil](http://go.microsoft.com/fwlink/?LinkId=224694). Para obter informações sobre como interpretar os resultados de uma sessão de desempenho, consulte [analisando dados de ferramentas de criação de perfil](http://go.microsoft.com/fwlink/?LinkId=224704).

## <a name="stress-test"></a>Teste de estresse

Você pode analisar o desempenho de estresse de seus aplicativos com a criação de testes de carga e testes de desempenho web no Visual Studio. Quando você cria um teste de carga no Visual Studio, você pode especificar uma combinação de fatores, chamado de cenário, para testar seu aplicativo contra. Esses fatores incluem o padrão de carga, o modelo de combinação de testes, combinação de testes, combinação de redes e combinação de navegadores da web. Cenários de teste de carga podem incluir testes de unidade e testes de desempenho na web.

Figura 1: Exemplo de resultados de teste de carga

![Exibição de gráficos de teste de carga em execução](../sharepoint/media/load-webgraphs.png "exibição de gráficos de teste de carga em execução")

Testes de desempenho Web simulam como um usuário final pode interagir com um aplicativo do SharePoint. Você pode criar testes de desempenho web gravando solicitações HTTP em uma sessão de navegador ou usando o **gravador de teste de desempenho na Web**. As solicitações da web aparecem na **Editor de teste de desempenho na Web** depois que a sessão do navegador for concluída. Em seguida, você pode depurar os resultados na **Visualizador de resultados de teste de desempenho na Web**. Você também pode compilar manualmente testes de desempenho na web usando o **Editor de teste de desempenho na Web**.

## <a name="test-user-interfaces"></a>Interfaces de usuário de teste

Testes de IU codificados orientam automaticamente seu aplicativo do SharePoint por meio de sua interface do usuário (IU). Esses testes abrangem os controles de interface do usuário, como botões e menus, para verificar se eles funcionam corretamente. Esse tipo de teste é particularmente útil se a validação ou outra lógica é executada na interface do usuário, como em uma página da web. Você também pode usar testes de IU codificados para automatizar testes manuais. Você está criando testes de IU codificados para seus aplicativos do SharePoint da mesma forma como cria testes para outros tipos de aplicativos. Para obter mais informações, consulte [teste de aplicativos do SharePoint 2010 com testes de IU codificados](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md).

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Passo a passo: Perfil de um aplicativo do SharePoint](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Demonstra como executar uma análise de perfil de amostragem em um aplicativo do SharePoint.|
|[Realizar um teste de desempenho no aplicativo antes do lançamento](/azure/devops/test/load-test/run-performance-tests-app-before-release?view=vsts)|Descreve como criar testes de carga, que ajudam você a aplicativos de teste de estresse do SharePoint.|
|[Efetuar teste de unidade em seu código](../test/unit-test-your-code.md)|Descreve como localizar erros lógicos em seu código usando testes de unidade.|
|[Testando os aplicativos do SharePoint 2010 com testes de IU codificados](../test/testing-sharepoint-2010-applications-with-coded-ui-tests.md)|Descreve como testar a interface do usuário de seus aplicativos do SharePoint.|

## <a name="see-also"></a>Consulte também

- [Compilar e depurar soluções do SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Melhorar a qualidade do código](../test/improve-code-quality.md)