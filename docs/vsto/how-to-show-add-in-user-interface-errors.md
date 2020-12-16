---
title: Como mostrar erros de interface do usuário do suplemento
description: Saiba como você pode usar o Visual Studio para mostrar programaticamente erros de interface do usuário do VTSO em aplicativos Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: e74d60fe6386575417114fe1ad4823704cf09d46
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528131"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Como mostrar erros de interface do usuário do suplemento
  Por padrão, se um suplemento do VSTO tentar manipular a interface do usuário do Microsoft Office (IU) e falhar, nenhuma mensagem de erro será exibida. No entanto, você pode configurar Microsoft Office aplicativos para exibir mensagens de erros relacionados à interface do usuário. Você pode usar essas mensagens para ajudar a determinar por que uma faixa de Ribbon personalizada não aparece, ou por que uma faixa de uma é exibida, mas nenhum controle aparece.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="to-show-vsto-add-in-user-interface-errors"></a>Para mostrar erros da interface do usuário do suplemento do VSTO

1. Inicie o aplicativo.

2. Clique na guia **arquivo** .

3. Clique em **Opções**.

4. No painel categorias, clique em **avançado**.

5. No painel de detalhes, selecione **mostrar erros da interface do usuário do suplemento do VSTO** e clique em **OK**.

    > [!NOTE]
    > Para o Outlook, a caixa de seleção **mostrar erros de interface do usuário do suplemento do VSTO** está localizada na seção **desenvolvedor** do painel detalhes. Para outros aplicativos, a caixa de seleção está localizada na seção **geral** do painel detalhes.

## <a name="see-also"></a>Veja também
- [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)
- [Criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)
- [Visão geral da faixa de faixas](../vsto/ribbon-overview.md)
- [Visão geral do painel Ações](../vsto/actions-pane-overview.md)
