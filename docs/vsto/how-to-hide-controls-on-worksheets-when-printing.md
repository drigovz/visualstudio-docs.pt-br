---
title: 'Como: Ocultar controles em planilhas durante a impressão'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 322c314a768545996f343526367de44c667ce89b
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53646793"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>Como: Ocultar controles em planilhas durante a impressão
  Quando você imprime um documento do Microsoft Office Excel que contém controles de formulários do Windows, os controles são visíveis na planilha impressa. Você pode ocultar os controles ao imprimir uma planilha.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Se você ocultar controles que exibem dados, como um <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, os dados no controle não estará visíveis na planilha impressa.  
  
> [!NOTE]  
>  Seu computador pode mostrar diferentes nomes ou locais para alguns dos elementos de interface do usuário do Visual Studio nas instruções a seguir. A edição do Visual Studio que você possui e as configurações que você usa determinam esses elementos. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>Para ocultar os controles quando uma planilha for impressa  
  
1.  Criar ou abrir um projeto do Excel no Visual Studio e verifique **Sheet1** está visível no designer. Para obter informações sobre como criar projetos, consulte [como: Criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Do **controles comuns** guia da **caixa de ferramentas**, arraste uma <xref:Microsoft.Office.Tools.Excel.Controls.Button> control para uma célula em `Sheet1`.  
  
3.  No **propriedades** janela, defina o <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> propriedade **False**.  
  
## <a name="see-also"></a>Consulte também  
 [Controles em documentos do Office](../vsto/controls-on-office-documents.md)   
 [Controles de formulários do Windows na visão geral de documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Como: Adicionar controles dos Windows Forms a documentos do Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Como: Redimensionar controles dentro de células da planilha](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  