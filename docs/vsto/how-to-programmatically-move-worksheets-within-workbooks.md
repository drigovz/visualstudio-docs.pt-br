---
title: 'Como: mover planilhas programaticamente dentro de pastas de trabalho'
description: Saiba como você pode alterar programaticamente a posição de planilhas em relação a outras planilhas em uma pasta de trabalho do Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, moving
- workbooks, moving worksheets in
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 165ac8f440b33d68dc70530731a5528ae23726b0
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525582"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Como: mover planilhas programaticamente dentro de pastas de trabalho
  Você pode alterar programaticamente a posição das planilhas em relação a outras planilhas em uma pasta de trabalho. Se você não especificar um local para a planilha movida, o Excel criará uma nova pasta de trabalho para contê-la.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Para mover uma planilha em uma personalização no nível do documento

1. Atribua o número total de planilhas na pasta de trabalho a uma variável e, em seguida, mova a primeira planilha para que ela se torne a última.

     [!code-csharp[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#24)]

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>Para mover uma planilha em um suplemento do VSTO

1. Atribua o número total de planilhas na pasta de trabalho a uma variável e, em seguida, mova a primeira planilha para que ela se torne a última.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#16)]

## <a name="see-also"></a>Veja também
- [Trabalhar com planilhas](../vsto/working-with-worksheets.md)
- [Como: ocultar planilhas programaticamente](../vsto/how-to-programmatically-hide-worksheets.md)
- [Como: excluir programaticamente planilhas de pastas de trabalho](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Como: proteger planilhas programaticamente](../vsto/how-to-programmatically-protect-worksheets.md)
- [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)
