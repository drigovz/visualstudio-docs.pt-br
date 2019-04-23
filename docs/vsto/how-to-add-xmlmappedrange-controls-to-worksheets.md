---
title: 'Como: Adicionar controles XMLMappedRange a planilhas'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cef35cd1aa19ad27e7c47227b726a44756b0fae8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60085704"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Como: Adicionar controles XMLMappedRange a planilhas
  Quando você mapeia um elemento XML a uma célula no Microsoft Office Excel, o Visual Studio adiciona automaticamente um <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controle à sua planilha.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
>  O <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controle não está disponível na **caixa de ferramentas** ou o **fontes de dados** janela. Além disso, não é possível criar <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> controla por meio de programação.

## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Para adicionar um controle XMLMappedRange a uma planilha

1. Abra a pasta de trabalho do Excel no designer do Visual Studio.

2. Abra a planilha em que você deseja adicionar o controle.

3. Sobre o **Developer** , clique em **origem**.

    > [!NOTE]
    >  Se o **desenvolvedor** guia não estiver visível na faixa de opções, você deve habilitá-lo. Para obter mais informações, confira [Como: Mostrar a guia Desenvolvedor na faixa de opções](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

     O **código-fonte XML** painel de tarefas é exibida.

4. No **origem XML** painel de tarefas, clique em **mapas XML**.

5. No **mapas XML** caixa de diálogo, clique em **Add**.

     O **código-fonte XML** caixa de diálogo é exibida.

6. Selecione um esquema XML do **origem XML** caixa de diálogo e clique em **abrir**.

     O esquema é adicionado para o **mapas XML** caixa de diálogo.

7. No **mapas XML** caixa de diálogo, clique em **Okey**.

8. Arraste um elemento dos **código-fonte XML** painel de tarefas para uma célula na planilha.

     Um <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> é criado e adicionado ao projeto.

    > [!NOTE]
    >  Se você arrastar um elemento pai do **origem XML** painel de tarefas, uma <xref:Microsoft.Office.Tools.Excel.ListObject> controle é criado.

## <a name="see-also"></a>Consulte também
- [Controle XmlMappedRange](../vsto/xmlmappedrange-control.md)
- [Automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Visão geral dos controles de host e de itens de host](../vsto/host-items-and-host-controls-overview.md)
- [Limitações programáticas de itens de host e controles de host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Como: Mapear esquemas para planilhas dentro do Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
