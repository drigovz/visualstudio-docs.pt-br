---
title: Usando regras de desempenho para analisar dados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3ea0f43b63eb8ec51ad7e8240844a804259374a8
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659336"
---
# <a name="use-performance-rules-to-analyze-data"></a>Usar regras de desempenho para analisar dados
Os avisos de desempenho das Ferramentas de Criação de Perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] indicam problemas em um aplicativo analisado que podem causar lentidão na execução do programa. Os avisos também podem indicar que talvez seja necessário alterar os métodos de coleta para coletar dados mais úteis. Avisos de desempenho são gerados automaticamente em uma sessão de criação de perfil. Os avisos são exibidos na janela **Lista de Erros** quando um arquivo de dados de criação de perfil está aberto no Visual Studio. Na janela **Lista de Erros**, é possível localizar o código-fonte do problema e exibir informações detalhadas sobre o erro, por exemplo, como resolvê-lo. Também é possível desabilitar avisos nos quais você não está interessado.

> [!NOTE]
> Os avisos de desempenho do criador de perfil são gerados pela análise dinâmica da execução do programa e são independentes dos avisos de Análise de Código. A Análise de Código também pode gerar avisos de desempenho para código gerenciado com base na análise estática do código-fonte. Para obter mais informações, confira [Analyze managed code quality](../code-quality/code-analysis-for-managed-code-overview.md) (Analisar a qualidade do código gerenciado) e [Performance warnings](/dotnet/fundamentals/code-analysis/quality-rules/performance-warnings) (Avisos de desempenho).

## <a name="in-this-section"></a>Nesta seção
- [Como exibir avisos de desempenho](../profiling/how-to-view-performance-warnings.md)

 Fornece informações sobre como abrir a janela **Lista de Erros** para exibir avisos de desempenho do criador de perfil.

- [Como: configurar regras de desempenho](../profiling/how-to-configure-performance-rules.md)

 Fornece informações sobre como ativar ou desativar avisos de desempenho individuais.

- [Referência de regras de desempenho](../profiling/performance-rules-reference.md)

 Fornece informações detalhadas sobre os avisos de desempenho do criador de perfil
