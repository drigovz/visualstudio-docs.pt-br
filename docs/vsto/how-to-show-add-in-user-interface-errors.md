---
title: 'Como: Mostrar erros de interface de usuário do suplemento'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 78cc4d2e85e2f7a5347fe0c8927c855160fbb511
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441784"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Como: Mostrar erros de interface de usuário do suplemento
  Por padrão, se um suplemento do VSTO tenta manipular a interface de usuário (IU) do Microsoft Office e falhar, nenhuma mensagem de erro é exibida. No entanto, você pode configurar aplicativos do Microsoft Office para exibir mensagens para erros relacionados à interface do usuário. Você pode usar essas mensagens para ajudar a determinar por que uma faixa de opções personalizada não aparece ou por que uma faixa de opções é exibida, mas não há controles aparecem.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="to-show-vsto-add-in-user-interface-errors"></a>Para mostrar erros de interface de usuário do suplemento do VSTO

1. Inicie o aplicativo.

2. Clique o **arquivo** guia.

3. Clique em **Opções**.

4. No painel de categorias, clique em **avançado**.

5. No painel de detalhes, selecione **erros de interface do usuário do suplemento do VSTO mostram**e, em seguida, clique em **Okey**.

    > [!NOTE]
    > Para o Outlook, o **erros de interface do usuário do suplemento do VSTO Mostrar** caixa de seleção está localizada no **desenvolvedor** seção do painel de detalhes. Para outros aplicativos, a caixa de seleção está localizada na **geral** seção do painel de detalhes.

## <a name="see-also"></a>Consulte também
- [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)
- [Criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)
- [Visão geral da faixa de opções](../vsto/ribbon-overview.md)
- [Visão geral do painel de ações](../vsto/actions-pane-overview.md)
