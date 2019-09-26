---
title: 'Como: Percorrer os registros de banco de dados em uma planilha'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: f0b3c6a8a9292ceda03c9d0020b78d9518ca49d9
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252041"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Como: Percorrer os registros de banco de dados em uma planilha
  O procedimento a seguir mostra como usar o designer para exibir um único campo de uma tabela de banco de dados em uma Microsoft Office planilha do Excel, com controles que permitem ao usuário final percorrer todos os registros.

 Você pode usar o designer somente em projetos de nível de documento. No entanto, você também pode adicionar controles e associá-los a dados programaticamente em tempo de execução. Para obter mais informações, confira [Passo a passo: Vinculação de dados simples no projeto](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)de suplemento do VSTO.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="to-scroll-through-database-records-in-a-worksheet"></a>Para rolar os registros de banco de dados em uma planilha

1. Abra um projeto de aplicativo do Excel no Visual Studio.

2. Abra a janela **Data Sources** e crie uma fonte de dados do banco de dado. Para obter mais informações, consulte [adicionar novas conexões](../data-tools/add-new-connections.md).

3. Expanda a tabela que contém os dados que você deseja mostrar e selecione a coluna específica.

4. Abra a lista de controles e selecione **NamedRange**.

5. Arraste o <xref:Microsoft.Office.Tools.Excel.NamedRange> controle para a célula onde você deseja que os dados sejam exibidos.

6. Na guia **Windows Forms** da caixa de **ferramentas**, adicione um <xref:System.Windows.Forms.BindingNavigator> controle à sua planilha e configure os controles que você deseja usar. Para obter mais informações, consulte [visão geral &#40;do&#41;controle BindingNavigator Windows Forms](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Consulte também
- [Associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)
