---
title: Visão geral das Ferramentas de Linguagem Específica do Domínio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75d1a9fc5ac7fa35afb53c89f5af016ed909d11e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55915949"
---
# <a name="overview-of-domain-specific-language-tools"></a>Visão geral das Ferramentas de Linguagem Específica do Domínio
Ferramentas de linguagem específica do domínio (ferramentas DSL), que são hospedados no Visual Studio, permitem que você criar uma linguagem específica de domínio e, em seguida, gerar tudo o que os usuários devem ter para criar modelos que são baseados na linguagem.

 As ferramentas a seguir estão incluídas nas Ferramentas DSL:

-   um assistente de projeto que usa modelos de solução diferentes para ajudá-lo a começar a desenvolver sua linguagem específica de domínio.

-   um designer gráfico para criar e editar sua definição de linguagem específica de domínio.

-   um mecanismo de validação que verifica se a definição de linguagem específica de domínio está bem formada e exibe erros e avisos quando há problemas.

-   um gerador de código que usa uma definição de linguagem específica de domínio como entrada e produz o código-fonte como saída.

## <a name="the-dsl-tools-solution"></a>A solução de Ferramentas DSL
 O Assistente de Designer Específico de Domínio fornece os seguintes modelos de solução:

- Fluxo de tarefas

- Diagramas de classe

- Linguagem mínima

- Modelos de componente

- WPF mínimo

- Windows.Forms mínimo

- Biblioteca de DSL

  Para obter mais informações, confira [Escolhendo um modelo de solução de linguagem específica de domínio](../modeling/choosing-a-domain-specific-language-solution-template.md).

  O assistente cria uma solução do Visual Studio que tem os seguintes projetos:

- Dsl

   O projeto DSL define a linguagem específica de domínio e suas ferramentas de edição e de processamento.

- **DslPackage**

   O projeto DslPackage determina como as ferramentas de linguagem integram com o Visual Studio.

## <a name="the-dsl-tools-graphical-interface"></a>A Interface gráfica das Ferramentas DSL
 Você pode usar a interface gráfica das Ferramentas DSL para adicionar elementos e relacionamentos à sua linguagem específica de domínio. Depois de adicionar os elementos, você poderá definir a aparência deles mapeando-os para formas, personalizando cores e adicionando decoradores. Você também pode adicionar elementos à caixa de ferramentas.

## <a name="validation-in-dsl-tools"></a>Validação nas Ferramentas DSL
 As DSL fornecem um nível de validação para verificar se o modelo de domínio atende aos requisitos básicos para geração de código. Normalmente, ao criar sua própria linguagem específica de domínio, você adicionaria sua própria validação para expressar suas regras de lógica de negócios. Para obter mais informações sobre a validação personalizada, confira [Validação em uma linguagem específica de domínio](../modeling/validation-in-a-domain-specific-language.md).

 É recomendável que você valide a linguagem específica de domínio com frequência durante sua criação. Se sua linguagem específica de domínio tiver erros de validação, você não poderá gerar o código-fonte. O processo de geração de código-fonte usando modelos é executado clicando em **Transformar Todos os Modelos** na barra de ferramentas do Gerenciador de Soluções. Sempre que você modificar a definição de linguagem, clique em **Transformar Todos os Modelos**. Para obter mais informações, confira [Como: criar uma solução de linguagem específica de domínio](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="customization-of-dsl-tools"></a>Personalização das Ferramentas DSL
 Você pode fornecer código adicional para refinar o comportamento do modelo e definir restrições em seu idioma. Se necessário, você pode fazer alterações significativas modificando os modelos de texto.

## <a name="distributing-your-dsl-solution"></a>Distribuindo sua solução de DSL
 Ferramentas DSL gera um pacote que está hospedado no Visual Studio. O pacote exibe uma caixa de ferramentas, um Gerenciador de DSL e outros elementos de interface do usuário que permitem que os usuários criem modelos usando a sua linguagem específica de domínio.

 Quando você compila e executa a solução de DSL Tools no Visual Studio, uma segunda instância do Visual Studio mostra como sua linguagem específica do domínio será exibido para o usuário da linguagem. Depois de verificar se tudo está funcionando corretamente, você poderá distribuir o arquivo `.vsix` que encontrará na pasta de build do projeto DslPackage. Esse arquivo pode ser usado para instalar a DSL como uma extensão do Visual Studio em outros computadores.  Para obter mais informações, confira [Implantando soluções de linguagem específica de domínio](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Consulte também

- [A instância experimental](../extensibility/the-experimental-instance.md)
- [Glossário das Ferramentas de Linguagem Específica de Domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)