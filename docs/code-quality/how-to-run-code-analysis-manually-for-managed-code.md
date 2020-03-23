---
title: 'Como: Executar a análise de código manualmente para código gerenciado'
ms.date: 11/04/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mavasani
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5fdeb56a0c0f4c5904a00ec53d64dae87aa4e9a5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431378"
---
# <a name="how-to-run-code-analysis-manually-for-managed-code-requires-visual-studio-2019-version-165-or-later"></a>Como: Executar a análise de código manualmente para código gerenciado (requer visual studio versão 16.5 ou posterior)
Por padrão, os analisadores de código .NET Compiler Platform ("Roslyn") analisam seu código C# ou Visual Basic à medida que você digita fazendo análise ao vivo, bem como durante a compilação. Portanto, você normalmente não precisaria acionar manualmente a análise do código. No entanto, existem alguns cenários em que você pode querer acionar manualmente a análise do código:

- Por padrão, a análise de código ao vivo executa analisadores apenas para arquivos abertos no Visual Studio. No entanto, você pode estar interessado em visualizar avisos de análise de código para todos os arquivos em um projeto ou solução específica. Se assim for, você gostaria de acionar a análise de código uma vez em um projeto ou uma solução. Alternativamente, você pode habilitar uma análise contínua de código ao vivo para executar em toda a solução. Para obter mais informações, [consulte Como: Configurar o escopo de análise de código ao vivo para código gerenciado](./configure-live-code-analysis-scope-managed-code.md).
- Você pode preferir o fluxo de trabalho de execução de execução de análise de código demanda em vez de análise contínua ao vivo ou análise de tempo de construção. Nesse caso, você pode desativar a execução do analisador durante a análise ao vivo e/ou a compilação. Para obter informações sobre a análise desativada, consulte [Como desativar a análise do código-fonte](disable-code-analysis.md). Então você gostaria de acionar manualmente a análise de código uma vez em um projeto ou uma solução. 

### <a name="run-code-analysis-manually"></a>Executar análise de código manualmente

1. No **Solution Explorer,** clique no projeto.

2. No menu **Analisar,** clique **em Executar análise de código em** nome do *projeto*.

A análise de código começará a ser executada em segundo plano. Você deve ver a mensagem **Executando a análise de código para \<>** de projeto... na barra de status do Visual Studio no canto inferior esquerdo. Uma vez concluída a análise de código, a mensagem de status mudará para **análise de código concluída para \<>do projeto **. A lista de erros será atualizada em breve com todos os diagnósticos de análise de código.
