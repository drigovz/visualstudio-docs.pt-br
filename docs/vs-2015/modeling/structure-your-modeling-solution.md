---
title: Estruturar sua solução de modelagem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2ba70ba4-2cea-4e01-93c2-055903d59470
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: edf9eaee512eda7439d1beea7303cd0e74b27178
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661034"
---
# <a name="structure-your-modeling-solution"></a>Estruturar a solução de modelagem

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para usar modelos com eficiência em um projeto de desenvolvimento, os integrantes da equipe devem ser capazes de trabalhar em modelos de partes diferentes do projeto ao mesmo tempo. Este tópico sugere um esquema para dividir o aplicativo em diferentes partes que correspondem às camadas em um diagrama de camadas geral.

Para iniciar em um projeto ou subprojeto rapidamente, é útil ter um modelo de projeto que segue a estrutura do projeto que você escolheu. Este tópico descreve como criar e usar um modelo desse tipo.

Este tópico pressupõe que você está trabalhando em um projeto que é grande o suficiente para exigir vários membros da equipe e talvez tenha várias equipes. O código e os modelos do projeto são armazenados em um sistema de controle do código-fonte, como [!INCLUDE[esprtfs](../includes/esprtfs-md.md)]. Pelo menos alguns membros da equipe usam o Visual Studio para desenvolver modelos e outros membros da equipe podem exibir os modelos usando outras versões do Visual Studio.

Para ver quais versões do Visual Studio dão suporte a cada ferramenta e recurso de modelagem, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="solution-structure"></a>Estrutura da solução

Em um projeto médio ou grande, a estrutura da equipe é baseada na estrutura do aplicativo. Cada equipe usa uma solução do Visual Studio.

#### <a name="to-divide-an-application-into-layers"></a>Para dividir um aplicativo em camadas

1. Baseie a estrutura de suas soluções na estrutura do seu aplicativo, como aplicativo Web, aplicativo de serviço ou aplicativo de área de trabalho. Uma variedade de arquiteturas comuns é discutida em [arquétipos de aplicativo no guia de arquitetura de aplicativos da Microsoft](http://go.microsoft.com/fwlink/?LinkId=196681).

2. Crie uma solução de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], que chamaremos de solução de arquitetura. Essa solução será usada para criar o design geral do sistema. Ele conterá modelos, mas sem código.

    Adicione um diagrama de camada a esta solução. No diagrama de camadas, desenhe a arquitetura que você escolheu para seu aplicativo. Por exemplo, o diagrama pode mostrar essas camadas e as dependências entre elas: apresentação; Lógica de negócios; e dados.

    Você pode criar o diagrama de camadas e uma nova solução do Visual Studio ao mesmo tempo usando o **novo comando UML ou diagrama de camada** no menu **arquitetura** .

3. Adicione aos diagramas UML do modelo de arquitetura que representam os conceitos comerciais importantes e os casos de uso referenciados no design de todas as camadas.

4. Crie uma solução do Visual Studio separada para cada camada no diagrama da camada de arquitetura.

    Essas soluções serão usadas para desenvolver o código das camadas.

5. Crie modelos UML que representarão os designs das camadas e os conceitos que são comuns a todas as camadas. Organize os modelos para que todos os modelos possam ser vistos na solução de arquitetura e os modelos relevantes possam ser vistos em cada camada.

    Você pode conseguir isso usando qualquer um dos procedimentos a seguir. A primeira alternativa cria um projeto de modelagem separado para cada camada, e a segunda cria um único projeto de modelagem que é compartilhado entre as camadas.

###### <a name="to-use-a-separate-modeling-project-for-each-layer"></a>Para usar um projeto de modelagem separado para cada camada

1. Crie um projeto de modelagem em cada solução de camada.

    Esse modelo conterá diagramas UML que descrevem os requisitos e o design dessa camada. Ele também pode conter diagramas de camada que mostram camadas aninhadas.

    Agora você tem um modelo para cada camada, além de um modelo para a arquitetura do aplicativo. Cada modelo está contido em sua própria solução. Isso permite que os membros da equipe trabalhem nas camadas ao mesmo tempo.

2. Para a solução de arquitetura, adicione o projeto de modelagem de cada solução de camada. Para fazer isso, abra a solução de arquitetura. Em Gerenciador de Soluções, clique com o botão direito do mouse no nó da solução, aponte para adicionar e clique em **projeto existente**. Navegue até o projeto de modelagem (. modelproj) em uma solução de camada.

    Cada modelo agora é visível em duas soluções: sua solução "inicial" e a solução de arquitetura.

3. Para o projeto de modelagem de cada camada, adicione um diagrama de camada. Comece com uma cópia do diagrama da camada de arquitetura. Você pode excluir partes que não são dependências do diagrama de camadas.

    Você também pode adicionar diagramas de camada que representam a estrutura detalhada dessa camada.

    Esses diagramas são usados para validar o código que é desenvolvido nessa camada.

4. Na solução arquitetura, edite os requisitos e modelos de design de todas as camadas usando o Visual Studio.

    Em cada solução de camada, desenvolva o código para essa camada, referindo-se ao modelo. Se você for conteúdo para fazer o desenvolvimento sem usar o mesmo computador para atualizar o modelo, poderá ler o modelo e desenvolver o código usando versões do Visual Studio que não podem criar modelos. Você também pode gerar código do modelo nessas versões.

    Esse método garante que nenhuma interferência será causada por desenvolvedores que editem os modelos de camada ao mesmo tempo.

    No entanto, como os modelos são separados, é difícil se referir a conceitos comuns. Cada modelo deve ter sua própria cópia dos elementos nos quais ele depende de outras camadas e da arquitetura. O diagrama de camada em cada camada deve ser mantido em sincronia com o diagrama da camada de arquitetura. É difícil manter a sincronização quando esses elementos são alterados, embora você possa desenvolver ferramentas para fazer isso.

###### <a name="to-use-a-separate-package-for-each-layer"></a>Para usar um pacote separado para cada camada

1. Na solução para cada camada, adicione o projeto de modelagem de arquitetura. Em Gerenciador de Soluções, clique com o botão direito do mouse no nó da solução, aponte para **Adicionar**e clique em **projeto existente**. O único projeto de modelagem agora pode ser acessado a partir de cada solução: o projeto de arquitetura e o projeto de desenvolvimento para cada camada.

2. No modelo UML compartilhado, crie um pacote para cada camada: em Gerenciador de Soluções, selecione o projeto de modelagem. No Gerenciador de modelos UML, clique com o botão direito do mouse no nó raiz do modelo, aponte para **Adicionar**e clique em **pacote**.

    Cada pacote conterá diagramas UML que descrevem os requisitos e o design da camada correspondente.

3. Se necessário, adicione diagramas de camada local para a estrutura interna de cada camada.

    Esse método permite que os elementos de design de cada camada façam referência direta às camadas e à arquitetura comum da qual ela depende.

    Embora o trabalho simultâneo em pacotes diferentes possa causar alguns conflitos, eles são razoavelmente fáceis de gerenciar, pois os pacotes são armazenados em arquivos separados. A maior dificuldade é causada pela exclusão de um elemento que é referenciado de um pacote dependente. Para obter mais informações, consulte [gerenciar modelos e diagramas sob controle de versão](../modeling/manage-models-and-diagrams-under-version-control.md).

## <a name="creating-architecture-templates"></a>Criando modelos de arquitetura

Na prática, você não criará todas as suas soluções do Visual Studio ao mesmo tempo, mas as adicionará à medida que o projeto progride. Você provavelmente também usará a mesma estrutura de solução em projetos futuros.  Para ajudá-lo a criar novas soluções rapidamente, você pode criar um modelo de solução ou de projeto. Você pode capturar o modelo em uma extensão de integração do Visual Studio (VSIX) para que seja fácil de distribuir e instalar em outros computadores.

Por exemplo, se você usa com frequência as soluções que têm camadas de apresentação, de negócios e de dados, você pode configurar um modelo que criará novas soluções que tenham essa estrutura.

#### <a name="to-create-a-solution-template"></a>Para criar um modelo de solução

1. [Baixe e instale o assistente de exportação de modelo](http://go.microsoft.com/fwlink/?LinkId=196686), caso ainda não tenha feito isso.

2. Crie a estrutura da solução que você deseja usar como ponto de partida para projetos futuros.

3. No menu **arquivo** , clique em **Exportar modelo como VSIX**. O **Assistente para exportar modelo como VSIX** é aberto.

4. Seguindo as instruções no assistente, selecione os projetos que você deseja incluir no modelo, forneça um nome e uma descrição para o modelo e especifique um local de saída.

> [!NOTE]
> O material neste tópico é dissociado e parafraseado das diretrizes de ferramentas de arquitetura do Visual Studio, escrito pelo Visual Studio ALM Rangers, que é uma colaboração entre MVPs (maior valor para profissionais), serviços da Microsoft e o Visual Studio equipe e gravadores de produto. [Clique aqui para baixar o pacote de diretrizes completo.](http://go.microsoft.com/fwlink/?LinkID=191984)

## <a name="related-materials"></a>Materiais relacionados

[Organizando e gerenciando seus modelos](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-9-Organizing-and-Managing-Your-Models/) – vídeo de Clint Edmondson.

[Diretrizes de ferramentas de arquitetura do Visual Studio](../modeling/visual-studio-architecture-tooling-guidance.md) – diretrizes adicionais sobre como gerenciar modelos em uma equipe

## <a name="see-also"></a>Consulte também

[Gerenciar modelos e diagramas sob controle de versão](../modeling/manage-models-and-diagrams-under-version-control.md) 
[usar modelos em seu processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)
