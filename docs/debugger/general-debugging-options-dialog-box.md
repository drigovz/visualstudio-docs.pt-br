---
title: Geral, Depuração, Caixa de Diálogo de Opções | Microsoft Docs
ms.date: 11/12/2019
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
ms.openlocfilehash: 98bbd65d11b26d9b35000e4acbe4d28a585f8ddc
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472691"
---
# <a name="general-debugging-options"></a>Opções gerais de depuração

Para definir as opções de depuração do Visual Studio, selecione **Opções de** > **ferramentas**e, em **Depuração,** selecione ou desmarque as caixas ao lado das opções **Geral.** Você pode restaurar todas as configurações padrão com **as** > **configurações** > de importação e exportação de ferramentas**Redefinir todas as configurações**. Para redefinir um subconjunto de configurações, salve suas configurações com o **Assistente de Configurações de Importação e Exportação** antes de fazer as alterações que deseja testar e, em seguida, importe as configurações salvas depois.

Você pode definir as seguintes opções **gerais:**

**Pergunte antes de excluir todos os pontos de interrupção**: Requer confirmação antes de completar o comando Excluir todos os pontos de **interrupção.**

**Quebre todos os processos quando um processo se rompe:** Simultaneamente quebra todos os processos aos quais o depurador é anexado, quando ocorre uma quebra.

**Quebre quando as exceções cruzarem os limites do AppDomain ou do gerenciado/nativo:** Na depuração gerenciada ou de modo misto, o tempo de execução do idioma comum pode capturar exceções que cruzam os limites do domínio do aplicativo ou os limites gerenciados/nativos quando as seguintes condições são verdadeiras:

1. Quando o código nativo chama o código gerenciado usando a interoperabilidade COM e o código gerenciado aciona uma exceção. Consulte [Introdução ao COM Interop](/dotnet/articles/visual-basic/programming-guide/com-interop/introduction-to-com-interop).

2. Quando o código gerenciado rodando no domínio do aplicativo 1 chama código gerenciado no domínio do aplicativo 2, e o código no domínio do aplicativo 2 lança uma exceção. Consulte [Programação com domínios de aplicativos](/dotnet/articles/framework/app-domains/index).

3. Quando o código chama uma função usando reflexão, e essa função lança uma exceção. Ver [Reflexão](/dotnet/framework/reflection-and-codedom/reflection).

Nas condições 2 e 3, a exceção `mscorlib` às vezes é capturada por código gerenciado em vez de pelo tempo de execução da linguagem comum. Esta opção não afeta a quebra em exceções capturadas por `mscorlib`.

**Habilitar depuração no nível do endereço**: Habilita recursos avançados para depuração no nível do endereço (a janela **Desmontagem,** a janela **Registros** e pontos de interrupção de endereço).

- **Mostrar desmontagem se a fonte não estiver disponível**: Mostra automaticamente a janela **Desmontagem** quando você depura o código para o qual a fonte não está disponível.

**Habilitar filtros de ponto de interrupção**: Permite definir filtros em pontos de interrupção para que eles afetem apenas processos específicos, threads ou computadores.

**Use o novo Helper de exceção**: Habilita o Helper de exceção que substitui o assistente de exceção. (O Helper de Exceção é suportado a partir do Visual Studio 2017)

> [!NOTE]
> Para código gerenciado, essa opção foi previamente chamada **De habilitar o assistente de exceção** .

**Habilitar apenas meu código**: O depurador exibe e entra apenas no código do usuário ("Meu Código"), ignorando o código do sistema e outro código que é otimizado ou que não tenha símbolos de depuração.

- **Aviso se não houver código de usuário no lançamento (somente gerenciado)**: Quando a depuração começar com Apenas Meu Código ativado, esta opção avisa se não houver código de usuário ("Meu Código").

**Habilitar a revisão da fonte .NET Framework**: Permite que o depurador entre na fonte .NET Framework. A ativação dessa opção desativa automaticamente O Meu Código. Os símbolos do .NET Framework serão baixados para um local de cache. Alterar o local do cache com a caixa de diálogo **Opções,** categoria **Depuração,** Página **Símbolos.**

**Passo sobre propriedades e operadores (somente gerenciado)**: Impede que o depurador entre em propriedades e operadores em código gerenciado.

**Habilitar avaliação de propriedades e outras chamadas de função implícita**: Ativa a avaliação automática das propriedades e chamadas de função implícita em variáveis janelas e a caixa de diálogo **QuickWatch.**

- **Função de conversão de seqüência de chamadas em objetos em janelas variáveis (c# e somente JavaScript)**: Executa uma chamada de conversão de string implícita ao avaliar objetos em janelas variáveis. O resultado é exibido como uma seqüência em vez do nome do tipo. Aplica-se somente à depuração no código em C. Essa configuração pode ser substituída pelo atributo DebuggerDisplay (veja [Usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).

**Habilitar suporte ao servidor de origem**: Informa o depurador do Visual Studio`srcsrv.dll`para obter arquivos de origem de servidores de origem que implementam o protocolo SrcSrv ( ). O Team Foundation Server e as Ferramentas de Depuração para o Windows são dois servidores de origem que implementam o protocolo. Para obter mais informações sobre a configuração do SrcSrv, consulte a documentação [do SrcSrv.](/windows-hardware/drivers/debugger/srcsrv) Além disso, consulte [Especificar símbolo (.pdb) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

> [!IMPORTANT]
> Como a leitura de arquivos *.pdb* pode executar código arbitrário nos arquivos, certifique-se de confiar no servidor.

- **Imprimir mensagens de diagnóstico do servidor de origem para a janela Saída**: Quando o suporte ao servidor de origem estiver ativado, essa configuração ativa a exibição de diagnóstico.

- **Permitir servidor de origem para conjuntos de confiança parcial (somente gerenciado)**: Quando o suporte ao servidor de origem estiver ativado, essa configuração substitui o comportamento padrão de não recuperar fontes para conjuntos de confiança parcial.

- **Sempre execute comandos de servidor de origem não confiáveis sem solicitação**: Quando o suporte ao servidor de origem estiver ativado, essa configuração substitui o comportamento padrão de solicitação ao executar um comando não confiável.

**Habilitar suporte ao Source Link**: Informa o depurador do Visual Studio para baixar arquivos de origem para arquivos *.pdb* que contenham informações do Source Link. Para obter mais informações sobre o Source Link, consulte a [especificação do link Origem](/dotnet/standard/library-guidance/sourcelink).

> [!IMPORTANT]
> Como o Source Link baixará arquivos usando http ou https, certifique-se de confiar no arquivo *.pdb.*

- **Volte para a autenticação do Git Credential Manager para todas as solicitações do Source Link**: Quando o suporte ao Source Link estiver ativado e uma solicitação do Source Link falhar na autenticação, o Visual Studio então chama o Gerenciador de Credenciais do Git.

**Destaque toda a linha para pontos de interrupção e declaração atual (somente C++):** Quando o depurador destaca um ponto de interrupção ou uma declaração atual, ele destaca toda a linha.

**Exigir arquivos de origem para corresponder exatamente à versão original**: Diz ao depurador para verificar se um arquivo de origem corresponde à versão do código-fonte usado para construir o executável que você está depurando. Quando a versão não corresponde, você é solicitado a encontrar uma fonte correspondente. Se uma fonte compatível não for encontrada, o código-fonte não será exibido durante a depuração.

**Redirecione todo o texto da janela de saída para a janela Imediato**: Envia todas as mensagens de depurador que normalmente apareceriam na janela **Saída** para a janela **'Imediato'.**

**Mostrar estrutura bruta de objetos em janelas variáveis**: Desliga todas as personalizações de visualização da estrutura do objeto. Para obter mais informações sobre personalizações de visualização, consulte [Criar visualizações personalizadas de objetos gerenciados](../debugger/create-custom-views-of-managed-objects.md).

**Suprimir a otimização do JIT na carga do módulo (somente gerenciada)**: Desativa a otimização JIT do código gerenciado quando um módulo é carregado e o JIT é compilado enquanto o depurador é conectado. Desativar a otimização pode facilitar a depuração de alguns problemas, embora às custas de desempenho. Se você estiver usando Apenas Meu Código, a supressão da otimização de JIT poderá fazer com que código que não seja do usuário apareça como código do usuário ("Meu Código"). Para obter mais informações, consulte [otimização e depuração do JIT](../debugger/jit-optimization-and-debugging.md).

**Habilite a depuração do JavaScript para ASP.NET (Chrome, Microsoft Edge e IE)**: Habilita o depurador de script para aplicativos ASP.NET. No primeiro uso no Chrome, talvez seja necessário entrar no navegador para habilitar as extensões do Chrome instaladas. Desabilite essa opção para reverter ao comportamento legado.

**Habilitar ferramentas de desenvolvedor de borda para aplicativos JavaScript UWP (Experimental)**: Permite ferramentas de desenvolvedor para aplicativos JavaScript UWP no Microsoft Edge.

**Habilite o depurador Chrome JavaScript legado para ASP.NET**: Habilita o depurador de script Chrome JavaScript legado para aplicativos ASP.NET. No primeiro uso no Chrome, talvez seja necessário entrar no navegador para habilitar as extensões do Chrome instaladas.

**Use uma maneira experimental de iniciar a depuração do Chrome JavaScript ao executar o Visual Studio como Administrador**: Diz ao Visual Studio para tentar uma nova maneira de iniciar o Chrome durante a depuração do JavaScript.

**Carregar as exportações de dll (somente nativo):** Carrega tabelas de exportação dll. Informações de símbolos das tabelas de exportação de dll podem ser úteis se você estiver trabalhando com mensagens do Windows, procedimentos do Windows (WindowProcs), objetos COM, ou marshaling, ou qualquer dll para a qual você não tem símbolos. A leitura das informações de exportação de dll gera certa sobrecarga. Desse modo, esse recurso é desativado por padrão.

Para ver quais símbolos estão disponíveis na tabela de exportação de uma dll, use `dumpbin /exports`. Os símbolos estão disponíveis para qualquer dll de 32 bits do sistema. Ao ler a saída `dumpbin /exports`, você pode ver o nome exato da função, incluindo caracteres não alfanuméricos. Isso é útil para definir um ponto de interrupção em uma função. Os nomes de função de tabelas de exportação de dll podem aparecer truncados em qualquer outro lugar no depurador. As chamadas são listadas na ordem de chamada, com a função atual (a mais profundamente aninhada) na parte superior. Para obter mais informações, confira [dumpbin /exports](/cpp/build/reference/dash-exports).

**Mostrar pilhas paralelas diagrama de baixo para cima**: Controla a direção em que as pilhas são exibidas na janela **Pilhas Paralelas.**

**Ignore as exceções de acesso à memória GPU se os dados gravados não alterarem o valor**: Ignora as condições de corrida detectadas durante a depuração se os dados não mudarem. Para obter mais informações, consulte [Código de GPU de depuração](../debugger/debugging-gpu-code.md).

**Use o modo de compatibilidade gerenciada**: Substitui o mecanismo de depuração padrão por uma versão herdada para habilitar esses cenários:

- Você está usando uma linguagem .NET diferente de C#, Visual Basic ou F# que fornece seu próprio Avaliador de Expressão (isso inclui C++/CLI).

- Você deseja ativar projetos Editar e Continuar para projetos C++ durante a depuração do modo misto.

> [!NOTE]
> A escolha do modo de compatibilidade gerenciada desativa alguns recursos que são implementados apenas no mecanismo de depuração padrão. O motor de depuração legado foi substituído no Visual Studio 2012.

**Use os avaliadores de expressão C# e VB legados**: O depurador usará os avaliadores de expressão Visual Studio 2013 C# ou Visual Basic em vez dos avaliadores de expressão baseados em Roslyn 2015.

**Alerte ao usar visualizadores personalizados de depuradores contra processos potencialmente inseguros (somente gerenciados):** O Visual Studio avisa quando você está usando um visualizador de depurador personalizado que está executando o código no processo dedepurado, porque ele pode estar executando código inseguro.

**Habilite o alocador de pilha de depuração do Windows (somente nativo):** Permite que o monte de depuração do windows melhore os diagnósticos de pilha. A ativação dessa opção afetará o desempenho da depuração.

**Habilitar ferramentas de depuração de ui para XAML**: A árvore visual ao vivo e as janelas Live Property Explore aparecerão quando você começar a depurar (**F5**) um tipo de projeto suportado. Para obter mais informações, consulte [Inspecione as propriedades XAML durante a depuração](../xaml-tools/inspect-xaml-properties-while-debugging.md).

- **Visualizar elementos selecionados em Live Visual Tree**: O elemento XAML cujo contexto é selecionado também é selecionado na janela Árvore Visual Ao **Vivo.**

- **Mostrar ferramentas de tempo de execução no aplicativo**: Mostra os comandos **Live Visual Tree** em uma barra de ferramentas na janela principal do aplicativo XAML que está sendo depurado. Esta opção foi introduzida no Visual Studio 2015 Update 2.

- **Habilitar XAML Hot Reload**: Permite que você use o recurso XAML Hot Reload com código XAML quando seu aplicativo estiver em execução. (Este recurso foi anteriormente chamado de "XAML Edit and Continue")

::: moniker range=">= vs-2019" 
- **Habilitar Apenas Meu XAML**: A partir da versão 16.4 do Visual Studio 2019, a **Árvore Visual Ao Vivo** por padrão mostra apenas XAML que é classificado como código de usuário. Se você desativar essa opção, todo o código XAML gerado será mostrado na ferramenta.

- **Desative o modo de seleção quando um elemento é selecionado** A partir da versão 16.4 do Visual Studio 2019, o botão seletor de elementos da barra de ferramentas no aplicativo **(Habilitar seleção)** desliga quando um elemento é selecionado. Se você desativar essa opção, a seleção de elementos permanecerá ativada até que você clique no botão da barra de ferramentas do aplicativo novamente.
::: moniker-end

**Habilite ferramentas de diagnóstico durante a depuração**: A janela **Ferramentas de diagnóstico** é exibida enquanto você está depurando.

**Mostrar tempo decorrido PerfTip durante a depuração**: A janela de código exibe o tempo decorrido de uma determinada chamada de método quando você está depurando.

**Ativar editar e continuar**: Habilita ristindo a funcionalidade Editar e Continuar durante a depuração.

- **Habilite editar e continuar nativo**: Você pode usar a funcionalidade Editar e Continuar enquanto depura o código C++ nativo. Para obter mais informações, consulte [Editar e Continuar (C++)](../debugger/edit-and-continue-visual-cpp.md).

- **Aplique alterações em continuar (somente nativo)**: O Visual Studio compila automaticamente e aplica quaisquer alterações de código pendentes que você tenha feito ao continuar o processo a partir de um estado de ruptura. Se não for selecionado, você pode optar por aplicar alterações usando o item **Aplicar Alterações de Código** no menu **Depuração.**

- **Alerte sobre o código obsoleto (somente nativo):** Obtenha avisos sobre código sumido.

**Mostrar executar para clicar no botão no editor durante a depuração**: Quando esta opção estiver selecionada, o botão [Executar para clicar](../debugger/debugger-feature-tour.md#run-to-a-point-in-your-code-quickly-using-the-mouse) será mostrado durante a depuração.

**Feche automaticamente o console quando a depuração parar**: Diz ao Visual Studio para fechar o console no final de uma sessão de depuração.

::: moniker range=">= vs-2019"
**Habilite a avaliação rápida de expressão (somente gerenciada):** Permite que o depurador tente uma avaliação mais rápida simulando a execução de propriedades e métodos simples.
::: moniker-end

## <a name="options-available-in-older-versions-of-visual-studio"></a>Opções disponíveis em versões mais antigas do Visual Studio

Se você estiver usando uma versão mais antiga do Visual Studio, algumas opções adicionais podem estar presentes.

**Habilitar o assistente de exceção**: Para código gerenciado, habilita o assistente de exceção. A partir do Visual Studio 2017, o Helper de Exceção substituiu o assistente de exceção.

**Descontrair a pilha de chamadas em exceções não manuseadas**: Faz com que a janela **Pilha de chamadas** reverta a pilha de chamadas para o ponto antes que a exceção não tratada ocorreu.

**Aviso se não houver símbolos no lançamento (somente nativo):** Exibe uma caixa de diálogo de aviso quando você depura um programa para o qual o depurador não tem informações de símbolos.

**Avisar se a depuração do script estiver desativada no lançamento**: Exibe uma caixa de diálogo de aviso quando o depurador é iniciado com a depuração de script desativada.

**Use o modo de compatibilidade nativa**: Quando esta opção é selecionada, o depurador usa o depurador nativo do Visual Studio 2010 em vez do novo depurador nativo.

- Use esta opção quando estiver depurando o código .NET C++, porque o novo mecanismo de depuração não suporta a avaliação de expressões .NET C++. No entanto, ativar o Modo de Compatibilidade Nativa desativa muitos recursos que dependem da implementação atual do depurador para funcionar. Por exemplo, o motor legado carece de muitos visualizadores para tipos embutidos, como `std::string` em projetos do Visual Studio 2015.   Use projetos do Visual Studio 2013 para a melhor experiência de depuração nesses casos.

## <a name="see-also"></a>Confira também

- [Depurando no Visual Studio](../debugger/index.yml)
- [Primeiro olhe para o depurador](../debugger/debugger-feature-tour.md)
