---
title: Criar regiões de formulário do Outlook
description: Saiba como você pode usar regiões de formulário para personalizar formulários do Microsoft Outlook para facilitar o design, o desenvolvimento e a depuração de regiões de formulário.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- MICROSOFT.OFFICE.TOOLS.OUTLOOK.FORMREGION
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio]
- form regions [Office development in Visual Studio], creating
- Outlook [Office development in Visual Studio], form regions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f3273c02416cac54dfd244ba4f163fb5d726413c
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847956"
---
# <a name="create-outlook-form-regions"></a>Criar regiões de formulário do Outlook
  Você pode usar regiões de formulário para personalizar Microsoft Office formulários do Outlook. O Visual Studio fornece ferramentas avançadas que facilitam o design, o desenvolvimento e a depuração de regiões de formulário.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Este tópico fornece as seguintes informações:

- [Vantagens de usar regiões de formulário](#Enhance)

- [Adicionar uma região de formulário do Outlook ao seu projeto](#Adding)

- [Usar o designer de região de formulário](#UsingFormRegionDesigner)

- [Usar uma região de formulário projetada no Outlook](#UsingFormRegionDesignedOutlook)

- [Adicionar código personalizado a uma região de formulário](#AddingCustomCode)

- [Compilar o projeto](#Building)

- [Depurar uma região de formulário](#Debugging)

- [Implantar uma região de formulário](#Deploying)

## <a name="advantages-of-using-form-regions"></a><a name="Enhance"></a> Vantagens de usar regiões de formulário
 As regiões de formulário oferecem muitas melhorias em relação ao desenvolvimento de formulários do Outlook tradicional:

- Personalize a página padrão de qualquer formulário padrão.

- Adicione até 12 páginas extras a qualquer formulário padrão.

- Substitua ou aprimore qualquer formulário padrão.

- Exiba a interface do usuário personalizada no painel de leitura e nos inspetores.

  Para obter mais informações, consulte [Personalizar páginas de formulário e regiões de formulário](/office/vba/outlook/Concepts/Forms/customizing-form-pages-and-form-regions).

## <a name="add-an-outlook-form-region-to-your-project"></a><a name="Adding"></a> Adicionar uma região de formulário do Outlook ao seu projeto
 Você pode usar o **novo** assistente de área de formulário do Outlook para criar uma nova região de formulário ou importar uma região de formulário que foi desenvolvida no Outlook. Além disso, se você tiver uma região de formulário usada em outro projeto de suplemento do VSTO do Outlook, poderá reutilizar sua região de formulário existente.

### <a name="create-a-new-form-region-by-using-the-wizard"></a><a name="CreatingFormRegion"></a> Criar uma nova região de formulário usando o assistente
 Para criar uma região de formulário, adicione um item de **região de formulário do Outlook** a um projeto de suplemento do VSTO do Outlook. Isso inicia o **novo** assistente de região de formulário do Outlook.

 Use o assistente para indicar se você deseja criar uma nova região de formulário ou importar uma região de formulário que foi desenvolvida no Outlook. Para obter mais informações sobre como criar uma nova região de formulário, consulte [usar o designer de região de formulário](#UsingFormRegionDesigner). Para obter mais informações sobre como usar uma região de formulário criada no Outlook, consulte [importar uma região de formulário projetada no Outlook](#UsingFormRegionDesignedOutlook).

 Use o assistente para especificar o tipo de região de formulário que você deseja criar. A tabela a seguir descreve cada tipo de região de formulário.

|Tipo de região|Descrição|
|-----------------|-----------------|
|Separate|Adiciona a região do formulário como uma nova página em um formulário do Outlook.|
|Adjacente|Anexa a região do formulário à parte inferior da página padrão de um formulário do Outlook.|
|Substituição|Adiciona a região do formulário como uma nova página que substitui a página padrão de um formulário do Outlook.|
|Substituir tudo|Substitui todo o formulário do Outlook pela região do formulário.|

 Você também pode usar o assistente para especificar condições de exibição e selecionar o tipo de formulário a ser estendido. Para obter mais informações, consulte [como: adicionar uma região de formulário a um projeto de suplemento do Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

 As seleções feitas no assistente afetam as opções que estão disponíveis em outras páginas do assistente. Por exemplo, se você selecionar **adjacente** ou **separado** na página **criar uma nova região de formulário do Outlook** , os campos **título** e **Descrição** não estarão disponíveis no **texto descritivo de fornecimento e selecione a página preferências de exibição** . Isso ocorre porque o Outlook não usa esses campos quando exibe uma região de formulário adjacente ou separada.

#### <a name="form-region-files"></a>Arquivos de região de formulário
 Quando você concluir o **novo** assistente de área de formulário do Outlook, o Visual Studio adicionará automaticamente os seguintes arquivos ao seu projeto:

- Um arquivo de código de região de formulário. Esse arquivo tem o nome que você especifica para o item da **região de formulário do Outlook** na caixa de diálogo **Adicionar novo item** . Adicione o código para manipular eventos de região de formulário para este arquivo.

- Um arquivo de código de designer de região de formulário. Esse arquivo contém o código gerado pelo designer de região de formulário e não deve ser editado diretamente.

- Um arquivo de armazenamento de formulário do Outlook (*. OFS*).

    > [!NOTE]
    > Esse arquivo só será adicionado ao projeto se você importar uma região de formulário que foi desenvolvida no Outlook.

#### <a name="form-region-factory-class"></a>Classe de fábrica de região de formulário
 O arquivo de código de região do formulário contém uma classe parcial que implementa a <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory> interface. Essa é a classe de fábrica de região de formulário. A classe de fábrica de região de formulário é responsável pela criação de novas instâncias da região do formulário.

 Você pode encontrar essa classe expandindo a região de **fábrica da região de formulário** .

 O assistente de **nova região de formulário do Outlook** adiciona atributos a essa classe que especificam o nome interno da região de formulário e as classes de mensagem que exibem a região do formulário. Você pode modificar esses atributos manualmente depois que o arquivo tiver sido adicionado ao projeto.

 A maior parte da classe de fábrica da região de formulário é implementada no arquivo de designer de região de formulário. No entanto, o `FormRegionInitializing` manipulador de eventos é exposto no arquivo de código de região do formulário. Você pode usar esse manipulador de eventos para especificar se o Outlook deve exibir a região do formulário. Para obter mais informações, consulte [manipular eventos de região do formulário](#HandlingFormRegionEvents).

### <a name="add-an-existing-form-region-to-your-project"></a><a name="AddingExistingFormRegion"></a> Adicionar uma região de formulário existente ao seu projeto
 Se você tiver uma região de formulário do Outlook que você usou em outro projeto do Outlook, poderá reutilizá-la em seu projeto de suplemento do VSTO do Outlook atual usando a caixa de diálogo **Adicionar item existente** .

 A região de formulário existente deve ter um arquivo de código (*. vb* ou *. cs*); Você não pode adicionar arquivos de armazenamento de formulário do Outlook (*. OFS*) usando a caixa de diálogo **Adicionar item existente** . No entanto, você pode criar uma nova região de formulário importando um arquivo de armazenamento de formulário do Outlook. Para obter mais informações, consulte [como: adicionar uma região de formulário a um projeto de suplemento do Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

## <a name="use-the-form-region-designer"></a><a name="UsingFormRegionDesigner"></a> Usar o designer de região de formulário
 O designer de região de formulário ajuda você a criar o layout e a aparência de uma região de formulário. Você pode arrastar controles gerenciados para a superfície do designer, clicar duas vezes em controles para abrir manipuladores de eventos e definir propriedades na janela **Propriedades** .

> [!NOTE]
> Você pode encontrar propriedades que afetam a maneira como a região de formulário aparece no Outlook abaixo do nó de **manifesto** na janela **Propriedades** .

 O designer de região de formulário estará disponível apenas se você selecionar **criar uma nova região de formulário** na página **selecionar como deseja criar a região de formulário** do assistente de **nova região de formulário do Outlook** .

 Há três maneiras de abrir o designer de região de formulário:

- Em **Gerenciador de soluções**, clique duas vezes no arquivo de código da região do formulário.

- Em **Gerenciador de soluções**, clique com o botão direito do mouse no arquivo de código da região do formulário e clique em **Designer de exibição**.

- Em **Gerenciador de soluções**, selecione o arquivo de código de região do formulário e, no menu **Exibir** , clique em **Designer**.

  O designer de região de formulário dá suporte apenas a controles gerenciados. Você não pode adicionar controles nativos do Outlook.

## <a name="import-a-form-region-designed-in-outlook"></a><a name="UsingFormRegionDesignedOutlook"></a> Importar uma região de formulário projetada no Outlook
 Ao projetar no Outlook, você pode adicionar controles nativos do Outlook à região do formulário. Os controles nativos do Outlook permitem que você se vincule aos dados do Outlook em tempo de design. No entanto, você não pode usar o designer de região de formulário para adicionar controles gerenciados ou alterar o design da região do formulário.

 Você pode importar regiões de formulário para um projeto de suplemento do VSTO do Outlook usando o assistente de **nova região de formulário do Outlook** . Na página **Selecione como você deseja criar a região do formulário** , selecione **importar um arquivo de armazenamento de formulário do Outlook (. ofs)**. Em seguida, você pode navegar até o local de um arquivo de armazenamento de formulário do Outlook (*. OFS*). (O Outlook salva as regiões de formulário como arquivos *. OFS* .)

 O assistente de **nova região de formulário do Outlook** copia o arquivo *. OFS* para o diretório do projeto e adiciona referências de controle ao arquivo de designer de região do formulário. Em seguida, você pode manipular eventos de controle no arquivo de código de região do formulário.

 Para manipular eventos em um projeto Visual Basic, selecione um evento na lista nome do método na parte superior do editor de código.

 Para manipular eventos em um projeto C#, assine eventos de controle no <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> método. Para obter mais informações, consulte [como assinar e cancelar a assinatura de eventos &#40;guia de programação C&#35;&#41;](/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events).

 Você pode alterar as propriedades da região do formulário no `InitializeManifest` método da classe de fábrica da região de formulário.

> [!NOTE]
> Para importar uma região de formulário, você deve estar trabalhando em um projeto que tenha como destino a mesma versão do Outlook que você instalou no computador de desenvolvimento. Por exemplo, se você tiver o Outlook 2010 instalado, a importação de uma região de formulário só funcionará em um projeto usando o modelo de projeto de **suplemento do Outlook 2010** .

### <a name="update-an-imported-form-regions-design"></a>Atualizar o design de uma região de formulário importada
 Você pode adicionar, remover ou alterar controles na região do formulário. Antes de fazer isso, faça backup de qualquer código que você adicionou ao arquivo de código da região do formulário. Em seguida, abra o arquivo *. OFS* no Outlook, modifique a região do formulário e salve as alterações. Use o **novo** assistente de área de formulário do Outlook para importar o arquivo *. OFS* modificado. Em seguida, você pode colar seu código no novo arquivo de código de região do formulário.

## <a name="add-custom-code-to-a-form-region"></a><a name="AddingCustomCode"></a> Adicionar código personalizado a uma região de formulário
 O <xref:Microsoft.Office.Tools.Outlook> namespace fornece acesso a classes que representam a região do formulário, o item do Outlook que exibe a região do formulário e outros itens úteis. O item da **região de formulário do Outlook** adiciona automaticamente uma referência a esse assembly no projeto e insere a instrução **using** ou **Imports** apropriada na parte superior do arquivo de código da região do formulário.

 Você pode usar classes, métodos e propriedades no `Microsoft.Office.Interop.Outlook` namespace para realizar a maioria das tarefas de programação do Outlook. Para obter mais informações sobre o modelo de objeto do Outlook, consulte [visão geral do modelo de objeto do Outlook](../vsto/outlook-object-model-overview.md). Para obter exemplos de tarefas típicas que fazem uso do modelo de objeto do Outlook, consulte [soluções do Outlook](../vsto/outlook-solutions.md).

### <a name="handle-form-region-events"></a><a name="HandlingFormRegionEvents"></a> Manipular eventos de região do formulário
 O item da **região de formulário do Outlook** adiciona automaticamente os três manipuladores de eventos a seguir ao arquivo de código da região do formulário.

|Evento|Descrição|
|-----------|-----------------|
|FormRegionInitializing|Ocorre antes que a região de formulário seja inicializada. Você pode verificar condições neste manipulador de eventos para determinar se o Outlook deve exibir a região do formulário. Para obter mais informações, consulte [como: impedir que o Outlook exiba uma região de formulário](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).|
|FormRegionShowing|Ocorre após uma instância da região do formulário ser criada, mas antes da região do formulário ser exibida.|
|FormRegionClosed|Ocorre antes da região do formulário ser fechada.|

## <a name="build-the-project"></a><a name="Building"></a> Compilar o projeto
 Quando você cria um projeto de suplemento do VSTO do Outlook que contém uma região de formulário, o Visual Studio adiciona as seguintes informações ao registro:

- Uma chave para cada classe de mensagem associada a uma ou mais regiões de formulário.

- Uma entrada para cada região de formulário e um valor associado que representa o nome do suplemento do VSTO do Outlook.

  O Outlook usa essas informações para carregar as regiões do formulário.

## <a name="debug-a-form-region"></a><a name="Debugging"></a> Depurar uma região de formulário
 Você pode depurar um suplemento do VSTO do Outlook que contenha uma região de formulário da mesma forma que depuraria outros [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projetos. Quando você inicia o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] depurador, o Visual Studio inicia automaticamente o Outlook.

 Para exibir a região do formulário, você deve abrir o item apropriado do Outlook. Por exemplo, se uma região de formulário adjacente for anexada à parte inferior de um item de email, abra um item de email.

## <a name="deploy-a-form-region"></a><a name="Deploying"></a> Implantar uma região de formulário
 As regiões de formulário são implantadas automaticamente com o suplemento do VSTO do Outlook associado. Portanto, você não precisa executar tarefas especiais para implantar uma região de formulário. Para obter mais informações sobre como implantar suplementos do VSTO, consulte [implantar uma solução do Office](../vsto/deploying-an-office-solution.md).

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Diretrizes para criar regiões de formulário do Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)|Fornece informações que podem ajudá-lo a otimizar suas regiões de formulário e evitar possíveis problemas.|
|[Como: adicionar uma região de formulário a um projeto de suplemento do Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|Mostra como criar uma região de formulário para estender um formulário Microsoft Office do Outlook padrão ou personalizado usando o novo assistente de **área de formulário do Outlook** .|
|[Associar uma região de formulário a uma classe de mensagem do Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|Explica como especificar quais Microsoft Office itens do Outlook exibem uma região de formulário associando a região de formulário à classe de mensagem de cada item.|
|[Walkthrough: criar uma região de formulário do Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)|Mostra como criar uma região de formulário personalizada que aparece como uma nova página na janela Inspetor de um item de contato.|
|[Walkthrough: importar uma região de formulário projetada no Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Mostra como criar uma região de formulário no Microsoft Office Outlook e, em seguida, importar a região de formulário para um projeto de suplemento do VSTO do Outlook usando o assistente de **nova região de formulário do Outlook** .|
|[Acessar uma região de formulário em tempo de execução](../vsto/accessing-a-form-region-at-run-time.md)|Descreve como escrever código para mostrar, ocultar ou modificar controles em uma região de formulário e permitir que os usuários executem o código de outras áreas em seu projeto usando a `Globals` classe.|
|[Como: impedir que o Outlook exiba uma região de formulário](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Mostra como impedir Microsoft Office Outlook exiba uma região de formulário para um item específico.|
|Mostra como acessar o item do Outlook no qual uma região de formulário é exibida.|
|[Ações personalizadas nas regiões de formulário do Outlook](../vsto/custom-actions-in-outlook-form-regions.md)|Descreve como permitir que os usuários respondam a um item do Outlook.|
