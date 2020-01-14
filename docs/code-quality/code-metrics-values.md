---
title: Calcular métricas de código
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ece5c08ca3aa4a9f5e5329dbf6d5fd6c9087d085
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75886409"
---
# <a name="code-metrics-values"></a>Valores de métricas de código

O aumento da complexidade de aplicativos de software moderno também aumenta a dificuldade de fazer o código confiável e fácil de manter. As métricas de código são um conjunto de medidas de software que fornecem aos desenvolvedores uma visão melhor do código que estão desenvolvendo. Ao tirar proveito das métricas de código, os desenvolvedores poderão entender quais tipos de e/ou os métodos devem ser reformulados ou mais minuciosamente. As equipes de desenvolvimento podem identificar possíveis riscos, entender o estado atual de um projeto e acompanhar o progresso durante o desenvolvimento de software.

Os desenvolvedores podem usar o Visual Studio para gerar dados de métricas de código que medem a complexidade e facilidade de manutenção de seu código gerenciado. Dados de métricas de código podem ser gerados para uma solução inteira ou um único projeto.

Para obter informações sobre como gerar dados de métricas de código no Visual Studio, consulte [como: gerar dados de métricas de código](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Medições de software

A lista a seguir mostra o código de resultados de métricas que calcula o Visual Studio:

- **Índice de facilidade de manutenção** -calcula um valor de índice entre 0 e 100 que representa a relativa facilidade de manutenção do código. Um valor alto significa melhor facilidade de manutenção. Classificações codificadas por cor podem ser usadas para identificar rapidamente pontos problemáticos em seu código. Uma classificação verde está entre 20 e 100 e indica que o código tem boa facilidade de manutenção. Uma classificação amarela é entre 10 e 19 e indica que o código é razoavelmente fácil de manter. Uma classificação vermelha é uma classificação entre 0 e 9 e indica pouca facilidade de manutenção. Para obter mais informações, consulte o [intervalo de índice de manutenção e](https://blogs.msdn.microsoft.com/codeanalysis/2007/11/20/maintainability-index-range-and-meaning/) o que significa a postagem no blog.

- **A complexidade ciclomática** -mede a complexidade do código estrutural. Ele é criado pelo cálculo do número de diferentes caminhos de código no fluxo do programa. Um programa que tem um fluxo de controle complexo requer mais testes para obter uma boa cobertura de código e é menos passível de manutenção. Para obter mais informações, consulte a [entrada da Wikipédia para complexidade ciclomática](https://wikipedia.org/wiki/Cyclomatic_complexity).

- **Profundidade de herança** – indica o número de classes diferentes que herdam uma da outra, de volta para a classe base. A profundidade da herança é semelhante ao acoplamento de classes, pois uma alteração em uma classe base pode afetar qualquer uma de suas classes herdadas. Quanto maior esse número, mais profunda a herança e maior o potencial para modificações na classe base resultam em uma alteração significativa. Para uma profundidade de herança, um valor baixo é bom e um valor alto é ruim.

- **Classe acoplamento** -mede o acoplamento de classes exclusivos por meio de parâmetros, variáveis locais, tipos de retorno, chamadas de método, instanciações genéricas ou modelo, as classes base, implementações de interface, os campos definidos nos tipos externos, e decoração do atributo. Design de software BOM determina que tipos e métodos devem ter alta coesão e acoplamento de baixa. Acoplamento alta indica um design que é difícil a reutilização e a manter o devido à suas muitas interdependências em outros tipos. Para obter mais informações, consulte a postagem do blog de [acoplamento de classes](https://blogs.msdn.microsoft.com/zainnab/2011/05/25/code-metrics-class-coupling/) .

::: moniker range=">=vs-2019"

- **Linhas de código-fonte** – indica o número exato de linhas de código-fonte que estão presentes no arquivo de origem, incluindo linhas em branco. Essa métrica está disponível a partir do Visual Studio 2019 versão 16,4 e Microsoft. CodeAnalysis. métricas (2.9.5).

- **Linhas de código executável** – indica o número aproximado de linhas ou operações de código executável. Esta é uma contagem do número de operações no código executável. Essa métrica está disponível a partir do Visual Studio 2019 versão 16,4 e Microsoft. CodeAnalysis. métricas (2.9.5). O valor normalmente é uma correspondência próxima à métrica anterior, **linhas de código**, que é a métrica baseada em instrução MSIL usada no modo herdado.
::: moniker-end
::: moniker range="vs-2017"

- **Linhas de código** -indica o número aproximado de linhas de código. A contagem é baseada no código IL e, portanto, não o número exato de linhas no arquivo de código de origem. Uma contagem alta pode indicar que um tipo ou método está tentando fazer muito trabalho e deve ser dividido. Isso também pode indicar que o tipo ou método pode ser difícil de manter.

   > [!NOTE]
   > O [versão de linha de comando](../code-quality/how-to-generate-code-metrics-data.md#command-line-code-metrics) do código ferramenta métricas contagens de linhas reais de código porque ele analisa o código-fonte em vez de IL.
::: moniker-end

## <a name="anonymous-methods"></a>Métodos anônimos

Uma *método anônimo* é apenas um método que não tem nome. Métodos anônimos são usados com mais frequência para passar um bloco de código como um parâmetro delegado. Os resultados de métricas de código para um método anônimo declarado em um membro, como um método ou acessador, são associados ao membro que declara o método. Eles não são associados com o membro que chama o método.

## <a name="generated-code"></a>Código gerado

Alguns compiladores e ferramentas de software geram código que é adicionado a um projeto e que o desenvolvedor do projeto não vê ou não deve ser alterada. Em grande parte, as métricas de código ignora o código gerado quando ela calcula os valores das métricas. Isso permite que os valores das métricas refletir o que o desenvolvedor possa ver e alterar.

Código gerado para o Windows Forms não é ignorado, porque ele é o código que o desenvolvedor possa ver e alterar.

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

- [Como: gerar dados de métricas de código](../code-quality/how-to-generate-code-metrics-data.md)
- [Use a janela de resultados de métricas de código](../code-quality/working-with-code-metrics-data.md)
