---
title: Referência gerenciada (desenvolvimento do Office no Visual Studio)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reference [Office development in Visual Studio], 2007 Microsoft Office system
- Office development in Visual Studio, reference
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 96737b2c5ad7196df873f38b87a6cdd6f11dc10b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865226"
---
# <a name="managed-reference-office-development-in-visual-studio"></a>Referência gerenciada (desenvolvimento do Office no Visual Studio)
  Esta seção contém documentação de referência de API para namespaces e tipos que são usados no Office projetos que se destinam a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Para obter a documentação de referência de API sobre os namespaces e tipos que são usados em projetos do Office destinados ao .NET Framework 3.5, consulte a seguinte seção de referência na documentação do Visual Studio: [ http://go.microsoft.com/fwlink/?LinkId=160658 ](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
> [!NOTE]  
>  Interessado em desenvolver soluções que estendem a experiência do Office em toda [várias plataformas](https://dev.office.com/add-in-availability)? Confira a nova [modelo de suplementos do Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Suplementos do Office têm uma superfície pequena em comparação com soluções e suplementos do VSTO, e você pode criá-los usando quase qualquer tecnologia, como HTML5, JavaScript, CSS3 e XML de programação da web.  
  
## <a name="in-this-section"></a>Nesta seção  
 <xref:Microsoft.Office.Tools>  
 Contém classes comuns à programação de soluções do Office. Isso inclui a classe base para suplementos do VSTO, classes para criar painéis de tarefas personalizados nos suplementos do VSTO, classes para a criação de marcas inteligentes em soluções do Excel e Word e classes para criar painéis de ações em personalizações no nível do documento.  
  
 <xref:Microsoft.Office.Tools.Excel>  
 Contém os controles de host e itens de host que podem ser usados em soluções para o Excel.  
  
 <xref:Microsoft.Office.Tools.Excel.Controls>  
 Contém controles do Excel e controles de formulários do Windows que podem ser usados em soluções para o Excel.  
  
 <xref:Microsoft.Office.Tools.Outlook>  
 Contém classes usadas pelos suplementos do VSTO para Outlook, incluindo classes que são usadas para criar regiões de formulário personalizadas.  
  
 <xref:Microsoft.Office.Tools.Ribbon>  
 Contém classes que são usadas para modificar programaticamente as personalizações da faixa de opções criadas usando o designer de faixa de opções.  
  
 <xref:Microsoft.Office.Tools.Word>  
 Contém os controles de host e itens de host que podem ser usados em soluções para o Word.  
  
 <xref:Microsoft.Office.Tools.Word.Controls>  
 Contém controles do Word e controles de formulários do Windows que podem ser usados em soluções para o Word.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications>  
 Contém o <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe e um conjunto de relacionadas as classes de dados armazenados em cache. Essas classes podem ser usadas para modificar alguns aspectos de personalizações no nível do documento em computadores que não têm o Microsoft Office instalado.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment>  
 Contém o <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> interface (que você pode implementar para criar um *lançar a ação de implantação* para uma solução do Office), as exceções que podem ser geradas durante a instalação de uma solução do Office e outras APIs que fazem parte do Visual Infraestrutura do Studio.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime>  
 Contém a maioria das exceções que podem ser lançadas pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], várias classes que podem ser usado para dados em cache em personalizações no nível de documento e outras APIs que fazem parte da infraestrutura do Visual Studio.  
  
 <xref:Microsoft.VisualStudio.Tools.Office.BuildTasks>  
 Contém classes de tarefa do MSBuild que são usadas para compilar projetos do Office.  
  
## <a name="see-also"></a>Consulte também  
 [Visual Studio tools para Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Introdução ao &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Instruções passo a passo e exemplos de desenvolvimento do office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)  
