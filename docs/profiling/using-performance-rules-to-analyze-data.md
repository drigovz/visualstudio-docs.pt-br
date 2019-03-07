---
title: Usando regras de desempenho para analisar dados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0e69de397f9c8f4160d81047f086a6db60741e8
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641644"
---
# <a name="use-performance-rules-to-analyze-data"></a>Usar regras de desempenho para analisar dados
Os avisos de desempenho das Ferramentas de Criação de Perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] indicam problemas em um aplicativo analisado que podem causar lentidão na execução do programa. Os avisos também podem indicar que talvez seja necessário alterar os métodos de coleta para coletar dados mais úteis. Avisos de desempenho são gerados automaticamente em uma sessão de criação de perfil. Os avisos são exibidos na janela **Lista de Erros** quando um arquivo de dados de criação de perfil está aberto no Visual Studio. Na janela **Lista de Erros**, é possível localizar o código-fonte do problema e exibir informações detalhadas sobre o erro, por exemplo, como resolvê-lo. Também é possível desabilitar avisos nos quais você não está interessado.

> [!NOTE]
>  Os avisos de desempenho do criador de perfil são gerados pela análise dinâmica da execução do programa e são independentes dos avisos de Análise de Código. A Análise de Código também pode gerar avisos de desempenho para código gerenciado com base na análise estática do código-fonte. Para obter mais informações, confira [Analyze managed code quality](/visualstudio/code-quality/code-analysis-for-managed-code-overview) (Analisar a qualidade do código gerenciado) e [Performance warnings](../code-quality/performance-warnings.md) (Avisos de desempenho).

## <a name="in-this-section"></a>Nesta seção
- [Como: Exibir avisos de desempenho](../profiling/how-to-view-performance-warnings.md)

 Fornece informações sobre como abrir a janela **Lista de Erros** para exibir avisos de desempenho do criador de perfil.

- [Como: Configurar regras de desempenho](../profiling/how-to-configure-performance-rules.md)

 Fornece informações sobre como ativar ou desativar avisos de desempenho individuais.

- [Referência de regras de desempenho](../profiling/performance-rules-reference.md)

 Fornece informações detalhadas sobre os avisos de desempenho do criador de perfil