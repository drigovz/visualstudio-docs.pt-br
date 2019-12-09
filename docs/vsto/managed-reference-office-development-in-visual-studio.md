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
ms.openlocfilehash: 137031202075d1c646cc7415042dd8d6eab72b78
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985763"
---
# <a name="managed-reference-office-development-in-visual-studio"></a>Referência gerenciada (desenvolvimento do Office no Visual Studio)
  Esta seção contém documentação de referência de API para namespaces e tipos que são usados em projetos do Office destinados ao [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou ao [!INCLUDE[net_v45](includes/net-v45-md.md)]. Para obter a documentação de referência de API sobre os namespaces e tipos que são usados em projetos do Office direcionados para o .NET Framework 3,5, consulte a seção de referência a seguir na documentação do Visual Studio: [referência gerenciada (desenvolvimento do Office no Visual Studio )](managed-reference-office-development-in-visual-studio.md).

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

 Contém a classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> e um conjunto de classes de dados em cache relacionadas. Essas classes podem ser usadas para modificar alguns aspectos de personalizações em nível de documento em computadores que não têm o Microsoft Office instalado.

 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment>

 Contém a interface <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> (que pode ser implementada para criar uma *ação pós-implantação* para uma solução do Office), exceções que podem ser geradas durante a instalação de uma solução do Office e outras APIs que fazem parte da infraestrutura do Visual Studio.

 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime>

 Contém a maioria das exceções que podem ser geradas pelo [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)], várias classes que podem ser usadas para armazenar dados em cache em personalizações em nível de documento e outras APIs que fazem parte da infraestrutura do Visual Studio.

 <xref:Microsoft.VisualStudio.Tools.Office.BuildTasks>

 Contém as classes de tarefa do MSBuild que são usadas para criar projetos do Office.

## <a name="see-also"></a>Consulte também
- [Visão geral do Visual Studio Tools for Office Runtime](visual-studio-tools-for-office-runtime-overview.md)
- [Introdução &#40;ao desenvolvimento do Office no Visual Studio&#41;](getting-started-office-development-in-visual-studio.md)
- [Exemplos e orientações de desenvolvimento do Office](office-development-samples-and-walkthroughs.md)
- [Projetar e criar soluções do Office](designing-and-creating-office-solutions.md)
