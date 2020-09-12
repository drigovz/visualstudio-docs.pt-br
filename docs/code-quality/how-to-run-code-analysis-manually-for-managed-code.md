---
title: Como executar a análise de código manualmente para .NET
ms.date: 09/02/2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c24fa8e835dced8332aa4c50870d6251bdd43e63
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037153"
---
# <a name="run-code-analysis-manually-for-net"></a>Executar análise de código manualmente para .NET
Por padrão, os analisadores de .NET Compiler Platform ("Roslyn") analisam seu código C# ou Visual Basic à medida que você digita fazendo análises ao vivo, bem como durante a compilação. Portanto, normalmente você não precisaria disparar manualmente a análise de código. No entanto, há alguns cenários em que você pode querer disparar manualmente a análise de código:

> [!NOTE]
> Executar a análise de código manualmente requer o Visual Studio 2019 versão 16,5 ou posterior

- Por padrão, a análise de código ao vivo executa analisadores somente para arquivos abertos no Visual Studio. No entanto, talvez você esteja interessado em exibir avisos de análise de código para todos os arquivos em um projeto ou solução específica. Nesse caso, você desejaria disparar a análise de código uma vez em um projeto ou em uma solução. Como alternativa, você pode habilitar a análise contínua de código ao vivo para ser executada em toda a solução. Para obter mais informações, consulte [como: configurar o escopo de análise de código ao vivo para código gerenciado](./configure-live-code-analysis-scope-managed-code.md).
- Você pode preferir o fluxo de trabalho de execução da análise de código sob demanda sobre análise dinâmica contínua ou análise em tempo de compilação. Nesse caso, você pode desabilitar a execução do analisador durante a análise dinâmica e/ou a compilação. Para obter informações sobre como desabilitar a análise, consulte [como desabilitar a análise de código-fonte](disable-code-analysis.md). Em seguida, você desejaria disparar manualmente a análise de código uma vez em um projeto ou em uma solução.

### <a name="run-code-analysis-manually"></a>Executar análise de código manualmente

1. Em **Gerenciador de soluções**, selecione o projeto.

2. No menu **analisar** , selecione **executar análise de código no** *nome do projeto*.

A análise de código começará a ser executada em segundo plano. Você deve ver a mensagem **executando a análise de código para \<project> ...** na barra de status do Visual Studio até o canto inferior esquerdo. Após a conclusão da análise de código, a mensagem de status será alterada para a **análise de código concluída para \<project> **. A lista de erros será atualizada em breve com todos os diagnósticos de análise de código.
