---
title: Copiar e colar formas no documento do Visio programaticamente
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 074a276fe37ef713d38078f60c4bee95145c4d8b
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402220"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Como: Copiar e colar formas em um documento do Visio de forma programática
  Programaticamente, você pode copiar formas em uma única página de um documento e colá-los em uma nova página no mesmo documento. Você pode optar por colá-los para o local padrão (o centro da janela ativa) ou para os mesmos locais de coordenadas que tiveram na página original.

## <a name="copy-and-paste-shapes"></a>Copiar e colar formas
 Para obter detalhes sobre o modelo de objeto, consulte a documentação de referência do VBA para o [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [ Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy), e [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) métodos e as [ Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](/office/vba/api/Visio.viscutcopypastecodes) sinalizador.

### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Para copiar formas para o Centro de outra página

- O exemplo a seguir demonstra como copiar as formas da primeira página e colá-los para o centro da segunda página.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]

## <a name="copy-and-paste-shapes-with-the-same-positions"></a>Copiar e colar formas com as mesmas posições
 Para obter detalhes sobre o modelo de objeto, consulte a documentação de referência do VBA para o [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [ Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy), e [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) métodos e as [ Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](/office/vba/api/Visio.viscutcopypastecodes) sinalizador.

 Se você precisar controlar o formato das informações coladas e (opcionalmente) estabelecer um link para um arquivo de origem (por exemplo, um documento do Microsoft Office Word), use o método PasteSpecial.

### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Para copiar formas e locais de forma para outra página

- O exemplo a seguir demonstra como copiar as formas da primeira página e o cola na segunda página com seus locais originais de coordenadas.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]

## <a name="see-also"></a>Consulte também
- [Soluções do Visio](../vsto/visio-solutions.md)
- [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)
- [Trabalhar com formas do Visio](../vsto/working-with-visio-shapes.md)
- [Como: Adicionar formas a um documento do Visio programaticamente](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)
