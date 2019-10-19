---
title: Caixa de diálogo geral, depuração, opções | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.options.General
- VS.ToolsOptionsPages.Debugger.General
- VS.ToolsOptionsPages.Debugger.ENC
- vs.debug.options.ENC
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Options dialog box, debugging
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6c53af4a8e0f42708ab94d7206a9c0cc54819798
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573547"
---
# <a name="general-debugging-options-dialog-box"></a>Caixa de diálogo Geral, Depuração, Opções
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A página**ferramentas/opções/depuração/geral** permite definir as seguintes opções:  
  
 **Perguntar antes de excluir todos os pontos de interrupção**  
 Requer a confirmação antes de concluir o comando de **Excluir todos os pontos de interrupção**.  
  
 **Interromper todos os processos quando um processo for interrompido**  
 Interrompe simultaneamente todos os processos ao qual o depurador é anexado, quando ocorre uma interrupção.  
  
 **Quebra quando as exceções cruzam AppDomain ou limites gerenciados/nativos**  
 Na depuração gerenciada ou de modo misto, o common language runtime pode capturar exceções que cruzem limites de domínio de aplicativo ou domínios gerenciados/nativos quando as seguintes condições forem verdadeiras:  
  
 1 \) quando o código nativo chama o código gerenciado usando a interoperabilidade COM e o código gerenciado gera uma exceção. Consulte [introdução à interoperabilidade com](https://msdn.microsoft.com/library/8bd62e68-383d-407f-998b-29aa0ce0fd67).  
  
 2 \) quando o código gerenciado em execução no domínio do aplicativo 1 chama o código gerenciado no domínio 2 do aplicativo e o código no aplicativo domínio 2 gera uma exceção. Consulte [programação com domínios de aplicativo](https://msdn.microsoft.com/bd36055b-56bd-43eb-b4d8-820c37172131).  
  
 3 \) quando o código chama uma função usando reflexão, e a função gera uma exceção. Consulte [reflexão](https://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775).  
  
 Em 2) e 3), a exceção é às vezes detectada pelo código gerenciado em `mscorlib` em vez do common language runtime. Esta opção não afeta a quebra em exceções capturadas por `mscorlib`.  
  
 **Habilitar depuração no nível de endereço**  
 Habilita recursos avançados para depurar a nível de endereço (a janela **Desmontagem**, a janela **Registros** e pontos de interrupção de endereço).  
  
 **Mostrar desmontagem se a origem não estiver disponível**  
 Mostra automaticamente a janela de **desmontagem** quando você tenta Depurar o código para o qual a origem está indisponível.  
  
 **Habilitar filtros de ponto de interrupção**  
 Permite que você defina filtros em pontos de interrupção para que eles afetem apenas processos, threads ou computadores específicos.  
  
 **Habilitar o assistente de exceção**  
 Somente para código gerenciado. Exceções gerenciadas Abra a caixa de diálogo Assistente de exceção.  Consulte [Assistente de exceção](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb).  
  
 **Desenrolar a pilha de chamadas em exceções sem tratamento**  
 Faz com que a janela **Pilha de Chamadas** reverta a pilha de chamadas ao ponto antes que a exceção sem tratamento ocorreu.  
  
 **Habilitar Apenas Meu Código**  
 O depurador exibe e percorre as etapas do código do usuário ("meu código") apenas, ignorando o código do sistema e outro código que é otimizado ou que não tem símbolos de depuração.  
  
 **Mostrar todos os membros de objetos que não são de usuário em janelas de variáveis (somente Visual Basic)**  
 Ativa a exibição de membros não-públicos em objetos que são de código não usuário (não "My Code").  
  
 **Avisar se não houver nenhum código de usuário na inicialização**  
 Quando a depuração começa com o Just My Code ativado, esta opção advertirá você se não houver nenhum código de usuário ("My Code").  
  
 **Habilitar a depuração de origem .NET Framework**  
 Permite que o depurador entre na fonte do .NET Framework. Habilitar esta opção desativa automaticamente Apenas Meus Código dos símbolos do .NET Framework que serão baixados em um local do cache. Você pode alterar o local do cache na caixa de diálogo **Opções** , categoria **depuração** , página **símbolos** .  
  
 **Percorrer Propriedades e operadores (somente gerenciado)**  
 Impede que o depurador entre em propriedades e operadores no código gerenciado.  
  
 **Habilitar a avaliação de propriedade e outras chamadas de função implícitas**  
 Ativa a classificação automática da propriedades e as chamadas de função implícitas nas janelas de variáveis e na caixa de diálogo **QuickWatch**.  
  
 **Chamar função de conversão de cadeia de caracteres em objetosC# em janelas de variáveis (e somente JavaScript)**  
 Executa uma chamada de conversão de cadeia de caracteres implícita ao avaliar objetos em janelas de variáveis. Portanto, o resultado é exibido como uma cadeia de caracteres em vez do nome do tipo. Aplica-se somente à depuração no código em C. Essa configuração pode ser substituída pelo atributo DebuggerDisplay (consulte [usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)).  
  
 **Habilitar suporte a servidor de origem**  
 Informe ao depurador do Visual Studio para obter os arquivos de origem dos servidores de origem que implementam o protocolo de SrcSrv (`srcsrv.dll`). O Team Foundation Server e as Ferramentas de Depuração para o Windows são dois servidores de origem que implementam o protocolo. Para obter mais informações sobre a configuração de SrcSrv, consulte a documentação Ferramentas de depuração para o Windows. Além disso, consulte [especificar símbolo (. pdb) e arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
> Como ler arquivos .pdb pode executar o código arbitrário em arquivos, certifique-se de que você confia no servidor.  
  
 **Imprimir mensagens de diagnóstico do servidor de origem na janela de saída**  
 Quando o suporte do servidor de origem é ativado, esta configuração ativa ao diagnóstico.  
  
 **Permitir servidor de origem para assemblies de confiança parcial (somente gerenciado)**  
 Quando o suporte do servidor de origem é ativado, esta configuração substitui o comportamento padrão de não recuperar as fontes dos assemblies de confiança parcial.  
  
 **Realçar toda a linha para pontos de interrupção e a instrução atual**  
 Quando o depurador realça um ponto de interrupção ou uma declaração atual, realça a linha inteira.  
  
 **Exigir que os arquivos de origem correspondam exatamente à versão original**  
 Informe ao depurador para verificar se um arquivo fonte corresponde à versão do código-fonte usado para criar o arquivo executável que você está depurando. Se a versão não corresponde, será solicitado que você localize uma origem correspondente. Se uma fonte compatível não for encontrada, o código-fonte não será exibido durante a depuração.  
  
 **Redirecionar todo o texto da janela de saída para a janela imediata**  
 Em vez disso, envia todas as mensagens do depurador que normalmente apareceriam na janela **Saída** para a janela **Imediato**.  
  
 **Mostrar estrutura bruta de objetos em janelas de variáveis**  
 Desative todas as personalizações de exibição da estrutura do objeto. Para obter mais informações sobre as personalizações de exibição, consulte [criar exibições personalizadas de objetos gerenciados](../debugger/create-custom-views-of-managed-objects.md).  
  
 **Suprimir a otimização JIT na carga do módulo (somente gerenciado)**  
 Desativa a otimização JIT de código gerenciado quando um módulo é carregado e JIT é compilado enquanto o depurador é anexado. Desativar a otimização pode facilitar a depuração de alguns problemas, embora às custas de desempenho. Se você estiver usando Apenas Meu Código, a supressão da otimização de JIT poderá fazer com que código que não seja do usuário apareça como código do usuário ("Meu Código").  
  
 **Avisar se nenhum símbolo for iniciado (somente nativo)**  
 Exibe uma caixa de diálogo de aviso quando você tenta Depurar um programa para o qual o depurador não tem informações de símbolo.  
  
 **Avisar se a depuração de script estiver desabilitada na inicialização**  
 Exibe uma caixa de diálogo de aviso quando o depurador é iniciado com a depuração de script desabilitada.  
  
 **Carregar exportações de dll**  
 Carrega tabelas de exportação de dll. Informações de símbolos das tabelas de exportação de dll podem ser úteis se você estiver trabalhando com mensagens do Windows, procedimentos do Windows (WindowProcs), objetos COM, ou marshaling, ou qualquer dll para a qual você não tem símbolos. A leitura das informações de exportação de dll gera certa sobrecarga. Desse modo, esse recurso é desativado por padrão.  
  
 Para ver quais símbolos estão disponíveis na tabela de exportação de uma dll, use `dumpbin /exports`. Os símbolos estão disponíveis para qualquer dll de 32 bits do sistema. Ao ler a saída `dumpbin /exports`, você pode ver o nome exato da função, incluindo caracteres não alfanuméricos. Isso é útil para definir um ponto de interrupção em uma função. Os nomes de função de tabelas de exportação de dll podem aparecer truncados em qualquer outro lugar no depurador. As chamadas são listadas na ordem de chamada, com a função atual (a mais profundamente aninhada) na parte superior. Para obter mais informações, consulte [dump bin/Exports](https://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).  
  
 **Mostrar diagrama de pilhas paralelas de baixo para cima**  
 Controla a direção em que as pilhas são exibidas na janela **Pilhas Paralelas**.  
  
 **Ignorar exceções de acesso à memória GPU se os dados gravados não alteraram o valor**  
 Ignora as condições de corrida detectadas durante a depuração caso os dados não tenham sido alterados. Para obter mais informações, consulte [depuração de código de GPU](../debugger/debugging-gpu-code.md).  
  
 **Usar modo de compatibilidade gerenciado**  
 Substitui o mecanismo de depuração padrão com uma versão herdada para habilitar estes cenários:  
  
- Você está usando uma linguagem .NET Framework diferente de C#, VB ou F#, que fornece seu próprio Avaliador de Expressão (incluindo C++/CLI).  
  
- Você deseja habilitar editar e continuar para projetos C++ enquanto a depuração de modo misto.  
  
  Observe que escolher o modo Compatibilidade gerenciada desativa alguns recursos que são implementados somente no mecanismo de depuração padrão.  
  
  **Usar o modo de compatibilidade nativo**  
  Quando essa opção é selecionada, o depurador usa o depurador nativo do Visual Studio 2010 em vez do novo depurador nativo.  
  
  Você deve usar essa opção quando estiver Depurando C++ o código .net, porque o novo mecanismo de depuração não oferece C++ suporte à avaliação de expressões .net. No entanto, habilitar o modo de compatibilidade nativa desabilita muitos recursos que dependem da implementação do depurador atual para operar. Por exemplo, o mecanismo herdado não tem muitos visualizadores para tipos internos como `std::string` em projetos do Visual Studio 2015.  Use Visual Studio 2013 projetos para a experiência de depuração ideal nesses casos.  
  
  **Usar os avaliadores de expressão herdados C# e VB**  
  O depurador usará os Visual Studio 2013 C#avaliadores de expressão/VB em vez dos avaliadores de expressão baseados em Roslyn do Visual Studio 2015.  
  
  **Avisar ao usar visualizadores de depurador personalizados contra processos potencialmente não seguros (somente gerenciados)**  
  O Visual Studio avisa quando você está usando um visualizador de depurador personalizado que está executando código no processo de depuração, pois ele poderia estar executando código não seguro.  
  
  **Habilitar o alocador de heap de depuração do Windows (somente nativo)**  
  Habilita o heap de depuração do Windows para melhorar o diagnóstico de heap. Habilitar essa opção afetará o desempenho da depuração.  
  
  **Habilitar ferramentas de depuração de interface do usuário para XAML**  
  A árvore visual ao vivo e a propriedade Live Explore o Windows aparecerão quando você iniciar a depuração (F5) de um tipo de projeto com suporte. Para obter mais informações, consulte [inspecionar propriedades XAML durante a depuração](../debugger/inspect-xaml-properties-while-debugging.md).  
  
  **Visualizar elementos selecionados na árvore visual dinâmica**  
  O elemento XAML cujo contexto está selecionado também é selecionado na janela da **árvore visual ao vivo** .  
  
  **Mostrar ferramentas de tempo de execução no aplicativo**  
  Mostra os comandos de **árvore visual ao vivo** em uma barra de ferramentas na janela principal do aplicativo XAML que está sendo depurado. Essa opção foi introduzida no Visual Studio 2015 atualização 2.  
  
  **Habilitar Ferramentas de Diagnóstico durante a depuração**  
  A janela de **ferramentas de diagnóstico** aparece enquanto você está depurando. Para obter mais informações, consulte [criação de perfil integrada ao depurador](/visualstudio/profiling/running-profiling-tools-with-or-without-the-debugger).  
  
  **Mostrar tempo decorrido dica durante a depuração**  
  A janela de código exibe o tempo decorrido de uma determinada chamada de método quando você está depurando.  
  
  **Habilitar editar e continuar**  
  Você pode usar a funcionalidade Editar e continuar durante a depuração.  
  
  **Habilitar editar e continuar nativo**  
  Você pode usar a funcionalidade Editar e continuar durante a depuração C++ de código nativo. Para obter mais informações, consulte [Editar e continuar ( C++Visual)](../debugger/edit-and-continue-visual-cpp.md).  
  
  **Aplicar alterações ao continuar (somente nativo)**  
  O Visual Studio compila e aplica automaticamente qualquer alteração de código pendente que você tenha feito ao continuar o processo de um estado de interrupção. Se não estiver selecionado, você poderá optar por aplicar as alterações usando o item "aplicar alterações de código" no menu Depurar.  
  
  **Avisar sobre código obsoleto (somente nativo)**  
  Obter avisos sobre código obsoleto.  
  
  **Permitir pré-compilação (somente nativo)**  
  A pré-compilação é permitida.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)
