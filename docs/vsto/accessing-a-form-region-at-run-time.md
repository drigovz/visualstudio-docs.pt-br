---
title: Acessar uma região de formulário em tempo de execução
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at run time
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5dd8818b57a1aa33b70254303150d8f00e36cc02
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255792"
---
# <a name="access-a-form-region-at-run-time"></a>Acessar uma região de formulário em tempo de execução

|Aplica-se a|
|----------------|
|As informações contidas neste tópico se aplicam somente aos tipos e versões de projetos do Microsoft Office. Para obter mais informações, consulte [recursos disponíveis por aplicativo do Office e tipo de projeto](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Tipo de projeto**<br /><br /> -Projetos do suplemento do VSTO<br /><br /> **Versão do Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|

 Use a `Globals` classe para acessar regiões de formulário de qualquer lugar dentro de seu projeto do Outlook. Para obter mais informações sobre a `Globals` classe, consulte [acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Acessar regiões de formulário que aparecem em uma janela específica do Inspetor do Outlook
 Para acessar todas as regiões de formulário que aparecem em um inspetor do Outlook específico, chame a `FormRegions` propriedade da `Globals` classe e passe um <xref:Microsoft.Office.Interop.Outlook.Inspector> objeto que represente o Inspetor.

 O exemplo a seguir obtém a coleção de regiões de formulário que aparecem no Inspetor que atualmente tem foco. Em seguida, este exemplo acessa uma região de formulário na coleção denominada `formRegion1` e define o texto que aparece em uma caixa de texto para `Hello World` .

 [!code-vb[Trin_Outlook_FR_Access#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#2)]
 [!code-csharp[Trin_Outlook_FR_Access#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#2)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Acessar regiões de formulário que aparecem em uma janela específica do Outlook Explorer
 Para acessar todas as regiões de formulário que aparecem em um Gerenciador do Outlook específico, chame a `FormRegions` propriedade da `Globals` classe e passe um <xref:Microsoft.Office.Interop.Outlook.Explorer> objeto que represente o Gerenciador.

 O exemplo a seguir obtém a coleção de regiões de formulário que aparecem no Gerenciador que tem o foco no momento. Em seguida, este exemplo acessa uma região de formulário na coleção denominada `formRegion1` e define o texto que aparece em uma caixa de texto para `Hello World` .

 [!code-vb[Trin_Outlook_FR_Access#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#3)]
 [!code-csharp[Trin_Outlook_FR_Access#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#3)]

## <a name="access-all-form-regions"></a>Acessar todas as regiões de formulário
 Para acessar todas as regiões de formulário que aparecem em todos os gerenciadores e todos os inspetores, chame a `FormRegions` propriedade da `Globals` classe.

 O exemplo a seguir obtém a coleção de regiões de formulário que aparecem em todos os gerenciadores e todos os inspetores. Esse exemplo acessa uma região de formulário denominada `formRegion1` e define o texto que aparece em uma caixa de texto para `Hello World` .

 [!code-vb[Trin_Outlook_FR_Access#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Access#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#1)]

## <a name="access-controls-on-a-form-region"></a>Controles de acesso em uma região de formulário
 Para acessar controles em uma região de formulário usando a `Globals` classe, você deve tornar os controles acessíveis para o código fora do arquivo de código de região do formulário.

### <a name="form-regions-designed-in-the-form-region-designer"></a>Regiões de formulário projetadas no designer de região de formulário
 Para C#, altere o modificador de cada controle que você deseja acessar. Para fazer isso, selecione cada controle no designer de região de formulário e altere a propriedade **modificadores** para **interno** ou **público** na janela **Propriedades** . Por exemplo, se você alterar a propriedade **modificadora** de `textBox1` para **interno**, poderá acessar `textBox1` digitando `Globals.FormRegions.FormRegion1.textBox1` .

 Por Visual Basic, não é necessário alterar o modificador.

### <a name="imported-form-regions"></a>Regiões de formulário importadas
 Quando você importa uma região de formulário que foi projetada no Outlook, o modificador de acesso de cada controle na região de formulário torna-se privado. Como você não pode usar o designer de região de formulário para modificar uma região de formulário importada, não há nenhuma maneira de alterar o modificador de um controle na janela **Propriedades** .

 Para habilitar o acesso a um controle de fora do arquivo de código da região do formulário, crie uma propriedade no arquivo de código da região do formulário para retornar esse controle.

 Para obter mais informações sobre como criar propriedades em C#, consulte [como: declarar e usar propriedades de leitura/gravação &#40;guia de programação C&#35;&#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties).

 Para obter mais informações sobre como criar propriedades no Visual Basic, consulte [como: criar uma propriedade (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property).

## <a name="see-also"></a>Confira também
- [Diretrizes para criar regiões de formulário do Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Walkthrough: criar uma região de formulário do Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Como: adicionar uma região de formulário a um projeto de suplemento do Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Ações personalizadas nas regiões de formulário do Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Associar uma região de formulário a uma classe de mensagem do Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Walkthrough: importar uma região de formulário projetada no Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Como: impedir que o Outlook exiba uma região de formulário](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
- [Criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)
- [Acessar a faixa de faixas em tempo de execução](../vsto/accessing-the-ribbon-at-run-time.md)
