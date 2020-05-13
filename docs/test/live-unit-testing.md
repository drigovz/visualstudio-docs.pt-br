---
title: Live Unit Testing
ms.date: 04/07/2020
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: 34200e8719ef25de3c54c612b967cf3d4f9bab85
ms.sourcegitcommit: 316dd2182dd56b0cbde49f0cd82e9f75baa2530f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2020
ms.locfileid: "81223691"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Como configurar e usar o Live Unit Testing

À medida que você está desenvolvendo um aplicativo, o Live Unit Testing executa automaticamente qualquer teste de unidade impactada em segundo plano e apresenta os resultados e a cobertura de código em tempo real. Durante a modificação do código, o Live Unit Testing fornece comentários sobre como as alterações afetaram os testes existentes e se o novo código adicionado é abrangido por um ou mais testes existentes. Isso gentilmente lembra você de escrever testes de unidade enquanto você está fazendo correções de bugs ou adicionando novos recursos.

> [!NOTE]
> O Teste de Unidade Ao Vivo está disponível para projetos C# e Visual Basic que visam o .NET Core ou o .NET Framework na edição Enterprise do Visual Studio.

Quando você usa o Live Unit Testing para seus testes, ele persiste dados sobre o status de seus testes. O uso de dados persistentes permite que o Live Unit Testing ofereça desempenho superior enquanto executa seus testes dinamicamente em resposta a alterações de código.

## <a name="supported-test-frameworks"></a>Estruturas de teste com suporte

O Live Unit Testing funciona com as três estruturas de teste de unidade populares listadas na tabela a seguir. A versão mínima suportada de seus adaptadores e frameworks também é mostrada. As estruturas de teste de unidade estão disponíveis em NuGet.org.

|Estrutura de teste  |Versão mínima do Adaptador do Visual Studio  |Versão mínima da Estrutura  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio versão 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter versão 3.5.1 |NUnit versão 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Se você tiver projetos de teste baseados em MSTest mais antigos que fazem referência ao Microsoft.VisualStudio.QualityTools.UnitTestFramework e não deseja passar para os pacotes mais novos do MSTest NuGet, atualize para o Visual Studio 2019 ou o Visual Studio 2017.

Em alguns casos, você pode precisar restaurar explicitamente os pacotes NuGet referenciados por um projeto para que o teste da unidade viva funcione. Você pode fazer isso fazendo uma compilação explícita da solução (selecione **Build** > **Rebuild Solution** no menu de alto nível do Visual Studio) ou restaurando pacotes na solução (clique com o botão direito do mouse na solução e selecione Restaurar **pacotes NuGet).**

## <a name="configure"></a>Configurar

Configure o teste da unidade ao vivo selecionando **opções** > de**ferramentas** na barra de menus do Visual Studio de nível superior e, em seguida, selecionando testes de **unidade ao vivo** no painel esquerdo da caixa de diálogo **Opções.**

> [!TIP]
> Depois que o teste da unidade ao vivo estiver ativado (consulte a próxima seção, [Iniciar, pausar e interromper o teste da unidade ao vivo),](#start-pause-and-stop)você também pode abrir a caixa de diálogo **Opções** selecionando**Opções****de teste da unidade de** > teste do **teste** > .

A imagem a seguir mostra as opções de configuração de teste de unidade ao vivo disponíveis na caixa de diálogo:

![Opções de configuração de teste de unidade ao vivo](./media/lut-options.png)

As opções configuráveis incluem:

- Se o Live Unit Testing é pausado quando uma solução é criada e depurada.

- Se o Live Unit Testing é pausado quando a energia da bateria do sistema fica abaixo de um limite especificado.

- Se o Live Unit Testing é executado automaticamente quando uma solução é aberta.

- Se você deseja habilitar o símbolo de depuração e a geração de comentário da documentação XML.

- O diretório no qual deseja armazenar os dados persistentes.

- A capacidade de excluir todos os dados persistentes. Isso é útil quando o Live Unit Testing está se comportando de forma imprevisível ou inesperada, o que sugere que os dados persistidos ficaram corrompidos.

- O intervalo após o qual um caso de teste se esespera. O padrão é 30 segundos.

- O número máximo de processos de teste criados pelo Live Unit Testing.

- A quantidade máxima de memória que os processos do Live Unit Testing podem consumir.

- O nível de informações gravadas na janela **Saída** do Live Unit Testing.

   As opções incluem sem log (**None**), somente mensagens de erro (**Error**), mensagens de erro e mensagens informativas (**Info**, o padrão) ou todos os detalhes (**Verbose**).

   Também é possível exibir a saída detalhada na janela **Saída** do Live Unit Testing atribuindo um valor igual a “1” a uma variável de ambiente no nível do usuário chamada `VS_UTE_DIAGNOSTICS` e reiniciando o Visual Studio.

   Para capturar mensagens de log detalhadas do MSBuild do Live Unit Testing em um arquivo, defina a variável de ambiente no nível do usuário `LiveUnitTesting_BuildLog` com o nome do arquivo que conterá o log.

## <a name="start-pause-and-stop"></a>Comece, pare e pare

Para habilitar o teste da unidade ao vivo, selecione **Teste** > ao vivo Iniciar**o teste** > da unidade**ao vivo** a partir do menu de alto nível do Visual Studio. Quando o teste da unidade ao vivo estiver ativado, as opções disponíveis no menu de teste da **unidade ao vivo** mudam de um único item, **Iniciar,** para **Pausa** e **Parar**:

- **A pausa** suspende temporariamente o teste da unidade viva.

  Quando o Teste de Unidade Ao Vivo é pausado, a visualização de cobertura não aparece no editor, mas todos os dados coletados são preservados. Para retomar o Live Unit Testing, selecione **Continuar** no menu Live Unit Testing. O Live Unit Testing faz o trabalho necessário para acompanhar todas as edições que foram feitas enquanto foi pausada e atualiza os glifos apropriadamente.

- **Pare** completamente os testes da unidade ao vivo. O Live Unit Testing descarta todos os dados coletados.

> [!NOTE]
> Se você iniciar o Teste de Unidade Viva em uma solução que não inclua um projeto de teste de unidade, as opções **Pausa** e **Parada** aparecerão no menu **de teste da unidade ao vivo,** mas o teste da unidade ao vivo não será iniciada. A **janela Saída** exibe uma mensagem que começa: "Nenhum adaptador de teste suportado é referenciado por esta solução...".

A qualquer momento, é possível pausar temporariamente ou parar por completo o Live Unit Testing. Você pode querer fazer isso, por exemplo, se você está no meio de uma refatoração e sabe que seus testes serão quebrados por um tempo.

## <a name="view-coverage-visualization"></a>Ver visualização da cobertura

Depois de habilitado, o Live Unit Testing atualiza cada linha de código no editor do Visual Studio para mostrar se o código que você está escrevendo está coberto por testes de unidade e se os testes que o cobrem estão passando. A imagem a seguir mostra linhas de código com testes de passagem e falha, bem como linhas de código que não são cobertas por testes. As linhas decoradas com um "✓" verde são cobertas apenas por testes aprovados, as linhas com um "x" vermelho são cobertas por um ou mais testes com falha e as linhas com um "➖" azul não são cobertas por nenhum teste.

![Cobertura de código no Visual Studio](./media/lut-codewindow.png)

A visualização da cobertura de teste da unidade ao vivo é atualizada imediatamente quando você modifica o código no editor de código. Durante o processamento das edições, a visualização altera para indicar que os dados não estão atualizados adicionando uma imagem de temporizador redondo abaixo dos símbolos que passam, falhando e não cobertos, como mostra a imagem a seguir.

![Cobertura de código no Visual Studio com ícone de temporizador](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Obtenha informações sobre o status do teste

Ao focalizar o símbolo de êxito ou de falha na janela de código, é possível ver quantos testes estão atingindo essa linha. Para ver o status dos testes individuais, selecione o símbolo:

![Status de teste para um símbolo no Visual Studio](./media/lut-failedinfo.png)

Além de fornecer os nomes e o resultado dos testes, a dica da ferramenta permite que você reexecute ou decine o conjunto de testes. Se você selecionar um ou mais dos testes na dica de ferramenta, é possível executar ou depurar apenas esses testes. Isso permite depurar seus testes sem ter que sair da janela de código. Ao depurar, além de observar quaisquer pontos de interrupção que você tenha definido, a execução do programa pausará quando o depurador executar um método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> que retorna um resultado inesperado.

Ao focalizar um teste com falha na dica de ferramenta, ele é expandido para fornecer informações adicionais sobre a falha, conforme mostrado na imagem a seguir. Para navegar diretamente para um teste com falha, clique duas vezes na dica da ferramenta.

![Informações de dica de ferramenta de teste com falha no Visual Studio](./media/lut-failedmsg.png)

Quando você navega para o teste com falha, o Live Unit Testing indica visualmente na assinatura do método os testes que possuem:

- passou (indicado por um béquer meio cheio, juntamente com um verde "✓")
- falhou (um béquer meio cheio🞩junto com um vermelho " ")
- não estão envolvidos no Teste de Unidade Ao Vivo (um béquer meio cheio junto com um "➖" azul)

Métodos de não teste não são decorados com um símbolo. A imagem a seguir ilustra todos os quatro tipos de métodos.

![Métodos de teste no Visual Studio com símbolo de aprovação ou falha](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Diagnosticar e corrigir falhas de teste

A partir do teste falho, você pode facilmente depurar o código do produto, fazer edições e continuar desenvolvendo sua aplicação. Como o Teste de Unidade Ao Vivo é executado em segundo plano, você não precisa parar e reiniciar o teste da unidade ao vivo durante o ciclo de depuração, edição e continuação.

Por exemplo, a falha de teste mostrada na imagem anterior foi causada por `true` uma suposição <xref:System.Char.IsLower%2A?displayProperty=fullName> incorreta no método de teste de que caracteres não alfabéticos retornam quando passados para o método. Depois de corrigir o método de teste, todos os testes devem passar. Você não precisa pausar ou parar o teste da unidade ao vivo.

::: moniker range="vs-2017"
## <a name="test-explorer"></a>Gerenciador de Testes

**Test Explorer** fornece uma interface que permite executar e depurar testes e analisar os resultados do teste. O Live Unit Testing é integrado ao **Gerenciador de Testes**. Quando o Live Unit Testing não está habilitado ou está parado, o **Gerenciador de Testes** exibe o status dos testes de unidade na última vez que um teste foi executado. Alterações no código-fonte exigem uma nova execução dos testes. Por outro lado, quando o Live Unit Testing está habilitado, o status dos testes de unidade no **Gerenciador de Testes** é atualizado imediatamente. Você não precisa fazer os testes da unidade explicitamente.

> [!TIP]
> Abra **o Teste da Unidade Ao Vivo** selecionando **test** > **windows** > test**explorer** no menu de alto nível do Visual Studio.

Você pode notar na janela **do Test Explorer** que alguns testes estão desbotados. Por exemplo, quando você habilita o Teste de Unidade Viva depois de abrir um projeto previamente salvo, a janela **do Test Explorer** tinha desaparecido tudo, menos o teste com falha, como mostra a imagem a seguir. Neste caso, o Live Unit Testing reexecutou o teste reprovado, mas não reexecutou os testes bem sucedidos. Isso porque os dados persistindo do Live Unit Testing indicam que não houve alterações desde que os testes foram executados pela última vez com sucesso.

![Teste reprovado no Test Explorer](media/lut-test-explorer.png)

Você pode executar novamente quaisquer testes que pareçam desbotados selecionando as opções **Executar tudo** ou **executar** no menu **Test Explorer.** Ou selecione um ou mais testes no menu **Test Explorer,** clique com o botão direito do mouse e selecione **Executar testes selecionados** ou **depurar testes selecionados** no menu pop-up. Conforme os testes são executados, eles são agrupados na parte superior.

Há algumas diferenças entre a execução e atualização automáticas dos resultados de teste do Live Unit Testing e a execução explícita de testes no **Gerenciador de Testes**. Entre elas, podemos incluir:

- A execução ou depuração de testes na janela Gerenciador de Testes executa binários regulares, ao passo que o Live Unit Testing executa binários instrumentados.
- O Live Unit Testing não cria um novo domínio de aplicativo para executar testes; em vez disso, ele executa testes no domínio padrão. Os testes executados na janela **Gerenciador de Testes** criam um novo domínio de aplicativo.
- O Live Unit Testing executa testes em cada assembly de teste sequencialmente. Na janela **Test Explorer,** você pode optar por executar vários testes em paralelo.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="live-unit-testing-window"></a>Janela de teste da unidade ao vivo

**O Live Unit Testing**, semelhante ao **Test Explorer,** fornece uma interface que permite executar e depurar testes e analisar os resultados dos testes. Quando o teste da unidade viva é ativado, o status dos testes unitários no **Test Explorer** é atualizado imediatamente. Você não precisa fazer os testes da unidade explicitamente. Quando o teste da unidade viva não está ativado ou é interrompido, o **Live Unit Testing** exibe o status dos testes unitários da última vez que um teste foi executado. Depois de reiniciar o Teste de Unidade Viva, uma alteração de código fonte é necessária para executar novamente os testes.

> [!TIP]
> Inicie o teste da unidade ao vivo selecionando **Test** > **Live Unit Testing** > **Start** a partir do menu de alto nível do Visual Studio. Você também pode abrir a janela **de teste da unidade ao vivo** usando a janela de teste de **visualização** > outra**unidade ao vivo do****Windows** > .

Você pode notar na janela de teste da **unidade ao vivo** que alguns testes estão desbotados. Por exemplo, quando você para e reinicia o Teste de Unidade Ao Vivo, a janela **de teste da unidade viva** desaparece de todos os testes, como mostra a imagem a seguir. Os resultados dos testes desbotados indicam que o teste não fazia parte da última execução do Teste de Unidade Viva. Os testes só são executados quando uma alteração no teste ou as dependências do teste são detectadas. Se não houver mudança, evita a realização desnecessariamente do teste. Neste caso, o resultado do teste acinzentado ainda está "atualizado", embora não tenha feito parte da última corrida.

![Testes desbotados no Test Explorer](media/vs-2019/lut-test-explorer.png)

Você pode refazer todos os testes que parecerem desbotados fazendo uma alteração de código.

Há algumas diferenças entre a execução e atualização automáticas dos resultados de teste do Live Unit Testing e a execução explícita de testes no **Gerenciador de Testes**. Entre elas, podemos incluir:

- A execução ou depuração de testes na janela Gerenciador de Testes executa binários regulares, ao passo que o Live Unit Testing executa binários instrumentados.
- O Live Unit Testing não cria um novo domínio de aplicativo para executar testes; em vez disso, ele executa testes no domínio padrão. Os testes executados na janela **Gerenciador de Testes** criam um novo domínio de aplicativo.
- O Live Unit Testing executa testes em cada assembly de teste sequencialmente. Na janela **Test Explorer,** você pode optar por executar vários testes em paralelo.
::: moniker-end

## <a name="large-solutions"></a>Grandes soluções

Se sua solução tiver 10 ou mais projetos, o Visual Studio exibirá a seguinte caixa de diálogo quando você:

- iniciar testes de unidade ao vivo e não há dados persistidos
- selecionar**opções de** >  **ferramentas** > **ao vivo Teste** > da unidade**excluir dados persistidos**

![Caixa de diálogo do Live Unit Testing para projetos grandes](media/lut-large-project.png)

O diálogo adverte que a execução dinâmica de um grande número de testes em grandes projetos pode afetar severamente o desempenho. Se você selecionar **OK**, o Live Unit Testing executará todos os testes na solução. Se você selecionar **Cancelar**, será possível selecionar os testes a serem executados. A seção a seguir explica como fazer isso.

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Incluir e excluir projetos de teste e métodos de teste

Para soluções com muitos projetos de teste, você pode controlar quais projetos e métodos individuais em um projeto participam do Live Unit Testing. Por exemplo, se você tiver uma solução com centenas de projetos de teste, será possível selecionar um conjunto direcionado de projetos de teste para fazer parte do Live Unit Testing. Existem várias maneiras de fazer isso, dependendo se você quer excluir todos os testes no projeto ou solução, incluir ou excluir a maioria dos testes, ou excluir testes individuais. O Live Unit Testing salva o estado de inclusão/exclusão como uma configuração de usuário e a memoriza quando uma solução é fechada e reaberta.

### <a name="exclude-all-tests-in-a-project-or-solution"></a>Exclua todos os testes em um projeto ou solução

Para selecionar os projetos individuais em testes de unidade, faça o seguinte após a inicialização do Live Unit Testing:

1. Clique com o botão direito do mouse no **Gerenciador de Soluções** e escolha **Testes Dinâmicos** > **Excluir** para excluir toda a solução.
1. Clique com o botão direito do mouse em cada projeto de teste que você gostaria de incluir nos testes e escolha **Testes** > ao vivo**Incluem**.

### <a name="exclude-individual-tests-from-the-code-editor-window"></a>Exclua testes individuais da janela do editor de código

É possível usar a janela do editor de código para incluir ou excluir métodos de teste individuais. Clique com o botão direito do mouse sobre a assinatura do método de teste na janela do editor de código e selecione uma das seguintes opções:

- **Testes ao vivo** > **Incluem \<>de método selecionado**
- **Testes ao vivo** > **excluem \<o método selecionado>**
- **Testes ao vivo** > **excluem todos, mas \<o método selecionado>**

### <a name="exclude-tests-programmatically"></a>Exclua os testes programáticamente

Você pode aplicar o atributo <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> para excluir, de forma programática, métodos, classes ou estruturas de relatar sua cobertura no Live Unit Testing.

Use os seguintes atributos para excluir métodos individuais do Teste de Unidade Viva:

- Para xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- Para NUnit: `[Category("SkipWhenLiveUnitTesting")]`
- Para MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

Use os seguintes atributos para excluir um conjunto inteiro de testes do Live Unit Testing:

- Para xUnit: `[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- Para NUnit: `[assembly: Category("SkipWhenLiveUnitTesting")]`
- Para MSTest: `[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Confira também

- [Ferramentas de teste de código](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Blog de teste de unidade ao vivo](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [Faq de teste de unidade ao vivo](live-unit-testing-faq.md)
- [Vídeo do Canal 9: Teste de unidade ao vivo no Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
