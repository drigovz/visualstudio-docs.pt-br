---
title: Medir o desempenho do código Python
description: Use o criador de perfil do Visual Studio para verificar o desempenho do código Python ao usar interpretadores baseados em CPython.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6e6a37301477b43063169143456fc21a3c783968
ms.sourcegitcommit: 4976419fae731860295dbcd072e6778832f7255d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97917919"
---
# <a name="profile-python-code"></a>Criar perfil do código do Python

Você pode criar um perfil de um aplicativo Python ao usar interpretadores baseados em CPython. (Confira [Matriz de recursos – criação de perfil](overview-of-python-tools-for-visual-studio.md#matrix-profiling) para saber a disponibilidade desse recurso para diferentes versões do Visual Studio.)

## <a name="profiling-for-cpython-based-interpreters"></a>Criação de perfil para interpretadores baseados em CPython

A criação de perfil é iniciada por meio do comando **debug**  >  **Launch Python Profile** menu, que abre uma caixa de diálogo de configuração:

![Caixa de diálogo de configuração de criação de perfil](media/profiling-start.png)

Quando você seleciona **OK**, o criador de perfil é executado e abre um relatório de desempenho por meio do qual é possível explorar como o tempo é gasto no aplicativo:

![Relatório de desempenho de criação de perfil](media/profiling-results.png)

> [!Note]
> Quando você criar o perfil de um aplicativo Python, o Visual Studio coleta dados durante o tempo de vida do processo. No momento, não é possível pausar a criação de perfil. Queremos ouvir seus comentários sobre recursos futuros. Use o botão **Comentários sobre o produto** no final desta página.

## <a name="profiling-for-ironpython"></a>Criação de perfil do IronPython

Como o IronPython não é um interpretador baseado em CPython, o recurso de criação de perfil não funciona.

Em vez disso, use o criador de perfil do .NET do Visual Studio iniciando *ipy.exe* diretamente como o aplicativo de destino, usando os argumentos apropriados para iniciar o script de inicialização. Inclua `-X:Debug` na linha de comando para garantir que todo o seu código Python possa ser depurado e seja passível à criação de perfil. Esse argumento gera um relatório de desempenho, incluindo o tempo gasto no runtime do IronPython e no código. O código é identificado usando nomes danificados.

Como alternativa, o IronPython tem alguns de seus próprios recursos de criação de perfis internos, mas atualmente não há nenhum visualizador adequado para eles. Consulte [An IronPython Profiler](/archive/blogs/curth/an-ironpython-profiler) (Um criador de perfil do IronPython) (blogs do MSDN) para ver o que está disponível.