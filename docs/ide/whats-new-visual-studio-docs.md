---
title: 'Documentos do Visual Studio: novidades para agosto de 2020 '
titleSuffix: ''
description: O que há de novo nos documentos do Visual Studio de agosto de 2020.
ms.date: 09/02/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 89844796-621B-4EF5-9D76-197084B011CB
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 4364bd62ac19be958632b8cb2dbbe907013e8a70
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89402238"
---
# <a name="visual-studio-docs-whats-new-for-august-2020"></a>Documentos do Visual Studio: novidades para agosto de 2020

Bem-vindo ao que há de novo nos documentos do Visual Studio de agosto de 2020. Este artigo lista algumas das principais alterações feitas no docs durante esse período. Para obter informações sobre as novidades nos meses anteriores, consulte o tópico novidades sobre o [histórico](whats-new-visual-studio-docs-history.md) .

## <a name="azure"></a>Azure

**Novos artigos**

- [Adicionar informações de aplicativo Azure usando os serviços conectados do Visual Studio](/visualstudio/azure/azure-app-insights-add-connected-service) – serviços conectados para VS 2019 16,7
- [Adicionar o cache do Azure para Redis usando os serviços conectados do Visual Studio](/visualstudio/azure/azure-cache-for-redis-add-connected-service) – serviços conectados para VS 2019 16,7
- [Adicionar Azure Cosmos DB ao seu aplicativo usando serviços conectados do Visual Studio](/visualstudio/azure/azure-cosmosdb-add-connected-service) -serviços conectados para VS 2019 16,7
- [Adicionar o Azure signalr usando serviços conectados do Visual Studio](/visualstudio/azure/azure-signalr-add-connected-service) -serviços conectados para VS 2019 16,7
- [Adicionar uma conexão com os serviços conectados ao banco de dados SQL do Azure](/visualstudio/azure/azure-sql-database-add-connected-service) para VS 2019 16,7

**Artigos atualizados**

- [Adicionando armazenamento do Azure usando os serviços conectados do Visual Studio](/visualstudio/azure/vs-azure-tools-connected-services-storage)
  - Serviços conectados para VS 2019 16,7
  - Artigo dos serviços conectados do armazenamento do Azure: atualizar interface do usuário e tipos de projeto com suporte

## <a name="code-quality"></a>Qualidade do código

**Novos artigos**

- [CA1310: especifique StringComparison para correção](/visualstudio/code-quality/ca1310) – adicione a documentação para CA1310 e atualize a documentação do CA1307
- [CA1837: Use Environment. ProcessId em vez de Process. GetCurrentProcess (). ID](/visualstudio/code-quality/ca1837) -docs para CA1837
- [CA1838: Evite `StringBuilder` parâmetros para P/Invokes](/visualstudio/code-quality/ca1838) -adicionar documentação para CA1838
- [CA2008: não crie tarefas sem passar por uma documentação TaskScheduler](/visualstudio/code-quality/ca2008) -Add para CA2008
- [CA2249: considere usar String. Contains em vez de String. IndexOf](/visualstudio/code-quality/ca2249) -docs para CA2249
- [CA2361: Certifique-se de que a classe gerada automaticamente contendo DataSet. ReadXml () não seja usada com dados não confiáveis](/visualstudio/code-quality/ca2361) -mais regras de DataSet/DataTable
- [CA2362: DataSet ou DataTable não seguro em tipo serializável gerado automaticamente pode ser vulnerável a ataques de execução remota de código](/visualstudio/code-quality/ca2362) -mais regras de conjunto de informações/DataTable
- [IL3000: Evite usar o caminho do arquivo de assembly de acesso ao publicar como uma](/visualstudio/code-quality/il3000) documentação de adição de arquivo único para IL3000
- [IL3001: Evite acessar o caminho do arquivo de assembly ao publicar como um arquivo único](/visualstudio/code-quality/il3001) – adicionar documentos para IL3001

**Updated**

- [CA1002: não expor listas genéricas](/visualstudio/code-quality/ca1002) – adicionar configurabilidade – seção superfície da API
- [CA1046: não sobrecarregar o operador Equals em tipos de referência](/visualstudio/code-quality/ca1046) -adicionar configurabilidade – seção superfície da API
- [CA1307: especifique StringComparison para fins de clareza](/visualstudio/code-quality/ca1307) -adicione documentação para CA1310 e atualize a documentação para CA1307
- [CA1700: não nomeie valores de enumeração &#39;reservado&#39;](/visualstudio/code-quality/ca1700) -adicionar a configurabilidade-seção superfície da API
- [CA1707: os identificadores não devem conter sublinhados](/visualstudio/code-quality/ca1707) -adicionar a configurabilidade-seção superfície da API
- [CA1822: marcar Membros como estático](/visualstudio/code-quality/ca1822) -adicionar configurabilidade – seção superfície da API
- [CA2351: Verifique se a entrada do conjunto de dados. ReadXml () é confiável](/visualstudio/code-quality/ca2351) -mais regras de conjunto de dados/DataTable
- [Instalar analisadores](/visualstudio/code-quality/install-roslyn-analyzers) de terceiros-estrutura e títulos alterados para a documentação de análise de código

## <a name="containers"></a>Contêineres

**Artigos atualizados**

- [Implantar um contêiner ASP.net em um registro de contêiner usando o Visual Studio](/visualstudio/containers/hosting-web-apps-in-docker) – atualizações das ferramentas de contêiner para a interface do usuário de publicação do visual Studio 16,7
- [Introdução ao Visual Studio kubernetes Tools](/visualstudio/containers/tutorial-kubernetes-tools) -kubernetes tutorial: adicionar etapas para remoção

## <a name="deployment"></a>Implantação

**Novos artigos**

- [Extensão de projetos de instalador do Visual Studio e .NET Core 3,1](/visualstudio/deployment/installer-projects-net-core) – criando uma nova página de ajuda para projetos do instalador recursos do .net Core 3,1

**Artigos atualizados**

- [Implantar seu aplicativo em uma pasta, IIS, Azure ou outra](/visualstudio/deployment/deploying-applications-services-and-components-resources) atualização de destino-implantação
- [Implantação no Visual Studio](/visualstudio/deployment/index) – atualizações de implantação

## <a name="extensibility"></a>Extensibilidade

**Artigos atualizados**
- [Subtipos de projeto](/visualstudio/extensibility/internals/project-subtypes) – corrigir recuo de itens de lista
- [Referência de valor de cor para Visual Studio](/visualstudio/extensibility/ux-guidelines/color-value-reference-for-visual-studio) -AB # 1759333 corrigir cabeçalhos de coluna ausentes

## <a name="get-started"></a>Introdução

**Artigos atualizados**

- [Etapa 5: implantar o aplicativo ASP.NET Core no Azure](/visualstudio/get-started/csharp/tutorial-aspnet-core-ef-step-05) -vídeo atualizações do tutorial para a nova interface do usuário dos serviços conectados

## <a name="ide"></a>IDE

**Novos artigos**

- [Alterar a tecla de ajuda F1 no Visual Studio](/visualstudio/ide/not-in-toc/change-f1-help-key) -página de ajuda F1 padrão de refatoração
- [Ajuda F1 para a](/visualstudio/ide/not-in-toc/default-f1-text-editor) página de ajuda do editor de texto – Refactor padrão F1
- [Converter `typeof` em `nameof` ](/visualstudio/ide/reference/convert-typeof-to-nameof) – converter typeof em refatoração de nameof
- [Simplificar a expressão LINQ](/visualstudio/ide/reference/simplify-linq-expression) -simplificar a refatoração de expressão LINQ

**Artigos atualizados**

- [Personalizar layouts de janela no Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio) – adicionar informações de guias de documento vertical com moniker ao tópico personalizar layouts de janela
- [Como relatar um problema com o Visual Studio para Mac ou com o Instalador do Visual Studio](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)
  - Adição de mais informações ao NMI
  - Redid a página inteira do problema do relatório
- [Ajuda F1](/visualstudio/ide/not-in-toc/default) -página de ajuda F1 padrão de refatoração
- [Caixa de diálogo recuperação automática, ambiente, opções](/visualstudio/ide/reference/autorecover-environment-options-dialog-box) – adicionar informações sobre locais de arquivo de salvamento automático atualizados
- [Opções, editor de texto, básico (Visual Basic),](/visualstudio/ide/reference/options-text-editor-basic-visual-basic) documentação básica de adição avançada para dicas de nome de parâmetro embutido
- [Opções, editor de texto, C#,](/visualstudio/ide/reference/options-text-editor-csharp-advanced) documentação básica de adição avançada para dicas de nome de parâmetro embutido
- [Dicas e truques de desempenho do Visual Studio](/visualstudio/ide/visual-studio-performance-tips-and-tricks) – adicionar as informações de ' desabilitar modo de mapa ' e ' desabilitar quebra automática de palavra '
- [Novidades no visual studio 2019](/visualstudio/ide/whats-new-visual-studio-2019) – atualizar o que há de novo no visual Studio 2019 com as informações do 16,7 GA

## <a name="rtvs"></a>RTVS

**Artigos atualizados**

- [Trabalhar com tabelas corrigidas SQL Server e R](/visualstudio/rtvs/integrating-sql-server-with-r) para incluir cabeçalhos de coluna

## <a name="community-contributors"></a>Colaboradores da Comunidade

As pessoas a seguir contribuíram para os documentos do Visual Studio durante esse período. Obrigado! Saiba como contribuir com os documentos do Visual Studio seguindo as orientações no guia do [colaborador](https://docs.microsoft.com/contribute/).

- [AlexB-SheldonMFG](https://github.com/AlexB-SheldonMFG) -Alex preto (11)
- [Youssef1313](https://github.com/Youssef1313) -Youssef Victor (8)
- [hyoshioka0128](https://github.com/hyoshioka0128) -Hiroshi Yoshioka (3)
- [AstroChoco](https://github.com/AstroChoco) -Qian Lu (chocolate) (1)
- [athyunnath](https://github.com/athyunnath) -athyunnath Eleti (1)
- [caro-Oviedo](https://github.com/caro-oviedo) -caro Oviedo (1)
- [Evangelink](https://github.com/Evangelink) -Amaury levé (1)
- [jethas-bennettjones](https://github.com/jethas-bennettjones) -Shafiq Jetha (1)
- [nebuk89](https://github.com/nebuk89) -Ben de St Paer-Gotch (1)
- [pcartwright81](https://github.com/pcartwright81) (1)
- [pkulikov](https://github.com/pkulikov) -Petr Kulikov (1)
- [riQQ](https://github.com/riQQ) (1)
- [tcmetzger](https://github.com/tcmetzger) -Timo Cornelius Metzger (1)
- [Weitzhandler](https://github.com/weitzhandler) -shimmy (1)