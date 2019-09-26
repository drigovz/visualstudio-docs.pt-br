---
title: Associar uma região de formulário a uma classe de mensagem do Outlook
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.InvalidMessageClassName
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FormRegionMessageClassAttribute
- form regions [Office development in Visual Studio], message classes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 45db262b6bf7843a3893c5d60f0b6eaea5fcb70b
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254572"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Associar uma região de formulário a uma classe de mensagem do Outlook
  Você pode especificar quais Microsoft Office itens do Outlook exibem uma região de formulário associando a região do formulário à classe de mensagem de cada item. Por exemplo, se você quiser acrescentar uma região de formulário à parte inferior de um item de email, poderá associar a região de formulário à `IPM.Note` classe de mensagem.

 Para associar uma região de formulário a uma classe de mensagem, especifique o nome da classe de mensagem no assistente de **nova região de formulário do Outlook** ou aplique um atributo à classe de fábrica de região de formulário.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="understand-outlook-message-classes"></a>Entender as classes de mensagens do Outlook
 Uma classe de mensagem do Outlook identifica um tipo de item do Outlook. A tabela a seguir lista esses oito tipos padrão de itens e seus nomes de classe de mensagem.

|Tipo de item do Outlook|Nome da classe da mensagem|
|-----------------------|------------------------|
|AppointmentItem|`IPM.Appointment`|
|ContactItem|`IPM.Contact`|
|DistListItem|`IPM.DistList`|
|JournalItem|`IPM.Activity`|
|Exclusões|`IPM.Note`|
|PostItem|`IPM.Post` ou `IPM.Post.RSS`|
|TaskItem|`IPM.Task`|

 Você também pode especificar os nomes das classes de mensagem personalizadas. As classes de mensagens personalizadas identificam formulários personalizados que você define no Outlook.

> [!NOTE]
> Para as regiões de formulário substituição e substituir, você pode especificar um novo nome de classe de mensagem personalizada. Você não precisa usar o nome de classe de mensagem de um formulário personalizado existente. O nome da classe de mensagem personalizada deve ser exclusivo. Uma maneira de garantir que o nome seja exclusivo é usar uma Convenção de nomenclatura semelhante à seguinte: \<> *StandardMessageClassName*. > Da *empresa.* \< Messageclassname > (por exemplo `IPM.Note.Contoso.MyMessageClass`:). \<

## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Associar uma região de formulário a uma classe de mensagem do Outlook
 Há duas maneiras de associar uma região de formulário a uma classe de mensagem:

- Use o assistente de **nova região de formulário do Outlook** .

- Aplicar atributos de classe.

### <a name="use-the-new-outlook-form-region-wizard"></a>Usar o assistente de nova área de formulário do Outlook
 Na página final do assistente de **nova região de formulário do Outlook** , você pode selecionar as classes de mensagem padrão e digitar os nomes das classes de mensagem personalizadas que deseja associar à região do formulário.

 As classes de mensagem padrão não estarão disponíveis se a região de formulário for projetada para substituir o formulário inteiro ou a página padrão de um formulário. Você pode especificar nomes de classe de mensagem padrão somente para formulários que adicionam uma nova página a um formulário ou que são anexados à parte inferior de um formulário. Para obter mais informações, confira [Como: Adicione uma região de formulário a um projeto](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)de suplemento do Outlook.

 Para incluir uma ou mais classes de mensagem personalizadas, digite seus nomes na caixa **quais classes de mensagens personalizadas exibirão esta região de formulário?** .

 Os nomes que você digitar devem estar em conformidade com as seguintes diretrizes:

- Use o nome da classe da mensagem totalmente qualificada (por exemplo: Placa. Note. contoso ").

- Use ponto e vírgula para separar vários nomes de classe de mensagem.

- Não inclua classes de mensagem padrão do Outlook, como "IPM. Observação "ou" IPM. Entre em contato com ". Inclua somente classes de mensagem personalizadas, como "IPM. Note. contoso ".

- Não especifique a classe de mensagem base por si só (por exemplo: "IPM").

- Não exceda 256 caracteres para cada nome de classe de mensagem.

  O assistente de **nova região de formulário do Outlook** valida o formato de sua entrada quando você clica em **concluir**.

> [!NOTE]
> O **novo** assistente de região de formulário do Outlook não verifica se os nomes de classe de mensagem que você fornece estão corretos ou válidos.

 Quando você concluir o assistente, o **novo** assistente de região de formulário do Outlook aplicará atributos à classe de região de formulário que contém os nomes de classe de mensagem especificados. Você também pode aplicar esses atributos manualmente.

### <a name="apply-class-attributes"></a>Aplicar atributos de classe
 Você pode associar uma região de formulário a uma classe de mensagem do Outlook depois de concluir o assistente de **nova região de formulário do Outlook** . Para fazer isso, aplique atributos à classe de fábrica da região do formulário.

 O exemplo a seguir mostra <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> dois atributos que foram aplicados a uma classe de fábrica de região `myFormRegion`de formulário chamada. O primeiro atributo associa a região de formulário a uma classe de mensagem padrão para um formulário de mensagem de email. O segundo atributo associa a região do formulário a uma classe de mensagem `IPM.Task.Contoso`personalizada denominada.

 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]

 Os atributos devem estar em conformidade com as seguintes diretrizes:

- Para classes de mensagens personalizadas, use o nome da classe de mensagem totalmente qualificado (por exemplo: Placa. Note. contoso ").

- Não especifique a classe de mensagem base por si só (por exemplo: "IPM").

- Não exceda 256 caracteres para cada nome de classe de mensagem.

- Não inclua os nomes das classes de mensagem padrão se a região de formulário Substituir o formulário inteiro ou a página padrão de um formulário. Você pode especificar nomes de classe de mensagem padrão somente para formulários que adicionam uma nova página a um formulário ou que são anexados à parte inferior de um formulário. Para obter mais informações, confira [Como: Adicione uma região de formulário a um projeto](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)de suplemento do Outlook.

  O Visual Studio valida o formato dos nomes de classe de mensagem quando você cria o projeto.

> [!NOTE]
> O Visual Studio não verifica se os nomes de classe de mensagem que você fornece estão corretos ou válidos.

## <a name="see-also"></a>Consulte também
- [Acessar uma região de formulário em tempo de execução](../vsto/accessing-a-form-region-at-run-time.md)
- [Criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)
- [Passo a passo: Criar uma região de formulário do Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Diretrizes para criar regiões de formulário do Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Visão geral de nome do formulário e classe de mensagem](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)
- [Como os formulários e itens do Outlook funcionam juntos](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)
