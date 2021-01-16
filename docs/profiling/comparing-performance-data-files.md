---
title: Comparando arquivos de dados de desempenho | Microsoft Docs
description: Use Ferramentas de Criação de Perfil para comparar dois arquivos de relatório (. vsp ou. vsps). A comparação mostra diferenças, regressões de desempenho e melhorias.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8d1c57c6c3dd8d7d01e37eae374c547e074d62e6
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533492"
---
# <a name="compare-performance-data-files"></a>Comparar arquivos de dados de desempenho

Ferramentas de Criação de Perfil funcionalidade de comparação de arquivos de dados permite que você selecione dois arquivos de relatório (.*VSP* ou. *vsps*) arquivos e gerar um relatório que mostra as diferenças, as regressões de desempenho e os aprimoramentos que ocorreram de uma sessão de criação de perfil para a outra.

Um relatório de comparação de arquivos de dados de Ferramentas de Criação de Perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] compara os resultados de uma análise em um arquivo de dados de criação de perfil com os resultados de uma análise de linha de base em outro arquivo de dados. Os dois arquivos de dados devem ter sido gerados usando o mesmo método de criação de perfil. O relatório das comparações analisadas é salvo como um. arquivo *vsps* .

O modo de exibição do relatório de comparação apresenta uma exibição de tabela dos dados alterados. A tabela apresenta o delta ou a alteração da linha de base. O delta é calculado determinando a diferença entre o valor antigo, o valor de linha de base e o valor do resultado da nova análise.

As comparações de dados do criador de perfil podem ser baseadas nas funções no código, nos módulos no aplicativo, nas linhas, nos IPs (ponteiros de instrução) e nos tipos.

Os dados de criação de perfil disponíveis para comparação incluem as informações exibidas nas colunas. Para obter definições desses nomes de coluna, consulte [exibições de relatório de desempenho](../profiling/performance-report-views.md).

Um limite pode ser definido para reduzir o ruído e filtrar dados na exibição de tabela de comparação das linhas que não tenham sido alterados por uma quantidade especificada.

## <a name="in-this-section"></a>Nesta seção

[Como comparar arquivos de dados de desempenho](../profiling/how-to-compare-performance-data-files.md)
