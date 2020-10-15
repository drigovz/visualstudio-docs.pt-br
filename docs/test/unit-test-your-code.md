---
title: Teste de unidade
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: be0f8f7eeb116a251477ce57027a2176119c2d17
ms.sourcegitcommit: 9c57730000d5ced37d3887f3928b17076f49d0f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099304"
---
# <a name="unit-test-your-code"></a>Efetue testes de unidade em seu código

Os testes de unidade fornecem aos desenvolvedores e testadores uma maneira rápida de procurar por erros lógicos nos métodos de classes em projetos do C#, do Visual Basic e do C++.

As ferramentas de testes de unidade incluem:

* **Gerenciador** &mdash; de testes Executar testes de unidade e ver seus resultados no **Gerenciador de testes**. Você pode usar qualquer estrutura de teste de unidade, incluindo estruturas de terceiros, que tenha um adaptador para o **Gerenciador de Testes**.

* **Estrutura de teste de unidade da Microsoft para código gerenciado** &mdash; A estrutura de teste de unidade da Microsoft para código gerenciado é instalada com o Visual Studio e fornece uma estrutura para testar o código .NET.

* **Estrutura de teste de unidade da Microsoft para C++** &mdash; A estrutura de teste de unidade da Microsoft para C++ é instalada como parte do **desenvolvimento de desktop com** carga de trabalho do c++. Ela fornece uma estrutura para testar o código nativo. As estruturas do Google Test, Boost.Test e CTest também estão incluídas e adaptadores de terceiros estão disponíveis para estruturas de teste adicionais. Para obter mais informações, confira [Escrever testes de unidade para C/C++](../test/writing-unit-tests-for-c-cpp.md).

* Ferramentas de cobertura de **código** &mdash; Você pode determinar a quantidade de código do produto que sua unidade testa em exercício de um comando no Gerenciador de testes.

* Estrutura de isolamento de **falsificações da Microsoft** &mdash; A estrutura de isolamento de falsificações da Microsoft pode criar classes e métodos substitutos para produção e código do sistema que criam dependências no código em teste. Ao implementar os delegados falsos para uma função, você controla o comportamento e a saída do objeto de dependência.

Você também pode usar o [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) para explorar seu código .NET para gerar dados de teste e um conjunto de testes de unidade. Para cada instrução no código, é gerada uma entrada de teste para executar essa instrução. Uma análise de caso é realizada para cada branch condicional do código.

## <a name="key-tasks"></a>Tarefas-chave

Use os artigos a seguir para ajudar com o entendimento e a criação dos testes de unidade:

|Tarefas|Tópicos associados|
|-|-----------------------|
|**Guias de início rápido e orientações:** Saiba mais sobre os testes de unidade no Visual Studio nos exemplos de código.|- [Walkthrough: criar e executar testes de unidade para código gerenciado](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />- [Início rápido: desenvolvimento controlado por testes com o Gerenciador de testes](../test/quick-start-test-driven-development-with-test-explorer.md)<br />- [Como: Adicionar testes de unidade a aplicativos C++](../test/how-to-use-microsoft-test-framework-for-cpp.md)|
|**Teste de unidade com o gerenciador de testes:** saiba como o gerenciador de testes pode ajudar a criar testes de unidade mais produtivos e eficientes.|- [Noções básicas do teste de unidade](../test/unit-test-basics.md)<br />- [Criar um projeto de teste de unidade](../test/create-a-unit-test-project.md)<br />- [Executar testes de unidade com o Gerenciador de testes](../test/run-unit-tests-with-test-explorer.md)<br />- [Instalar estruturas de teste de unidade de terceiros](../test/install-third-party-unit-test-frameworks.md)|
|**Código C++ do teste de unidade**|- [Gravar testes de unidade para C/C++](../test/writing-unit-tests-for-c-cpp.md)|
|**Isolamento de testes de unidade**|- [Isolar código em teste com falsificações da Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Uso da cobertura de código para identificar qual proporção do código do projeto é testada:** saiba mais sobre o recurso de cobertura de código das ferramentas de teste do Visual Studio.|- [Use a cobertura de código para determinar a quantidade de código que está sendo testada](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Executar análise de estresse e desempenho usando testes de carga:** Saiba como criar testes de carga para ajudar a isolar problemas de desempenho e estresse em seu aplicativo.|- [Início rápido: criar um projeto de teste de carga](../test/quickstart-create-a-load-test-project.md)<br />- [Teste de carga (Azure Test Plans e TFS)](/azure/devops/test/load-test/index?view=vsts&preserve-view=true)|
|**Definir Gates de qualidade:** Saiba como criar Gates de qualidade para impor que os testes sejam executados antes do check-in ou mesclagem do código.|- [Políticas de check-in (TFVC do Azure Repos)](/azure/devops/repos/tfvc/add-check-policies?view=vsts&preserve-view=true)|
|**Definir opções de teste:** Saiba como configurar opções de teste, por exemplo, onde os resultados de teste são armazenados.|[Configurar testes de unidade usando um arquivo .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="api-reference-documentation"></a>Documentação da referência de API

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> descreve o namespace UnitTesting, que fornece atributos, exceções, asserções e outras classes que oferecem suporte a testes de unidade.
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> descreve o namespace UnitTesting.Web, que estende o namespace UnitTesting dando suporte para o ASP.NET e a testes de unidade do serviço Web.

## <a name="see-also"></a>Veja também

- [Melhorar a qualidade do código](../test/improve-code-quality.md)