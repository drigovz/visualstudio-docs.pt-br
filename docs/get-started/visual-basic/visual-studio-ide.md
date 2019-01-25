---
title: Visão geral para desenvolvedores de Visual Basic
ms.date: 11/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 506581dc329249fc4043e01222163499f2de46d7
ms.sourcegitcommit: a715de2ba8c703f37aa2102567b1aa2c0f05a117
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2018
ms.locfileid: "54405316"
---
# <a name="welcome-to-the-visual-studio-ide--visual-basic"></a>Bem-vindo ao IDE do Visual Studio | Visual Studio

O *ambiente de desenvolvimento integrado* do Visual Studio é um painel de inicialização criativo que você pode usar para editar, depurar e compilar o código e, em seguida, publicar um aplicativo. Um IDE (ambiente de desenvolvimento integrado) é um programa repleto de recursos que pode ser usado por muitos aspectos do desenvolvimento de software. Além do editor e do depurador padrão fornecidos pela maioria dos IDEs, o Visual Studio inclui compiladores, ferramentas de preenchimento de código, designers gráficos e muitos outros recursos para facilitar o processo de desenvolvimento de software.

![O IDE do Visual Studio](../media/visual-studio-ide.png)

Esta imagem mostra o Visual Studio com um projeto aberto e várias importantes janelas de ferramentas que você provavelmente usará:

- O [**Gerenciador de Soluções**](../../ide/solutions-and-projects-in-visual-studio.md) (parte superior direita) permite exibir, navegar e gerenciar os arquivos de código. O **Gerenciador de Soluções** pode ajudar a organizar o código agrupando os arquivos em [soluções e projetos](tutorial-projects-solutions.md).

- A [janela do editor](../../ide/writing-code-in-the-code-and-text-editor.md) (parte central), na qual você provavelmente passará a maior parte do tempo, exibe o conteúdo do arquivo. É nela em que você pode editar o código ou criar uma interface do usuário, como uma janela com botões e caixas de texto.

- A [janela de Saída](../../ide/reference/output-window.md) (parte central inferior) é o local em que o Visual Studio envia notificações, como mensagens de erro e de depuração, avisos do compilador, mensagens de status da publicação e muito mais. Cada fonte de mensagem tem uma guia própria.

- O [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (canto inferior direito) permite que você acompanhe itens de trabalho e compartilhe o código com outras pessoas usando tecnologias de controle de versão como o [Git](https://git-scm.com/) e o [TFVC (Controle de Versão do Team Foundation)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Edições

O Visual Studio está disponível para o Windows e o Mac. O [Visual Studio para Mac](/visualstudio/mac/) tem muitas das mesmas funcionalidades do Visual Studio 2017 e é otimizado para o desenvolvimento de aplicativos móveis e multiplataforma. Este artigo concentra-se na versão do Visual Studio 2017 para Windows.

Há três edições do Visual Studio 2017: Community, Professional e Enterprise. Veja [Comparar IDEs do Visual Studio 2017](https://visualstudio.microsoft.com/vs/compare/) para saber quais recursos são compatíveis com cada edição.

## <a name="popular-productivity-features"></a>Recursos de produtividade populares

Alguns dos recursos populares no Visual Studio que ajudam você a ser mais produtivo durante o desenvolvimento de software incluem:

- [Refatoração](../../ide/refactoring-in-visual-studio.md)

   A refatoração inclui operações como renomeação inteligente de variáveis, extração de uma ou mais linhas de código em um novo método, alteração da ordem dos parâmetros de método e muito mais.

   ![Refatoração no Visual Studio](media/refactoring-menu.png)

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense é um termo usado para um conjunto de recursos que exibe informações sobre o código diretamente no editor e, em alguns casos, escreve pequenos trechos de código para você. É como ter a documentação básica embutida no editor, o que evita que você tenha que consultar informações de tipo em outro lugar. Os recursos do IntelliSense variam de acordo com a linguagem. Para saber mais, consulte [C# IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md) e [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md). A seguinte ilustração mostra como o IntelliSense exibe uma lista de membros para um tipo:

   ![Lista de membros do Visual Studio](media/intellisense-list-members.png)

- [Início Rápido](../../ide/reference/quick-launch-environment-options-dialog-box.md)

   O Visual Studio pode parecer assustador, às vezes, com tantas propriedades, opções e menus. A caixa de pesquisa **Início Rápido** é uma ótima maneira de encontrar rapidamente o que você precisa no Visual Studio. Quando você começa a digitar o nome de algo que está procurando, o Visual Studio lista resultados que levam você exatamente para o local em que precisa ir. Caso você precise adicionar uma funcionalidade ao Visual Studio, por exemplo, para adicionar suporte a outra linguagem de programação, o **Início Rápido** fornecerá resultados que abrem o Instalador do Visual Studio para instalar uma carga de trabalho ou um componente individual.

   ![Caixa de pesquisa Início Rápido no Visual Studio](../media/quick-launch-nuget.png)

- Rabiscos e [Ações Rápidas](../../ide/quick-actions.md)

   Rabiscos são sublinhados ondulados que alertam você sobre erros ou problemas potenciais no código durante a digitação. Essas pistas visuais permitem que você corrija os problemas imediatamente sem esperar que o erro seja descoberto durante o build ou quando você executar o programa. Se você focalizar um rabisco, verá informações adicionais sobre o erro. Uma lâmpada também pode ser exibida na margem esquerda com ações, conhecidas como Ações Rápidas, para corrigir o erro.

   ![Rabiscos no Visual Studio](media/squiggles-error.png)

- [Hierarquia de chamadas](../../ide/reference/call-hierarchy.md)

   A janela **Hierarquia de Chamadas** mostra os métodos que chamam um método selecionado. Essas podem ser informações úteis quando você está considerando alterar ou remover o método ou quando está tentando rastrear um bug.

   ![Exibir a hierarquia de chamadas no Visual Studio](media/call-hierarchy.png)

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   O CodeLens ajuda você a encontrar referências e alterações no código, bugs vinculados, itens de trabalho, revisões de código e testes de unidade, tudo isso sem sair do editor.

   ![CodeLens no Visual Studio](media/codelens.png)

   > [!NOTE]
   > O CodeLens não está disponível na edição Visual Studio 2017 Community.

- [Ir para Definição](../../ide/go-to-and-peek-definition.md)

   O recurso Ir para Definição leva você diretamente para o local em que uma função ou um tipo está definido.

   ![Ir para Definição no Visual Studio](media/go-to-definition-menu.png)

- [Inspecionar Definição](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   A janela **Espiar Definição** mostra a definição de um método ou um tipo sem, na verdade, abrir um arquivo separado.

   ![Inspecionar Definição no Visual Studio](media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>Instalar o IDE do Visual Studio

Este artigo de visão geral orienta você a criar um projeto simples e a experimentar algumas das coisas que você pode fazer com o Visual Studio, como alterar o tema de cores, usar o [IntelliSense](../../ide/using-intellisense.md) como um auxílio de codificação e depurar um aplicativo para ver o valor de uma variável durante a execução do programa. Para começar, [baixe o Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) e instale-o no sistema.

O instalador modular permite escolher e instalar *cargas de trabalho*, que são grupos de recursos necessários para a linguagem de programação ou para a plataforma de sua preferência. Para seguir as etapas de [criação de um programa](#create-a-program), selecione a carga de trabalho **Desenvolvimento multiplataforma do .NET Core** durante a instalação.

![Carga de trabalho de desenvolvimento multiplataforma do .NET Core no Instalador do Visual Studio](../media/dotnet-core-cross-platform-workload.png)

Ao iniciar o Visual Studio pela primeira vez, opcionalmente, você pode [entrar](../../ide/signing-in-to-visual-studio.md) usando sua conta Microsoft ou sua conta corporativa ou de estudante.

## <a name="customize-visual-studio"></a>Personalizar o Visual Studio

Personalize a interface do usuário do Visual Studio, incluindo a alteração do tema de cores padrão.

### <a name="change-the-color-theme"></a>Alterar o tema de cores

Para alterar para o tema **Escuro**:

1. Na barra de menus, escolha **Ferramentas** > **Opções** para abrir a caixa de diálogo **Opções**.

2. Na página de opções **Ambiente** > **Geral**, altere a seleção **Tema de cores** para **Escuro** e, em seguida, escolha **OK**.

   ![Alterar o tema de cores para escuro no Visual Studio](media/change-color-theme.png)

   O tema de cores para todo o IDE é alterado para **Escuro**.

   ![Visual Studio no tema escuro](../../ide/media/quickstart-personalize-dark-theme.png)

### <a name="select-environment-settings"></a>Selecionar configurações do ambiente

Primeiro, configuraremos o Visual Studio para usar configurações de ambiente adequadas aos desenvolvedores em Visual Basic.

1. Na barra de menus, escolha **Ferramentas** > **Importar e Exportar Configurações**.

2. No **Assistente de Importação e Exportação de Configurações**, selecione **Redefinir todas as configurações** na primeira página e, em seguida, escolha **Avançar**.

3. Na página **Salvar Configurações Atuais**, selecione uma opção para salvar suas configurações atuais ou não e, em seguida, escolha **Avançar**. Se você ainda não personalizou as configurações, selecione **Não, apenas redefina as configurações, substituindo minhas configurações atuais**.

4. Na página **Escolher uma Coleção Padrão de Configurações**, escolha **Visual Basic** e depois **Concluir**.

5. Na página **Redefinição Concluída**, escolha **Fechar**.

Para conhecer outras maneiras pelas quais você pode personalizar o IDE, confira [Personalizar o Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-program"></a>Criar um programa

Vamos nos aprofundar e criar um programa simples.

1. Abra o Visual Studio. Na barra de menus, escolha **Arquivo** > **Novo Projeto**.

   ![Arquivo > Novo projeto na barra de menus](media/file-new-project-menu.png)

2. A caixa de diálogo **Novo Projeto** mostra vários *modelos* de projeto. Um modelo contém as configurações e os arquivos básicos necessários para um tipo de projeto fornecido. Escolha a categoria **.NET Core** em **Visual Basic** e escolha o modelo **Aplicativo de Console (.NET Core)**. Na caixa de texto **Nome**, digite **HelloWorld** e, em seguida, selecione o botão **OK**.

   ![Modelo de aplicativo .NET Core](media/overview-npd.png)

   > [!NOTE]
   > Se você não vir a categoria **.NET Core**, será necessário instalar a carga de trabalho **Desenvolvimento de plataforma cruzada do .NET Core**. Para fazer isso, escolha o link **Abrir o Instalador do Visual Studio** na parte inferior esquerda da caixa de diálogo **Novo Projeto**. Depois que o Instalador do Visual Studio for aberto, role a tela para baixo, selecione a carga de trabalho **Desenvolvimento multiplataforma do .NET Core** e, em seguida, selecione **Modificar**.

   O Visual Studio cria o projeto. É um aplicativo "Olá, Mundo" simples que chama o método <xref:System.Console.WriteLine?displayProperty=nameWithType> para exibir a cadeia de caracteres literal "Olá, Mundo!" na janela do console (saída do programa).

   Logo em seguida, você deverá ver algo parecido com isto:

   ![Visual Studio IDE](media/overview-ide-console-app.png)

   O código Visual Basic para o aplicativo é mostrado na janela do editor, que ocupa a maior parte do espaço. Observe que o texto é colorizado automaticamente para indicar diferentes partes do código, como palavras-chave e tipos. Além disso, pequenas linhas verticais tracejadas no código indicam a correspondência de chaves e os números de linha ajudam a localizar o código posteriormente. Escolha os pequenos sinais de subtração demarcados para recolher ou expandir blocos de código. Esse recurso de estrutura de tópicos do código permite ocultar os códigos desnecessários, ajudando a minimizar a desordem na tela. Os arquivos de projeto são listados no lado direito em uma janela chamada **Gerenciador de Soluções**.

   ![IDE do Visual Studio com caixas de vermelhas](media/overview-ide-console-app-red-boxes.png)

   Há outros menus e outras janelas de ferramentas disponíveis, mas por enquanto, vamos seguir em frente.

3. Agora, inicie o aplicativo pressionando **Ctrl**+**F5**.

   O Visual Studio compila o aplicativo e uma janela do console é aberta com a mensagem **Olá, Mundo!**. Agora você tem um aplicativo em execução.

   ![Janela do console](../media/overview-console-window.png)

4. Para fechar a janela do console, pressione qualquer tecla do teclado.

5. Vamos adicionar um código adicional ao aplicativo. Adicione o código Visual Basic a seguir antes da linha que diz `Console.WriteLine("Hello World!")`:

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Esse código exibe **Qual é seu nome?** na janela do console e, em seguida, aguarda até que o usuário insira um texto seguido da tecla **Enter**.

6. Altere a linha que indica `Console.WriteLine("Hello World!")` para o seguinte código:

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

7. Execute o aplicativo novamente pressionando **Ctrl**+**F5**.

   O Visual Studio recompila o aplicativo e uma janela do console é aberta e solicita seu nome.

8. Insira seu nome na janela do console e pressione **Enter**.

   O programa o saúda por nome.

   ![Entrada da janela do console](media/overview-console-input.png)

9. Pressione qualquer tecla para fechar a janela do console e interromper o programa em execução.

## <a name="use-refactoring-and-intellisense"></a>Usar a refatoração e o IntelliSense

Vamos examinar algumas das maneiras pelas quais a [refatoração](../../ide/refactoring-in-visual-studio.md) e o [IntelliSense](../../ide/using-intellisense.md) podem ajudar você a codificar com mais eficiência.

Primeiro, vamos renomear a variável `name`:

1. Clique duas vezes na variável `name` para selecioná-la.

2. Digite o novo nome da variável, **username**.

   Observe que uma caixa cinza é exibida ao redor da variável e uma lâmpada é exibida na margem.

3. Selecione o ícone de lâmpada para mostrar as [Ações Rápidas](../../ide/quick-actions.md) disponíveis. Selecione **Renomear 'name' como 'username'**.

   ![Ação de renomeação no Visual Studio](media/rename-quick-action.png)

   A variável é renomeada no projeto, o que, em nosso caso, são apenas dois locais.

4. Agora vamos dar uma olhada no IntelliSense. Abaixo da linha que indica `Console.WriteLine("Hello " + username + "!")`, digite o seguinte fragmento de código:

    ```vb
   Dim now = Date.
   ```

   Uma caixa exibe os membros da classe <xref:System.DateTime>. Além disso, a descrição do membro atualmente selecionado é exibida em uma caixa separada.

   ![O IntelliSense lista membros no Visual Studio](media/intellisense-list-members.png)

5. Selecione o membro chamado **Now**, que é uma propriedade da classe, clicando duas vezes nele ou selecionando-o usando as teclas de direção e pressionando **Tab**.

6. Abaixo disso, digite ou cole as seguintes linhas de código:

   ```vb
   Dim dayOfYear = now.DayOfYear
   Console.Write("Day of year: ")
   Console.WriteLine(dayOfYear)
   ```

   > [!TIP]
   > <xref:System.Console.Write%2A?displayProperty=nameWithType> é um pouco diferente de <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, pois não adiciona um terminador de linha após a impressão. Isso significa que a próxima parte do texto que é enviada para a saída será impressa na mesma linha. Focalize cada um desses métodos no código para ver a descrição.

7. Em seguida, usaremos a refatoração novamente para tornar o código um pouco mais conciso. Clique na variável `now` na linha `Dim now = Date.Now`.

   Observe que um pequeno ícone de chave de fenda é exibido na margem dessa linha.

8. Clique no ícone de chave de fenda para ver quais sugestões estão disponíveis no Visual Studio. Nesse caso, está mostrando a refatoração [Variável temporária embutida](../../ide/reference/inline-temporary-variable.md) para remover uma linha de código sem alterar o comportamento geral do código:

   ![Refatoração de variável temporária embutida no Visual Studio](media/inline-temporary-variable-refactoring.png)

9. Clique em **Variável temporária embutida** para refatorar o código.

10. Execute o programa novamente pressionando **Ctrl**+**F5**. A saída é semelhante ao seguinte:

    ![Janela do console com saída do programa](media/overview-console-final.png)

## <a name="debug-code"></a>Depurar o código

Ao escrever o código, você precisa executá-lo e testá-lo para verificar se há bugs. O sistema de depuração do Visual Studio permite que você execute em etapas uma instrução no código por vez e inspecione variáveis durante o processo. Defina *pontos de interrupção* que interrompem a execução do código em uma linha específica. Observe como o valor de uma variável é alterado durante a execução do código e muito mais.

Vamos definir um ponto de interrupção para ver o valor da variável `username` enquanto o programa está "em andamento".

1. Encontre a linha de código que indica `Console.WriteLine("Hello " + username + "!")`. Para definir um ponto de interrupção nessa linha de código, ou seja, para fazer com que o programa pause a execução nessa linha, clique na margem mais à esquerda do editor. Clique também em qualquer lugar na linha de código e, em seguida, pressione **F9**.

   Um círculo vermelho é exibido na margem da extrema esquerda, e o código é realçado em vermelho.

   ![Ponto de interrupção na linha de código no Visual Studio](media/breakpoint.png)

1. Inicie a depuração selecionando **Depuração** > **Iniciar Depuração** ou pressionando **F5**.

1. Quando a janela do console for exibida e solicitar seu nome, digite-o e pressione **Enter**.

   O foco retorna para o editor de códigos do Visual Studio e a linha de código com o ponto de interrupção é realçada em amarelo. Isso significa que ela é a próxima linha de código que será executada pelo programa.

1. Passe o mouse sobre a variável `username` para ver seu valor. Como alternativa, clique com o botão direito do mouse em `username` e selecione **Adicionar Inspeção** para adicionar a variável à janela **Inspeção**, na qual você também pode ver o valor.

   ![Valor da variável durante a depuração no Visual Studio](media/debugging-variable-value.png)

1. Para permitir que o programa seja executado até a conclusão, pressione **F5** novamente.

Para obter mais detalhes sobre a depuração no Visual Studio, consulte [Tour dos recursos do depurador](../../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Próximas etapas

Explore ainda mais o Visual Studio seguindo um dos seguintes artigos introdutórios:

> [!div class="nextstepaction"]
> [Saiba como usar o editor de códigos](tutorial-editor.md)

> [!div class="nextstepaction"]
> [Saiba mais sobre projetos e soluções](tutorial-projects-solutions.md)

## <a name="see-also"></a>Consulte também

- Descubra [mais recursos do Visual Studio](../../ide/advanced-feature-overview.md)
- Visite [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- Leia [The Visual Studio blog](https://blogs.msdn.microsoft.com/visualstudio/) (O blog do Visual Studio)
- Confira os cursos gratuitos do Visual Studio em [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033)