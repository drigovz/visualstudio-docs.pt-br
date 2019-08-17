---
title: Referência gerenciada (desenvolvimento do Office no Visual Studio)
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reference [Office development in Visual Studio], 2007 Microsoft Office system
- Office development in Visual Studio, reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: da10833f8340d5308321038bb0500ca8408b40bb
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551769"
---
# <a name="managed-reference-office-development-in-visual-studio"></a>Referência gerenciada (desenvolvimento do Office no Visual Studio)
  Esta seção contém documentação de referência de API para namespaces e tipos que são usados em projetos do Office [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] destinados ao [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]ou ao. Para obter a documentação de referência de API sobre os namespaces e tipos que são usados em projetos do Office direcionados para o .NET Framework 3,5, consulte a seção de referência [http://go.microsoft.com/fwlink/?LinkId=160658](http://go.microsoft.com/fwlink/?LinkId=160658)a seguir na documentação do Visual Studio:.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>Nesta seção
 <xref:Microsoft.Office.Tools>

 Contém classes comuns à programação de soluções do Office. Isso inclui a classe base para suplementos do VSTO, classes para a criação de painéis de tarefas personalizados em suplementos do VSTO, classes para a criação de marcas inteligentes em soluções do Excel e do Word e classes para a criação de painéis de ações em personalizações em nível de documento.

 <xref:Microsoft.Office.Tools.Excel>

 Contém controles de host e itens de host que podem ser usados em soluções para o Excel.

 <xref:Microsoft.Office.Tools.Excel.Controls>

 Contém controles do Excel e controles de Windows Forms que podem ser usados em soluções para o Excel.

 <xref:Microsoft.Office.Tools.Outlook>

 Contém classes usadas por suplementos do VSTO para o Outlook, incluindo classes que são usadas para criar regiões de formulário personalizadas.

 <xref:Microsoft.Office.Tools.Ribbon>

 Contém classes que são usadas para modificar programaticamente personalizações da faixa de forma criadas usando o designer de faixa de faixas.

 <xref:Microsoft.Office.Tools.Word>

 Contém controles de host e itens de host que podem ser usados em soluções para o Word.

 <xref:Microsoft.Office.Tools.Word.Controls>

 Contém controles de texto e controles de Windows Forms que podem ser usados em soluções para o Word.

 <xref:Microsoft.VisualStudio.Tools.Applications>

 Contém a <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe e um conjunto de classes de dados em cache relacionadas. Essas classes podem ser usadas para modificar alguns aspectos de personalizações em nível de documento em computadores que não têm o Microsoft Office instalado.

 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment>

 Contém a <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> interface (que você pode implementar para criar uma *ação de pós-implantação* para uma solução do Office), exceções que podem ser geradas ao instalar uma solução do Office e outras APIs que fazem parte da infraestrutura do Visual Studio.

 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime>

 Contém a maioria das exceções que podem ser geradas pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], várias classes que podem ser usadas para armazenar dados em cache em personalizações em nível de documento e outras APIs que fazem parte da infraestrutura do Visual Studio.

 <xref:Microsoft.VisualStudio.Tools.Office.BuildTasks>

 Contém as classes de tarefa do MSBuild que são usadas para criar projetos do Office.

## <a name="see-also"></a>Consulte também
- [Visão geral do Visual Studio Tools for Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Introdução &#40;ao desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Exemplos e orientações de desenvolvimento do Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)
