---
title: Depurador de sombreador HLSL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.shaderviewer
ms.assetid: 4ccec541-3c49-42bd-972a-686eb3a88fbc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 164c404f3bce6b8216092635e3489843039fb1eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72735297"
---
# <a name="hlsl-shader-debugger"></a>Depurador de sombreador HLSL
O depurador do HLSL no Analisador de Gráficos do Visual Studio ajuda a entender como o código do sombreador HLSL funciona sob condições reais do seu aplicativo.

 Este é o depurador HLSL:

 ![Depurando HLSL usando inspeção e janelas de pilha de chamadas.](media/gfx_diag_demo_hlsl_debugger_orientation.png "gfx_diag_demo_hlsl_debugger_orientation")

## <a name="understanding-the-hlsl-debugger"></a>Noções básicas do depurador HLSL
 O depurador HLSL pode ajudar você a entender os problemas que ocorrem no código do sombreador. A depuração do código HLSL no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se parece com a depuração de código que foi escrito em outras linguagem, como no C++, C# ou Visual Basic. Você pode inspecionar o conteúdo das variáveis, definir pontos de interrupção, avançar no código e percorrer até a pilha de chamadas, exatamente como faz ao depurar outras linguagens.

 No entanto, como as GPUs alcançam alto desempenho executando o código do sombreador em centenas de threads simultaneamente, o depurador do HLSL foi projetado para trabalhar em conjunto com as outras ferramentas do analisador de gráficos para apresentar todas essas informações de forma a ajudá-lo a fazer sentido. O analisador de gráficos recria quadros capturados usando informações que foram registradas em um log de gráficos; o depurador do HLSL não monitora a execução da GPU em tempo real à medida que ele executa o código do sombreador. Como um log de gráficos contém informações suficientes para recriar qualquer parte da saída e como a análise de gráficos fornece ferramentas que podem ajudá-lo a identificar o pixel exato e o evento em que ocorre um erro, o depurador HLSL só precisa simular o thread do sombreador exato em que você está interessado. Isso significa que o trabalho do sombreador pode ser simulado na CPU, onde seu funcionamento interno é no modo de exibição completa. Isso é o que proporciona ao depurador HLSL uma experiência de depuração parecida com a de uma CPU.

 No entanto, o depurador HLSL, atualmente, encontra-se limitado por estes motivos:

- O depurador HLSL não dá suporte a Edit-and-Continue, mas você pode fazer alterações em seus sombreadores e, em seguida, regenerar o quadro para ver os resultados.

- Não é possível depurar um aplicativo e seu código de sombreador ao mesmo tempo. No entanto, você pode alternar entre eles.

- É possível adicionar variáveis e registros à janela Inspeção, mas expressões não têm suporte.

  Entretanto, o depurador HLSL oferece a melhor experiência de depuração e mais parecida com a de uma CPU, que de outra forma não seria possível.

## <a name="hlsl-shader-edit--apply"></a>Editar e aplicar sombreador HLSL
 O depurador de sombreador HLSL não oferece suporte para Editar e Continuar da mesma maneira que o depurador de CPU, porque o modelo de execução GPU não permite que o estado do sombreador seja desfeito. Em vez disso, o depurador HLSL dá suporte a Editar e Aplicar, o que permite que você edite os arquivos de origem HLSL e escolha **Aplicar** para gerar novamente o quadro para ver o efeito das alterações. O código de sombreador modificado é armazenado em um arquivo separado para preservar a integridade dos arquivos de origem HLSL originais do projeto, mas quando você estiver satisfeito com as alterações você pode escolher **Copiar para...** para copiar as alterações para o seu projeto. Usando esse recurso, você pode iterar rapidamente no código do sombreador que contém erros e eliminar as etapas caras de recompilação e captura do seu do fluxo de trabalho de depuração do HLSL.

## <a name="hlsl-disassembly"></a>Desmontagem do HLSL
 O depurador de sombreador HLSL fornece uma lista de assembly de sombreador HLSL à direita da lista de código-fonte do HLSL.

## <a name="debugging-hlsl-code"></a>Depurando código HLSL
 Você pode acessar o depurador do HLSL de estágios de pipeline ou janelas de histórico de pixel.

#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pipeline-stages-window"></a>Para iniciar o depurador HLSL da janela Estágios de Pipeline Gráficos

1. Na janela **Gráficos – Estágios de Pipeline**, localize o estágio de pipeline que está associado ao sombreador que deseja depurar.

2. Abaixo do título do estágio de pipeline, escolha **Iniciar Depuração**, que aparece como uma pequena seta verde.

    > [!NOTE]
    > Esse ponto de entrada no depurador HLSL depura apenas o primeiro thread do sombreador para o estágio correspondente, isto é, o primeiro vértice ou pixel que é processado. Você pode usar o histórico de pixel para acessar outros threads desses estágios de sombreador.

#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pixel-history"></a>Para iniciar o depurador HLSL do Histórico de Pixel de Gráficos

1. Na janela **histórico de pixels de gráficos** , expanda a chamada de desenho associada ao sombreador que você deseja depurar. Cada chamada de desenho pode corresponder a vários primitivos.

2. Nos detalhes da chamada de desenho, expanda um primitivo cuja contribuição de cor resultante sugira um bug em seu código de sombreador. Se vários primitivos sugerirem um bug, escolha o primeiro primitivo que o sugere, de modo que você possa evitar uma acumulação de erros, o que pode dificultar o diagnóstico do problema.

3. Nos detalhes do primitivo, escolha se quer depurar o **Sombreador de Vértices** ou o **Sombreador de Pixel**. Depure o sombreador de vértices quando você suspeitar que o sombreador de pixel está correto, mas está gerando uma contribuição de cor incorreta porque o sombreador de vértices está passando constantes incorretas a ele. Caso contrário, depure o sombreador de pixel.

    À direita do sombreador escolhido, escolha **Iniciar Depuração**, que aparece como uma pequena seta verde.

   > [!NOTE]
   > Esse ponto de entrada no depurador HLSL depura o thread do sombreador de pixel, que corresponde à chamada de desenho, ao primitivo e ao pixel que você escolheu, ou os threads do sombreador de vértices, cujos resultados são interpolados pela chamada de desenho, pelo primitivo e pelo pixel que você escolheu. No caso de sombreadores de vértices, você ainda pode refinar o ponto de entrada para um vértice específico expandindo os detalhes do sombreador de vértices.

   Para obter exemplos de como usar o depurador HLSL para depurar erros de sombreador, consulte [exemplos](graphics-diagnostics-examples.md) ou os passo a passos vinculados a na seção Consulte também.

## <a name="see-also"></a>Confira também
- [Passo a passo: Objetos ausentes devido ao sombreamento de vértice](walkthrough-missing-objects-due-to-vertex-shading.md)
- [Passo a passo: Como depurar erros de renderização devido ao sombreamento](walkthrough-debugging-rendering-errors-due-to-shading.md)
- [Passo a passo: Como usar o Diagnóstico de Gráficos para depurar um sombreador de computação](walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md)