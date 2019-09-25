---
title: Caixa de diálogo geral, depuração, opções | Microsoft Docs
ms.date: 11/09/2018
ms.topic: reference
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db4756107bb9f5e7e766634897013649db351faa
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211018"
---
# <a name="general-debugging-options"></a>Opções gerais de depuração

Para definir opções do depurador do Visual Studio, selecione**Opções**de **ferramentas** > e, em **depuração** , marque ou desmarque as caixas ao lado das opções **gerais** . Você pode restaurar todas as configurações padrão com **ferramentas** > **importar e exportar configurações** > **redefinir todas as configurações**. Para redefinir um subconjunto de configurações, salve suas configurações com o **Assistente de importação e exportação de configurações** antes de fazer as alterações que você deseja testar e, em seguida, importe as configurações salvas posteriormente.

Você pode definir as seguintes opções **gerais** :

**Perguntar antes de excluir todos os pontos de interrupção**: Requer a confirmação antes de concluir o comando de **Excluir todos os pontos de interrupção**.

**Interromper todos os processos quando um processo for interrompido**: Interrompe simultaneamente todos os processos ao qual o depurador é anexado, quando ocorre uma interrupção.

**Interromper quando exceções cruzarem AppDomain ou limites gerenciados/nativos**: Na depuração gerenciada ou de modo misto, o common language runtime pode capturar exceções que cruzem limites de domínio de aplicativo ou domínios gerenciados/nativos quando as seguintes condições forem verdadeiras:

1. Quando o código nativo chama o código gerenciado usando a interoperabilidade COM e o código gerenciado aciona uma exceção. Consulte [introdução à interoperabilidade com](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Quando o código gerenciado executado no domínio do aplicativo 1 chama o código gerenciado no domínio 2 do aplicativo, e o código no aplicativo domínio 2 gera uma exceção. Consulte [programação com domínios de aplicativo](/dotnet/articles/framework/app-domains/index).

3. Quando o código chama uma função usando reflexão, e essa função gera uma exceção. Consulte [reflexão](/dotnet/framework/reflection-and-codedom/reflection).

Nas condições 2 e 3, às vezes, a exceção é capturada pelo `mscorlib` código gerenciado em vez de pelo Common Language Runtime. Esta opção não afeta a quebra em exceções capturadas por `mscorlib`.

**Habilitar depuração no nível do endereço**: Habilita recursos avançados para depurar a nível de endereço (a janela **Desmontagem**, a janela **Registros** e pontos de interrupção de endereço).

- **Mostrar desmontagem se a fonte não estiver disponível**:   Mostra automaticamente a janela de **desmontagem** quando você depura o código para o qual a origem está indisponível.

**Habilitar filtros de ponto de interrupção**: Permite que você defina filtros em pontos de interrupção de modo que eles afetem somente processos, threads ou computadores específicos.

**Usar o novo Auxiliar de Exceção**: Habilita o auxiliar de exceção que substitui o assistente de exceção. (O auxiliar de exceção tem suporte a partir do Visual Studio 2017)

> [!NOTE]
> Para código gerenciado, essa opção anteriormente era chamada **habilitar o assistente de exceção** .

**Habilitar Apenas Meu Código**: O depurador exibe e percorre as etapas do código do usuário ("meu código") apenas, ignorando o código do sistema e outro código que é otimizado ou que não tem símbolos de depuração.

- **Avisar se não houver código de usuário na inicialização (Somente gerenciado)** :   Quando a depuração começa com o Just My Code ativado, esta opção advertirá você se não houver nenhum código de usuário ("My Code").

**Habilitar depuração do código-fonte do .NET Framework**: Permite que o depurador entre na fonte do .NET Framework. Habilitar essa opção desabilita automaticamente Apenas Meu Código. .NET Framework símbolos serão baixados em um local de cache. Altere o local do cache com a caixa de diálogo **Opções** , categoria **depuração** , página **símbolos** .

**Depurar parcialmente propriedades e operadores (Somente gerenciado)** : Impede que o depurador entre em propriedades e operadores no código gerenciado.

**Habilitar a avaliação da propriedade e outras chamadas de função implícitas**: Ativa a classificação automática da propriedades e as chamadas de função implícitas nas janelas de variáveis e na caixa de diálogo **QuickWatch**.

- **Função de conversão de cadeia de caracteres de chamada em objetos em janelas de variáveis (somente C# e JavaScript)** : Executa uma chamada de conversão de cadeia de caracteres implícita ao avaliar objetos em janelas de variáveis. O resultado é exibido como uma cadeia de caracteres em vez do nome do tipo. Aplica-se somente à depuração no código em C. Essa configuração pode ser substituída pelo atributo DebuggerDisplay (consulte [usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).

**Habilitar suporte a servidor de origem**: Informe ao depurador do Visual Studio para obter os arquivos de origem dos servidores de origem que implementam o protocolo de SrcSrv (`srcsrv.dll`). O Team Foundation Server e as Ferramentas de Depuração para o Windows são dois servidores de origem que implementam o protocolo. Para obter mais informações sobre a configuração do SrcSrv, consulte a documentação do [srcsrv](/windows-hardware/drivers/debugger/srcsrv) . Além disso, consulte [especificar símbolo (. pdb) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Como ler arquivos *.pdb* pode executar o código arbitrário em arquivos, certifique-se de que você confia no servidor.

- **Imprimir mensagens de diagnóstico de servidor de código-fonte na janela de Saída**:   Quando o suporte do servidor de origem é ativado, esta configuração ativa ao diagnóstico.

- **Permite ao servidor de origem confiar parcialmente em assemblies (somente gerenciado)** :   Quando o suporte do servidor de origem é ativado, esta configuração substitui o comportamento padrão de não recuperar as fontes dos assemblies de confiança parcial.

- **Sempre executar comandos não confiáveis do servidor de código-fonte sem perguntar**:   Quando o suporte ao servidor de origem está habilitado, essa configuração substitui o comportamento padrão de solicitação ao executar um comando não confiável.

**Habilitar suporte de Link de Origem**: Instrui o depurador do Visual Studio a baixar arquivos de origem para arquivos *. pdb* que contêm informações de link de origem. Para obter mais informações sobre o link de origem, consulte a [especificação do link de origem](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/source_link.md).

> [!IMPORTANT]
> Como o link de origem baixará arquivos usando http ou HTTPS, certifique-se de confiar no arquivo *. pdb* .

- **Fazer o fallback para autenticação de Gerenciador de Credenciais do Git para todas as solicitações de Vínculo da Fonte**:   Quando o suporte ao link de origem está habilitado e uma solicitação de link de origem falha na autenticação, o Visual Studio chama o Git Credential Manager.

**Realçar toda a linha para pontos de interrupçãoC++ e a instrução atual (somente)** : Quando o depurador realça um ponto de interrupção ou uma declaração atual, realça a linha inteira.

**Exigir que os arquivos de código-fonte correspondam exatamente à versão original**: Informe ao depurador para verificar se um arquivo fonte corresponde à versão do código-fonte usado para criar o arquivo executável que você está depurando. Quando a versão não corresponder, você será solicitado a localizar uma fonte correspondente. Se uma fonte compatível não for encontrada, o código-fonte não será exibido durante a depuração.

**Redirecionar todo o texto da Janela Saída para a Janela Imediato**: Em vez disso, envia todas as mensagens do depurador que normalmente apareceriam na janela **Saída** para a janela **Imediato**.

**Mostrar estrutura bruta de objetos nas janelas de variáveis**: Desative todas as personalizações de exibição da estrutura do objeto. Para obter mais informações sobre as personalizações de exibição, consulte [criar exibições personalizadas de objetos gerenciados](../debugger/create-custom-views-of-dot-managed-objects.md).

**Suprimir otimização JIT no carregamento do módulo (somente gerenciado)** : Desativa a otimização JIT de código gerenciado quando um módulo é carregado e JIT é compilado enquanto o depurador é anexado. Desativar a otimização pode facilitar a depuração de alguns problemas, embora às custas de desempenho. Se você estiver usando Apenas Meu Código, a supressão da otimização de JIT poderá fazer com que código que não seja do usuário apareça como código do usuário ("Meu Código"). Para obter mais informações, consulte [otimização e depuração JIT](../debugger/jit-optimization-and-debugging.md).

**Habilitar depuração do JavaScript para ASP.NET (Chrome, Microsoft Edge e IE)** : Habilita o depurador de script para aplicativos ASP.NET. Na primeira utilização no Chrome, talvez seja necessário entrar no navegador para habilitar as extensões do Chrome que você instalou. Desabilite esta opção para reverter para o comportamento herdado.

**Habilitar as Ferramentas para Desenvolvedores do Microsoft Edge para Aplicativos de JavaScript da UWP (Experimental)** : Habilita as ferramentas de desenvolvedor para aplicativos de JavaScript UWP no Microsoft Edge.

**Habilitar depurador JavaScript Chrome herdado para ASP.NET**: Habilita o depurador de script JavaScript do Chrome herdado para aplicativos ASP.NET. Na primeira utilização no Chrome, talvez seja necessário entrar no navegador para habilitar as extensões do Chrome que você instalou.

**Usar maneira experimental de iniciar a depuração de JavaScript do Chrome ao executar o Visual Studio como Administrador**: Diz ao Visual Studio para experimentar uma nova maneira de iniciar o Chrome durante a depuração de JavaScript.

**Carregar exportações de dll (somente Nativo)** : Carrega tabelas de exportação de dll. Informações de símbolos das tabelas de exportação de dll podem ser úteis se você estiver trabalhando com mensagens do Windows, procedimentos do Windows (WindowProcs), objetos COM, ou marshaling, ou qualquer dll para a qual você não tem símbolos. A leitura das informações de exportação de dll gera certa sobrecarga. Desse modo, esse recurso é desativado por padrão.

Para ver quais símbolos estão disponíveis na tabela de exportação de uma dll, use `dumpbin /exports`. Os símbolos estão disponíveis para qualquer dll de 32 bits do sistema. Ao ler a saída `dumpbin /exports`, você pode ver o nome exato da função, incluindo caracteres não alfanuméricos. Isso é útil para definir um ponto de interrupção em uma função. Os nomes de função de tabelas de exportação de dll podem aparecer truncados em qualquer outro lugar no depurador. As chamadas são listadas na ordem de chamada, com a função atual (a mais profundamente aninhada) na parte superior. Para obter mais informações, confira [dumpbin /exports](/cpp/build/reference/dash-exports).

**Mostrar diagrama de pilhas paralelas de baixo para cima**: Controla a direção em que as pilhas são exibidas na janela **Pilhas Paralelas**.

**Ignorar as exceções de acesso de memória da GPU se o valor dos dados gravados não forem alterados**: Ignora as condições de corrida detectadas durante a depuração caso os dados não tenham sido alterados. Para obter mais informações, consulte [depuração de código de GPU](../debugger/debugging-gpu-code.md).

**Usar modo de compatibilidade gerenciado**: Substitui o mecanismo de depuração padrão com uma versão herdada para habilitar estes cenários:

- Você está usando um idioma .NET Framework diferente de C#, Visual Basic ou F# que fornece seu próprio avaliador de expressão (isso C++inclui/CLI).

- Você deseja habilitar editar e continuar para projetos C++ durante a depuração de modo misto.

> [!NOTE]
> A escolha do modo de compatibilidade gerenciado desabilita alguns recursos que são implementados somente no mecanismo de depuração padrão. O mecanismo de depuração herdado foi substituído no Visual Studio 2012.

**Usar os avaliadores da expressão de C# e VB herdados**: O depurador usará o Visual Studio 2013 C# ou Visual Basic avaliadores de expressão em vez dos avaliadores de expressão baseados em Roslyn do Visual Studio 2015.

**Avisar ao usar visualizadores do depurador personalizados contra processos potencialmente inseguros (somente Gerenciados)** : O Visual Studio avisa quando você está usando um visualizador de depurador personalizado que está executando o código no processo depurado, pois ele poderia estar executando um código não seguro.

**Habilitar alocador de heap de depuração do Windows (somente Nativo)** : Habilita o heap de depuração do Windows para melhorar o diagnóstico de heap. Habilitar essa opção afetará o desempenho da depuração.

**Habilitar as Ferramentas de Depuração da Interface do Usuário para XAML**: A árvore visual ao vivo e a propriedade Live Explore o Windows aparecerão quando você iniciar a depuração (**F5**) de um tipo de projeto com suporte. Para obter mais informações, consulte [inspecionar propriedades XAML durante a depuração](../debugger/inspect-xaml-properties-while-debugging.md).

- **Visualizar os elementos selecionados na Árvore Visual Dinâmica**:   O elemento XAML cujo contexto está selecionado também é selecionado na janela da **árvore visual ao vivo** .

- **Mostrar ferramentas de tempo de execução no aplicativo**: Mostra os comandos de **árvore visual ao vivo** em uma barra de ferramentas na janela principal do aplicativo XAML que está sendo depurado. Essa opção foi introduzida no Visual Studio 2015 atualização 2.

- **Habilitar o Hot recarregamento de XAML**: Permite que você use o recurso de recarga ativa XAML com código XAML quando seu aplicativo está em execução. (Anteriormente, esse recurso era chamado de "edição XAML e continuação")

**Habilitar as Ferramentas de Diagnóstico durante a depuração**: A janela de **ferramentas de diagnóstico** aparece enquanto você está depurando.

**Mostrar tempo decorrido de Dica de Desempenho durante a depuração**: A janela de código exibe o tempo decorrido de uma determinada chamada de método quando você está depurando.

**Habilita o Editar e Continuar**: Habilita a funcionalidade Editar e continuar durante a depuração.

- **Habilita o Editar e Continuar Nativo**: Você pode usar a funcionalidade Editar e continuar durante a depuração C++ de código nativo. Para obter mais informações, consulte [Editar e continuar ( C++Visual)](../debugger/edit-and-continue-visual-cpp.md).

- **Aplicar alterações ao continuar (somente nativo)** : O Visual Studio compila e aplica automaticamente qualquer alteração de código pendente que você tenha feito ao continuar o processo de um estado de interrupção. Se não estiver selecionado, você poderá optar por aplicar as alterações usando o item **aplicar alterações de código** no menu **depurar** .

- **Avisar sobre código obsoleto (somente nativo)** :   Obter avisos sobre código obsoleto.

**Mostrar executar para clicar no botão no editor durante a depuração**: Quando essa opção for selecionada, o botão [Executar para clicar](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) será exibido durante a depuração.

**Fechar automaticamente o console quando a depuração parar**: Informa ao Visual Studio para fechar o console no final de uma sessão de depuração.

::: moniker range=">= vs-2019" 
**Habilitar a avaliação rápida de expressão (somente gerenciado)** : Permite que o depurador tente uma avaliação mais rápida simulando a execução de propriedades e métodos simples.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Opções disponíveis em versões mais antigas do Visual Studio

Se você estiver usando uma versão mais antiga do Visual Studio, algumas opções adicionais poderão estar presentes.

**Habilitar o Assistente de exceção**: Para código gerenciado, habilita o assistente de exceção. A partir do Visual Studio 2017, o auxiliar de exceção substituiu o assistente de exceção.

**Voltar para a pilha de chamadas em exceções não tratadas**: Faz com que a janela **Pilha de Chamadas** reverta a pilha de chamadas ao ponto antes que a exceção sem tratamento ocorreu.

**Avisar se não houver símbolos na inicialização (somente nativo)** : Exibe uma caixa de diálogo de aviso quando você depura um programa para o qual o depurador não tem informações de símbolo.

**Avisar se a depuração do script estiver desabilitada na inicialização**: Exibe uma caixa de diálogo de aviso quando o depurador é iniciado com a depuração de script desabilitada.

**Use o modo de compatibilidade nativo**: Quando essa opção é selecionada, o depurador usa o depurador nativo do Visual Studio 2010 em vez do novo depurador nativo.

- Use esta opção quando estiver Depurando C++ o código .net, pois o novo mecanismo de depuração não oferece C++ suporte à avaliação de expressões .net. No entanto, habilitar o modo de compatibilidade nativa desabilita muitos recursos que dependem da implementação do depurador atual para operar. Por exemplo, o mecanismo herdado não tem muitos visualizadores para tipos internos, como `std::string` nos projetos do Visual Studio 2015.   Use Visual Studio 2013 projetos para a experiência de depuração ideal nesses casos.

## <a name="see-also"></a>Consulte também

- [Depurando no Visual Studio](../debugger/index.yml)
- [Introdução ao depurador](../debugger/debugger-feature-tour.md)
