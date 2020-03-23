---
title: Uso de vários processadores para criar projetos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5dc62112324f7ad19c47b346ac8c1e3f86570b0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631296"
---
# <a name="use-multiple-processors-to-build-projects"></a>Usar vários processadores para criar projetos

MSBuild pode tirar proveito dos sistemas com vários processadores ou vários núcleos processadores. Um processo de compilação separado é criado para cada processador disponível. Por exemplo, se o sistema possui quatro processadores, então quatro processos de compilação são criados. O MSBuild pode processar essas compilações simultaneamente e, portanto, o tempo total de compilação é reduzido. No entanto, a construção em paralelo apresenta algumas alterações em como os processos de compilação ocorrem. Este tópico aborda essas alterações.

## <a name="project-to-project-references"></a>Referências projeto a projeto

 Quando o Microsoft Build Engine encontra uma referência p2P (project-to-project) enquanto está usando compilações paralelas para construir um projeto, ele constrói a referência apenas uma vez. Se dois projetos tiverem a mesma referência P2P, a referência não é reconstruída para cada projeto. Em vez disso, o mecanismo de compilação retorna a mesma referência P2P para ambos os projetos que dependem dele. As solicitações futuras na sessão para o mesmo destino recebem a mesma referência P2P.

## <a name="cycle-detection"></a>Detecção do ciclo

 A detecção de ciclo funciona da mesma forma que no MSBuild 2.0, exceto que agora o MSBuild pode relatar a detecção do ciclo em um momento diferente ou na compilação.

## <a name="errors-and-exceptions-during-parallel-builds"></a>Erros e exceções durante compilações paralelas

 Em compilações paralelas, erros e exceções podem ocorrer em momentos diferentes que fazem em uma compilação não paralelos e quando um projeto não será compilado, continuam as compilações do projeto. O MSBuild não impedirá qualquer construção de projeto que esteja sendo construída em paralelo com a que falhou. Outros projetos continuam a ser criados até que tenham êxito ou falha. No entanto, se <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A> foi habilitado, então nenhum build será interrompido, mesmo que ocorra um erro.

## <a name="c-project-vcxproj-and-solution-sln-files"></a>C++ projeto (.vcxproj) e solução (.sln) arquivos

 Ambos os projetos C++*(.vcxproj)* e os arquivos solution *(.sln)* podem ser passados para a [tarefa MSBuild](../msbuild/msbuild-task.md). Para projetos C++, o VCWrapperProject é chamado e, em seguida, o projeto interno do MSBuild é criado. Para soluções C++, é criado um SolutionWrapperProject e, em seguida, o projeto interno do MSBuild é criado. Em ambos os casos, o projeto resultante é tratado da mesma forma que qualquer outro projeto MSBuild.

## <a name="multi-process-execution"></a>Execução multiprocesso

 Quase todas as atividades relacionadas à compilação exigem o diretório atual para permanecer constante ao longo do processo de compilação para evitar erros de caminho. Portanto, os projetos não podem ser executados em diferentes segmentos no MSBuild porque causariam a criação de vários diretórios.

 Para evitar esse problema, mas ainda habilitar compilações de vários processadores, o MSBuild usa o "isolamento de processos". Usando o isolamento do processo, o `n` MSBuild `n` pode criar um máximo de processos, onde é igual ao número de processadores disponíveis no sistema. Por exemplo, se o MSBuild criar uma solução em um sistema que tenha dois processadores, então apenas dois processos de compilação serão criados. Novamente, esses processos são usados para criar todos os projetos na solução.

## <a name="see-also"></a>Confira também

- [Construa vários projetos em paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [Tarefas](../msbuild/msbuild-tasks.md)
