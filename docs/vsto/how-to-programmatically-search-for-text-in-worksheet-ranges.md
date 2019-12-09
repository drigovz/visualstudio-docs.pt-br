---
title: 'Como: Pesquisar por programação de texto em intervalos de planilhas'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0ffc06c2f50f7a304ef76ac1451ee47419143afb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985818"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Como: Pesquisar por programação de texto em intervalos de planilhas
  O método <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> do objeto <xref:Microsoft.Office.Interop.Excel.Range> permite que você pesquise por texto dentro do intervalo. Esse texto também pode ser qualquer uma das cadeias de caracteres de erro que podem aparecer em uma célula de planilha, como `#NULL!` ou `#VALUE!`. Para obter mais informações sobre cadeias de caracteres de erro, consulte [valores de erro de célula](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 O exemplo a seguir pesquisa um intervalo chamado `Fruits` e modifica a fonte de células que contêm a palavra "maçãs". Esse procedimento também usa o método <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>, que usa as configurações de pesquisa definidas anteriormente para repetir a pesquisa. Você especifica a célula após a qual Pesquisar e o método <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> manipula o restante.

> [!NOTE]
> A pesquisa do método de <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> volta para o início do intervalo de pesquisa depois de atingir o final do intervalo. Seu código deve garantir que a pesquisa não seja encapsulada em um loop infinito. O procedimento de exemplo mostra uma maneira de lidar com isso usando a propriedade <xref:Microsoft.Office.Interop.Excel.Range.Address%2A>.

## <a name="to-search-for-text-in-a-worksheet-range"></a>Para Pesquisar texto em um intervalo de planilha

1. Declare variáveis para acompanhar todo o intervalo, o primeiro intervalo encontrado e o intervalo localizado atual.

    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]

2. Procure a primeira correspondência, especificando todos os parâmetros, exceto a célula a ser pesquisada.

    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]

3. Continue pesquisando contanto que haja correspondências.

    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]

4. Compare o primeiro intervalo encontrado (`firstFind`) a **Nothing**. Se `firstFind` não contiver nenhum valor, o código armazenará o intervalo encontrado (`currentFind`).

    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]

5. Saia do loop se o endereço do intervalo encontrado corresponder ao endereço do primeiro intervalo encontrado.

    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]

6. Defina a aparência do intervalo encontrado.

    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]

7. Execute outra pesquisa.

    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]

   O exemplo a seguir mostra o método Complete.

## <a name="example"></a>Exemplo
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]

## <a name="see-also"></a>Consulte também
- [Trabalhar com intervalos](../vsto/working-with-ranges.md)
- [Como: aplicar estilos programaticamente a intervalos em pastas de trabalho](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Como fazer referência programaticamente a intervalos de planilha no código](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
