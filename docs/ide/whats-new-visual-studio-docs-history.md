---
title: 'Documentos do Visual Studio: histórico das novidades '
titleSuffix: ''
description: Histórico de novidades nos documentos do Visual Studio
ms.date: 09/30/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 511DAFC7-896E-449A-BFF7-0E8F7BBA8A78
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 6d0b60c548e4e5d42a10e82754d045073f016f8b
ms.sourcegitcommit: ea3c985a23851b424127f2205f617446b6536578
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91621744"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>Histórico de novidades nos documentos do Visual Studio

Bem-vindo ao histórico das novidades dos documentos do Visual Studio. Este tópico contém as principais alterações no docs antes de setembro de 2020 (a partir de 2020 de julho). Para obter as novidades mais recentes, consulte [Visual Studio docs: What ' s New in the docs](whats-new-visual-studio-docs.md).

## <a name="august-2020"></a>Agosto de 2020
### <a name="azure"></a>Azure

**Novos artigos**

- [Adicionar informações de aplicativo Azure usando os serviços conectados do Visual Studio](../azure/azure-app-insights-add-connected-service.md) – serviços conectados para VS 2019 16,7
- [Adicionar o cache do Azure para Redis usando os serviços conectados do Visual Studio](../azure/azure-cache-for-redis-add-connected-service.md) – serviços conectados para VS 2019 16,7
- [Adicionar Azure Cosmos DB ao seu aplicativo usando serviços conectados do Visual Studio](../azure/azure-cosmosdb-add-connected-service.md) -serviços conectados para VS 2019 16,7
- [Adicionar o Azure signalr usando serviços conectados do Visual Studio](../azure/azure-signalr-add-connected-service.md) -serviços conectados para VS 2019 16,7
- [Adicionar uma conexão com os serviços conectados ao banco de dados SQL do Azure](../azure/azure-sql-database-add-connected-service.md) para VS 2019 16,7

**Artigos atualizados**

- [Adicionando armazenamento do Azure usando os serviços conectados do Visual Studio](../azure/vs-azure-tools-connected-services-storage.md)
  - Serviços conectados para VS 2019 16,7
  - Artigo dos serviços conectados do armazenamento do Azure: atualizar interface do usuário e tipos de projeto com suporte

### <a name="code-quality"></a>Qualidade do código

**Novos artigos**

- [CA1310: especifique StringComparison para correção](../code-quality/ca1310.md) – adicione a documentação para CA1310 e atualize a documentação do CA1307
- [CA1837: Use Environment. ProcessId em vez de Process. GetCurrentProcess (). ID](../code-quality/ca1837.md) -docs para CA1837
- [CA1838: Evite `StringBuilder` parâmetros para P/Invokes](../code-quality/ca1838.md) -adicionar documentação para CA1838
- [CA2008: não crie tarefas sem passar por uma documentação TaskScheduler](../code-quality/ca2008.md) -Add para CA2008
- [CA2249: considere usar String. Contains em vez de String. IndexOf](../code-quality/ca2249.md) -docs para CA2249
- [CA2361: Certifique-se de que a classe gerada automaticamente contendo DataSet. ReadXml () não seja usada com dados não confiáveis](../code-quality/ca2361.md) -mais regras de DataSet/DataTable
- [CA2362: DataSet ou DataTable não seguro em tipo serializável gerado automaticamente pode ser vulnerável a ataques de execução remota de código](../code-quality/ca2362.md) -mais regras de conjunto de informações/DataTable
- [IL3000: Evite usar o caminho do arquivo de assembly de acesso ao publicar como uma](../code-quality/il3000.md) documentação de adição de arquivo único para IL3000
- [IL3001: Evite acessar o caminho do arquivo de assembly ao publicar como um arquivo único](../code-quality/il3001.md) – adicionar documentos para IL3001

**Updated**

- [CA1002: não expor listas genéricas](../code-quality/ca1002.md) – adicionar configurabilidade – seção superfície da API
- [CA1046: não sobrecarregar o operador Equals em tipos de referência](../code-quality/ca1046.md) -adicionar configurabilidade – seção superfície da API
- [CA1307: especifique StringComparison para fins de clareza](../code-quality/ca1307.md) -adicione documentação para CA1310 e atualize a documentação para CA1307
- [CA1700: não nomeie valores de enumeração &#39;reservado&#39;](../code-quality/ca1700.md) -adicionar a configurabilidade-seção superfície da API
- [CA1707: os identificadores não devem conter sublinhados](../code-quality/ca1707.md) -adicionar a configurabilidade-seção superfície da API
- [CA1822: marcar Membros como estático](../code-quality/ca1822.md) -adicionar configurabilidade – seção superfície da API
- [CA2351: Verifique se a entrada do conjunto de dados. ReadXml () é confiável](../code-quality/ca2351.md) -mais regras de conjunto de dados/DataTable
- [Instalar analisadores](../code-quality/install-roslyn-analyzers.md) de terceiros-estrutura e títulos alterados para a documentação de análise de código

### <a name="containers"></a>Contêineres

**Artigos atualizados**

- [Implantar um contêiner ASP.net em um registro de contêiner usando o Visual Studio](../containers/hosting-web-apps-in-docker.md) – atualizações das ferramentas de contêiner para a interface do usuário de publicação do visual Studio 16,7
- [Introdução ao Visual Studio kubernetes Tools](../containers/tutorial-kubernetes-tools.md) -kubernetes tutorial: adicionar etapas para remoção

### <a name="deployment"></a>Implantação

**Novos artigos**

- [Extensão de projetos de instalador do Visual Studio e .NET Core 3,1](../deployment/installer-projects-net-core.md) – criando uma nova página de ajuda para projetos do instalador recursos do .net Core 3,1

**Artigos atualizados**

- [Implantar seu aplicativo em uma pasta, IIS, Azure ou outra](../deployment/deploying-applications-services-and-components-resources.md) atualização de destino-implantação
- [Implantação no Visual Studio](../deployment/index.yml) – atualizações de implantação

### <a name="extensibility"></a>Extensibilidade

**Artigos atualizados**
- [Subtipos de projeto](../extensibility/internals/project-subtypes.md) – corrigir recuo de itens de lista
- [Referência de valor de cor para Visual Studio](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md) -AB # 1759333 corrigir cabeçalhos de coluna ausentes

### <a name="get-started"></a>Introdução

**Artigos atualizados**

- [Etapa 5: implantar o aplicativo ASP.NET Core no Azure](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md) -vídeo atualizações do tutorial para a nova interface do usuário dos serviços conectados

### <a name="ide"></a>IDE

**Novos artigos**

- [Alterar a tecla de ajuda F1 no Visual Studio](./not-in-toc/change-f1-help-key.md) -página de ajuda F1 padrão de refatoração
- [Ajuda F1 para a](./not-in-toc/default-f1-text-editor.md) página de ajuda do editor de texto – Refactor padrão F1
- [Converter `typeof` em `nameof` ](./reference/convert-typeof-to-nameof.md) – converter typeof em refatoração de nameof
- [Simplificar a expressão LINQ](./reference/simplify-linq-expression.md) -simplificar a refatoração de expressão LINQ

**Artigos atualizados**

- [Personalizar layouts de janela no Visual Studio](./customizing-window-layouts-in-visual-studio.md) – adicionar informações de guias de documento vertical com moniker ao tópico personalizar layouts de janela
- [Como relatar um problema com o Visual Studio para Mac ou com o Instalador do Visual Studio](./how-to-report-a-problem-with-visual-studio.md)
  - Adição de mais informações ao NMI
  - Redid a página inteira do problema do relatório
- [Ajuda F1](./not-in-toc/default.md) -página de ajuda F1 padrão de refatoração
- [Caixa de diálogo recuperação automática, ambiente, opções](./reference/autorecover-environment-options-dialog-box.md) – adicionar informações sobre locais de arquivo de salvamento automático atualizados
- [Opções, editor de texto, básico (Visual Basic),](./reference/options-text-editor-basic-visual-basic.md) documentação básica de adição avançada para dicas de nome de parâmetro embutido
- [Opções, editor de texto, C#,](./reference/options-text-editor-csharp-advanced.md) documentação básica de adição avançada para dicas de nome de parâmetro embutido
- [Dicas e truques de desempenho do Visual Studio](./visual-studio-performance-tips-and-tricks.md) – adicionar as informações de ' desabilitar modo de mapa ' e ' desabilitar quebra automática de palavra '
- [Novidades no visual studio 2019](./whats-new-visual-studio-2019.md) – atualizar o que há de novo no visual Studio 2019 com as informações do 16,7 GA

### <a name="rtvs"></a>RTVS

**Artigos atualizados**

- [Trabalhar com tabelas corrigidas SQL Server e R](../rtvs/integrating-sql-server-with-r.md) para incluir cabeçalhos de coluna

## <a name="july-2020"></a>Julho de 2020
### <a name="code-quality"></a>Qualidade do código

**Novos artigos**

- [CA1417: não use `OutAttribute` parâmetros de cadeia de caracteres para P/Invokes](../code-quality/ca1417.md) -adicionar documentação para CA1417
- [CA1805: não inicializar desnecessariamente.](../code-quality/ca1805.md) -Adicionar documentos para CA1805
- [CA1836: prefira IsEmpty ao longo da contagem quando disponível](../code-quality/ca1836.md) – adicione a documentação para CA1836 (prefira IsEmpty com contagem)
- [CA2016: encaminhe o parâmetro CancellationToken para métodos que usam um](../code-quality/ca2016.md) documento CA2016-encaminhar o parâmetro CancellationToken para métodos que usam um
- [CA2350: Verifique se a entrada de DataTable. ReadXml () é confiável](../code-quality/ca2350.md) – documentos de regras de desserialização de conjunto de dados/DataTable iniciais
- [CA2351: Verifique se a entrada do conjunto de dados. ReadXml () é confiável](../code-quality/ca2351.md) – documentos de regras de desserialização de conjunto de dados/DataTable iniciais
- [CA2352: DataSet ou DataTable não seguro em tipo serializável pode ser vulnerável a ataques de execução remota de código](../code-quality/ca2352.md) -documentos iniciais de regras de desserialização de conjunto de texto/DataTable
- [CA2353: DataSet ou DataTable não seguro no tipo serializável](../code-quality/ca2353.md) – documentos de regras de desserialização de conjunto de texto inicial/DataTable
- [CA2354: um DataSet não seguro ou DataTable no grafo de objeto desserializado pode ser vulnerável ao ataque de execução de código remoto](../code-quality/ca2354.md) -documentos de regras de desserialização de conjunto de usuários/DataTable iniciais
- [CA2355: DataSet não seguro ou DataTable no grafo de objeto desserializado](../code-quality/ca2355.md) -documentos de regras de desserialização de conjunto de tabelas/DataTable iniciais
- [CA2356: tipo de DataSet ou DataTable não seguro no grafo de objeto desserializado da Web](../code-quality/ca2356.md) -documentos de regras de desserialização de conjunto de texto/DataTable inicial

### <a name="containers"></a>Contêineres

**Novos artigos**

- [Configurar processo local com](../containers/configure-local-process-with-kubernetes.md) o processo kubernetes-local com kubernetes: configuração de YAML
- [Usar processo local com kubernetes (visualização)](../containers/local-process-kubernetes.md) – migração de espaços de desenvolvimento
- [Como o processo local com Kubernetes funciona](../containers/overview-local-process-kubernetes.md)
  - Processo local para kubernetes: Adicionar seção de roteamento
  - Migração de espaços de desenvolvimento

### <a name="cross-platform"></a>Plataforma cruzada

**Artigos atualizados**

- [Log de alterações (ferramentas do Visual Studio para Unity, Windows)](../cross-platform/change-log-visual-studio-tools-for-unity.md) -VSTU o changelog no 4.7.1.0
- [Log de alterações (ferramentas do Visual Studio para Unity, Mac)](../cross-platform/change-log-visual-studio-tools-for-unity-mac.md) -retapar o changelog VSTUM para 2.7.1.0

### <a name="get-started"></a>Introdução

**Novos artigos**

- [Tutorial: estender um aplicativo de console C# simples](../get-started/csharp/tutorial-console-part-2.md) – versão Extend calçada tutorial de primeira versão

### <a name="ide"></a>IDE

**Novos artigos**

- [Diretrizes da comunidade de desenvolvedores](./developer-community-guidelines.md) – diretrizes de DevCom adicionadas
- [Conclusão do IntelliSense para tipos não importados e métodos de extensão](./reference/intellisense-completion-unimported-types-extension-methods.md)

### <a name="install"></a>Instalar

**Novos artigos**

- [Atualizar o Visual Studio usando um mínimo de layout offline](../install/update-minimal-layout.md) – recurso de layout mínimo de documento
- [Guia do Visual Studio Enterprise](../install/visual-studio-enterprise-guide.md) – guia empresarial

### <a name="javascript"></a>JavaScript

**Novos artigos**

- [Compilar código typescript (Node.js)](../javascript/compile-typescript-code-npm.md) – compilação e compilação do typescript
- [Compilar código typescript (ASP.NET Core)](../javascript/compile-typescript-code-nuget.md) – compilação e compilação do typescript

### <a name="msbuild"></a>MSBuild

**Novos artigos**

- [Metadados de item MSBuild comuns](../msbuild/common-msbuild-item-metadata.md) -MSBuild: Adicionar tabela para metadados opcionais com link e LinkBase
- [Filtros de solução no MSBuild](../msbuild/solution-filters.md) – filtros de solução do MSBuild

### <a name="test"></a>Teste

**Novos artigos**

- [Depurar e analisar testes de unidade com o Test Explorer](../test/debug-unit-tests-with-test-explorer.md) -trabalho de desempenho do Test Explorer

**Artigos atualizados**

- [Configurar testes de unidade usando um arquivo *. RunSettings*](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
  - Atualizações para configurar testes de unidade usando um arquivo RunSettings
  - A descrição da opção de culpa foi alterada e o exemplo foi adicionado.