---
title: Editando testes de IU codificados usando o Editor de Teste de IU Codificado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.codedUItest.testeditor
helpviewer_keywords:
- coded UI test, Coded UI Test Editor
ms.assetid: 76435c4b-593e-43a3-a9fe-709a7f9f5e0f
caps.latest.revision: 42
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c070f1bafb157e3979eb9c1f49b317b17807f1e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "82587004"
---
# <a name="editing-coded-ui-tests-using-the-coded-ui-test-editor"></a>Editando testes de interface de usuário codificada usando o editor de teste de interface de usuário codificada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

o Editor de testes de interface de usuário codificada permite modificar facilmente os testes de IU codificados. Ao usar o Editor de Teste de IU Codificado, é possível localizar, exibir e editar as propriedades de métodos de teste e ações de interface do usuário. Além disso, é possível utilizar o mapa de controles de interface do usuário para exibir e editar os controles correspondentes.

 **Requisitos**

- Visual Studio Enterprise

## <a name="why-should-i-do-this"></a>Por que devo fazer isso?
 Usar o Editor de Teste de IU Codificado é mais rápido e eficiente do que editar o código utilizando métodos de testes de IU codificados por meio do Editor de Códigos. Com o Editor de Teste de IU Codificado, é possível usar a barra de ferramentas e os menus de atalho para localizar e modificar rapidamente valores de propriedade associados a ações e controles de interface do usuário. Por exemplo, é possível utilizar a barra de ferramentas do Editor de Teste de IU Codificado para executar os seguintes comandos:

 ![Edição de teste da interface do usuário](../test/media/uitesteditor.png "UITestEditor")

1. [Localizar](../ide/finding-and-replacing-text.md) ajuda a localizar ações e controles de interface do usuário.

2. [Excluir](#CodedUITestEditor_DeleteUIActions) remove ações de interface do usuário indesejadas.

3. **Renomear** altera os nomes de métodos de teste e controles.

4. **Propriedades** abre a janela Propriedades do item selecionado.

5. [Dividir em um novo método](#CodedUITestEditor_SplitMethods) permite modularizar as ações de interface do usuário.

6. [Mover o Código](#CodedUITestEditor_MoveMethods) adiciona o código personalizado aos métodos de teste.

7. [Inserir Atraso Antes](#CodedUITestEditor_InsertDelay) adiciona uma pausa antes de uma ação de interface do usuário, especificada em milissegundos.

8. [Localizar o Controle de interface do usuário](#CodedUITestEditor_LocateUIControl) identifica o local do controle na interface do usuário do aplicativo em teste.

9. [Localizar tudo](#CodedUITestEditor_LocateDecendants) ajuda a verificar a propriedade de controle e as alterações significativas nos controles do aplicativo.

## <a name="how-do-i-do-this"></a>Como faço isso?
 Em [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], abrir o arquivo UIMap.uitest afiliado ao teste de IU codificado no projeto de teste de IU codificado o exibirá automaticamente no Editor de Teste de IU Codificado. Os procedimentos a seguir descrevem como localizar e editar métodos de teste e propriedades das ações e dos controles de interface do usuário usando a barra de ferramentas e os menus de atalho do editor.

## <a name="open-a-coded-ui-test"></a>Abrir um teste de IU codificado
 É possível exibir e editar testes de IU codificado baseados no Visual C# e no Visual Basic por meio do Editor de Teste de IU Codificado.

 ![Menu de contexto Editar com o Construtor de Teste de IU Codificado](../test/media/editcodeduitest.png "EditCodedUITest")

 No Gerenciador de Soluções, abra o menu de atalho do **UIMap.uitest** e escolha **Abrir**. O teste de IU codificado é exibido no Editor de Teste de IU Codificado. Agora, é possível exibir e editar os métodos, as ações e os controles correspondentes registrados no teste de IU codificado.

> [!TIP]
> Ao selecionar uma ação de interface do usuário localizada em um método do painel **Ações de interface do usuário**, o controle correspondente será realçado. Também é possível modificar a ação de interface do usuário ou as propriedades dos controles.

 *Não vejo* o Editor de Teste de IU Codificado.
Você pode estar usando uma versão do Visual Studio Enterprise anterior a 2012. O Editor de Teste de IU Codificado também estava disponível no Feature Pack 2 do Visual Studio 2010, com uma assinatura do MSDN. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Feature Pack 2 do Microsoft Visual Studio 2010](https://msdn.microsoft.com/library/gg269474.aspx).

## <a name="modify-ui-action-properties-and-their-corresponding-control-properties"></a><a name="CodedUITestEditor_EditActionAndControlProperties"></a> Modificar propriedades de ação de interface do usuário e as propriedades de controle correspondentes
 Por meio do Editor de Teste de IU Codificado, é possível localizar e exibir rapidamente todas as ações de interface do usuário de métodos de teste. Ao selecionar a ação de interface do usuário no editor, o controle correspondente será realçado automaticamente. Do mesmo modo, ao selecionar um controle, as ações de interface do usuário correspondentes serão realçadas. Selecionar uma ação ou controle de interface do usuário facilita o uso da janela Propriedades para modificar as propriedades correspondentes.

 ![Propriedades da ação da interface do usuário](../test/media/codeduiedituiaction.png "CodedUIEditUIAction") Editar propriedades da ação da interface do usuário

 Para modificar as propriedades de uma ação de interface do usuário, no painel **Ações de interface do usuário**, expanda o método de teste que contém uma ação de IU cujas propriedades você deseja editar, selecione a ação de interface do usuário e, em seguida, modifique as propriedades usando a janela Propriedades.

 Por exemplo, se um servidor não estiver disponível e houver uma ação de interface do usuário associada ao navegador da Web que indica **Acesse a página da Web ‘<http://Contoso1/default.aspx’>**, você poderá alterar a URL para `‘http://Contoso2/default.aspx’`.

 ![Propriedades de controle](../test/media/codeduitestcontrolprop.png "CodedUITestControlProp") Editar propriedades de controle

 Os procedimentos usados para modificar as ações de interface do usuário também podem ser utilizados para modificar as propriedades de um controle. No painel **Mapa do Controle de interface do usuário**, selecione o controle a ser editado e modifique as propriedades por meio da janela Propriedades.

 Por exemplo, um desenvolvedor pode ter alterado a propriedade **(ID)** em um controle de botão no código-fonte do aplicativo que está sendo testado de "idSubmit" para "idLogin". Com a alteração da propriedade **(ID)** no aplicativo, o teste de IU codificado não poderá localizar o controle de botão e falhará. Nesse caso, o testador pode abrir a coleção **Propriedades de Pesquisa** e alterar a propriedade **Id** para que ela corresponda ao novo valor usado pelo desenvolvedor no aplicativo. O testador também pode alterar o valor da propriedade **nome amigável** de "enviar" para "logon". Com essa alteração, a ação de interface do usuário associada ao Editor de Teste de IU Codificado será atualizada de “Escolher o botão ‘Enviar’” para “Escolher o botão ‘Logon’”.

 Após concluir as modificações, salve-as no arquivo UIMap.Designer escolhendo **Salvar** na barra de ferramentas [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 *O que mais eu deveria saber?*
 **Sobre**

- ![Dica](../test/media/tip.png "Dica") Se o janela Propriedades não for exibido, pressione e mantenha pressionada a **tecla Alt** enquanto pressiona **Enter**ou pressione **F4**.

- ![Dica](../test/media/tip.png "Dica") Para desfazer as alterações de propriedade feitas, selecione **desfazer** no menu **Editar** ou pressione CTRL + Z.

- ![Dica](../test/media/tip.png "Dica") Você pode usar o botão **Localizar** na barra de ferramentas do editor de teste de interface do usuário codificado para abrir a ferramenta localizar e substituir no Visual Studio. Em seguida, será possível usar o controle Localizar para localizar uma ação de interface do usuário no Editor de Teste de IU Codificado. Por exemplo, você pode tentar localizar “Clique no botão ‘Logon’”. Isso pode ser útil em testes grandes. Não é possível utilizar a funcionalidade de substituição na ferramenta Localizar e Substituir no Editor de Teste de IU Codificado. Para obter mais informações, consulte o controle Localizar em [Localizando e Substituindo Texto](../ide/finding-and-replacing-text.md).

- ![Dica](../test/media/tip.png "Dica") Às vezes, pode ser difícil visualizar onde os controles estão localizados na interface do usuário do aplicativo em teste. Um dos recursos do Editor de Teste de IU Codificado é a seleção de um controle listado no mapa de controle da interface do usuário e a exibição da localização desse controle no aplicativo em teste. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Localizar um Controle de interface do usuário no aplicativo em Teste](#CodedUITestEditor_LocateUIControl) pode ser consultado mais adiante neste tópico.

- ![Dica](../test/media/tip.png "Dica") Pode ser necessário expandir o controle de contêiner que contém o controle que você deseja editar. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Localizar um controle e seus descendentes](#CodedUITestEditor_LocateDecendants) pode ser consultado mais adiante neste tópico.

## <a name="delete-unwanted-ui-actions"></a><a name="CodedUITestEditor_DeleteUIActions"></a> Excluir ações de interface do usuário indesejadas
 É possível remover ações de interface do usuário indesejadas do teste de IU codificado facilmente.

 ![Excluir a ação de interface do usuário](../test/media/codeduideleteuiaction.png "CodedUIDeleteUIAction")

 No painel **Ações de interface do usuário**, expanda o método de teste que contém a ação de interface do usuário a ser excluída. Abra o menu de atalho da ação de interface do usuário e escolha **Excluir**.

## <a name="split-a-test-method-into-two-separate-methods"></a><a name="CodedUITestEditor_SplitMethods"></a> Dividir um método de teste em dois métodos separados
 É possível dividir um método de teste para refinar ou modularizar as ações de interface do usuário. Por exemplo, o teste pode ter um único método de teste com ações de interface do usuário em duas caixas de controles. As ações de interface do usuário podem ser modularizadas com mais eficiência em dois métodos que correspondam a um contêiner.

 ![SPLT um método de teste](../test/media/codeduitestsplitmethod1.png "CodedUITestSplitMethod1")

 ![Dois métodos de teste](../test/media/codeduitestsplitmethod2.png "CodedUITestSplitMethod2")

 No painel **Ações de interface do usuário**, expanda o método de teste a ser dividido em dois métodos separados e selecione a ação de interface do usuário em que o novo método de teste começará. Abra o menu de atalho da ação de interface do usuário e escolha **Dividir em um novo método** ou escolha o botão **Dividir em um novo método** na barra de ferramentas do Editor de Teste de IU Codificado. O novo método de teste será exibido no painel Ações de interface do usuário. Ele contém as ações de interface do usuário da ação em que a divisão foi especificada.

 Após a conclusão do método de divisão, salve as alterações no arquivo UIMap.Designer escolhendo **Salvar** na barra de ferramentas [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 *O que mais eu deveria saber?*
 **Questões importantes**

- Aviso de ![ícone de cuidado](../test/media/caution.gif "atenção") **:** se você dividir um método, deverá modificar qualquer código que chame o método existente para também chamar o novo método que você está prestes a criar se ainda quiser que essas ações de interface do usuário sejam incluídas. Quando um método é dividido, uma caixa de diálogo do Microsoft Visual Studio é exibida. Ela avisa que é necessário modificar os códigos que chamam o método existente para que eles também chamem o novo método a ser criado. Escolha **Sim**.

  **Sobre**

- ![Dica](../test/media/tip.png "Dica") Para desfazer a divisão, escolha **desfazer** no menu **Editar** ou pressione CTRL + Z.

- ![Dica](../test/media/tip.png "Dica") Você pode renomear o novo método. Selecione-o no painel Ações de interface do usuário e escolha o botão **Renomear** na barra de ferramentas do Editor de Teste de IU Codificado.

   - ou -

   Abra o menu de atalho do novo método de teste e escolha **Renomear**.

   Uma caixa de diálogo do Microsoft Visual Studio é exibida. Ela avisa que é necessário modificar os códigos que referenciam o método. Escolha **Sim**.

## <a name="move-a-test-method-to-the-uimap-file-to-facilitate-customization"></a><a name="CodedUITestEditor_MoveMethods"></a> Mover um método de teste para o arquivo UIMap a fim de facilitar a personalização
 Se que um dos métodos de teste no teste de IU codificado requerer um código personalizado, será necessário movê-lo para o arquivo UIMap.cs ou UIMap.vb. Caso contrário, o código será substituído sempre que o teste de IU codificado for recompilado. Se o método não for movido, o código personalizado será substituído sempre que o teste for recompilado.

 No painel **ação da interface do usuário** , selecione o método de teste que você deseja mover para o arquivo UIMap.cs ou UIMap. vb para facilitar a funcionalidade de código personalizado que não será substituída quando o código de teste for recompilado. Em seguida, escolha o botão **Mover Código** na barra de ferramentas do Editor de Teste de IU Codificado ou abra o menu de atalho do método de teste e escolha **Mover Código**. O método de teste é removido do arquivo UIMap.uitest e não é mais exibido no painel Ações de interface do usuário. Para editar o arquivo de teste movido, abra o arquivo UIMap.cs ou UIMap.vb no Gerenciador de Soluções.

 Após mover o método, salve as alterações no arquivo UIMap.Designer escolhendo **Salvar** na barra de ferramentas [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 *O que mais eu deveria saber?*
 **Questões importantes**

- Aviso de ![ícone de cuidado](../test/media/caution.gif "atenção") **:** depois de mover um método, você não poderá mais editá-lo usando o editor de teste de interface do usuário codificado. Você deve adicionar seu código personalizado e mantê-lo usando o Editor de Códigos. Quando um método é movido, uma caixa de diálogo do Microsoft Visual Studio é exibida. Ela avisa que o método será movido do arquivo UIMap.uitest para o arquivo UIMap.cs ou UIMap.vb e que não será possível editar o método usando o Editor de Teste de IU Codificado. Escolha **Sim**.

  **Sobre**

- ![Dica](../test/media/tip.png "Dica") Para desfazer a movimentação, selecione **desfazer** no menu **Editar** ou pressione CTRL + Z. No entanto, em seguida, será necessário remover manualmente o código do arquivo UIMap.cs ou UIMap.vb.

## <a name="locating-a-ui-control-in-the-application-under-test"></a><a name="CodedUITestEditor_LocateUIControl"></a> Localizar um Controle de interface do usuário no aplicativo em teste
 Algumas vezes, pode ser difícil visualizar onde os controles estão localizados na interface do usuário do aplicativo em teste. Um dos recursos do Editor de Teste de IU Codificado é a seleção de um controle listado no mapa de controle da interface do usuário e a exibição da localização desse controle no aplicativo em teste. O recurso **Localizar o Controle de interface do usuário** no aplicativo em teste também pode ser usado para verificar modificações na propriedade de pesquisa de um controle.

 ![Localizar o controle de interface do usuário](../test/media/codeduilocatecontrol.png "CodedUILocateControl")

 ![Controle localizado no aplicativo em teste](../test/media/codeduilocatecontrol2.png "CodedUILocateControl2")

 No painel **Mapa de Controle de interface do usuário**, selecione o controle a ser localizado no aplicativo associado ao teste. Depois, abra o menu de atalho do controle e, em seguida, escolha **Localizar o Controle de interface do usuário**. No aplicativo em teste, o controle será designado com uma borda azul.

 *O que mais eu deveria saber?*
 **Questões importantes**

- Aviso de ![ícone de cuidado](../test/media/caution.gif "atenção") **:** antes de localizar um controle de interface do usuário, verifique se o aplicativo associado ao teste está em execução.

  **Sobre**

- ![Dica](../test/media/tip.png "Dica") Como alternativa, você pode usar a opção **Localizar tudo** para verificar se todos os controles em um contêiner podem estar localizados corretamente. Essa opção será descrita na próxima seção.

## <a name="locating-a-control-and-its-descendants"></a><a name="CodedUITestEditor_LocateDecendants"></a> Localizar um controle e seus descendentes
 É possível verificar se todos os controles em um contêiner estão localizados corretamente na interface do usuário do aplicativo em teste. Isso pode ser útil para verificar alterações de propriedade de pesquisa realizadas no contêiner. Além disso, se houve alterações significativas na interface do usuário do aplicativo em teste, é possível validar se os controles de propriedades de pesquisa existentes ainda estão corretos.

 ![Localizar todos os controles descendentes](../test/media/codeduilocateall.png "CodedUILocateAll")

 ![Todos os controles localizados](../test/media/codeduilocateall2.png "CodedUILocateAll2")

 No painel **Mapa de Controle de Interface do Usuário**, selecione a caixa de controles cujos descendentes você deseja localizar e exibir. Depois, abra o menu de atalho do controle e escolha **Localizar Tudo**. A caixa de controles e todos os controles descendentes serão marcados no Editor de Teste de IU Codificado com uma marca de seleção verde ou um “X” vermelho. Essas marcas permitem saber se os controles foram localizados com êxito no aplicativo em teste.

 *O que mais eu deveria saber?*
 **Questões importantes**

- Aviso de ![ícone de cuidado](../test/media/caution.gif "atenção") **:** antes de localizar os controles da interface do usuário, verifique se o aplicativo associado ao teste está em execução.

## <a name="inserting-a-delay-before-a-ui-action"></a><a name="CodedUITestEditor_InsertDelay"></a> Inserir um atraso antes de uma ação de interface do usuário
 Ocasionalmente, convém instruir o teste a aguardar a ocorrência de determinados eventos, como a exibição de uma janela, o desaparecimento da barra de progresso etc. Ao utilizar o Editor de Teste de IU Codificado, isso pode ser feito inserindo um atraso antes de uma ação de interface do usuário. É possível especificar quantos segundos o atraso durará.

 ![Inserir atraso antes de uma ação de interface do usuário](../test/media/codeduidelay.png "CodedUIDelay")

 ![Atraso adicionado com 5 segundos](../test/media/codeduidealy2.png "CodedUIDealy2")

 No painel **Ações de interface do usuário**, expanda o método de teste que contém a ação de interface do usuário na qual o atraso será inserido. Selecione a ação de interface do usuário. Depois, abra o menu de atalho da ação de interface do usuário e escolha **Inserir Atraso Antes**. Um atraso será inserido e realçado antes da ação de interface do usuário selecionada com o seguinte texto: **Aguarde 1 segundo de atraso de usuário entre ações**. Na janela Propriedades, altere o valor para da propriedade **Atraso** para o número desejado de milissegundos.

 Após a inserção do atraso, salve as alterações no arquivo UIMap.Designer escolhendo **Salvar** na barra de ferramentas [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 *O que mais eu deveria saber?*
 **Observações**

- ![Prerequsite](../test/media/prereq.png "Pré-requisito") Se você precisar garantir que um controle específico esteja disponível antes de uma ação da interface do usuário, considere adicionar código personalizado ao método de teste usando o método UITestControl. WaitForControlXXX () apropriado. [!INCLUDE[crdefault](../includes/crdefault-md.md)][Fazer testes de IU codificados aguarda eventos específicos durante a reprodução](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

  **Sobre**

- ![Dica](../test/media/tip.png "Dica") Se o janela Propriedades não for exibido, pressione e mantenha pressionada a tecla ALT enquanto pressiona ENTER ou, alternativamente, pressione F4.

## <a name="external-resources"></a>Recursos externos

### <a name="guidance"></a>Diretrizes
 [Testes de Entrega Contínua com o Visual Studio 2012 – Capítulo 2: Teste de Unidade: Testando o Interior](https://msdn.microsoft.com/library/jj159340.aspx)

### <a name="faq"></a>Perguntas frequentes
 [Perguntas frequentes sobre testes de IU codificados – 1](https://docs.microsoft.com/archive/blogs/mathew_aniyan/content-index-for-coded-ui-test)

 [Perguntas frequentes sobre testes de IU codificados – 2](https://social.msdn.microsoft.com/Forums/en-US/vsautotest/thread/3a74dd2c-cef8-4923-abbf-7a91f489e6c4)

### <a name="forum"></a>Fórum
 [Teste de Automação de interface do usuário do Visual Studio (inclui CodedUI)](https://social.msdn.microsoft.com/Forums/en-US/vsautotest)

## <a name="see-also"></a>Consulte Também
 [Use a automação da interface do usuário para testar seu código](../test/use-ui-automation-to-test-your-code.md) [criando testes de IU codificados](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) [criando um teste de interface do usuário codificado por dados](../test/creating-a-data-driven-coded-ui-test.md) [gerando um teste de interface do usuário codificado de uma ação existente](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) [: criando, editando e mantendo um teste de IU codificado](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
