---
title: Saiba como testar códigos com o Live Unit Testing
ms.date: 08/31/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 748dfc592fbf7a3b9737e9f418362067b92bb8ff
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594286"
---
# <a name="get-started-with-live-unit-testing"></a>Introdução ao Live Unit Testing

Quando você habilita o Teste de Unidade Ao Vivo em uma solução do Visual Studio, ele retrata visualmente a cobertura do teste e o status de seus testes. O Live Unit Testing também executa dinamicamente testes sempre que você modifica seu código e notifica imediatamente quando suas alterações causam a falha dos testes.

O teste da unidade viva pode ser usado para testar soluções que visam o .NET Framework ou o .NET Core. Neste tutorial, você aprenderá a usar o Live Unit Testing criando uma biblioteca de classes simples que tem como alvo o .NET Standard e criará um projeto MSTest que visa o .NET Core para testá-lo.

A solução C# completa pode ser baixada do repositório [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) no GitHub.

## <a name="prerequisites"></a>Pré-requisitos

Este tutorial requer que você tenha instalado a edição Visual Studio Enterprise com a carga de trabalho **de desenvolvimento multiplataforma .NET Core.**

## <a name="create-the-solution-and-the-class-library-project"></a>Criar a solução e o projeto de biblioteca de classes

Comece criando uma solução do Visual Studio chamada UtilityLibraryes que consiste em um único projeto de biblioteca de classe .NET Standard, StringLibrary.

A solução é apenas um contêiner para um ou mais projetos. Para criar uma solução em branco, abra o Visual Studio e faça o seguinte:

1. Selecione **Arquivo** > **Novo** > **Projeto** no menu de alto nível do Visual Studio.

1. Digite **Solução** na caixa de pesquisa de modelo e selecione o modelo **Solução em Branco**.

   ::: moniker range="vs-2017"

   ![A caixa de diálogo **Novo Projeto**](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Conclua a criação da solução.

Agora que você criou a solução, você criará uma biblioteca de classes chamada StringLibrary que contém uma série de métodos de extensão para trabalhar com strings.

1. No **Solution Explorer,** clique com o botão direito do mouse na solução UtilityLibraries e selecione **Adicionar** > **novo projeto**.

::: moniker range="vs-2017"

2. Na caixa de diálogo **Adicionar Novo Projeto** selecione o nó C# e, em seguida, selecione **.NET Standard**.

   > [!NOTE]
   > Como nossa biblioteca tem como alvo o .NET Standard em vez de uma implementação .NET específica, ela pode ser chamada de qualquer implementação .NET que suporte essa versão do .NET Standard. Para obter mais informações, confira [.NET Standard](/dotnet/standard/net-standard).

3. Selecione o modelo **Biblioteca de classe (.NET Padrão)** no painel direito e insira **StringLibrary** na caixa de texto **Nome,** como mostra a seguinte imagem:

   ![Caixa de diálogo **Adicionar Novo Projeto**](./media/lut-start/add-project-cs.png)

4. Selecione **OK** para criar o projeto.

::: moniker-end

::: moniker range=">=vs-2019"

2. Digite **biblioteca de classes** na caixa de pesquisa de modelo e selecione o modelo **Biblioteca de Classes (.NET Standard)**. Clique em **Avançar**.

   > [!NOTE]
   > Como nossa biblioteca tem como alvo o .NET Standard em vez de uma implementação .NET específica, ela pode ser chamada de qualquer implementação .NET que suporte essa versão do .NET Standard. Para obter mais informações, confira [.NET Standard](/dotnet/standard/net-standard).

3. Nomeie o projeto **StringLibrary**.

4. Clique em **Criar** para criar o projeto.

::: moniker-end

5. Substitua todo o código existente na janela de código pelo código a seguir:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   StringLibrary tem três métodos estáticos:

   - `StartsWithUpper` retornará `true` se uma cadeia de caracteres começar com um caractere maiúsculo, caso contrário, retornará `false`.

   - `StartsWithLower` retornará `true` se uma cadeia de caracteres começar com um caractere minúsculo, caso contrário, retornará `false`.

   - `HasEmbeddedSpaces` retornará `true` se uma cadeia de caracteres contiver um caractere de espaço em branco inserido, caso contrário, retornará `false`.

6. Selecione **Build** > **Build Solution** no menu de alto nível do Visual Studio. A construção deve ter sucesso.

## <a name="create-the-test-project"></a>Criar um projeto de teste

O próximo passo é criar o projeto de teste de unidade para testar a biblioteca StringLibrary. Crie testes de unidade, executando as seguintes etapas:

1. No **Solution Explorer,** clique com o botão direito do mouse na solução UtilityLibraries e selecione **Adicionar** > **novo projeto**.

::: moniker range="vs-2017"

2. Na caixa de diálogo **Adicionar Novo Projeto** selecione o nó C# e, em seguida, selecione **.NET Core**.

   > [!NOTE]
   > Você não precisa escrever os testes de unidade na mesma linguagem da biblioteca de classes.

3. Selecione o modelo **Unit Test Project (.NET Core)** no painel direito e insira **StringLibraryTests** na caixa de texto **Nome,** como mostra a imagem a seguir:

   ![A caixa de diálogo **Adicionar Novo Projeto** do projeto de teste de unidade](./media/lut-start/add-unit-test-cs.png)

4. Selecione **OK** para criar o projeto.

::: moniker-end

::: moniker range=">=vs-2019"

2. Digite **teste de unidade** na caixa de pesquisa de modelo e selecione o modelo **Projeto de Teste de Unidade (.NET Core)**. Clique em **Avançar**.

3. Nomeie o projeto **StringLibraryTests**.

4. Clique em **Criar** para criar o projeto.

::: moniker-end

   > [!NOTE]
   > Este tutorial de introdução usa o Live Unit Testing com o framework de teste do MSTest. Você também pode usar as estruturas de teste xUnit e NUnit.

5. O projeto de teste de unidade não pode acessar automaticamente a biblioteca de classes que ele está testando. Forneça acesso à biblioteca de teste adicionando uma referência ao projeto de biblioteca de classes. Para isso, clique com `StringLibraryTests` o botão direito do mouse no projeto e **selecione Adicionar** > **referência**. Na caixa de diálogo **Gerenciador de** referência, certifique-se de que a guia **Solução** está selecionada e selecione o projeto StringLibrary, conforme mostrado na imagem a seguir.

   ![A caixa de diálogo **Gerenciador de Referências**](./media/lut-start/add-reference.png)

6. Substitua o código de teste de unidade clichê que o modelo fornece pelo código a seguir:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

7. Salve o projeto selecionando o ícone **Salvar** na barra de ferramentas.

8. Como o código de teste da unidade inclui alguns caracteres não-ASCII, o Visual Studio exibe a seguinte caixa de diálogo para avisar que alguns caracteres serão perdidos se você salvar o arquivo em seu formato ASCII padrão. Escolha o botão **Salvar com Outra Codificação**.

   ![Escolha uma codificação de arquivo](media/lut-start/ascii-encoding.png)

9. Na lista de isto de **codificação** da caixa de diálogo **Opções de salvamento antecipado,** escolha **Unicode (UTF-8 sem assinatura) - Página de código 65001**, como mostra a imagem a seguir:

   ![Escolhendo a codificação UTF-8](media/lut-start/utf8-encoding.png)

10. Compibar o projeto de teste da unidade selecionando **build** > **rebuild solution** a partir do menu de alto nível do Visual Studio.

Você criou uma biblioteca de classes e também alguns testes de unidade para ela. Agora você terminou as etapas preliminares necessárias para usar o Live Unit Testing.

## <a name="enable-live-unit-testing"></a>Habilitar o Live Unit Testing

Até agora, embora você tenha escrito os testes para a biblioteca de classes stringlibrary, você não executou-os. O Live Unit Testing executa-os automaticamente ao ser habilitado. Para isso, faça o seguinte:

1. Opcionalmente, selecione a janela de código que contém o código para StringLibrary. Este é *Class1.cs* para um projeto C# ou *Class1.vb* para um projeto Visual Basic. (Esta etapa permite que você inspecione visualmente o resultado de seus testes e a extensão da cobertura de código uma vez que você habilite o teste da unidade ao vivo.)

1. Selecione **Teste** > **Live Unit Testing** > de unidade ao vivo**Iniciar** a partir do menu de alto nível do Visual Studio.

1. O Visual Studio inicia o Live Unit Testing, que executa automaticamente todos os seus testes.

Quando ele termina de executar os testes, o **Gerenciador de Testes** exibe os resultados gerais e o resultado dos testes individuais. Além disso, a janela de código exibe graficamente a cobertura de código de teste e o resultado dos testes. Como mostra a imagem a seguir, todos os três testes foram executados com sucesso. Ela também mostra que nossos testes cobriram todos os caminhos de código no método `StartsWithUpper` e que todos esses testes foram executados com êxito (o que é indicado pela marca de verificação verde "✓"). Finalmente, mostra que nenhum dos outros métodos na StringLibrary tem cobertura de código (que é indicado por uma linha azul, "➖").

![O Gerenciador de Testes e a janela de código depois que o Service Fabric Explorer é iniciado](media/lut-start/lut-results-cs.png)

Você também pode obter informações mais detalhadas sobre a cobertura do teste e os resultados de teste selecionando um ícone de cobertura de código específico na janela de código. Para examinar este detalhe, faça o seguinte:

1. Clique na marca de verificação verde na linha em que está escrito `if (String.IsNullOrWhiteSpace(s))` no método `StartsWithUpper`. Como mostra a imagem a seguir, o Live Unit Testing indica que três testes cobrem essa linha de código, e que todos foram executados com sucesso.

   ![Cobertura de código para a instrução condicional 'if'](media/lut-start/code-coverage-cs1.png)

1. Clique na marca de verificação verde na linha em que está escrito `return Char.IsUpper(s[0])` no método `StartsWithUpper`. Como mostra a imagem a seguir, o Live Unit Testing indica que apenas dois testes cobrem essa linha de código, e que todos foram executados com sucesso.

   ![Cobertura de código para a instrução return](media/lut-start/code-coverage-cs2.png)

A questão mais importante que o Live Unit Testing identifica é uma cobertura de código incompleta. Isso será abordado na próxima seção.

## <a name="expand-test-coverage"></a>Expandir a cobertura do teste

Nesta seção, você estenderá os testes de unidade para o método `StartsWithLower`. Enquanto você estiver fazendo isso, o Live Unit Testing continuará a testar o código dinamicamente.

Para estender a cobertura de código para o método `StartsWithLower`, faça o seguinte:

1. Adicione os seguintes métodos `TestStartsWithLower` e `TestDoesNotStartWithLower` no arquivo de código-fonte do teste do projeto:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Modifique `DirectCallWithNullOrEmpty` o método adicionando o seguinte código [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) imediatamente após a chamada ao método.

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. O Live Unit Testing executa automaticamente os testes novos e modificados quando você modifica o código-fonte. Como mostra a imagem a seguir do **Test Explorer,** todos os testes, incluindo os dois que você adicionou e o que você modificou, foram bem sucedidos.

   ![O Explorador de Testes após expandir a cobertura do teste](media/lut-start/test-dynamic.png)

1. Mude para a janela que contém o código-fonte da classe StringLibrary. Agora, o Live Unit Testing mostra que a cobertura de código foi estendida para o método `StartsWithLower`.

    ![Cobertura de código do método StartsWithLower](media/lut-start/lut-extended-cs.png)

Em alguns casos, testes bem-sucedidos no **Test Explorer** podem ser acinzentados. Isso indica que um teste está sendo executado no momento, ou que o teste não foi executado novamente porque não houve alterações de código que afetariam o teste desde que foi executado pela última vez.

Até agora, todos os nossos testes tiveram êxito. Na próxima seção, vamos examinar como você pode tratar uma falha de teste.

## <a name="handle-a-test-failure"></a>Lidar com uma falha de teste

Nesta seção, você vai explorar como é possível usar o Live Unit Testing para identificar, corrigir e solucionar problemas de falhas de teste. Você fará isso expandindo a cobertura do teste para o método `HasEmbeddedSpaces`.

1. Adicione o seguinte método ao arquivo de teste:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Quando o teste é executado, o `TestHasEmbeddedSpaces` Teste da Unidade Viva indica que o método falhou, como mostra a imagem a seguir:

   ![O Explorador de Testes relatando um teste falho](media/lut-start/test-failure.png)

1. Selecione a janela que exibe o código da biblioteca. O Live Unit Testing expandiu `HasEmbeddedSpaces` a cobertura de código para o método. Ele também relata uma falha de teste adicionando um "🞩" vermelho nas linhas cobertas por testes com falha.

1. Passe o mouse sobre a linha com a assinatura do método `HasEmbeddedSpaces`. O Live Unit Testing exibe uma dica de ferramenta que informa que o método é coberto por um teste, como mostra a imagem a seguir:

   ![Informações de teste da unidade ao vivo em um teste falho](media/lut-start/test-failure-info-cs.png)

1. Selecione o teste **TestHasEmbeddedSpaces**. O Live Unit Testing oferece uma série de opções, como executar todos os testes, executar os testes selecionados, depurar todos os testes e depurar testes selecionados, como mostra a imagem a seguir:

   ![Opções de teste de unidade ao vivo para um teste com falha](media/lut-start/test-failure-options.png)

1. Selecione **Depurar Selecionado** para depurar o teste com falha.

1. O Visual Studio executa o teste no modo de depuração.

   O teste atribui cada string em uma `phrase` matriz a `HasEmbeddedSpaces` uma variável nomeada e passa-a para o método. A execução do programa fica em pausa e invoca o depurador na primeira vez em que a expressão assert é `false`. A caixa de diálogo de exceção resultante do valor inesperado na chamada do [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) método é mostrada na imagem a seguir.

   ![Diálogo de exceção de teste de unidade ao vivo](media/lut-start/exception-dialog-cs.png)

   Além disso, todas as ferramentas de depuração que o Visual Studio fornece estão disponíveis para nos ajudar a solucionar problemas do nosso teste falho, como mostra a imagem a seguir:

   ![Ferramentas de depuração do Visual Studio](media/lut-start/debugging-tools-cs.png)

   Observe que na janela **Autos** o valor da variável `phrase` é "Name\tDescription", que é o segundo elemento da matriz. O método de teste espera que `HasEmbeddedSpaces` retorne `true` ao receber essa cadeia de caracteres, mas ele retorna `false`. Evidentemente, ele não reconhece "\t", o caractere de tabulação, como um espaço inserido.

1. Selecione **Depurar** > **Continuar,** pressione **F5**ou clique no botão **Continuar** na barra de ferramentas para continuar executando o programa de teste. Como ocorreu uma exceção sem tratamento, o teste foi encerrado.
Isso fornece informações suficientes para uma investigação preliminar do bug. Ou `TestHasEmbeddedSpaces` (a rotina de teste) fez uma suposição incorreta ou `HasEmbeddedSpaces` não reconhece corretamente todos os espaços inseridos.

1. Para diagnosticar e corrigir o `StringLibrary.HasEmbeddedSpaces` problema, comece pelo método. Examine a comparação no método `HasEmbeddedSpaces`. Ele considera um espaço inserido como U+0020. No entanto, o padrão Unicode inclui vários outros caracteres de espaço. Isso sugere que o código da biblioteca testou um caractere de espaço em branco incorretamente.

1. Substitua a comparação de igualdade por uma chamada para o método <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName>:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. O Live Unit Testing reexecuta automaticamente o método de teste com falha e atualiza os resultados na janela de código e no **Test Explorer,** como mostra a imagem a seguir:

    ![Teste bem-sucedido hasembeddedspaces](media/lut-start/test-success-cs.png)

## <a name="see-also"></a>Confira também

- [Teste de unidade ao vivo no Visual Studio](live-unit-testing.md)
- [Perguntas frequentes sobre o Live Unit Testing](live-unit-testing-faq.md)
