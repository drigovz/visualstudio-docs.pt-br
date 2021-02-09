---
title: Visão geral do modelo de objeto do Outlook
description: Saiba como você pode interagir com os objetos que são fornecidos pelo modelo de objeto do Outlook para desenvolver suplementos do VSTO para o Microsoft Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.OutlookAddin
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], object model overview
- object models [Office development in Visual Studio], Office
- objects [Office development in Visual Studio], Office object models
- object models [Office development in Visual Studio], Outlook
- Office object models
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 316ead76be1f84fccc6f675b204587008e8a194a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885294"
---
# <a name="outlook-object-model-overview"></a>Visão geral do modelo de objeto do Outlook
  Para desenvolver suplementos do VSTO para Microsoft Office Outlook, você pode interagir com os objetos que são fornecidos pelo modelo de objeto do Outlook. O modelo de objeto do Outlook fornece classes e interfaces que representam itens na interface do usuário. Por exemplo, o <xref:Microsoft.Office.Interop.Outlook.Application> objeto representa o aplicativo inteiro, o <xref:Microsoft.Office.Interop.Outlook.Folder> objeto representa uma pasta que contém mensagens de email ou outros itens, e o <xref:Microsoft.Office.Interop.Outlook.MailItem> objeto representa uma mensagem de email.

 Este tópico fornece uma breve visão geral de alguns dos objetos principais no modelo de objeto do Outlook. Para obter recursos em que você pode saber mais sobre o modelo de objeto completo do Outlook, consulte [usar a documentação do modelo de objeto do Outlook](#refdoc).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-objects-in-an-outlook-project"></a>Acessar objetos em um projeto do Outlook
 O Outlook fornece muitos objetos com os quais você pode interagir. Para usar o modelo de objeto com eficiência, você deve estar familiarizado com os seguintes objetos de nível superior:

- <xref:Microsoft.Office.Interop.Outlook.Application>

- <xref:Microsoft.Office.Interop.Outlook.Explorer>

- <xref:Microsoft.Office.Interop.Outlook.Inspector>

- <xref:Microsoft.Office.Interop.Outlook.Folder>

- <xref:Microsoft.Office.Interop.Outlook.MailItem>

- <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>

- <xref:Microsoft.Office.Interop.Outlook.TaskItem>

- <xref:Microsoft.Office.Interop.Outlook.ContactItem>

### <a name="application-object"></a>Objeto de aplicativo
 O <xref:Microsoft.Office.Interop.Outlook.Application> objeto representa o aplicativo do Outlook e é o objeto de nível mais alto no modelo de objeto do Outlook. Alguns dos membros mais importantes desse objeto incluem:

- O método [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) que você pode usar para criar um novo item, como uma mensagem de email, uma tarefa ou um compromisso.

- A <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> propriedade, que pode ser usada para acessar as janelas que exibem o conteúdo de uma pasta na interface do usuário do Outlook.

- A <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> propriedade, que você pode usar para acessar as janelas que exibem o conteúdo de um único item, como uma mensagem de email ou solicitação de reunião.

  Para obter uma instância do <xref:Microsoft.Office.Interop.Outlook.Application> objeto, use o campo aplicativo da `ThisAddIn` classe em seu projeto. Para obter mais informações, consulte [programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md).

> [!NOTE]
> Para ajudar a evitar avisos de segurança ao usar propriedades e métodos que são bloqueados pelo Object Model Guard do Outlook, obtenha os objetos do Outlook do campo aplicativo da `ThisAddIn` classe. Para obter mais informações, consulte [considerações de segurança específicas para soluções do Office](../vsto/specific-security-considerations-for-office-solutions.md).

### <a name="explorer-object"></a>Objeto do Gerenciador
 O <xref:Microsoft.Office.Interop.Outlook.Explorer> objeto representa uma janela que exibe o conteúdo de uma pasta que contém itens como mensagens de email, tarefas ou compromissos. O <xref:Microsoft.Office.Interop.Outlook.Explorer> objeto inclui métodos e propriedades que você pode usar para modificar a janela e eventos que são gerados quando a janela é alterada.

 Para obter um <xref:Microsoft.Office.Interop.Outlook.Explorer> objeto, siga um destes procedimentos:

- Use a <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> Propriedade do <xref:Microsoft.Office.Interop.Outlook.Application> objeto para acessar todos os <xref:Microsoft.Office.Interop.Outlook.Explorer> objetos no Outlook.

- Use o <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> método do <xref:Microsoft.Office.Interop.Outlook.Application> objeto para obter o <xref:Microsoft.Office.Interop.Outlook.Explorer> foco no momento.

- Use o `GetExplorer` método do <xref:Microsoft.Office.Interop.Outlook.Folder> objeto para obter o <xref:Microsoft.Office.Interop.Outlook.Explorer> para a pasta atual.

### <a name="inspector-object"></a>Objeto inspector
 O <xref:Microsoft.Office.Interop.Outlook.Inspector> objeto representa uma janela que exibe um único item, como uma mensagem de email, uma tarefa ou um compromisso. O <xref:Microsoft.Office.Interop.Outlook.Inspector> objeto inclui métodos e propriedades que você pode usar para modificar a janela e eventos que são gerados quando a janela é alterada.

 Para obter um <xref:Microsoft.Office.Interop.Outlook.Inspector> objeto, siga um destes procedimentos:

- Use a <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> Propriedade do <xref:Microsoft.Office.Interop.Outlook.Application> objeto para acessar todos os <xref:Microsoft.Office.Interop.Outlook.Inspector> objetos no Outlook.

- Use o <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> método do <xref:Microsoft.Office.Interop.Outlook.Application> objeto para obter o <xref:Microsoft.Office.Interop.Outlook.Inspector> foco no momento.

- Use o `GetInspector` método de um item específico, como <xref:Microsoft.Office.Interop.Outlook.MailItem> ou <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> , para recuperar o Inspetor associado a ele.

### <a name="folder-object"></a>Objeto de pasta
 O <xref:Microsoft.Office.Interop.Outlook.Folder> objeto representa uma pasta que contém mensagens de email, contatos, tarefas e outros itens. O Outlook fornece 16 <xref:Microsoft.Office.Interop.Outlook.Folder> objetos padrão.

 Os <xref:Microsoft.Office.Interop.Outlook.Folder> objetos padrão são definidos pelos <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders> valores de enumeração. Por exemplo,

 Microsoft. Office. Interop. Outlook. OlDefaultFolders. olFolderInbox corresponde à pasta **inbox** no Outlook.

 Para obter um exemplo que mostra como acessar um padrão <xref:Microsoft.Office.Interop.Outlook.Folder> e criar um novo <xref:Microsoft.Office.Interop.Outlook.Folder> , consulte [como: criar programaticamente itens de pasta personalizados](../vsto/how-to-programmatically-create-custom-folder-items.md).

### <a name="mailitem-object"></a>Objeto MailItem
 O <xref:Microsoft.Office.Interop.Outlook.MailItem> objeto representa uma mensagem de email. <xref:Microsoft.Office.Interop.Outlook.MailItem> Os objetos geralmente estão em pastas, como **inbox**, **Items enviados** e caixa de **saída**. <xref:Microsoft.Office.Interop.Outlook.MailItem> expõe propriedades e métodos que podem ser usados para criar e enviar mensagens de email.

 Para obter um exemplo que mostra como criar uma mensagem de email, consulte [como: criar programaticamente um item de email](../vsto/how-to-programmatically-create-an-e-mail-item.md).

### <a name="appointmentitem-object"></a>Objeto AppointmentItem
 O <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> objeto representa uma reunião, um compromisso único ou um compromisso ou reunião recorrente na pasta **calendário** . O <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> objeto inclui métodos que executam ações, como responder ou encaminhar solicitações de reunião, e propriedades que especificam detalhes da reunião, como o local e a hora.

 Para obter um exemplo que mostra como criar um compromisso, consulte [como: criar programaticamente uma solicitação de reunião](../vsto/how-to-programmatically-create-a-meeting-request.md).

### <a name="taskitem-object"></a>Objeto TaskItem
 O <xref:Microsoft.Office.Interop.Outlook.TaskItem> objeto representa uma tarefa a ser executada em um período de tempo especificado. <xref:Microsoft.Office.Interop.Outlook.TaskItem> os objetos estão localizados na pasta **tarefas** .

 Para criar uma tarefa, use o método [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) do <xref:Microsoft.Office.Interop.Outlook.Application> objeto e passe o valor <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> para o parâmetro.

### <a name="contactitem-object"></a>Objeto ContactItem
 O <xref:Microsoft.Office.Interop.Outlook.ContactItem> objeto representa um contato na pasta **contatos** . <xref:Microsoft.Office.Interop.Outlook.ContactItem> os objetos contêm uma variedade de informações de contato para as pessoas que representam, como endereços, endereços de email e números de telefone.

 Para obter um exemplo que mostra como criar um novo contato, consulte [como: adicionar programaticamente uma entrada aos contatos do Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Para obter um exemplo que mostra como procurar um contato existente, consulte [como: pesquisar programaticamente por um contato específico](../vsto/how-to-programmatically-search-for-a-specific-contact.md).

## <a name="use-the-outlook-object-model-documentation"></a><a name="refdoc"></a> Usar a documentação do modelo de objeto do Outlook
 Para obter informações completas sobre o modelo de objeto do Outlook, consulte a referência do assembly de interoperabilidade primária do Outlook (PIA) e a referência do modelo de objeto do VBA.

### <a name="primary-interop-assembly-reference"></a>Referência de assembly de interoperabilidade primária
 A referência do PIA do Outlook documenta os tipos nos assemblies de interoperabilidade primários para o Outlook 2010. Para obter mais informações, consulte [referência de assembly de interoperabilidade primária do Outlook 2010](/previous-versions/office/developer/office-2010/bb652780(v=office.14)).

 Além de fornecer informações para todos os tipos nos PIAs, esta documentação também fornece informações adicionais sobre a estrutura dos PIAs e exemplos de código para tarefas comuns de automação do Outlook.

### <a name="vba-object-model-reference"></a>Referência de modelo de objeto VBA
 A referência do modelo de objeto do VBA documenta o modelo de objeto do Outlook conforme ele é exposto ao código Visual Basic for Applications (VBA). Para obter mais informações, consulte [referência de modelo de objeto do Outlook 2010](/office/vba/api/overview/Outlook/object-model).

 Todos os objetos e membros na referência do modelo de objeto do VBA correspondem a tipos e membros no PIA do Outlook. Por exemplo, o objeto inspector na referência de modelo de objeto do VBA corresponde ao <xref:Microsoft.Office.Interop.Outlook.Inspector> objeto no pia do Outlook. Embora a referência de modelo de objeto do VBA Forneça exemplos de código para a maioria das propriedades, métodos e eventos, você deve converter o código VBA nesta referência para Visual Basic ou Visual C# se quiser usá-los em um projeto do VSTO do Outlook Add-In que você cria usando o Visual Studio.

### <a name="related-topics"></a>Tópicos relacionados

|Title|Descrição|
|-----------|-----------------|
|[Trabalhar com itens de contato](../vsto/working-with-contact-items.md)|Fornece tópicos que mostram como executar tarefas com contatos.|
|[Trabalhar com itens de email](../vsto/working-with-mail-items.md)|Fornece tópicos que mostram como executar tarefas com itens de email.|
|[Trabalhar com pastas](../vsto/working-with-folders.md)|Fornece tópicos que mostram como executar tarefas com pastas.|
|[Trabalhar com itens de calendário](../vsto/working-with-calendar-items.md)|Fornece tópicos que mostram como executar tarefas com itens de calendário.|
|[Como: determinar programaticamente o item atual do Outlook](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Mostra como exibir o nome da pasta atual e algumas informações sobre o item selecionado.|
