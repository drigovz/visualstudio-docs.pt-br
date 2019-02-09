---
title: Análise de código para visão geral do C/C++
ms.date: 04/28/2018
ms.topic: conceptual
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 07ba2c64be0af987b82c870b89d3451b5d48d28f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55947634"
---
# <a name="code-analysis-for-cc-overview"></a>Análise de código para visão geral do C/C++

A ferramenta de análise de código C/C++ fornece informações sobre possíveis defeitos no seu código-fonte C/C++. Entre os erros de codificação comuns reportados pela ferramenta estão estouros de buffer, memória não inicializada, desreferências de ponteiro nulo, memória e perdas de recurso. A ferramenta também pode executar verificações em relação a [diretrizes principais do C++](http://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="ide-integrated-development-environment-integration"></a>Integração de IDE (ambiente de desenvolvimento integrado)

A ferramenta de análise de código é totalmente integrada dentro do IDE do Visual Studio.

Durante o processo de build, todos os avisos gerados para o código-fonte aparecem na Lista de Erros. Você pode navegar para o código-fonte que causou o aviso e ver informações adicionais sobre a causa e possíveis soluções do problema.

## <a name="command-line-support"></a>Suporte de linha de comando

Você também pode usar a ferramenta de análise da linha de comando, conforme mostrado no exemplo a seguir:

```cmd
C:\>cl /analyze Sample.cpp
```

**Visual Studio 2017 versão 15.7 e posterior** você pode executar a ferramenta da linha de comando com qualquer sistema de compilação, incluindo o CMake.

## <a name="pragma-support"></a>suporte de #pragma

Você pode usar o `#pragma` diretiva para tratar avisos como erros; ativar ou desativar avisos e suprimir avisos para linhas individuais de código. Para obter mais informações, confira [Como: Definir propriedades de análise de código para projetos C/C++](how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="annotation-support"></a>Suporte de anotação

As anotações melhoram a precisão da análise de código. As anotações fornecem informações adicionais sobre pré e pós-condições nos parâmetros de função e nos tipos retornados. Para obter mais informações, confira [Como: especificar informações de código adicionais usando __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Execute a ferramenta de análise como parte da política de check-in

Talvez você queira exigir que todos os check-ins do código-fonte satisfaçam determinadas políticas. Em particular, convém verificar se a análise foi executada como uma etapa do build local mais recente. Para obter mais informações de como habilitar uma política de check-in de análise de código, confira [Criando e usando políticas de check-in de análise de código](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>Integração do Team Build

Você pode usar os recursos integrados do sistema de build para executar a ferramenta de análise de código como uma etapa do processo de build do [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]. Para obter mais informações, confira [Azure Pipelines](/azure/devops/pipelines/index?view=vsts).

## <a name="see-also"></a>Consulte também

- [Início Rápido: Análise de código para C/C++](quick-start-code-analysis-for-c-cpp.md)
- [Passo a passo: Analisar o código C/C++ em busca de defeitos](walkthrough-analyzing-c-cpp-code-for-defects.md)
- [Análise de código para avisos do C/C++](code-analysis-for-c-cpp-warnings.md)
- [Usar os verificadores de diretrizes de núcleo do C++](using-the-cpp-core-guidelines-checkers.md)
- [Referência de verificador das diretrizes principais do C++](code-analysis-for-cpp-corecheck.md)
- [Usar conjuntos de regras para especificar as regras do C++ para execução](using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Analisar a qualidade do Driver usando as ferramentas de análise de código](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
- [Análise de código para avisos de Drivers](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)
