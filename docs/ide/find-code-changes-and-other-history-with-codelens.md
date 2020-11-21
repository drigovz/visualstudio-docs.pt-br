---
title: Localizar alterações de código e outro histórico com o CodeLens
description: Saiba mais sobre o CodeLens e como usá-lo explorar o histórico do seu código sem precisar sair do editor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.CodeLens
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 485287239a13f61d10ee39bad854a0f3bdae4f55
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006699"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Localizar alterações de código e outro histórico com o CodeLens

O CodeLens permite que você mantenha o foco no trabalho enquanto descobre o que aconteceu com seu código – sem sair do editor. Encontre referências e alterações no código, bugs vinculados, itens de trabalho, revisões de código e testes de unidade.

::: moniker range=">=vs-2019"

> [!NOTE]
> O CodeLens está disponível no Visual Studio Community Edition, no entanto, os indicadores de *controle do código-fonte* não estão disponíveis nesta edição.

::: moniker-end

::: moniker range="vs-2017"

> [!NOTE]
> O CodeLens está disponível apenas nas edições Visual Studio Enterprise e Professional. Ele não está disponível na edição Visual Studio Community.

::: moniker-end

Ver onde e como as partes individuais do código são usadas em sua solução:

![Indicadores do CodeLens no editor de códigos](../ide/media/codelens-overview.png)

Entre em contato com sua equipe sobre alterações em seu código sem sair do editor:

![CodeLens – contate sua equipe](../ide/media/codelens-contact-info.png)

Para escolher os indicadores que você deseja ver ou desativar o CodeLens e voltar, vá para **ferramentas**  >  **Opções**  >  **Editor de texto**  >  **todos os idiomas**  >  **CodeLens**.

## <a name="find-references-to-your-code"></a>Localize referências ao seu código

Encontre referências no código C# ou Visual Basic.

1. Escolha o indicador **referências** ou pressione **Alt**+**2**.

   ![Referências do CodeLens](../ide/media/codelens-view-references.png)

   > [!NOTE]
   > Se o indicador mostrar **0 referências**, isso indicará que você não tem nenhuma referência do código C# ou Visual Basic. No entanto, pode haver referências em outros itens, como arquivos *.xaml* e *.aspx*.

2. Para exibir o código de referência, focalize a referência na lista.

   ![CodeLens – espiar referência](../ide/media/codelens-peek-reference.png)

3. Para abrir o arquivo que contém a referência, clique duas vezes na referência.

### <a name="code-maps"></a>Mapas de código

Para ver as relações entre o código e suas referências, [crie um mapa de códigos](../modeling/map-dependencies-across-your-solutions.md). No menu de atalho do mapa de códigos, selecione **Mostrar Todas as Referências**.

![CodeLens – referências no mapa de códigos](../ide/media/codelensmappedreferences.png)

## <a name="find-changes-in-your-code"></a>Encontre alterações no código

Inspecione o histórico do código para descobrir o que aconteceu com ele. Ou examine as alterações antes que elas tenham sido mescladas em seu código para que você possa entender melhor como as alterações em outras ramificações podem afetar seu código.

Você precisa de:

- Edição do Visual Studio Enterprise ou Professional

- Azure DevOps Services, Team Foundation Server 2013 ou posterior ou Git

- [Skype for Business](/skypeforbusiness/) para entrar em contato com sua equipe no editor de códigos

Para o código C# ou Visual Basic armazenado com o TFVC (Controle de Versão do Team Foundation) ou Git, você obtém detalhes do CodeLens nos níveis de classe e de método (indicadores no *nível do elemento de código*). Se seu repositório Git estiver hospedado no TfGit, você receberá links para itens de trabalho do TFS.

![Indicadores no nível do elemento de código](../ide/media/codelens-element-level-indicators.png)

Para arquivo de tipos diferentes de *.cs* ou *.vb*, obtenha detalhes do CodeLens do arquivo inteiro em um só lugar na parte inferior da janela (indicadores no *nível do arquivo*).

![Indicadores do CodeLens no nível do arquivo](../ide/media/almcodelensfilelevelindicators.png)

### <a name="code-element-level-indicators"></a>Indicadores no nível do elemento de código

Os indicadores no nível do elemento de código permitem que você veja quem alterou o código e quais alterações foram feitas. Os indicadores no nível do elemento de código estão disponíveis para o código C# e Visual Basic.

Isto é o que você vê ao usar o TFVC (Controle de Versão do Team Foundation) no Team Foundation Server ou no Azure DevOps Services:

![CodeLens: obter o histórico de alterações do código no TFVC](../ide/media/codelens-code-changes.png)

O período de tempo padrão são os últimos 12 meses. Se o código estiver armazenado no Team Foundation Server, você poderá alterar o período executando o [comando TFSConfig](/azure/devops/server/command-line/tfsconfig-cmd) com o [comando CodeIndex](../ide/codeindex-command.md) e com o sinalizador **/indexHistoryPeriod**.

Para ver um histórico detalhado de todas as alterações, incluindo as de mais de um ano atrás, escolha **Mostrar todas as alterações de arquivo**:

![Mostrar todas as alterações de código](../ide/media/codelens-show-all-file-changes.png)

A janela **Histórico** é exibida:

![Janela Histórico de todas as alterações do código](../ide/media/codelenscodechangeshistory.png)

Quando os arquivos estão em um repositório Git e você escolhe o indicador de alterações no nível do elemento de código, isto é o que você vê:

![CodeLens: obter o histórico de alterações do código no Git](../ide/media/codelens-code-changes-git.png)

### <a name="file-level-indicators"></a>Indicadores no nível do arquivo

Encontre alterações de um arquivo inteiro nos indicadores no nível do arquivo na parte inferior da janela:

![CodeLens: obter detalhes do arquivo de código](../ide/media/codelens-file-level.png)

> [!NOTE]
> Os indicadores no nível do arquivo não estão disponíveis para arquivos C# e Visual Basic.

Para ver mais detalhes sobre uma alteração, clique com o botão direito do mouse nesse item. Dependendo se você estiver usando o TFVC ou o Git, haverá opções para comparar as versões do arquivo, exibir detalhes e acompanhar o conjunto de alterações, obter a versão selecionada do arquivo e enviar por email para o autor dessa alteração. Alguns desses detalhes são exibidos em **Team Explorer**.

É possível ver quem alterou seu código ao longo do tempo. Isso pode ajudá-lo a encontrar padrões nas alterações da sua equipe e avaliar o impacto delas.

![CodeLens: ver o histórico de alterações do código como um grafo](../ide/media/codelens.png)

### <a name="find-changes-in-your-current-branch"></a>Encontre alterações na sua ramificação atual

Sua equipe pode ter vários branches, por exemplo, um branch principal e um branch de desenvolvimento filho, para reduzir o risco de interrupção de código estável.

![CodeLens: localizar alterações em seu Branch atual](../ide/media/codelensfirstbranchconceptual.png)

Você pode descobrir quantas pessoas alteraram seu código e quantas alterações foram feitas na ramificação principal pressionando **ALT** + **6**:

![CodeLens: encontre quantas alterações foram feitas no branch](../ide/media/codelens-branch-changes.png)

### <a name="find-when-your-code-was-branched"></a>Descubra quando o código foi ramificado

Para saber quando o código foi ramificado, navegue para o código no branch filho. Em seguida, selecione o indicador **alterações** ou pressione **Alt**+**6**:

![CodeLens: descobrir quando o código foi ramificado](../ide/media/codelens-first-branch.png)

### <a name="find-incoming-changes-from-other-branches"></a>Descubra alterações recebidas de outras ramificações

![CodeLens: encontrar alterações de código em outros branches](../ide/media/codelensbranchchangecheckinconceptual.png)

Veja as alterações recebidas. Na seguinte captura de tela, foi feita uma correção de bug no branch "Dev":

![CodeLens: alteração com check-in em outro branch](../ide/media/codelens-branch-changes-dev.png)

Examine a alteração sem sair do branch atual ("Main"):

![CodeLens: ver a alteração recebida de outro branch](../ide/media/codelens-branch-changes-main.png)

### <a name="find-when-changes-got-merged"></a>Descubra onde as alterações foram mescladas

Você pode ver quando as alterações foram mescladas, para que você possa determinar quais alterações são incluídas no branch:

![CodeLens-localizar quando as alterações foram mescladas](../ide/media/codelensbranchmergedconceptual.png)

Por exemplo, agora o código no branch Main tem a correção de bug do branch "Dev":

![CodeLens – alterações mescladas entre branches](../ide/media/codelens-branch-merged.png)

### <a name="compare-an-incoming-change-with-your-local-version"></a>Comparar uma alteração recebida com a versão local

Compare uma alteração de entrada com sua versão local pressionando **Shift** + **F10** ou clicando duas vezes no conjunto de alterações.

![CodeLens: comprar a alteração recebida com a versão local](../ide/media/codelens-branch-incoming-change-menu.png)

### <a name="branch-icons"></a>Ícones do branch

O ícone na coluna **Branch** indica como o branch está relacionado ao branch no qual você está trabalhando.

|**Ícone**|**A alteração foi proveniente de:**|
|--------------| - |
|![CodeLens: alteração de ícone do branch atual](../ide/media/codelensbranchcurrenticon.png)|A ramificação atual|
|![CodeLens: alteração de ícone do branch pai](../ide/media/codelensbranchparenticon.png)|A ramificação pai|
|![CodeLens: alteração de ícone do branch filho](../ide/media/codelensbranchchildicon.png)|Uma ramificação filha|
|![CodeLens: alteração de ícone do branch par](../ide/media/codelensbranchpeericon.png)|Uma ramificação par|
|![CodeLens: alteração de ícone do branch mais distante](../ide/media/codelensbranchfurtherawayicon.png)|Uma ramificação mais distante que uma pai, filha ou par|
|![CodeLens: mesclagem de ícone pai](../ide/media/codelensbranchmergefromparenticon.png)|Uma mesclagem da ramificação pai para uma ramificação filha|
|![CodeLens: mesclagem de ícone do branch filho](../ide/media/codelensbranchmergefromchildicon.png)|Uma mesclagem de uma ramificação filha para a ramificação pai|
|![CodeLens: mesclagem de ícone do branch não relacionado](../ide/media/codelensbranchmergefromunrelatedicon.png)|Uma mesclagem de uma ramificação não relacionada (mesclagem sem base)|

## <a name="linked-work-items"></a>Itens de trabalho vinculados

Encontre itens de trabalho vinculados selecionando o indicador **itens de trabalho** ou pressionando **Alt**+**8**.

![CodeLens – encontrar itens de trabalho de um código específico](../ide/media/codelens-work-items.png)

## <a name="linked-code-reviews"></a>Revisões de código vinculadas

Encontre revisões de código vinculadas selecionando o indicador **revisões**. Para usar o teclado, mantenha pressionada a tecla **Alt** e, em seguida, pressione **Seta para a esquerda** ou **Seta para a direita** para navegar pelas opções de indicador.

![CodeLens – exibir solicitações de revisão de código](../ide/media/codelens-code-reviews.png)

## <a name="linked-bugs"></a>Bugs vinculados

Encontre bugs vinculados selecionando o indicador **bugs** ou pressionando **Alt**+**7**.

![CodeLens – encontrar bugs vinculados a conjuntos de alterações](../ide/media/codelens-bugs-changesets.png)

## <a name="contact-the-owner-of-an-item"></a>Contatar o proprietário de um item

Encontre o autor de um item selecionando o indicador **autores** ou pressionando **Alt**+**5**.

![Contatar o proprietário de um item](../ide/media/codelens-contact-item-owner.png)

Abra o menu de atalho de um item para ver as opções de contato. Se você tiver o Lync ou o Skype for Business instalado, você verá estas opções:

![Opções de contato para um item](../ide/media/codelens-item-contact-menu.png)

## <a name="associated-unit-tests"></a>Testes de unidade associados

Descubra testes de unidade existentes para o código C# ou Visual Basic sem abrir o **Gerenciador de Testes**.

1. Acesse o código do aplicativo que tem o [código de teste de unidade](../test/unit-test-your-code.md) associado.

2. Se você ainda não tiver feito isso, crie seu aplicativo para carregar os indicadores de teste do CodeLens.

3. Examine os testes do código pressionando **ALT** + **3**.

     ![CodeLens – escolher o status do teste no editor de códigos](../ide/media/codelens-choose-test-indicator.png)

4. Se um ícone de aviso for exibido, ![ícone de aviso](../ide/media/codelenstestwarningicon.png)isso indicará que os testes ainda não foram executados; portanto, execute-os.

     ![CodeLens – exibir testes de unidade ainda não executados](../ide/media/codelens-tests-not-yet-run.png)

5. Para examinar a definição de um teste, clique duas vezes no item de teste na janela do indicador CodeLens para abrir o arquivo de código no editor.

     ![CodeLens – ir para a definição de teste de unidade](../ide/media/codelens-unit-test-definition.png)

6. Para examinar os resultados do teste, escolha o indicador status do teste (ícone de ![ teste de falha ](../ide/media/codelenstestfailedicon.png) ou ![ ícone de teste aprovado ](../ide/media/codelenstestpassedicon.png) ) ou pressione **ALT** + **1**.

     ![CodeLens – ver o resultado do teste de unidade](../ide/media/codelens-unit-test-result.png)

7. Para ver quantas pessoas alteraram esse teste, quem alterou esse teste ou quantas alterações foram feitas nesse teste, [encontre o histórico do código](#find-changes-in-your-code) e os itens vinculados.

## <a name="keyboard-shortcuts"></a>Atalhos do teclado

Para usar o teclado para selecionar indicadores, pressione a tecla **Alt** e mantenha-a pressionada para exibir as teclas numéricas relacionadas e, em seguida, pressione o número que corresponde ao indicador que você deseja selecionar.

![Números de acesso do teclado](../ide/media/codelens-alt-keys.png)

> [!NOTE]
> Para selecionar o indicador **revisões**, mantenha **Alt** pressionado usando as teclas de seta para a esquerda e direita para navegar.

## <a name="q--a"></a>Perguntas e Respostas

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a>P: Como fazer ativar ou desativar CodeLens ou escolher quais indicadores ver?

**R:** é possível ativar ou desativar indicadores, exceto o indicador de referências. Vá para **ferramentas**  >  **Opções**  >  **Editor de texto**  >  **todos os idiomas**  >  **CodeLens**.

Quando os indicadores são ativados, você pode abrir as opções do CodeLens nos indicadores.

![CodeLens – ativar ou desativar indicadores](../ide/media/codelensturnoffonindicatorsfromcode.png)

Ative e desative os indicadores de nível de arquivo do CodeLens usando os ícones de divisas na parte inferior da janela do editor.

![Ativar e desativar indicadores no nível do arquivo](../ide/media/codelensfilelevelonandoff.png)

### <a name="q-where-is-codelens"></a>P: Em que local o CodeLens se encontra?

**R:** o CodeLens é exibido no código C# e Visual Basic no nível de método, classe, indexador e propriedade. O CodeLens é exibido no nível de arquivo para todos os outros tipos de arquivos.

- Certifique-se que o CodeLens está ativado. Vá para **ferramentas**  >  **Opções**  >  **Editor de texto**  >  **todos os idiomas**  >  **CodeLens**.

- Se seu código estiver armazenado no TFS, certifique-se de que a indexação do código está ativada usando o [comando CodeIndex](../ide/codeindex-command.md) com o [comando TFS Config](/azure/devops/server/command-line/tfsconfig-cmd).

- Os indicadores relacionados a DevOps são exibidos apenas quando os itens de trabalho são vinculados ao código e quando você tem permissão para abrir itens de trabalho vinculados. Confirme que você tem [permissões de membro da equipe](/azure/devops/organizations/security/view-permissions?view=vsts&preserve-view=true).

- Os indicadores de teste de unidade não são exibidos quando o código do aplicativo não tem testes de unidade. Os indicadores de status do teste aparecem automaticamente em projetos de teste. Se você souber que o código do aplicativo tem testes de unidade, mas os indicadores de teste não aparecerem, tente criar a solução (**Ctrl** + **Shift** + **B**).

::: moniker range=">=vs-2019"

> [!TIP]
> O CodeLens está disponível no Visual Studio Community Edition, no entanto, os indicadores de *controle do código-fonte* não estão disponíveis nesta edição.

::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> O CodeLens não está disponível na edição Visual Studio Community.

::: moniker-end

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>P: Por que eu não vejo os detalhes de item de trabalho para uma confirmação?

**R:** Isso pode acontecer porque o CodeLens não consegue localizar os itens de trabalho no Azure Boards nem no TFS. Verifique se você está conectado ao projeto que tem esses itens de trabalho e se tem permissões para vê-los. Além disso, os detalhes do item de trabalho poderão não ser exibidos se a descrição de confirmação contiver informações incorretas sobre as IDs de item de trabalho no Azure Boards ou no TFS.

### <a name="q-why-dont-i-see-the-skype-indicators"></a>P: Por que não vejo os indicadores do Skype?

**R:** Os indicadores do Skype não serão exibidos se você não tiver entrado no Skype for Business, não o tiver instalado ou não tiver uma configuração compatível. No entanto, você ainda poderá enviar o email:

![CodeLens – contatar o proprietário do conjunto de alterações por email](../ide/media/codelenscodesendmailchangesetnolync1.png)

**Quais configurações do Skype e do Lync são compatíveis?**

- Skype for Business (32 bits ou 64 bits)

- Lync 2010 ou posterior sozinho (32 bits ou 64 bits), mas não Lync Basic 2013 com o Windows 8.1

O CodeLens não dá suporte a diferentes versões do Lync ou do Skype instaladas. Talvez elas não estejam localizadas para todas as versões localizadas do Visual Studio.

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>P: como posso alterar a fonte e a cor do CodeLens?

**R:** Acesse **Ferramentas** > **Opções** > **Ambiente** > **Fontes e Cores**.

![CodeLens – alterar as configurações de fonte e cor](../ide/media/codelensoptionsfontscolorssettings.png)

Para usar o teclado:

1. Pressione **ALT** + **T** + **o** para abrir a caixa de diálogo **Opções** .

2. Pressione **Seta para cima** ou **Seta para baixo** para acessar o nó **Ambiente**. Em seguida, pressione **Seta para a esquerda** para expandir o nó.

3. Pressione **Seta para baixo** para acessar **Fontes e Cores**.

4. Pressione **Tab** para ir para a lista **Mostrar configurações de** e, em seguida, pressione a **seta para baixo** para selecionar **CodeLens**.

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>P: Posso mover o HUD do CodeLens?

**R:** Sim, escolha o ![ícone de Encaixe](../ide/media/codelensdockwindow.png) para encaixar o CodeLens como uma janela.

![Botão Encaixar na janela do indicador do CodeLens](../ide/media/codelensselectdockwindow.png)

![Janela Referências de CodeLens encaixada](../ide/media/codelensreferencesdockedwindow.png)

### <a name="q-how-do-i-refresh-the-indicators"></a>P: Como posso atualizar os indicadores?

**R:** isso depende do indicador:

- **Referências**: este indicador é atualizado automaticamente quando o código é alterado. Se o indicador **referências** estiver encaixado como uma janela separada, atualize o indicador selecionando **Atualizar**:

   ![Botão Atualizar em Referências do CodeLens](../ide/media/codelensviewreferencesdocked.png)

- **Equipe**: atualize esses indicadores selecionando **Atualizar Indicadores da Equipe CodeLens** no menu de clique com o botão direito:

   ![Item de menu Atualizar Indicadores da Equipe CodeLens](../ide/media/codelensrefreshindicatorsfromcode.png)

- **Teste**: [encontre os testes de unidade do código](#associated-unit-tests) para atualizar o indicador **Teste**.

### <a name="q-whats-local-version"></a>P: O que é "Versão Local"?

**R:** A seta **Versão local** aponta para o conjunto de alterações mais recente na versão local de um arquivo. Quando o servidor tem um conjunto de alterações mais recente, elas são exibidas acima ou abaixo da seta **Versão local**, dependendo da ordem usada para classificar os conjuntos de alterações.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>P: posso gerenciar a maneira como o CodeLens processa o código para mostrar o histórico e os itens vinculados?

**R:** Sim. Se o código estiver no TFS, use o [comando CodeIndex](../ide/codeindex-command.md) com o [comando TFS Config](/azure/devops/server/command-line/tfsconfig-cmd).

### <a name="q-my-codelens-test-indicators-no-longer-appear-in-my-file-when-i-first-open-my-solution-how-can-i-load-them"></a>P: Meus indicadores de teste do CodeLens não aparecem mais no meu arquivo quando abro minha solução pela primeira vez. Como posso carregá-los?

**R:** Recompile seu projeto para obter os indicadores de teste do CodeLens para carregar no seu arquivo. Para melhorar o desempenho, o Visual Studio não busca mais informações de origem para os indicadores de teste quando os arquivos de código são carregados. Os indicadores de teste são carregados após um build ou quando você navega até um teste clicando duas vezes nele no **Gerenciador de Testes**.

## <a name="see-also"></a>Confira também

- [Recursos do editor de código](../ide/writing-code-in-the-code-and-text-editor.md)
