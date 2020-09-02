---
title: Valores de métricas de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics
- code analysis
- measure code quality
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23dba7b7c29c05b55af2c461f36bdaa4b46b948f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667728"
---
# <a name="code-metrics-values"></a>Valores de métricas do código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

As métricas de código são um conjunto de medidas de software que fornecem aos desenvolvedores uma visão melhor do código que estão desenvolvendo. Aproveitando as métricas de código, os desenvolvedores podem entender quais tipos e/ou métodos devem ser retrabalhados ou testados com mais detalhes. As equipes de desenvolvimento podem identificar possíveis riscos, compreender o estado atual de um projeto e acompanhar o progresso durante o desenvolvimento de software.

## <a name="software-measurements"></a>Medições de software
 A lista a seguir mostra os resultados de métricas de código que o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] calcula:

- **Índice de facilidade de manutenção** – calcula um valor de índice entre 0 e 100 que representa a facilidade relativa de manter o código. Um valor alto significa melhor facilidade de manutenção. As Classificações codificadas por cor podem ser usadas para identificar rapidamente os pontos problemáticos em seu código. Uma classificação verde é entre 20 e 100 e indica que o código tem boa facilidade de manutenção. Uma classificação amarela é entre 10 e 19 e indica que o código é de manutenção moderada. Uma classificação vermelha é uma classificação entre 0 e 9 e indica baixa facilidade de manutenção.

- **Complexidade ciclomática** – mede a complexidade estrutural do código. Ele é criado calculando o número de caminhos de código diferentes no fluxo do programa. Um programa que tenha um fluxo de controle complexo exigirá mais testes para obter uma boa cobertura de código e será menos passível de manutenção.

    > [!NOTE]
    > Em alguns casos, o cálculo da complexidade ciclomática para um método em [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] difere das versões anteriores. Para obter mais informações, consulte a seção "alterações nos cálculos de complexidade de código do Visual Studio 2010" de [solucionar problemas de métricas de código](../code-quality/troubleshooting-code-metrics-issues.md).

- **Profundidade de herança** – indica o número de definições de classe que se estendem para a raiz da hierarquia de classe. Quanto mais profunda for a hierarquia, mais difícil será entender onde métodos e campos específicos são definidos ou/e redefinidos.

- **Acoplamento de classe** – mede o acoplamento para classes exclusivas por meio de parâmetros, variáveis locais, tipos de retorno, chamadas de método, instanciações genéricas ou de modelo, classes base, implementações de interface, campos definidos em tipos externos e decoração de atributo. Um bom design de software determina que os tipos e métodos devem ter alta coesão e acoplamento baixo. O acoplamento alto indica um design que é difícil de reutilizar e manter devido a muitas interdependências em outros tipos.

- **Linhas de código** – indica o número aproximado de linhas no código. A contagem é baseada no código IL e, portanto, não é o número exato de linhas no arquivo de código-fonte. Uma contagem muito alta pode indicar que um tipo ou método está tentando fazer muito trabalho e deve ser dividido. Ele também pode indicar que o tipo ou o método pode ser difícil de manter.

## <a name="anonymous-methods"></a>Métodos anônimos
 Um *método anônimo* é apenas um método que não tem nome. Os métodos anônimos são usados com mais frequência para passar um bloco de código como um parâmetro delegado. Os resultados de métricas para um método anônimo que é declarado em um membro, como um método ou acessador, são associados ao membro que declara o método. Eles não estão associados ao membro que chama o método.

 Para obter mais informações sobre como as métricas de código tratam métodos anônimos, consulte [métodos anônimos e análise de código](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Código gerado
 Algumas ferramentas de software e compiladores geram código que é adicionado a um projeto e que o desenvolvedor do projeto não vê ou não deve ser alterado. Principalmente, as métricas de código ignoram o código gerado quando calcula os valores de métricas. Isso permite que os valores de métrica reflitam o que o desenvolvedor pode ver e alterar.

 O código gerado para Windows Forms não é ignorado, pois é um código que o desenvolvedor pode ver e alterar.

## <a name="see-also"></a>Consulte Também
 [Medindo complexidade e facilidade de manutenção do código gerenciado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
