---
title: Analisando a qualidade do aplicativo usando ferramentas de análise de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.analysisresults
helpviewer_keywords:
- application quality, analyzing
- code analysis
- team-based development, analyzing application quality
ms.assetid: 21680516-ddb5-446d-90d4-19d94f6ec699
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f8ec0706530cd61653d44533654cf453d25eb42e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919070"
---
# <a name="analyzing-application-quality-by-using-code-analysis-tools"></a>Analisando a qualidade do aplicativo usando as ferramentas de análise de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nesta seção [analisando a qualidade de código gerenciado](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) , a análise de código do Visual Studio para código gerenciado fornece informações sobre assemblies gerenciados, como violações das regras de programação e design definidas nas diretrizes de design do Microsoft .NET Framework. As mensagens de aviso identificam problemas de programação e de design relevantes e, quando possível, fornecem informações de como corrigir o problema.

 [Analisando a qualidade de código C/C++ usando a análise de código](../code-quality/analyzing-c-cpp-code-quality-by-using-code-analysis.md) A ferramenta de análise de código do C/C++ fornece informações para os desenvolvedores sobre possíveis defeitos em seu código-fonte C/C++. Erros de codificação comuns relatados pela ferramenta incluem estouros de buffer, memória não inicializada, desreferências de ponteiro nulo e perdas de memória e de recursos.

 [Usando conjuntos de regras para agrupar regras de análise de código](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) Selecione e crie *conjuntos de regras* para aplicar ao seu projeto.

 [Erros do aplicativo de análise de código](../code-quality/code-analysis-application-errors.md) Corrija os erros na funcionalidade de análise de código.

 [Aprimorando a qualidade do código com as políticas de check-in do projeto de equipe](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md) Ao usar o Controle de Versão do Team Foundation (TFVC), você pode criar políticas de check-in para seus projetos de equipe que impõem práticas que levam a um melhor código e desenvolvimento de grupo mais eficiente. As políticas de check-in são regras que são definidas no nível do projeto de equipe e impostas em computadores de desenvolvedor antes do código ter permissão para fazer check-in.

### <a name="code-analysis-for-drivers"></a>Análise de código para drivers
 As ferramentas de análise de código podem ajudar a melhorar a estabilidade e a confiabilidade de seu driver, analisando sistematicamente o código-fonte do driver.

 [Analisando a qualidade do driver usando ferramentas de análise de código](/windows-hardware/drivers/devtest/tools-for-verifying-drivers) A análise de código para drivers é uma ferramenta de verificação estática de tempo de compilação que detecta erros básicos de codificação em programas em C e C++ e inclui um módulo especializado projetado para detectar erros no código de driver de modo kernel (principalmente). O SDV (verificador de driver estático) é uma ferramenta de verificação estática que analisa sistematicamente o código-fonte de drivers do modo kernel do Windows. SDV determina se o driver interage corretamente com o kernel do sistema operacional Windows.

 [Análise de código para avisos de drivers](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings) Descreve os avisos que a análise de código dos drivers relata quando detecta um possível erro no código do driver.

## <a name="related-tasks"></a>Related Tasks
 [Medindo a complexidade e a manutenção do código gerenciado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) Insira a descrição aqui.

 [Teste de unidade em seu código](../test/unit-test-your-code.md) Insira a descrição aqui.
