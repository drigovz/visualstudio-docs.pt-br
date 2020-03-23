---
title: 'Como: Executar a análise de código legado manualmente para obter código gerenciado'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9d2693bcff8e83839b4171bae60b138c967f10e5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432227"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Como: Executar a análise de código legado manualmente para obter código gerenciado
A ferramenta de análise de código fornece informações sobre possíveis defeitos em seu código-fonte. Você pode executar a análise de código automaticamente com cada compilação de um projeto de código, e também pode executar a análise de código manualmente. As regras verificadas quando a análise de código é executada são especificadas na página de Análise de Código das páginas de propriedade do projeto. Para obter mais informações, [consulte Como: Configurar a análise de código para um projeto de código gerenciado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>Para executar a análise de código manualmente

1. Se você estiver na versão 16.5 do Visual Studio 2019 ou posterior, execute o seguinte comando no prompt de comando antes de iniciar o Visual Studio:

```
set EnableLegacyCodeAnalysis = true
```

2. No **Solution Explorer,** clique no projeto.

3. No menu **Analisar,** clique **em Executar análise de código em** nome do *projeto*.

