---
title: 'Documentos do Visual Studio: histórico das novidades '
titleSuffix: ''
description: Histórico de novidades nos documentos do Visual Studio
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
ms.openlocfilehash: 8505f98163c57fe276bcf4c76195fe843300394f
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809460"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>Histórico de novidades nos documentos do Visual Studio

Bem-vindo ao histórico das novidades dos documentos do Visual Studio. Este tópico contém as principais alterações no docs antes de agosto de 2020 (a partir de 2020 de julho). Para obter as novidades mais recentes, consulte [Visual Studio docs: What ' s New in the docs](whats-new-visual-studio-docs.md).

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