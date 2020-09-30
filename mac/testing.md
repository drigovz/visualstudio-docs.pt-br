---
title: Ferramentas de teste de Visual Studio para Mac
ms.date: 08/03/2020
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio for Mac]
- unit tests [Visual Studio for Mac]
ms.author: jomatthi
author: jmatthiesen
ms.openlocfilehash: 758bdcb0d854247847e4d0d56152840643402bf4
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91580955"
---
# <a name="testing-tools-in-visual-studio-for-mac"></a>Ferramentas de teste no Visual Studio para Mac

Visual Studio para Mac ferramentas de teste podem ajudá-lo e sua equipe a desenvolver e sustentar altos padrões de excelência de código. Os testes de unidade podem ser escritos e executados usando o Microsoft Unit Test Framework (MSTest), xUnit ou NUnit.

## <a name="creating-tests"></a>Criando testes
Para começar a usar o teste, você pode criar um novo projeto de teste em sua solução clicando com o botão direito do mouse em sua solução e escolhendo o menu **adicionar > novo projeto...** . Em seguida, escolha uma das categorias de teste no lado esquerdo da caixa de diálogo (por exemplo, a **Web e Console >** a categoria de testes). Selecione o tipo de projeto de teste que você deseja criar e clique em Avançar. Siga as instruções nas caixas de diálogo que aparecem e um novo projeto de teste será adicionado à sua solução.

![Diálogo novo projeto com a seção Web e console > testes selecionados, mostrando os projetos xUnit, MSTest e NUnit](media/create-new-test-project.PNG)

> [!NOTE]
> Para obter mais informações sobre o teste de unidade de seus aplicativos .NET Core e a seleção de estruturas de teste de unidade, consulte os [testes de unidade no .NET Core e .net Standard](/dotnet/core/testing/?pivots=xunit) documentação.

## <a name="running-tests"></a>Executando testes
A janela de **testes de unidade** é usada para executar testes de unidade e é aberta usando o menu **exibir > painéis > testes de unidade** . Os testes de unidade em sua solução são automaticamente descobertos e mostrados nesta janela, onde você pode executar todos os testes ou um conjunto de testes que você selecionou.

![Janela de teste mostrando uma lista de testes de unidade e uma barra de ferramentas para executar ou interromper testes.](media/test-window.PNG)

Ao editar uma classe C# que contém testes de unidade, você pode executar testes clicando com o botão direito do mouse na classe de teste ou em um método de teste e escolhendo o menu **Executar teste (s)** ou **teste (s) de depuração** . A escolha do item de menu **Executar teste (s)** executará os testes na janela de teste, escolhendo que o menu **teste (s) de depuração** fará o mesmo e anexará o depurador para que você possa solucionar problemas de seu código.

![Menu de atalho do editor com opções de testes de execução e depuração](media/run-tests-context-menu.PNG)

À medida que os testes estão em execução, uma janela **resultados de teste** é exibida para que você possa examinar os testes bem-sucedidos ou com falha e a saída da execução desses testes.

![Janela de resultados de teste mostrando um teste com falha e uma contagem de 21 testes aprovados e 1 teste com falha.](media/test-results-window.PNG)

## <a name="see-also"></a>Confira também

- [Teste de unidade no .NET Core e no .NET Standard](/dotnet/core/testing)
- [Introdução ao teste de unidade (Visual Studio no Windows)](/visualstudio/test/getting-started-with-unit-testing)
- [Noções básicas do teste de unidade (Visual Studio no Windows)](/visualstudio/test/unit-test-basics)