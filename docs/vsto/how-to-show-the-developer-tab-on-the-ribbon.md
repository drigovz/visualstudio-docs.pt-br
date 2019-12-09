---
title: 'Como: Mostrar a guia Desenvolvedor na faixa de faixas'
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b6641cca4ef2288452b2f6959482b311a5b07a4
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551780"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Como: Mostrar a guia Desenvolvedor na faixa de faixas
  Para acessar a guia **desenvolvedor** na faixa de faixas de um aplicativo do Office, você deve configurá-lo para mostrar essa guia porque ela não aparece por padrão. Por exemplo, você deve mostrar essa guia se quiser adicionar um <xref:Microsoft.Office.Tools.Word.GroupContentControl> a uma personalização em nível de documento para o Word.

> [!NOTE]
> Esta orientação se aplica somente ao Office 2010 ou a aplicativos posteriores. Se você quiser mostrar essa guia no sistema de Microsoft Office de 2007, consulte a seguinte versão deste tópico [como: Mostre a guia Desenvolvedor na faixa de](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
)faixas.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> O acesso não tem uma guia de **desenvolvedor** .

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-show-the-developer-tab"></a>Para mostrar a guia desenvolvedor

1. Inicie qualquer um dos aplicativos do Office com suporte neste tópico. Consulte o **aplica-se a:** observação anteriormente neste tópico.

2. Na guia **arquivo** , escolha o botão **Opções** .

     A figura a seguir mostra a guia **arquivo** e o botão **opções** no Office 2010.

     ![Escolhendo arquivo, opções no Outlook 2010](../vsto/media/vsto-office-file-tab.png "Escolhendo arquivo, opções no Outlook 2010")

     A figura a seguir mostra a guia **arquivo** no Office 2013.

     ![A guia arquivo no Outlook 2013](../vsto/media/vsto-office2013-filetab.png "A guia arquivo no Outlook 2013")

     A figura a seguir mostra o botão **Opções** no Office 2013.

     ![O botão Opções na versão prévia do Outlook 2013](../vsto/media/vsto-office2013-optionsbutton.png "O botão Opções na versão prévia do Outlook 2013")

3. Na caixa de diálogo opções de _ApplicationName_, escolha o botão **Personalizar faixa** de**opção** .

     A figura a seguir mostra a caixa de diálogo Options e o botão **Custom Ribbon da faixa** de **opções** no Excel 2010. O local desse botão é semelhante em todos os outros aplicativos listados na seção "aplica-se a", próximo à parte superior deste tópico.

     ![O botão Personalizar faixa de] medida (../vsto/media/vsto-office2010-customizeribbonbutton.png "O botão Personalizar faixa de") medida

4. Na lista de guias principais, marque a caixa de seleção **desenvolvedor** .

     A figura a seguir mostra a caixa de seleção do **desenvolvedor** no [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]Word 2010 e. O local dessa caixa de seleção é semelhante em todos os outros aplicativos listados na seção "aplica-se a" na parte superior deste tópico.

     ![A caixa de seleção do desenvolvedor no diálogo opções do Word](../vsto/media/vsto-office2010-developercheckbox.png "A caixa de seleção do desenvolvedor no diálogo opções do Word")

5. Escolha o botão **OK** para fechar a caixa de diálogo **Opções** .

## <a name="see-also"></a>Consulte também
- [Personalização da interface do usuário do Office](../vsto/office-ui-customization.md)
