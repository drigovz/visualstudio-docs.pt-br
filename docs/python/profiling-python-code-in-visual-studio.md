---
title: Medir o desempenho do código Python
description: Use o criador de perfil do Visual Studio para verificar o desempenho do código Python ao usar interpretadores baseados em CPython.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e31286a9b0ea3852ad1fe788d4ff6c4c66e7e4f0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62784255"
---
# <a name="profile-python-code"></a>Criar perfil do código do Python

Você pode criar um perfil de um aplicativo Python ao usar interpretadores baseados em CPython. (Confira [Matriz de recursos – criação de perfil](overview-of-python-tools-for-visual-studio.md#matrix-profiling) para saber a disponibilidade desse recurso para diferentes versões do Visual Studio.)

## <a name="profiling-for-cpython-based-interpreters"></a>Criação de perfil para interpretadores baseados em CPython

A criação de perfil é iniciada por meio do comando de menu **Analisar** > **Iniciar Criação de Perfil do Python**, que abre uma caixa de diálogo de configuração:

![Caixa de diálogo de configuração de criação de perfil](media/profiling-start.png)

Quando você seleciona **OK**, o criador de perfil é executado e abre um relatório de desempenho por meio do qual é possível explorar como o tempo é gasto no aplicativo:

![Relatório de desempenho de criação de perfil](media/profiling-results.png)

> [!Note]
> No momento, o Visual Studio oferece suporte somente a esse nível de criação de perfil de aplicativo completo, mas certamente queremos ouvir seus comentários sobre recursos futuros. Use o botão **Comentários sobre o produto** no final desta página.

## <a name="profiling-for-ironpython"></a>Criação de perfil do IronPython

Como o IronPython não é um interpretador baseado em CPython, o recurso de criação de perfil não funciona.

Em vez disso, use o criador de perfil do .NET do Visual Studio iniciando *ipy.exe* diretamente como o aplicativo de destino, usando os argumentos apropriados para iniciar o script de inicialização. Inclua `-X:Debug` na linha de comando para garantir que todo o seu código Python possa ser depurado e seja passível à criação de perfil. Esse argumento gera um relatório de desempenho, incluindo o tempo gasto no tempo de execução do IronPython e no código. O código é identificado usando nomes danificados.

Como alternativa, o IronPython tem alguns de seus próprios recursos de criação de perfis internos, mas atualmente não há nenhum visualizador adequado para eles. Consulte [An IronPython Profiler](https://blogs.msdn.microsoft.com/curth/2009/03/30/an-ironpython-profiler/) (Um criador de perfil do IronPython) (blogs do MSDN) para ver o que está disponível.
