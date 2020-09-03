---
title: 'Documentos do Visual Studio: histórico das novidades '
titleSuffix: ''
description: Histórico das novidades do Visual Studio docs
ms.date: 09/01/2020
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
ms.openlocfilehash: 9f5fc25f6bb25c9471b1de1d464fa6afc4c80b3b
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89410500"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>Histórico das novidades do Visual Studio docs

Bem-vindo ao histórico das novidades dos documentos do Visual Studio. Este tópico contém as principais alterações no docs antes de agosto de 2020 (a partir de 2020 de julho). Para obter as novidades mais recentes, consulte [Visual Studio docs: What ' s New in the docs](whats-new-visual-studio-docs.md).

## <a name="july-2020"></a>Julho de 2020
### <a name="code-quality"></a>Qualidade do código

**Novos artigos**

- [CA1417: não use `OutAttribute` parâmetros de cadeia de caracteres para P/Invokes](/visualstudio/code-quality/ca1417) -adicionar documentação para CA1417
- [CA1805: não inicializar desnecessariamente.](/visualstudio/code-quality/ca1805) -Adicionar documentos para CA1805
- [CA1836: prefira IsEmpty ao longo da contagem quando disponível](/visualstudio/code-quality/ca1836) – adicione a documentação para CA1836 (prefira IsEmpty com contagem)
- [CA2016: encaminhe o parâmetro CancellationToken para métodos que usam um](/visualstudio/code-quality/ca2016) documento CA2016-encaminhar o parâmetro CancellationToken para métodos que usam um
- [CA2350: Verifique se a entrada de DataTable. ReadXml () é confiável](/visualstudio/code-quality/ca2350) – documentos de regras de desserialização de conjunto de dados/DataTable iniciais
- [CA2351: Verifique se a entrada do conjunto de dados. ReadXml () é confiável](/visualstudio/code-quality/ca2351) – documentos de regras de desserialização de conjunto de dados/DataTable iniciais
- [CA2352: DataSet ou DataTable não seguro em tipo serializável pode ser vulnerável a ataques de execução remota de código](/visualstudio/code-quality/ca2352) -documentos iniciais de regras de desserialização de conjunto de texto/DataTable
- [CA2353: DataSet ou DataTable não seguro no tipo serializável](/visualstudio/code-quality/ca2353) – documentos de regras de desserialização de conjunto de texto inicial/DataTable
- [CA2354: um DataSet não seguro ou DataTable no grafo de objeto desserializado pode ser vulnerável ao ataque de execução de código remoto](/visualstudio/code-quality/ca2354) -documentos de regras de desserialização de conjunto de usuários/DataTable iniciais
- [CA2355: DataSet não seguro ou DataTable no grafo de objeto desserializado](/visualstudio/code-quality/ca2355) -documentos de regras de desserialização de conjunto de tabelas/DataTable iniciais
- [CA2356: tipo de DataSet ou DataTable não seguro no grafo de objeto desserializado da Web](/visualstudio/code-quality/ca2356) -documentos de regras de desserialização de conjunto de texto/DataTable inicial

### <a name="containers"></a>Contêineres

**Novos artigos**

- [Configurar processo local com](/visualstudio/containers/configure-local-process-with-kubernetes) o processo kubernetes-local com kubernetes: configuração de YAML
- [Usar processo local com kubernetes (visualização)](/visualstudio/containers/local-process-kubernetes) – migração de espaços de desenvolvimento
- [Como o processo local com Kubernetes funciona](/visualstudio/containers/overview-local-process-kubernetes)
  - Processo local para kubernetes: Adicionar seção de roteamento
  - Migração de espaços de desenvolvimento

### <a name="cross-platform"></a>Plataforma cruzada

**Artigos atualizados**

- [Log de alterações (ferramentas do Visual Studio para Unity, Windows)](/visualstudio/cross-platform/change-log-visual-studio-tools-for-unity) -VSTU o changelog no 4.7.1.0
- [Log de alterações (ferramentas do Visual Studio para Unity, Mac)](/visualstudio/cross-platform/change-log-visual-studio-tools-for-unity-mac) -retapar o changelog VSTUM para 2.7.1.0

### <a name="get-started"></a>Introdução

**Novos artigos**

- [Tutorial: estender um aplicativo de console C# simples](/visualstudio/get-started/csharp/tutorial-console-part-2) – versão Extend calçada tutorial de primeira versão

### <a name="ide"></a>IDE

**Novos artigos**

- [Diretrizes da comunidade de desenvolvedores](/visualstudio/ide/developer-community-guidelines) – diretrizes de DevCom adicionadas
- [Conclusão do IntelliSense para tipos não importados e métodos de extensão](/visualstudio/ide/reference/intellisense-completion-unimported-types-extension-methods)

### <a name="install"></a>Instalar

**Novos artigos**

- [Atualizar o Visual Studio usando um mínimo de layout offline](/visualstudio/install/update-minimal-layout) – recurso de layout mínimo de documento
- [Guia do Visual Studio Enterprise](/visualstudio/install/visual-studio-enterprise-guide) – guia empresarial

### <a name="javascript"></a>JavaScript

**Novos artigos**

- [Compilar código typescript (Node.js)](/visualstudio/javascript/compile-typescript-code-npm) – compilação e compilação do typescript
- [Compilar código typescript (ASP.NET Core)](/visualstudio/javascript/compile-typescript-code-nuget) – compilação e compilação do typescript

### <a name="msbuild"></a>MSBuild

**Novos artigos**

- [Metadados de item MSBuild comuns](/visualstudio/msbuild/common-msbuild-item-metadata) -MSBuild: Adicionar tabela para metadados opcionais com link e LinkBase
- [Filtros de solução no MSBuild](/visualstudio/msbuild/solution-filters) – filtros de solução do MSBuild

### <a name="test"></a>Teste

**Novos artigos**

- [Depurar e analisar testes de unidade com o Test Explorer](/visualstudio/test/debug-unit-tests-with-test-explorer) -trabalho de desempenho do Test Explorer

**Artigos atualizados**

- [Configurar testes de unidade usando um arquivo *. RunSettings*](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - Atualizações para configurar testes de unidade usando um arquivo RunSettings
  - A descrição da opção de culpa foi alterada e o exemplo foi adicionado.