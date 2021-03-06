---
title: 'Como: Ocultar controles em planilhas ao imprimir'
description: Saiba que você pode ocultar os controles ao imprimir um Microsoft Office planilha do Excel que contém Windows Forms controles.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d87da5c22969fc355fe473e9505c61429b8023f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934800"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Como: Ocultar controles em planilhas ao imprimir
  Quando você imprime um documento Microsoft Office Excel que contém Windows Forms controles, os controles ficam visíveis na planilha impressa. Você pode ocultar os controles ao imprimir uma planilha.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> Se você ocultar controles que exibem dados, como um <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> , os dados no controle não estarão visíveis na planilha impressa.

> [!NOTE]
> Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, consulte [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Para ocultar controles quando uma planilha é impressa

1. Crie ou abra um projeto do Excel no Visual Studio e verifique se **Sheet1** está visível no designer. Para obter informações sobre como criar projetos, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na guia **controles comuns** da caixa de **ferramentas**, arraste um <xref:Microsoft.Office.Tools.Excel.Controls.Button> controle para uma célula em `Sheet1` .

3. Na janela **Propriedades** , defina a <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> propriedade como **false**.

## <a name="see-also"></a>Confira também
- [Controles em documentos do Office](../vsto/controls-on-office-documents.md)
- [Visão geral dos controles de Windows Forms em documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Como: adicionar controles de Windows Forms a documentos do Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Como: redimensionar controles nas células da planilha](../vsto/how-to-resize-controls-within-worksheet-cells.md)
