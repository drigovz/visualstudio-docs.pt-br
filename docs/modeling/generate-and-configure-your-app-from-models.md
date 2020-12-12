---
title: Gerar e configurar o aplicativo por meio de modelos
description: Saiba o que um modelo representa e como você pode gerar ou configurar partes do seu aplicativo a partir de um modelo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25a0b83d3ac7be95c42ca0c4e53a188569bb5770
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361866"
---
# <a name="generate-and-configure-your-app-from-models"></a>Gerar e configurar o aplicativo por meio de modelos
Você pode gerar ou configurar partes do seu aplicativo a partir de um modelo.

 O modelo representa os requisitos mais diretamente do que o código. Ao derivar o comportamento do aplicativo diretamente do modelo, você pode responder a requisitos alterados de forma muito mais rápida e confiável do que ao atualizar o código. Embora seja necessário algum trabalho inicial para configurar a derivação, esse investimento é retornado se você espera alterações nos requisitos ou se planeja fazer várias variantes do produto.

## <a name="generating-the-code-of-your-application-from-a-model"></a>Gerando o código do seu aplicativo a partir de um modelo
 A maneira mais fácil de gerar código é usando modelos de texto. Você pode gerar código na mesma solução do Visual Studio na qual você mantém o modelo. Para obter mais informações, consulte:

- [Geração de código na hora de design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

- [Gerando código a partir de uma linguagem específica do domínio](../modeling/generating-code-from-a-domain-specific-language.md)

  Esse método é fácil de aplicar de forma incremental. Comece com um aplicativo que funciona apenas para um caso específico e escolha algumas partes dele que você deseja variar do modelo. Renomeie os arquivos de origem dessas partes para que se tornem arquivos de modelo de texto (. TT). Neste ponto, os arquivos Source. cs serão gerados automaticamente a partir dos arquivos de modelo, de modo que o aplicativo funcionará como antes.

  Em seguida, você pode pegar uma parte do código e substituí-la por uma expressão de modelo de texto, que lê o modelo e gera essa parte do arquivo de origem. Pelo menos um valor do modelo deve gerar a origem original para que, novamente, você possa executar o aplicativo e ele funcionará como antes. Depois de testar diferentes valores de modelo, você pode passar para a inserção de expressões de modelo em outra parte do código.

  Esse método incremental significa que a geração de código geralmente é uma abordagem de baixo risco. Os aplicativos resultantes geralmente executam quase, bem como uma versão escrita manual.

  No entanto, se você começar com um aplicativo existente, poderá descobrir que muita refatoração é necessária para separar os diferentes comportamentos governados pelo modelo para que eles possam ser variados independentemente. Recomendamos que você avalie esse aspecto do aplicativo ao estimar o custo do seu projeto.

## <a name="configuring-your-application-from-a-model"></a>Configurando seu aplicativo a partir de um modelo
 Se você quiser variar o comportamento do aplicativo em tempo de execução, não poderá usar a geração de código, que gera o código-fonte antes da compilação do aplicativo. Em vez disso, você pode criar seu aplicativo para ler o modelo e variar seu comportamento de acordo. Para obter mais informações, consulte:

- [Como abrir um modelo a partir de um arquivo no código do programa](../modeling/how-to-open-a-model-from-file-in-program-code.md)

  Esse método também pode ser aplicado incrementalmente, mas há mais trabalho no início. Você precisa escrever o código que lerá o modelo e configurar uma estrutura que permita que seus valores sejam acessíveis para as partes variáveis. Tornar as partes variáveis genéricas é mais cara do que a geração de código.

  Um aplicativo genérico geralmente é executado menos bem do que suas contrapartes específicas. Se o desempenho for crucial, seu plano de projeto deverá incluir uma avaliação desse risco.

## <a name="developing-a-derived-application"></a>Desenvolvendo um aplicativo derivado
 Você pode encontrar as seguintes diretrizes gerais úteis.

- **Iniciar específico e generalizar.** Grave uma versão específica do seu aplicativo primeiro. Essa versão deve funcionar em um conjunto de condições. Quando estiver satisfeito de estar funcionando corretamente, você poderá fazer com que parte dele derive de um modelo. Estenda as partes derivadas gradualmente.

     Por exemplo, crie um site que tenha um conjunto específico de páginas da Web antes de criar um aplicativo Web que apresenta páginas definidas em um modelo.

- **Modele os aspectos variantes.** Identifique os aspectos que irão variar, seja entre uma implantação e outra, ou ao longo do tempo conforme os requisitos mudam. Esses são os aspectos que devem ser derivados de um modelo.

     Por exemplo, se o conjunto de páginas da Web e os links entre elas forem alterados, mas o estilo e o formato das páginas forem sempre iguais, o modelo deverá descrever os links, mas não precisará descrever o formato das páginas.

- **Preocupações separadas.** Se os aspectos variáveis puderem ser divididos em áreas independentes, use modelos separados para cada área. Usando o ModelBus, você pode definir operações que afetam os dois modelos e restrições entre eles.

     Por exemplo, use um modelo para definir a navegação entre as páginas da Web e um modelo diferente para definir o layout das páginas.

- **Modele o requisito, não a solução.** Projete o modelo para que ele descreva os requisitos do usuário. Por outro lado, não projete a notação de acordo com os aspectos variáveis da implementação.

     Por exemplo, o modelo de navegação da Web deve representar páginas da Web e hiperlinks entre elas. O modelo de navegação na Web não deve representar fragmentos de HTML ou classes em seu aplicativo.

- **Gerar ou interpretar?** Se os requisitos para uma implantação específica raramente forem alterados, gere o código do programa do modelo. Se os requisitos forem alterados com frequência ou coexistirem em mais de uma variante na mesma implantação, grave o aplicativo para que ele possa ler e interpretar um modelo.

     Por exemplo, se você usar o modelo de site para desenvolver uma série de sites diferentes e instalados separadamente, você deverá gerar o código do site a partir do modelo. Mas você usa seu modelo para controlar um site que é alterado todos os dias, então é melhor escrever um servidor Web que leia o modelo e apresente o site de acordo.

- **UML ou DSL?** Considere criar sua notação de modelagem usando estereótipos para estender o UML. Defina uma DSL se não houver nenhum diagrama UML que atenda à finalidade. Mas Evite interromper a semântica padrão do UML.

     Por exemplo, um diagrama de classes UML é uma coleção de caixas e setas; com essa notação, você pode, teoricamente, definir qualquer coisa. Mas não recomendamos que você use o diagrama de classe, exceto onde você está, na verdade, descrevendo um conjunto de tipos. Por exemplo, você poderia adaptar os diagramas de classe para descrever diferentes tipos de páginas da Web.

## <a name="see-also"></a>Veja também

- [Gerando código a partir de uma linguagem específica do domínio](../modeling/generating-code-from-a-domain-specific-language.md)
- [Como abrir um modelo a partir de um arquivo no código do programa](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [Geração de código na hora de design usando modelos de texto T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
