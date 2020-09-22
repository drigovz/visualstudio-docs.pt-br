---
title: Executar análise de código herdado manualmente (.NET)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ca865b33d59f87453cafc337e1595c9d772b17a2
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808607"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Como executar a análise de código herdada manualmente para código gerenciado

A ferramenta de análise de código fornece informações sobre possíveis defeitos em seu código-fonte. Você pode executar a análise de código automaticamente com cada compilação de um projeto de código e também pode executar a análise de código manualmente. As regras que são verificadas quando a análise de código é executada são especificadas na página análise de código das páginas de propriedades do projeto. Para obter mais informações, consulte [como: configurar a análise de código para um projeto de código gerenciado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>Para executar a análise de código manualmente

1. Se você estiver no Visual Studio 2019 versão 16,5 ou posterior, execute o seguinte comando no prompt de comando antes de iniciar o Visual Studio:

```
set EnableLegacyCodeAnalysis = true
```

2. Em **Gerenciador de soluções**, clique no projeto.

3. No menu **analisar** , clique em **executar análise de código no** *nome do projeto*.
