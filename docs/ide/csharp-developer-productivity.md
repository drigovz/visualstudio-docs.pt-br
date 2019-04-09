---
title: Aumentar a produtividade de desenvolvimento do .NET
description: Uma visão geral da navegação, da análise de código, do teste de unidade e de outros recursos para ajudá-lo a escrever um código .NET melhor mais rápido.
author: kuhlenh
ms.author: gewarren
manager: jillfra
ms.date: 03/26/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: e7b451cf18a461f94e1d8682652e16dac9ee8ab2
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58790453"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>Guia de produtividade do Visual Studio para desenvolvedores de C#

Saiba como o Visual Studio torna os desenvolvedores mais produtivos do que nunca. Aproveite nossas melhorias em desempenho e produtividade como a navegação para assemblies descompilados, sugestões de nomes de variáveis durante a digitação, um modo de exibição de hierarquia no **Gerenciador de Testes**, opção Ir para Todos (**Ctrl**+**T**) para navegar para as declarações de arquivo/tipo/membro/símbolo, um **Auxiliar de Exceção** inteligente, configuração e imposição de estilo de código e muitas correções de código e refatorações.

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>Estou acostumado aos atalhos de teclado de um outro editor

::: moniker range="vs-2017"

**Novo no Visual Studio 2017 versão 15.8**

::: moniker-end

Se você estiver vindo de outro IDE ou ambiente de codificação, poderá alterar o esquema do teclado para o *Visual Studio Code* ou *ReSharper (Visual Studio)*:

![Esquemas de teclado no Visual Studio](../ide/media/VS2017Guide-Keyboard.png)

Algumas extensões também oferecem esquemas de teclado:

- [Teclas de acesso para Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emulação de Emacs](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Estes são os atalhos populares do Visual Studio:

| Atalho (todos os perfis) | Comando | Descrição |
|-|-|-|
| **Ctrl**+**T** | Ir para Todos | Navegar diretamente para qualquer declaração de símbolo, arquivo, tipo ou membro |
| **F12** (também **Ctrl**+**Clique**) | Ir para definição | Vá até onde um símbolo estiver definido |
| **Ctrl**+**F12** | Ir Para Implementação | Navegue de um membro ou tipo base até suas várias implementações |
| **Shift**+**F12** | Localizar Todas as Referências | Veja todas as referências de símbolo ou de literal |
| **Ctrl**+**.** (também **Alt**+**Enter** no Perfil C#) | Ações e Refatorações Rápidas | Veja quais correções de código, ações de geração de código, refatorações ou outras ações rápidas estão disponíveis na posição do cursor ou na seleção do código |
| **Ctrl**+**D** | Duplicar linha | Duplica a linha de código onde o cursor está posicionado (disponível no **Visual Studio 2017 versão 15.6** e posterior) |
| **Shift**+**Alt**+**+**/**-** | Expandir/Reduzir seleção | Expande ou reduz a seleção atual no editor (disponível no **Visual Studio 2017 versão 15.5** e posteriores) |
| **Shift** + **Alt** + **.** | Inserir próximo sinal de interpolação correspondente | Adiciona uma seleção e um sinal de interpolação no próximo local que corresponde à seleção atual (disponível no **Visual Studio 2017 versão 15.8** e posterior) |
| **Ctrl**+**Q** | Pesquisar | Pesquise todas as configurações do Visual Studio |
| **F5** | Iniciar a depuração | Inicie a depuração do aplicativo |
| **Ctrl**+**F5** | Executar sem Depurar | Execute o aplicativo localmente sem depuração |
| **Ctrl**+**K**,**D** (Perfil Padrão) ou **Ctrl**+**E**,**D** (Perfil C#) | [Formatar Documento](code-styles-and-quick-actions.md#format-document-command) | Limpe as violações de formatação de um arquivo com base nas configurações de nova linha, de espaçamento e de recuo |
| **Ctrl**+**\\**,**Ctrl**+**E** (Perfil Padrão) ou **Ctrl**+**W**,**E** (Perfil do C#) | Exibir Lista de Erros | Veja todos os erros no documento, no projeto ou na solução |
| **Alt** + **PgUp/PgDn** | Ir para o problema seguinte/anterior | Vá para o erro, aviso ou sugestão seguinte/anterior no documento (disponível no **Visual Studio 2017 versão 15.8** e posterior) |

> [!NOTE]
> Algumas extensões desassociam as associações de teclas padrão do Visual Studio. Para usar os comandos a acima, restaure as associações de teclas para os padrões do Visual Studio acessando **Ferramentas** > **Importar e Exportar Configurações** > **Redefinir todas as configurações** ou **Ferramentas** > **Opções** > **Teclado** > **Redefinir**.

Para obter mais informações sobre os comandos e atalhos de teclado, confira os [atalhos de teclado](../ide/tips-and-tricks-for-visual-studio.md).

## <a name="navigate-quickly-to-files-or-types"></a>Navegar rapidamente para arquivos ou tipos

O Visual Studio 2017 tem um recurso chamado **Ir para Todos** (**Ctrl**+**T**). **Ir para Todos** permite que você acesse rapidamente qualquer declaração de arquivo, tipo, membro ou símbolo.

- Altere a localização desta barra de pesquisa ou desative a visualização de navegação dinâmica usando o ícone de **engrenagem**.
- Filtre os resultados usando uma sintaxe, como `t mytype`.
- Defina o escopo da pesquisa somente para o documento atual.
- Há suporte para a correspondência de Camelcase.

![Ir para todos no Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules-on-a-codebase"></a>Impor regras de estilo de código em uma base de código

Use um arquivo *.editorconfig* para codificar as convenções de codificação e aplicá-las à fonte.

::: moniker range="vs-2017"

- Você pode instalar a [extensão Serviços de linguagem EditorConfig](https://aka.ms/editorconfig), que torna mais fácil adicionar e editar um arquivo *.editorconfig* no Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

- Criar automaticamente um arquivo *.editorconfig* com base nas configurações de estilo de código em **Ferramentas** > **Opções** > **Editor de texto**  > **C#** > **Estilo de código**.

   ![Gerar o arquivo .editorconfig a partir das configurações no VS 2019](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- Experimente a [extensão do IntelliCode para o Visual Studio](/visualstudio/intellicode/intellicode-visual-studio). Essa extensão experimental infere os estilos de código a partir do código existente e, em seguida, cria um arquivo *.editorconfig* não vazio com suas preferências de estilo de código já definidas.

- Confira a [documentação das opções de convenção de codificação .NET](editorconfig-code-style-settings-reference.md).

- Confira [este gist](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8) para obter um exemplo de arquivo *.editorconfig*.

![Imposição de estilo de código no Visual Studio](../ide/media/VSGuide_CodeStyle.png)

## <a name="refactorings-and-code-fixes"></a>Refatorações e correções de código

O Visual Studio vem com muitas refatorações, ações de geração de códigos e correções de códigos. As linhas onduladas vermelhas representam erros, as linhas onduladas verdes representam avisos e os três pontos cinzas representam sugestões de código. Acesse as correções de código clicando no ícone de lâmpada/chave de fenda ou pressionando **Ctrl**+**.** ou **Alt**+**Enter**. Cada correção vem com uma janela de visualização que mostra a diferença do código em tempo real de como a correção funciona.

As correções rápidas e refatorações comuns incluem:

- *Renomear*
- *Método Extract*
- *Alterar assinatura do método*
- *Gerar construtor*
- *Método Generate*
- *Mover Tipo para Arquivo*
- *Adicionar Null-Check*
- *Adicionar Parâmetro*
- *Remover Usos Desnecessários*
- *Loop Foreach para uma consulta LINQ ou um método LINQ*
- *Efetuar pull de membros*
- Para obter mais informações, confira os [recursos de geração de código](code-generation-in-visual-studio.md)

Você pode [instalar analisadores FxCop](../code-quality/install-fxcop-analyzers.md) para sinalizar problemas de códigos. Ou escrever sua própria refatoração ou correção de código com [analisadores Roslyn](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix).

Vários membros da comunidade escreveram extensões gratuitas que adicionam outras inspeções de código:

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [SonarLint para Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)

![Refatorações no Visual Studio](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>Localizar Usos, Ir Para Implementação e Navegar para Assemblies Descompiladas

O Visual Studio tem muitos recursos para ajudar você a pesquisar e [navegar em seu código](../ide/navigating-code.md).

| Recurso | Atalho | Detalhes/melhorias |
|- | - | -|
| Localizar Todas as Referências | **Shift**+**F12**| Os resultados são coloridos e podem ser agrupados por projeto, definição e tipo de referência, como leitura ou escrita. Também é possível "bloquear" resultados. |
| Ir Para Implementação | **Ctrl**+**F12** | É possível usar “Ir para definição” na palavra-chave `override` para navegar até o membro substituído |
| Ir para definição | **F12** ou **Ctrl**+**Clique**| Pressione **Ctrl** enquanto clica para navegar até a definição |
| Inspecionar Definição | **Alt**+**F12** | Exibição embutida de uma definição |
| Visualizador de Estrutura | Linhas cinzas pontilhadas entre chaves | Passe o mouse para ver a estrutura do código |
| Navegação para assemblies descompilados | **F12** ou **Ctrl**+**Clique** | Navegue para a fonte externa (descompilada com ILSpy) habilitando a funcionalidade: **Ferramentas** > **Opções** > **Editor de Texto** > **C#** > **Avançado** > **Habilitar navegação para fontes descompiladas**. |

![Ir para Todos e Localizar Todas as Referências](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>IntelliSense aprimorado

Baixe a [extensão do IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode) para obter [conclusões de código de reconhecimento de contexto](/visualstudio/intellicode/intellicode-visual-studio) em vez de apenas uma lista em ordem alfabética. É possível também treinar um [modelo personalizado do IntelliSense](/visualstudio/intellicode/custom-model-faq) com base em suas próprias bibliotecas específicas de domínio.

## <a name="unit-testing"></a>Teste de unidade

A partir do Visual Studio 2017, há vários aprimoramentos na experiência de teste. Você pode realizar testes com as estruturas de teste MSTest v1, MSTest v2, NUnit ou XUnit.

- A detecção de testes do **Gerenciador de Testes** é rápida.
- Organize seus testes no **Gerenciador de Testes** com a *classificação hierárquica*.
- O [Live Unit Testing](../test/live-unit-testing.md) executa continuamente os testes afetados pelas alterações de código e atualiza os ícones do editor embutido para informar o status dos testes. Inclua ou exclua testes específicos ou projetos de teste pelo Live Test Set (conjunto de teste de modo real).

![Exibição de hierarquia do Gerenciador de Testes no Visual Studio](../ide/media/VSGuide_Testing.png)

## <a name="debugging"></a>Depuração

Alguns dos recursos de depuração do Visual Studio incluem:

::: moniker range=">=vs-2019"

- A capacidade de pesquisar uma cadeia de caracteres dentro das janelas **Inspeção**, **Autos** e **Locais**.
- *Clique para executar*, que permite focalizar uma linha de código, pressionar o ícone verde 'executar' que é exibido e executar o programa até atingir essa linha.
- **Auxiliar de Exceção**, que coloca as informações mais importantes no nível superior na caixa de diálogo, por exemplo, qual variável `null` está em uma `NullReferenceException`.
- [Depuração para retroceder novamente](../debugger/view-historical-application-state.md), que permite voltar a pontos de interrupção ou etapas anteriores e exibir o estado do aplicativo no passado.
- [Depuração de instantâneo](/azure/application-insights/app-insights-snapshot-debugger), que permite investigar o estado de um aplicativo Web online no momento em que uma exceção foi lançada (é necessário estar no Azure).

::: moniker-end

::: moniker range="vs-2017"

- *Clique para executar*, que permite focalizar uma linha de código, pressionar o ícone verde 'executar' que é exibido e executar o programa até atingir essa linha.
- **Auxiliar de Exceção**, que coloca as informações mais importantes no nível superior na caixa de diálogo, por exemplo, qual variável `null` está em uma `NullReferenceException`.
- [Depuração para retroceder novamente](../debugger/view-historical-application-state.md), que permite voltar a pontos de interrupção ou etapas anteriores e exibir o estado do aplicativo no passado.
- [Depuração de instantâneo](/azure/application-insights/app-insights-snapshot-debugger), que permite investigar o estado de um aplicativo Web online no momento em que uma exceção foi lançada (é necessário estar no Azure).

::: moniker-end

![Auxiliar de Exceção no Visual Studio](../ide/media/VSGuide_Debugging.png)

## <a name="version-control"></a>Controle de versão

Você pode usar o Git ou o TFVC para armazenar e atualizar seu código no Visual Studio.

::: moniker range=">=vs-2019"

- Instalar as [solicitações de pull para o Visual Studio](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs) para criar, examinar, fazer check-out e executar solicitações de pull sem sair do Visual Studio.

::: moniker-end

- Organize as alterações locais no [Team Explorer](reference/team-explorer-reference.md) e use a barra de status para acompanhar confirmações e alterações pendentes.

- Configure a integração e a entrega contínuas de seus projetos de ASP.NET dentro do Visual Studio com a extensão [Ferramentas de entrega contínua do Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio).

![Controle do código-fonte no Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>Que outros recursos eu devo conhecer?

Aqui está uma lista dos recursos do editor e de produtividade para escrever códigos com mais eficiência. Pode ser necessário ativar alguns recursos, pois eles ficam desativados por padrão (eles podem indexar itens em seu computador, são controversos ou atualmente são experimentais).

| Recurso | Detalhes | Como habilitar |
|-|-|-|
| Arquivo local no Gerenciador de Soluções | Realça o arquivo ativo no **Gerenciador de Soluções** | **Ferramentas** > **Opções** > **Projetos e Soluções** > **Acompanhar Item Ativo no Gerenciador de Soluções** |
| Adicionar usos para tipos em assemblies de referência e pacotes do NuGet | Mostra uma lâmpada de erro com uma correção de código para instalar um pacote do NuGet para um tipo não referenciado | **Ferramentas** > **Opções** > **Editor de Texto** > **C#** > **Avançado** > **Sugerir usos para tipos em assemblies de referência** e **Sugerir usos para tipos em pacotes NuGet** |
| Habilitar análise de solução completa | Ver todos os erros na solução na **Lista de Erros** | **Ferramentas** > **Opções** > **Editor de Texto** > **C#** > **Avançado** > **Habilitar análise completa da solução** |
| Habilitar a navegação para origens descompiladas | Habilite Ir Para a Definição em tipos/membros de fontes externas e usar o descompilador ILSpy para mostrar os corpos de método | **Ferramentas** > **Opções** > **Editor de Texto** > **C#** > **Avançado** > **Habilitar navegação para fontes descompiladas** |
| Modo de conclusão/sugestão | Altera o comportamento de conclusão no IntelliSense. Os desenvolvedores com experiência em IntelliJ tendem a usar uma configuração diferente da configuração padrão aqui. | **Menu** > **Editar** > **IntelliSense** > **Ativar/Desativar Modo de Preenchimento** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Exibe informações de referência de código e o histórico de alterações no editor | **Ferramentas** > **Opções** > **Editor de Texto** > **Todas as Linguagens** > **CodeLens** |
| [Snippets de código](../ide/visual-csharp-code-snippets.md) | Ajudar a apagar um código clichê comum | Digite um nome de snippet e pressione **Tab** duas vezes. |