---
title: 'Como: Adicionar controles ao modo de exibição Backstage '
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bb038fdebdfefeb5f401860c17b5567028c3bb77
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56621338"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Como: Adicionar controles ao modo de exibição Backstage
  Você pode usar o Designer de faixa de opções para adicionar controles ao menu que é aberta quando você clica o **arquivo** guia. Quando você executa o aplicativo, controles que podem ser adicionados para o **arquivo** guia será exibida em um grupo chamado **Add-ins**.

 Você não pode posicionar controles antes ou depois de controles internos usando o designer de faixa de opções no Visual Studio. Um controle interno é um controle que já aparece no modo de exibição Backstage. Se você desejar posicionar controles antes ou depois de controles internos, você deve usar um XML de faixa de opções. Para obter mais informações sobre **da faixa de opções (XML)**, consulte [XML da faixa de opções](../vsto/ribbon-xml.md). Para obter mais informações sobre como personalizar o modo de exibição Backstage, consulte [Introdução ao modo de exibição Backstage do Office 2010 para desenvolvedores](http://go.microsoft.com/fwlink/?LinkId=182189) e [personalizar o modo de exibição Backstage do Office 2010 para desenvolvedores](http://go.microsoft.com/fwlink/?LinkId=182188).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-controls-to-backstage-view"></a>Para adicionar controles ao modo de exibição Backstage

1.  Abra o item de faixa de opções no modo de exibição de Design.

     Para obter informações sobre como adicionar um **faixa de opções (Visual Designer)** item ao seu projeto, consulte [como: Introdução à personalização da faixa de opções](../vsto/how-to-get-started-customizing-the-ribbon.md).

2.  No Designer de faixa de opções, clique o **arquivo** guia.

     Um designer de menu é exibido. Essa superfície de design não contém todos os controles.

3.  Dos **controles de faixa de opções do Office** guia da **caixa de ferramentas**, arraste qualquer um dos seguintes controles para o designer de menu:

    -   Botão

    -   CheckBox

    -   Galeria

    -   Menu

    -   Separador

    -   SplitButton

    -   ToggleButton

4.  Arraste os controles para movê-los para novas posições no menu.

## <a name="see-also"></a>Consulte também
- [Visão geral da faixa de opções](../vsto/ribbon-overview.md)
- [Designer da faixa de opções](../vsto/ribbon-designer.md)
- [XML da faixa de opções](../vsto/ribbon-xml.md)
- [Como: Introdução ao personalizar a faixa de opções](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Passo a passo: Criar uma guia personalizada usando o Designer de faixa de opções](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
