---
title: Ações personalizadas nas regiões de formulário do Outlook
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 817cf9fe8698c2908e873246a8971f90fe72b460
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71254448"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Ações personalizadas nas regiões de formulário do Outlook
  Ações exibem botões que permitem que os usuários respondam a um item Microsoft Office Outlook. Por exemplo, para responder a um item de email, os usuários clicam nos botões **responder**, **responder a todos**ou **encaminhar** ação. Cada uma dessas ações cria um novo item de email e popula os campos do item usando as informações do item original.

 Você pode criar uma ação personalizada que abre qualquer tipo de item do Outlook. Por exemplo, você pode adicionar uma ação personalizada que abre um novo compromisso ou item de tarefa. Defina as propriedades de uma ação personalizada ou use um código personalizado para preencher os campos do novo item. As ações personalizadas aparecem na lista suspensa **ações personalizadas** de um item aberto em uma janela do Inspetor do Outlook.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-custom-actions-to-a-form-region"></a>Adicionar ações personalizadas a uma região de formulário
 Para adicionar uma ação personalizada a uma região de formulário, use a caixa de diálogo **ações personalizadas** . Você pode abrir a caixa de diálogo **ações personalizadas** selecionando a região de formulário em **Gerenciador de soluções**, expandindo o nó **manifesto** na **janela Propriedades**, selecionando a propriedade **CustomActions** e clicando no botão de reticências (![elipse do designer móvel ASP.net](../sharepoint/media/mwellipsis.gif "Elipse do designer móvel ASP.NET")).

 Você pode usar a caixa de diálogo **ações personalizadas** para especificar um *formulário de destino*. Um formulário de destino é o formulário que aparece quando o usuário executa a ação personalizada.

 Você também pode usar a caixa de diálogo **ações personalizadas** para especificar como deseja que as informações do item original apareçam no formulário de destino.

 A tabela a seguir descreve as propriedades que estão disponíveis na caixa de diálogo **ações personalizadas** .

|Propriedade|Descrição|
|--------------|-----------------|
|**AddressLike**|Especifica como o formulário de destino será endereçado.|
|**Corpo**|Especifica como o corpo do item original é acrescentado ao formulário de destino.|
|**Habilitada**|Indica se a ação personalizada está habilitada. Se essa propriedade for definida como **false**, a ação personalizada será desabilitada.|
|**Método**|Especifica o tipo de resposta disponível quando a ação personalizada é executada. A ação personalizada pode enviar o formulário, abrir o formulário ou avisar o usuário se deseja enviar ou abrir o formulário.|
|**Nome**|Especifica o nome interno que você pode usar para fazer referência a essa ação personalizada no código.|
|**ShowOnRibbon**|Indica se a ação personalizada deve ser exibida na faixa de faixas do item original.|
|**SubjectPrefix**|Especifica o texto que é inserido no início da linha de assunto do formulário de destino.|
|**TargetForm**|Especifica o nome da classe de mensagem do formulário de destino. Por exemplo, digite **IPM. Tarefa** para abrir um formulário de tarefa.|
|**Título**|Especifica o rótulo do botão de ação personalizado.|

## <a name="customize-a-custom-action-at-run-time"></a>Personalizar uma ação personalizada em tempo de execução
 Você também pode adicionar o comportamento à ação personalizada usando código. Por exemplo, você pode adicionar código que usa os nomes de destinatários de email e adiciona esses nomes como participantes em um novo item de compromisso. Para fazer isso, manipule o evento [CustomAction](/office/vba/api/Outlook.MailItem.CustomAction) do [objeto MailItem](/office/vba/api/Outlook.MailItem).

## <a name="see-also"></a>Confira também
- [Criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)
- [Walkthrough: criar uma região de formulário do Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Associar uma região de formulário a uma classe de mensagem do Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
