---
title: 'Como: Criar um receptor de evento para uma instância de lista específica | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: deba5e493f58a99e672e362977406670e1eee0e1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60094340"
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>Como: Criar um receptor de evento para uma instância de lista específica
  Um receptor de evento da instância de lista responde a eventos que ocorrem em qualquer instância de uma definição de lista. Embora o modelo de receptor de evento não permite o direcionamento de uma instância de lista específica, você pode modificar um receptor de eventos com escopo em uma definição de lista para responder a eventos em uma instância de lista específica.

 Usar como destino de uma instância de lista específica, na *Elements. XML* para o receptor de evento, substitua `ListTemplateId` com `ListUrl` e adicione a URL da instância de lista.

## <a name="create-a-list-instance-event-receiver"></a>Criar um receptor de evento de instância de lista
 As etapas a seguir mostram como modificar um receptor de evento de item de lista para responder apenas a eventos que ocorrem em uma instância de lista de avisos personalizados.

#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>Para modificar um receptor de eventos para responder a uma instância de lista específica

1. Em um navegador, abra o site do SharePoint.

2. No painel de navegação **lista** link.

3. No **todo o conteúdo do Site** , escolha o **criar** link.

4. No **Create** caixa de diálogo, escolha o **anúncios** digite, nomeie o comunicado **TestAnnouncements**e, em seguida, escolha o **criar**botão.

5. No [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], criar um projeto de receptor de evento.

6. No **que tipo de receptor de eventos você deseja?** , escolha **eventos de Item de lista**.

    > [!NOTE]
    >  Você também pode selecionar qualquer outro tipo de receptor de evento que tem como escopo a uma definição de lista, por exemplo, **listar eventos de Email** ou **eventos de fluxo de trabalho de lista**.

7. No **qual item deve ser a origem do evento?** , escolha **anúncios**.

8. No **manipular os eventos a seguir** lista, selecione o **um item está sendo adicionado** caixa de seleção e, em seguida, escolha o **concluir** botão.

9. Na **Gerenciador de soluções**, em EventReceiver1, abra *Elements. XML*.

     O receptor de evento atualmente faz referência a definição de lista de anúncios, usando a seguinte linha:

    ```xml
    <Receivers ListTemplateId="104">
    ```

     Altere essa linha ao texto a seguir:

    ```xml
    <Receivers ListUrl="Lists/TestAnnouncements">
    ```

     Isso instrui o receptor de eventos para responder apenas a eventos que ocorrem no novo **TestAnnouncements** lista de avisos que você acabou de criar. Você pode alterar o `ListURL` atributo para fazer referência a qualquer instância de lista no servidor do SharePoint.

10. Abra o arquivo de código para o receptor de evento e colocar um ponto de interrupção no método ItemAdding.

11. Escolha o **F5** tecla para compilar e executar a solução.

12. No SharePoint, escolha o **TestAnnouncements** link no painel de navegação.

13. Escolha o **adicionar novo comunicado** link.

14. Insira um título para o comunicado e, em seguida, escolha o **salvar** botão.

     Observe que o ponto de interrupção é atingido quando o novo item é adicionado à lista de anúncios personalizados.

15. Escolha o **F5** tecla para continuar.

16. No painel de navegação, escolha o **listas** vincular e, em seguida, escolha o **anúncios** link.

17. Adicione um novo anúncio.

     Observe que o receptor de evento não disparam no anúncio novo porque o receptor está configurado para responder apenas a eventos na instância de lista de comunicado personalizado, **TestAnnouncements**.

## <a name="see-also"></a>Consulte também
- [Como: Criar um receptor de eventos](../sharepoint/how-to-create-an-event-receiver.md)
- [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)
