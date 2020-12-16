---
title: Como rolar por registros de banco de dados em uma planilha
description: Saiba como você pode usar o designer para exibir um único campo de uma tabela de banco de dados em uma planilha do Microsoft Excel
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 536a3cca0337e8879e64cbc3ffc15b8411c201b6
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528167"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Como rolar por registros de banco de dados em uma planilha
  O procedimento a seguir mostra como usar o designer para exibir um único campo de uma tabela de banco de dados em uma Microsoft Office planilha do Excel, com controles que permitem ao usuário final percorrer todos os registros.

 Você pode usar o designer somente em projetos de nível de documento. No entanto, você também pode adicionar controles e associá-los a dados programaticamente em tempo de execução. Para obter mais informações, consulte [Walkthrough: vinculação de dados simples no projeto de suplemento do VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="to-scroll-through-database-records-in-a-worksheet"></a>Para rolar os registros de banco de dados em uma planilha

1. Abra um projeto de aplicativo do Excel no Visual Studio.

2. Abra a janela **Data Sources** e crie uma fonte de dados do banco de dado. Para obter mais informações, consulte [adicionar novas conexões](../data-tools/add-new-connections.md).

3. Expanda a tabela que contém os dados que você deseja mostrar e selecione a coluna específica.

4. Abra a lista de controles e selecione **NamedRange**.

5. Arraste o <xref:Microsoft.Office.Tools.Excel.NamedRange> controle para a célula onde você deseja que os dados sejam exibidos.

6. Na guia **Windows Forms** da caixa de **ferramentas**, adicione um <xref:System.Windows.Forms.BindingNavigator> controle à sua planilha e configure os controles que você deseja usar. Para obter mais informações, consulte [visão geral do controle BindingNavigator &#40;Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Veja também
- [Associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)
