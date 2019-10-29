---
title: Visão geral do modelo de objeto do Outlook
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6545815a0a24a3ba8579298151194fdd81edee77
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985688"
---
# <a name="outlook-object-model-overview"></a>Visão geral do modelo de objeto do Outlook
  Para desenvolver suplementos do VSTO para Microsoft Office Outlook, você pode interagir com os objetos que são fornecidos pelo modelo de objeto do Outlook. O modelo de objeto do Outlook fornece classes e interfaces que representam itens na interface do usuário. Por exemplo, o objeto <xref:Microsoft.Office.Interop.Outlook.Application> representa o aplicativo inteiro, o objeto <xref:Microsoft.Office.Interop.Outlook.Folder> representa uma pasta que contém mensagens de email ou outros itens, e o objeto <xref:Microsoft.Office.Interop.Outlook.MailItem> representa uma mensagem de email.

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
 O objeto <xref:Microsoft.Office.Interop.Outlook.Application> representa o aplicativo do Outlook e é o objeto de nível mais alto no modelo de objeto do Outlook. Alguns dos membros mais importantes desse objeto incluem:

- O método [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) que você pode usar para criar um novo item, como uma mensagem de email, uma tarefa ou um compromisso.

- A propriedade <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A>, que pode ser usada para acessar as janelas que exibem o conteúdo de uma pasta na interface do usuário do Outlook.

- A propriedade <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A>, que você pode usar para acessar as janelas que exibem o conteúdo de um único item, como uma mensagem de email ou solicitação de reunião.

  Para obter uma instância do objeto <xref:Microsoft.Office.Interop.Outlook.Application>, use o campo aplicativo da classe `ThisAddIn` em seu projeto. Para obter mais informações, consulte [programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md).

> [!NOTE]
> Para ajudar a evitar avisos de segurança ao usar propriedades e métodos que são bloqueados pelo Object Model Guard do Outlook, obtenha os objetos do Outlook do campo aplicativo da classe `ThisAddIn`. Para obter mais informações, consulte [considerações de segurança específicas para soluções do Office](../vsto/specific-security-considerations-for-office-solutions.md).

### <a name="explorer-object"></a>Objeto do Gerenciador
 O objeto <xref:Microsoft.Office.Interop.Outlook.Explorer> representa uma janela que exibe o conteúdo de uma pasta que contém itens como mensagens de email, tarefas ou compromissos. O objeto <xref:Microsoft.Office.Interop.Outlook.Explorer> inclui métodos e propriedades que você pode usar para modificar a janela e eventos que são gerados quando a janela é alterada.

 Para obter um objeto <xref:Microsoft.Office.Interop.Outlook.Explorer>, siga um destes procedimentos:

- Use a propriedade <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> do objeto <xref:Microsoft.Office.Interop.Outlook.Application> para acessar todos os objetos <xref:Microsoft.Office.Interop.Outlook.Explorer> no Outlook.

- Use o método <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A> do objeto <xref:Microsoft.Office.Interop.Outlook.Application> para obter a <xref:Microsoft.Office.Interop.Outlook.Explorer> que atualmente tem o foco.

- Use o método `GetExplorer` do objeto <xref:Microsoft.Office.Interop.Outlook.Folder> para obter a <xref:Microsoft.Office.Interop.Outlook.Explorer> da pasta atual.

### <a name="inspector-object"></a>Objeto inspector
 O objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> representa uma janela que exibe um único item, como uma mensagem de email, uma tarefa ou um compromisso. O objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> inclui métodos e propriedades que você pode usar para modificar a janela e eventos que são gerados quando a janela é alterada.

 Para obter um objeto <xref:Microsoft.Office.Interop.Outlook.Inspector>, siga um destes procedimentos:

- Use a propriedade <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> do objeto <xref:Microsoft.Office.Interop.Outlook.Application> para acessar todos os objetos <xref:Microsoft.Office.Interop.Outlook.Inspector> no Outlook.

- Use o método <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> do objeto <xref:Microsoft.Office.Interop.Outlook.Application> para obter a <xref:Microsoft.Office.Interop.Outlook.Inspector> que atualmente tem o foco.

- Use o método `GetInspector` de um item específico, como um <xref:Microsoft.Office.Interop.Outlook.MailItem> ou <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>, para recuperar o Inspetor associado a ele.

### <a name="folder-object"></a>Objeto de pasta
 O objeto <xref:Microsoft.Office.Interop.Outlook.Folder> representa uma pasta que contém mensagens de email, contatos, tarefas e outros itens. O Outlook fornece 16 objetos de <xref:Microsoft.Office.Interop.Outlook.Folder> padrão.

 Os objetos de <xref:Microsoft.Office.Interop.Outlook.Folder> padrão são definidos pelo <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders> valores de enumeração. Por exemplo,

 Microsoft. Office. Interop. Outlook. OlDefaultFolders. olFolderInbox corresponde à pasta **inbox** no Outlook.

 Para obter um exemplo que mostra como acessar um <xref:Microsoft.Office.Interop.Outlook.Folder> padrão e criar um novo <xref:Microsoft.Office.Interop.Outlook.Folder>, consulte [como: criar programaticamente itens de pasta personalizados](../vsto/how-to-programmatically-create-custom-folder-items.md).

### <a name="mailitem-object"></a>Objeto MailItem
 O objeto <xref:Microsoft.Office.Interop.Outlook.MailItem> representa uma mensagem de email. <xref:Microsoft.Office.Interop.Outlook.MailItem> objetos geralmente estão em pastas, como Inbox, **Items enviados**e **caixa**de **saída**. <xref:Microsoft.Office.Interop.Outlook.MailItem> expõe propriedades e métodos que podem ser usados para criar e enviar mensagens de email.

 Para obter um exemplo que mostra como criar uma mensagem de email, consulte [como: criar programaticamente um item de email](../vsto/how-to-programmatically-create-an-e-mail-item.md).

### <a name="appointmentitem-object"></a>Objeto AppointmentItem
 O objeto <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> representa uma reunião, um compromisso único ou um compromisso ou reunião recorrente na pasta **calendário** . O objeto <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> inclui métodos que executam ações como responder ou encaminhar solicitações de reunião e propriedades que especificam detalhes da reunião, como o local e a hora.

 Para obter um exemplo que mostra como criar um compromisso, consulte [como: criar programaticamente uma solicitação de reunião](../vsto/how-to-programmatically-create-a-meeting-request.md).

### <a name="taskitem-object"></a>Objeto TaskItem
 O objeto <xref:Microsoft.Office.Interop.Outlook.TaskItem> representa uma tarefa a ser executada em um período de tempo especificado. <xref:Microsoft.Office.Interop.Outlook.TaskItem> objetos estão localizados na pasta **tarefas** .

 Para criar uma tarefa, use o método [CreateItem](/previous-versions/office/developer/office-2003/aa220082(v=office.11)) do objeto <xref:Microsoft.Office.Interop.Outlook.Application> e passe o valor <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> para o parâmetro.

### <a name="contactitem-object"></a>Objeto ContactItem
 O objeto <xref:Microsoft.Office.Interop.Outlook.ContactItem>representa um contato na pasta **contatos** . os objetos de <xref:Microsoft.Office.Interop.Outlook.ContactItem> contêm uma variedade de informações de contato para as pessoas que representam, como endereços, endereços de email e números de telefone.

 Para obter um exemplo que mostra como criar um novo contato, consulte [como: adicionar programaticamente uma entrada aos contatos do Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Para obter um exemplo que mostra como procurar um contato existente, consulte [como: pesquisar programaticamente por um contato específico](../vsto/how-to-programmatically-search-for-a-specific-contact.md).

## <a name="refdoc"></a>Usar a documentação do modelo de objeto do Outlook
 Para obter informações completas sobre o modelo de objeto do Outlook, consulte a referência do assembly de interoperabilidade primária do Outlook (PIA) e a referência do modelo de objeto do VBA.

### <a name="primary-interop-assembly-reference"></a>Referência de assembly de interoperabilidade primária
 A referência do PIA do Outlook documenta os tipos nos assemblies de interoperabilidade primários para o Outlook 2010. Para obter mais informações, consulte [referência de assembly de interoperabilidade primária do Outlook 2010](/previous-versions/office/developer/office-2010/bb652780(v=office.14)).

 Além de fornecer informações para todos os tipos nos PIAs, esta documentação também fornece informações adicionais sobre a estrutura dos PIAs e exemplos de código para tarefas comuns de automação do Outlook.

### <a name="vba-object-model-reference"></a>Referência de modelo de objeto VBA
 A referência do modelo de objeto do VBA documenta o modelo de objeto do Outlook conforme ele é exposto ao código Visual Basic for Applications (VBA). Para obter mais informações, consulte [referência de modelo de objeto do Outlook 2010](/office/vba/api/overview/Outlook/object-model).

 Todos os objetos e membros na referência do modelo de objeto do VBA correspondem a tipos e membros no PIA do Outlook. Por exemplo, o objeto inspector na referência do modelo de objeto do VBA corresponde ao objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> no PIA do Outlook. Embora a referência de modelo de objeto do VBA Forneça exemplos de código para a maioria das propriedades, métodos e eventos, você deve converter o código VBA nesta referência C# para Visual Basic ou Visual se quiser usá-los em um projeto de suplemento do VSTO do Outlook criado por usando o Visual Studio.

### <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Trabalhar com itens de contato](../vsto/working-with-contact-items.md)|Fornece tópicos que mostram como executar tarefas com contatos.|
|[Trabalhar com itens de email](../vsto/working-with-mail-items.md)|Fornece tópicos que mostram como executar tarefas com itens de email.|
|[Trabalhar com pastas](../vsto/working-with-folders.md)|Fornece tópicos que mostram como executar tarefas com pastas.|
|[Trabalhar com itens de calendário](../vsto/working-with-calendar-items.md)|Fornece tópicos que mostram como executar tarefas com itens de calendário.|
|[Como: determinar programaticamente o item atual do Outlook](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Mostra como exibir o nome da pasta atual e algumas informações sobre o item selecionado.|
