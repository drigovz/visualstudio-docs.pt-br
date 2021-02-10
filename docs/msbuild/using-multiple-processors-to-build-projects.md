---
title: Uso de vários processadores para criar projetos | Microsoft Docs
description: Saiba como o MSBuild aproveita os sistemas que têm vários processadores ou núcleos criando um processo de compilação separado para cada processador disponível.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c1560b40fe94af8dae5223981dd8e0c790320085
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946365"
---
# <a name="use-multiple-processors-to-build-projects"></a>Usar vários processadores para criar projetos

MSBuild pode tirar proveito dos sistemas com vários processadores ou vários núcleos processadores. Um processo de compilação separado é criado para cada processador disponível. Por exemplo, se o sistema possui quatro processadores, então quatro processos de compilação são criados. O MSBuild pode processar essas compilações simultaneamente e, portanto, o tempo de compilação geral é reduzido. No entanto, a construção em paralelo apresenta algumas alterações em como os processos de compilação ocorrem. Este tópico aborda essas alterações.

## <a name="project-to-project-references"></a>Referências projeto a projeto

 Quando o Microsoft Build Engine encontra uma referência de ponto a projeto (P2P) enquanto está usando compilações paralelas para compilar um projeto, ele cria a referência apenas uma vez. Se dois projetos tiverem a mesma referência P2P, a referência não é reconstruída para cada projeto. Em vez disso, o mecanismo de compilação retorna a mesma referência P2P para ambos os projetos que dependem dele. As solicitações futuras na sessão para o mesmo destino recebem a mesma referência P2P.

## <a name="cycle-detection"></a>Detecção do ciclo

 As funções de detecção de ciclo são as mesmas que faziam no MSBuild 2,0, exceto pelo fato de que agora o MSBuild pode relatar a detecção do ciclo em uma hora diferente ou na compilação.

## <a name="errors-and-exceptions-during-parallel-builds"></a>Erros e exceções durante compilações paralelas

 Em compilações paralelas, erros e exceções podem ocorrer em momentos diferentes que fazem em uma compilação não paralelos e quando um projeto não será compilado, continuam as compilações do projeto. O MSBuild não interromperá qualquer compilação de projeto que esteja compilando em paralelo com aquela que falhou. Outros projetos continuam a ser criados até que tenham êxito ou falha. No entanto, se <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A> foi habilitado, então nenhum build será interrompido, mesmo que ocorra um erro.

## <a name="c-project-vcxproj-and-solution-sln-files"></a>Arquivos do projeto C++ (. vcxproj) e da solução (. sln)

 Os projetos C++ (*. vcxproj*) e de solução (*. sln*) podem ser passados para a [tarefa do MSBuild](../msbuild/msbuild-task.md). Para projetos C++, VCWrapperProject é chamado e, em seguida, o projeto interno do MSBuild é criado. Para soluções C++, um SolutionWrapperProject é criado e, em seguida, o projeto interno do MSBuild é criado. Em ambos os casos, o projeto resultante é tratado da mesma forma que qualquer outro projeto do MSBuild.

## <a name="multi-process-execution"></a>Execução multiprocesso

 Quase todas as atividades relacionadas à compilação exigem o diretório atual para permanecer constante ao longo do processo de compilação para evitar erros de caminho. Portanto, os projetos não podem ser executados em threads diferentes no MSBuild porque eles farão com que vários diretórios fossem criados.

 Para evitar esse problema, mas ainda habilitar compilações de vários processadores, o MSBuild usa "isolamento de processo". Usando o isolamento de processo, o MSBuild pode criar um máximo de `n` processos, onde `n` é igual ao número de processadores disponíveis no sistema. Por exemplo, se o MSBuild criar uma solução em um sistema que tenha dois processadores, somente dois processos de compilação serão criados. Novamente, esses processos são usados para criar todos os projetos na solução.

## <a name="see-also"></a>Confira também

- [Crie vários projetos em paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [Tarefas](../msbuild/msbuild-tasks.md)
