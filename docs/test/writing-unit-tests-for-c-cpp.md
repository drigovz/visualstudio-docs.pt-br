---
title: Escrever testes de unidade para C/C++
description: Escreva testes de unidade C++ no Visual Studio usando várias estruturas de teste, incluindo CTest, Boost.Test e Google Test.
ms.date: 02/08/2020
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 0eaf41dc0bf3e21dfbf4018261844181d594f0d5
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649610"
---
# <a name="write-unit-tests-for-cc-in-visual-studio"></a>Gravar testes de unidade para C/C++ no Visual Studio

Você pode escrever e executar seus testes de unidade C++ usando a janela **Test Explorer.** Funciona como em outras línguas. Para saber mais sobre como usar o **Gerenciador de Testes**, consulte [Executar testes de unidade com o Gerenciador de Testes](run-unit-tests-with-test-explorer.md).

> [!NOTE]
> Não há suporte para alguns recursos no C++, como o Live Unit Testing, Testes de Interface do Usuário Codificados e IntelliTest.

O Visual Studio inclui estas estruturas de teste para C++, sem a necessidade de fazer outros downloads:

- Microsoft Unit Testing Framework para C/C++
- Google Test
- Boost.Test
- CTest

Além de usar as estruturas instaladas, você pode escrever seu próprio adaptador de teste para qualquer estrutura que você gostaria de usar dentro do Visual Studio. Um adaptador de teste pode integrar testes de unidade à janela **Gerenciador de Testes**. Vários adaptadores de terceiros são disponibilizados no [Visual Studio Marketplace](https://marketplace.visualstudio.com). Para obter mais informações, consulte [Instalar estruturas de teste de unidades de terceiros](install-third-party-unit-test-frameworks.md).

**Visual Studio 2017 e posterior (Professional e Enterprise)**

Os projetos de teste de unidade C++ são compatíveis com o [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md).

**Visual Studio 2017 e posterior (todas as edições)**

- **O Adaptador de Teste do Google** é incluído como um componente padrão do desenvolvimento da área de trabalho com carga de trabalho **C++.** Ele tem um modelo de projeto que você pode adicionar a uma solução. Use o menu adicionar novo **projeto** com o botão direito do mouse no nó da solução no **Solution Explorer** para adicioná-lo. Ele também tem opções que você pode configurar através **de opções de ferramentas.** > **Options** Para obter mais informações, consulte [Como: Usar o Teste do Google no Visual Studio](how-to-use-google-test-for-cpp.md).

- **Boost.Test** é incluído como um componente padrão do desenvolvimento da área de trabalho com carga de trabalho **C++.** Ele é integrado com **o Test Explorer,** mas atualmente não tem um modelo de projeto. Deve ser configurado manualmente. Para obter mais informações, consulte [Como: Usar boost.test no Visual Studio](how-to-use-boost-test-for-cpp.md).

- O suporte para **CTest** está incluído no componente **Ferramentas CMake para C++**, que faz parte da carga de trabalho **Desenvolvimento para desktop com C++**. Para obter mais informações, consulte [Como: Usar CTest no Visual Studio](how-to-use-ctest-for-cpp.md).

**Visual Studio 2015 e versões anteriores**

Você pode baixar as extensões do adaptador de teste do Google e do Adaptador Boost.Test no Visual Studio Marketplace. Encontre-os no [adaptador de teste para o adaptador Boost.Test](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforBoostTest) e [Test para o Teste do Google](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.TestAdapterforGoogleTest).

## <a name="basic-test-workflow"></a>Fluxo de trabalho básico de teste

As seções a seguir mostram as etapas básicas para começar os testes de unidade para C++. A configuração básica é semelhante tanto para as estruturas de teste da Microsoft quanto do Google. O Boost.Test requer a criação manual de um projeto de teste.

::: moniker range="vs-2019"

### <a name="create-a-test-project-in-visual-studio-2019"></a>Crie um projeto de teste no Visual Studio 2019

Você define e executa testes dentro de um ou mais projetos de teste. Você cria os projetos na mesma solução que o código que deseja testar. Para adicionar um novo projeto de teste a uma solução existente, clique com o botão direito do mouse no nó Solução no **Solution Explorer**. No menu pop-up, escolha **Adicionar** > **novo projeto**. Defina **Linguagem de programação** como C++ e digite "teste" na caixa de pesquisa. A ilustração a seguir mostra os projetos de teste que estão disponíveis quando o **Desenvolvimento de área de trabalho com C++** e a carga de trabalho **Desenvolvimento de UWP** estão instalados:

![Projetos de teste C++ no Visual Studio 2019](media/vs-2019/cpp-new-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

### <a name="create-a-test-project-in-visual-studio-2017"></a>Crie um projeto de teste no Visual Studio 2017

Você define e executa testes dentro de um ou mais projetos de teste. Você cria os projetos na mesma solução que o código que deseja testar. Para adicionar um novo projeto de teste, clique com o botão direito do mouse no nó Solução no **Solution Explorer** e escolha **Adicionar** > **novo projeto**. No painel esquerdo, escolha **o teste Visual C++.** Em seguida, escolha um dos tipos de projeto no painel central. A ilustração a seguir mostra os projetos de teste disponibilizados quando a carga de trabalho **Desenvolvimento de Área de Trabalho com C++** é instalada:

![Projetos de teste C++](media/cpp-new-test-project.png)

::: moniker-end

### <a name="create-references-to-other-projects-in-the-solution"></a>Criar referências a outros projetos na solução

Para habilitar o acesso às funções do projeto em teste, adicione uma referência ao projeto em seu projeto de teste. Clique com o botão direito do mouse no nó do projeto de teste no **Solution Explorer** para obter um menu pop-up. Escolha **adicionar** > **referência**. Na caixa de diálogo Adicionar referência, escolha os projetos que deseja testar.

![Adicionar referência](media/cpp-add-ref-test-project.png)

### <a name="link-to-object-or-library-files"></a>Vincular a arquivos de biblioteca ou objeto

Se o código de teste não exportar as funções que você deseja testar, será possível adicionar os arquivos .obj ou .lib de saída para as dependências do projeto de teste. Para obter mais informações, consulte [Para vincular os testes aos arquivos do objeto ou da biblioteca](how-to-use-microsoft-test-framework-for-cpp.md#object_files).

### <a name="add-include-directives-for-header-files"></a>Adicionar diretivas de inclusão aos arquivos de cabeçalho

Em seguida, no arquivo *.cpp* do teste de unidade, adicione uma diretiva `#include` a todos os arquivos de cabeçalho que declaram os tipos e as funções que você deseja testar. Digite `#include "` e, depois, o IntelliSense será ativado para ajudá-lo a escolher. Repita essas etapas nos outros cabeçalhos.

![Adicionar diretivas de inclusão](media/cpp-add-includes-test-project.png)

Para evitar ter que digitar o caminho completo em cada declaração de incluir no arquivo de origem, você pode adicionar as pastas necessárias nas**propriedades** >  **do projeto** > **C/C++** > **Diretórios adicionais adicionais****gerais** > .

### <a name="write-test-methods"></a>Gravar métodos de teste

> [!NOTE]
> Esta seção mostra a sintaxe da Microsoft Unit Testing Framework para C/C++. Ela está documentada na [Referência de API do Microsoft.VisualStudio.TestTools.CppUnitTestFramework](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). Para obter a documentação do Google Test, confira [Prévia do Google Test](https://github.com/google/googletest/blob/master/googletest/docs/primer.md). Quanto ao Boost.Test, confira [Biblioteca do Boost Test: a estrutura de teste de unidade](https://www.boost.org/doc/libs/1_46_0/libs/test/doc/html/utf.html).

O arquivo *.cpp* em seu projeto de teste tem uma classe de stub e um método definidos para você. Eles mostram um exemplo de como escrever código de teste. As assinaturas usam as macros TEST_CLASS e TEST_METHOD, que tornam os métodos descobertos a partir da janela **do Test Explorer.**

![Adicionar diretivas de inclusão](media/cpp-write-test-methods.png)

TEST_CLASS e TEST_METHOD fazem parte do [Framework de Teste Nativo da Microsoft](microsoft-visualstudio-testtools-cppunittestframework-api-reference.md). O **Gerenciador de Testes** descobre os métodos de teste em outras estruturas com suporte, de maneira semelhante.

Um TEST_METHOD retorna nulo. Para produzir um resultado do teste, use os métodos estáticos na classe `Assert` para testar os resultados reais em relação a o que é esperado. No exemplo a seguir, considere que `MyClass` tem um construtor que usa uma `std::string`. É possível testar se o construtor inicializa a classe conforme o esperado da seguinte forma:

```cpp
TEST_METHOD(TestClassInit)
{
    std::string name = "Bill";
    MyClass mc(name);
    Assert::AreEqual(name, mc.GetName());
}
```

No exemplo anterior, o resultado da chamada `Assert::AreEqual` determina o resultado do teste: aprovação ou falha. A classe Assert contém vários outros métodos para comparar os resultados esperados aos resultados reais.

Você pode adicionar *características* aos métodos de teste para especificar proprietários de teste, prioridade e outras informações. Depois, é possível usar esses valores para classificar e agrupar os testes no **Gerenciador de Testes**. Para obter mais informações, consulte [Executar testes de unidade com o Gerenciador de Testes](run-unit-tests-with-test-explorer.md).

### <a name="run-the-tests"></a>Executar os testes

1. No menu **Teste**, escolha **Windows** > **Gerenciador de Testes**. A ilustração a seguir mostra um projeto de teste cujos testes ainda não foram executados.

   ![Test Explorer antes de executar testes](media/cpp-test-explorer.png)

   > [!NOTE]
   > A integração do CTest com o **Gerenciador de Testes** ainda não está disponível. Execute testes de CTest no menu principal do CMake.

1. Se nem todos os seus testes estiverem visíveis na janela, construa o projeto de teste clicando com o botão direito do mouse no nó no **Solution Explorer** e escolhendo **Build** or **Rebuild**.

1. No **Test Explorer,** escolha **Executar tudo**ou selecione os testes específicos que deseja executar. Clique com o botão direito do mouse para ver outras opções, incluindo a execução em modo de depuração com pontos de interrupção habilitados. Depois de executar todos os testes, a janela mostrará quais testes foram aprovados e quais falharam:

![Gerenciador de Testes depois da execução dos testes](media/cpp-test-explorer-passed.png)

Para testes com falha, a mensagem mostra detalhes que ajudam a diagnosticar a causa. Clique com o botão direito do mouse no teste de falha para um menu pop-up. Escolha **Depuração Testes selecionados** para passar pela função onde ocorreu a falha.

Para saber mais sobre como usar o **Gerenciador de Testes**, consulte [Executar testes de unidade com o Gerenciador de Testes](run-unit-tests-with-test-explorer.md).

Para obter mais informações relacionadas ao teste unitário, consulte [os fundamentos básicos do teste unitário](unit-test-basics.md)

## <a name="use-codelens"></a>Usar o CodeLens

**Visual Studio 2017 e posterior (edições Professional e Enterprise)**

[CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) permite que você veja rapidamente o status de um teste de unidade sem sair do editor de código.

Você pode inicializar o CodeLens para um projeto de teste de unidade do C++ em qualquer uma das seguintes formas:

- Editar e compilar sua solução ou projeto de teste.
- Recompilar sua solução ou projeto.
- Execute testes da janela do Explorador de **Teste.**

Depois de inicializado, você pode ver ícones de status de teste acima de cada teste de unidade.

![Ícones do CodeLens C++](media/cpp-test-codelens-icons.png)

Clique no ícone para obter mais informações ou para executar ou depurar o teste de unidade:

![Execução e depuração do CodeLens C++](media/cpp-test-codelens-run-debug.png)

## <a name="see-also"></a>Confira também

- [Unidade teste seu código](unit-test-your-code.md)
