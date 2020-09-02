---
title: Designer da faixa de opções
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, about Ribbon Designer
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- customizing the Ribbon, about Ribbon Designer
- Ribbon [Office development in Visual Studio], visual designer
- customizing the Ribbon
- custom Ribbon
- designers [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon [Office development in Visual Studio], common tasks
- Ribbon Designer [Office development in Visual Studio]
- read-only properties
- Ribbon [Office development in Visual Studio], shortcut keys
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e1c2941b0c088a832540fd3380c993fe2c380b44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985621"
---
# <a name="ribbon-designer"></a>Designer da faixa de opções
  O designer de faixa de Ribbon é uma tela de Design Visual. Use o designer de faixa de faixas para adicionar guias, grupos e controles personalizados à faixa de faixas de um aplicativo Microsoft Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Para abrir o designer de faixa de faixas, adicione um item **da faixa de Ribbon (designer visual)** ao seu projeto. Em seguida, você pode usar as ferramentas de design para as seguintes tarefas:

- [Criar o layout da faixa de opção](#DesigningRibbonLayout)

- [Manipular eventos e definir propriedades de controle](#HandleEventsSetProperties)

- [Adicionar controles à exibição de Backstage](#CustomizingMicrosoftOfficeButton)

> [!NOTE]
> Há algumas tarefas que você não pode realizar usando o designer de faixa de faixas. Para obter mais informações sobre essas tarefas e como você pode realizá-las, consulte [visão geral do Ribbon](../vsto/ribbon-overview.md).

## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>Adicionar um item da faixa de visualização (designer visual) a um projeto
 Para usar o designer de faixa de faixas, adicione um novo item **da faixa de Ribbon (designer visual)** ao seu projeto. Para obter mais informações, consulte [como: começar a personalizar a faixa de](../vsto/how-to-get-started-customizing-the-ribbon.md)visualização.

 Quando você adiciona um novo item **da faixa de opções (Visual Designer)** , o Visual Studio adiciona automaticamente os seguintes arquivos ao seu projeto:

- Um arquivo de código da faixa de uma. Esse arquivo tem o nome que você especifica para o item **da faixa de visualização (Visual Designer)** na caixa de diálogo **Adicionar novo item** . Adicione o código para lidar com os eventos da faixa de para este arquivo.

- Um arquivo de código do designer de faixa de faixas. Esse arquivo contém o código gerado pelo designer de faixa de faixas e não deve ser editado diretamente.

- Um arquivo de recurso. Esse arquivo contém os valores de propriedade de cada controle na faixa de faixas.

  Se você já tiver um item da **faixa de Ribbon (designer visual)** de outro projeto, poderá reutilizá-lo em seu projeto atual usando a caixa de diálogo **Adicionar item existente** .

## <a name="design-a-ribbon"></a><a name="DesigningRibbonLayout"></a> Criar uma faixa de uma
 Há três maneiras de abrir o designer de faixa de opções:

- Em **Gerenciador de soluções**, clique duas vezes no arquivo de código da faixa de bits.

- Em **Gerenciador de soluções**, clique com o botão direito do mouse no arquivo de código da faixa de bits e clique em **Designer de exibição**.

- Em **Gerenciador de soluções**, selecione o arquivo de código da faixa de opções e, em seguida, clique em **Designer** no menu **Exibir** .

  O designer de faixa de faixas contém uma guia e um grupo padrão. Você pode remover a guia padrão e o grupo do designer de faixa de faixas. Para remover o grupo padrão, clique com o botão direito do mouse em **grupo1**e clique em **excluir**. Para remover a guia padrão, clique com o botão direito do mouse em uma área vazia da superfície de design e clique **na guia Remover faixa**de bits.

  Você também pode adicionar guias, grupos e controles personalizados ao designer de faixa de faixas. Você pode encontrar esses controles na **caixa de ferramentas**, no grupo controles de faixa de guia do **Office** . Há três maneiras de adicionar controles do grupo de **controles da faixa** de opções do Office ao designer de faixa de opções:

- Arraste um controle para uma área apropriada no designer de faixa de faixas.

- Clique em um controle e, em seguida, clique em uma área apropriada no designer de faixa de faixas.

- Selecione uma área apropriada no designer e clique duas vezes em um controle na **caixa de ferramentas**.

### <a name="ribbon-design-workflow"></a>Fluxo de trabalho de design da faixa
 Siga estas etapas básicas para criar o layout da faixa de opção:

1. [Adicione uma guia personalizada à faixa de faixas](#AddTabToRibbon).

2. [Adicione grupos à guia](#AddGroupsToTab).

3. [Adicione controles aos grupos](#AddControlsToGroups).

   Os controles só podem ser descartados em grupos; Você não pode arrastar um controle diretamente para uma guia ou para a faixa de faixas. Os grupos podem ser descartados somente em guias; Não é possível arrastar um grupo diretamente para uma faixa de faixas.

   Organize os controles arrastando-os para as posições corretas. Você pode definir as propriedades de um controle usando a janela **Propriedades** .

   Não é possível arrastar controles de uma guia para outra na faixa de faixas. Se você quiser mover um controle para outra guia, deverá usar o comando **recortar** para remover o controle de uma guia e, em seguida, colar o controle em outra guia. Se você recortar o controle e colá-lo, o manipulador de eventos deixará de funcionar. Você pode reconectar o manipulador de eventos na janela **Propriedades** . Para obter mais informações, consulte [janela Propriedades](../ide/reference/properties-window.md).

### <a name="add-custom-tabs-to-the-ribbon"></a><a name="AddTabToRibbon"></a> Adicionar guias personalizadas à faixa de faixas
 Há três maneiras de adicionar uma guia personalizada à faixa de opções:

- Adicione uma guia da **caixa de ferramentas**.

- Clique com o botão direito do mouse no designer de faixa de faixas e clique **na guia adicionar faixa**de bits.

- Abra o **Editor de coleção de guias**e clique em **Adicionar**.

   Para abrir o **Editor de coleção de guias**, na janela **Propriedades** , selecione a propriedade **guias** e clique no botão de reticências ![ASP.net elipse do designer móvel](../sharepoint/media/mwellipsis.gif "Elipse do designer móvel ASP.NET").

  Depois de adicionar uma guia, você pode adicionar grupos para conter controles.

#### <a name="remove-custom-tabs-from-the-ribbon"></a>Remover guias personalizadas da faixa de faixas
 Há três maneiras de remover uma guia personalizada da faixa de opções:

- Clique com o botão direito do mouse no designer e clique **na guia Remover faixa**de bits.

- No painel **comandos** da janela **Propriedades** , clique na **guia Remover faixa de faixas**.

- Abra o **Editor de coleção de guias**, selecione a guia e, em seguida, clique em **remover**.

#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>Alterar a posição de uma guia na faixa de posições
 Você pode alterar a ordem das guias personalizadas em uma faixa de faixas. Você também pode posicionar guias personalizadas antes ou depois de uma guia interna na faixa de bits. Para obter mais informações, consulte [como alterar a posição de uma guia na faixa de faixas](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

#### <a name="customize-built-in-tabs-on-the-ribbon"></a>Personalizar guias internas na faixa de faixas
 Uma guia interna é uma guia que já está na faixa de bits de um aplicativo Microsoft Office. Por exemplo, a guia **dados** é uma guia interna no Excel.

 Você pode adicionar grupos e controles a uma guia interna. Por padrão, um grupo personalizado é exibido como o último grupo em uma guia interna, embora você possa movê-lo antes ou depois de qualquer grupo interno na guia.

 Não é possível remover grupos internos.

 Para obter detalhes sobre como personalizar uma guia interna, consulte [como: personalizar uma guia interna](../vsto/how-to-customize-a-built-in-tab.md).

### <a name="add-groups-to-a-tab"></a><a name="AddGroupsToTab"></a> Adicionar grupos a uma guia
 Os grupos organizam logicamente os controles na faixa de faixas. Adicionar grupos a guias. Adicione todos os outros controles ao grupo.

### <a name="add-controls-to-groups"></a><a name="AddControlsToGroups"></a> Adicionar controles a grupos
 Adicione um ou mais controles a um grupo. A tabela a seguir descreve cada controle.

|Control|Descrição|
|-------------|-----------------|
|**Box**|Um contêiner que organiza controles em um grupo. Você pode adicionar qualquer controle a uma caixa, exceto um separador, um grupo ou uma guia. Uma caixa pode ser horizontal ou vertical.|
|**Botão**|Um botão que inicia uma ação. Você pode adicionar um botão a um grupo, a um grupo de botões, a uma lista suspensa, a uma galeria, a um menu ou a um botão de divisão.|
|**ButtonGroup**|Um grupo que contém um ou mais botões, botões de alternância, menus, botões de divisão e galerias. Você pode adicionar um grupo de botões a um grupo ou a um menu.|
|**CheckBox**|Uma caixa selecionada ou desmarcada para ativar ou desativar uma opção.|
|**ComboBox**|Uma caixa de edição com uma caixa de listagem anexada. Os usuários podem digitar ou selecionar sua escolha. A caixa exibe a seleção atual. Use a <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> propriedade para adicionar e remover itens em tempo de execução antes ou depois que a faixa de faixas é carregada no aplicativo do Office.|
|**DropDown**|Uma lista de itens que o usuário pode selecionar. O usuário não pode digitar um novo item em uma lista suspensa.<br /><br /> Use a <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> propriedade para adicionar itens à lista. Você pode adicionar e remover itens em tempo de execução.<br /><br /> Use a <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> propriedade para adicionar botões à lista. No entanto, você não pode adicionar e remover botões em tempo de execução depois que a faixa de faixas é carregada no aplicativo do Office.|
|**Edição**|Uma caixa na qual o usuário pode digitar texto.|
|**Clip**|Um menu que apresenta uma matriz ou grade de opções visuais das quais os usuários podem selecionar. Você pode controlar o layout das seleções no menu. Use as <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> Propriedades e <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> para especificar o número de linhas e colunas que exibirão os itens e os botões da galeria.|
|**Rotular**|Texto que você pode usar para identificar controles na faixa de faixas.|
|**Menu**|Uma lista suspensa que pode conter qualquer um dos seguintes controles:<br /><br /> -Botão<br />-Caixa de seleção<br />-Galeria<br />-Menu<br />-Botão de divisão<br />-Botão de alternância<br />-Separador<br /><br /> Para adicionar um controle a um menu no designer de faixa de faixas, clique na seta para baixo no menu para expor a superfície de design do menu. Em seguida, você pode arrastar os controles da faixa de **ferramentas da Toolbox** para o menu. Para organizar controles, arraste-os para as posições desejadas.<br /><br /> Para adicionar controles ao <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> depois que a faixa de faixas é carregada no aplicativo do Office, você deve definir a <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> propriedade como **true** antes que a faixa de faixas seja carregada. Para obter informações sobre como fazer isso, consulte [visão geral do modelo de objeto da faixa](../vsto/ribbon-object-model-overview.md)de informações.|
|**Caractere**|Uma barra fina usada para separar itens em uma lista. Quando adicionado a um grupo, a barra é vertical. Quando adicionado a um menu, a barra é horizontal.|
|**SplitButton**|Um botão com um menu anexado. Um botão de divisão pode conter qualquer um dos seguintes controles:<br /><br /> -Botão<br />-Caixa de seleção<br />-Galeria<br />-Menu<br />-Botão de divisão<br />-Botão de alternância<br />-Separador<br /><br /> Como o menu, o botão de divisão tem sua própria superfície de design. No entanto, ao contrário de um menu, você só pode atualizar os itens em um botão de divisão antes que a faixa de faixas seja carregada no aplicativo do Office. Para obter informações sobre como atualizar os itens em um botão de divisão, consulte [visão geral do modelo de objeto da faixa](../vsto/ribbon-object-model-overview.md)de medida.|
|**ToggleButton**|Um botão que aparece pressionado ou não pressionado.|

## <a name="handle-events-and-setting-properties"></a><a name="HandleEventsSetProperties"></a> Manipular eventos e propriedades de configuração
 O designer de faixa de Ribbon permite que você defina as propriedades de controle em tempo de design usando a janela **Propriedades** . Além disso, a faixa de faixas expõe um modelo de objeto fortemente tipado que você pode usar para obter e definir as propriedades dos controles da faixa de tipos em tempo de execução.

 Você pode clicar duas vezes em qualquer controle no designer para abrir um manipulador de eventos para o evento padrão do controle. Você pode criar manipuladores de eventos para todos os outros eventos de controle usando a janela **Propriedades** .

 Os eventos e as propriedades da faixa de lista estão localizados no <xref:Microsoft.Office.Tools.Ribbon> namespace. O item **da faixa de visualização (Visual Designer)** adiciona automaticamente uma referência a esse assembly no projeto e insere a instrução **using** ou **Imports** apropriada na parte superior do arquivo de código da faixa de lista.

 Para obter informações sobre como lidar com eventos da faixa de opção e definir as propriedades dos controles da faixa de opção em tempo de execução, consulte [visão geral do modelo de objeto](../vsto/ribbon-object-model-overview.md)

## <a name="customize-backstage-view"></a><a name="CustomizingMicrosoftOfficeButton"></a> Personalizar o modo de exibição do Backstage
 Você pode usar o designer de faixa de Ribbon para adicionar controles ao menu que é aberto quando você clica na guia **arquivo** . Esse menu é chamado de modo de exibição de Backstage.

 Você não pode posicionar controles antes ou depois de controles internos usando o designer de faixa de faixas. Um controle interno é um controle que já aparece no modo de exibição de Backstage. Se você quiser posicionar controles antes ou depois de controles internos, deverá usar o XML da faixa de bits. Para obter mais informações sobre a **faixa de faixas (XML)**, consulte [XML da faixa](../vsto/ribbon-xml.md)de para. Para obter mais informações sobre como personalizar o modo de exibição de Backstage, consulte [introdução ao modo de exibição de Backstage do office 2010 para desenvolvedores](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) e [Personalizar o modo de exibição do Backstage do Office 2010 para desenvolvedores](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]

 Para obter informações sobre como adicionar controles ao modo de exibição de Backstage, consulte [como: adicionar controles ao modo de exibição de Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).

## <a name="accessibility-in-the-ribbon-designer"></a><a name="Accessibility"></a> Acessibilidade no designer de faixa de faixas
 Você pode usar atalhos de teclado para mover controles no designer de faixa de faixas. Alguns atalhos de teclado se aplicam a todos os controles e alguns se aplicam somente a controles que têm menus.

 Os atalhos de teclado que se aplicam a todos os controles são mostrados na tabela a seguir.

|Ação|Atalho de teclado|
|------------|-----------------------|
|Mover um controle antes do controle anterior na lista.|**Ctrl** + **Para cima**<br /><br /> **Ctrl** + **À esquerda**|
|Mover um controle após o próximo controle na lista.|**Ctrl** + **Para baixo**<br /><br /> **Ctrl** + **À direita**|
|Mova a seleção de um controle para outro no mesmo grupo. Para um painel suspenso, mova entre o controle pai e os controles no painel suspenso.|**Operante**<br /><br /> **Para baixo**|
|Iterar progressivamente todos os controles.|**Guia**|
|Iterar para o inverso através de todos os controles.|**Shift** + **Guia**|
|Excluir o controle ou conjunto de controles selecionado.|**Delete (excluir)**|
|Copie os controles selecionados.|**Ctrl** + **C**|
|Recortar os controles selecionados.|**Ctrl** + **X**|
|Colar controles da área de transferência.|**Ctrl** + **V**|
|Selecione a **caixa de ferramentas**.|**Ctrl** + **ALT** + **X**|
|Selecione o componente pai.|**Esc**|

 Os atalhos de teclado que se aplicam somente ao menu Microsoft Office, <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> e <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> são mostrados na tabela a seguir.

|Ação|Atalho de teclado|
|------------|-----------------------|
|Selecione o controle pai se o painel suspenso estiver aberto e houver um controle selecionado no painel suspenso.|**Mantida**|
|Feche o painel suspenso se o painel suspenso estiver aberto e o controle pai estiver selecionado.|**Mantida**|
|Abra o painel suspenso.|**Certo**|
|Selecione o primeiro controle no painel suspenso se o painel suspenso estiver aberto.|**Certo**|
|Feche um painel suspenso.|**Esc**|

## <a name="see-also"></a>Confira também

- [Visão geral da faixa de faixas](../vsto/ribbon-overview.md)
- [XML da faixa de opções](../vsto/ribbon-xml.md)
- [Walkthrough: criar uma guia personalizada usando o designer de faixa de faixas](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Como exportar uma faixa de faixas do designer de faixa de das faixas para XML da faixa de modo](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Como: começar a personalizar a faixa de faixas](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Acessar a faixa de faixas em tempo de execução](../vsto/accessing-the-ribbon-at-run-time.md)
