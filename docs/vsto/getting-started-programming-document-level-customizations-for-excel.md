---
title: Começar a programar personalizações no nível de documento para Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 47762c781b24a31b90c75e5f8d9f0d00a6d3363d
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870133"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Começar a programar personalizações no nível de documento para Excel
  Se você estiver apenas começando criar personalizações em nível de documento do Microsoft Office Excel usando o Visual Studio, aqui está o que você precisa saber.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="understand-how-document-level-customizations-for-excel-work"></a>Entender as personalizações no nível do documento como para o trabalho do Excel  
 Uma personalização no nível de documento para Excel baseia-se em torno de uma única pasta de trabalho. Para começar a usar a personalização, o usuário final abre a pasta de trabalho ou cria a pasta de trabalho de um modelo do Excel. Eventos na pasta de trabalho, por exemplo, digitando nas células ou clicar em botões e itens de menu, podem chamar métodos de manipulação de eventos no assembly. Quando a pasta de trabalho é fechada, os recursos fornecidos pela personalização não estão mais disponíveis no Excel, somente no documento que continha.  
  
 Para obter mais informações, consulte [arquitetura de personalizações no nível do documento](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="create-document-level-projects-for-excel"></a>Criar projetos de nível de documento para Excel  
 Para criar uma personalização no nível de documento para Excel, use o modelo de projeto de modelo do Excel ou de pasta de trabalho do Excel na **novo projeto** caixa de diálogo. Esses modelos incluem referências de assembly necessárias e os arquivos de projeto.  
  
 Para obter mais informações sobre como criar um projeto de nível de documento para Excel, consulte [como: Criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Para obter mais informações sobre os modelos de projeto, consulte [visão geral de modelos de projeto do Office](../vsto/office-project-templates-overview.md).  
  
## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Pastas de trabalho do programa Excel usando itens de host e controles de host  
 *Itens de host* e *hospedar controles* são classes que fornecem o modelo de programação para personalizações no nível do documento criadas usando o Visual Studio.  
  
 Itens de host fornecem um ponto de entrada para seu código, e pode também atuam como contêineres para controles dos Windows Forms e controles de host. Em projetos de nível de documento para Excel, esses itens de host são representados pela `ThisWorkbook`, `Sheet1`, `Sheet2`, e `Sheet3` classes.  
  
 Controles de host se baseiam em objetos nativos do Excel, como objetos de lista e intervalos. Controles de host fornecem funcionalidade semelhante aos objetos nativos do Excel, mas também têm novos eventos, o suporte do designer e o recurso de associação de dados. Eles são exibidos como objetos de primeira classe no código do seu projeto e no IntelliSense, o que torna mais fácil para se referir a objetos específicos diretamente no seu código sem precisar navegar no modelo de objeto do Excel.  
  
 Para mais informações, consulte os seguintes tópicos:  
  
-   [Personalizações em nível de documento do programa](../vsto/programming-document-level-customizations.md)  
  
-   [Automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [Visão geral dos controles de host e de itens de host](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customize-the-user-interface-of-excel"></a>Personalizar a interface do usuário do Excel  
 A maioria das soluções do Microsoft Office modificar a interface do usuário (IU) do aplicativo do Office para fornecer aos usuários interagir com a solução de alguma maneira. Há muitas maneiras em que você pode modificar a interface do usuário do Excel usando uma personalização no nível de documento. Por exemplo, você pode adicionar controles à faixa de opções, ou você pode exibir um painel de ações. Para obter mais informações, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).  
  
 Você também pode abrir a pasta de trabalho que está associada com seu projeto diretamente no Visual Studio. Quando a pasta de trabalho é aberta no Visual Studio, você pode modificar a pasta de trabalho usando a interface de usuário do Excel. Você também pode usar a pasta de trabalho como uma superfície de design, que permite que você arraste os controles em planilhas. Para obter mais informações, consulte [projetos do Office no ambiente do Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="use-data-binding"></a>Usar associação de dados  
 Os controles de host também estão na lista de controles que você pode arrastar o **fontes de dados** janela. Adicionar controles de host desta forma automaticamente associa-os à fonte de dados que você configurou usando a janela. Sem escrever nenhum código, você pode exibir dados de bancos de dados, web services e objetos de negócios. Para obter mais informações, consulte [ligar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Próximas etapas  
 Para saber como criar uma personalização no nível de documento para Excel, consulte [passo a passo: Criar a primeira personalização no nível de documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). Este passo a passo apresenta a você as ferramentas de desenvolvimento do Office no Visual Studio e o modelo de programação para personalizações no nível de documento do Excel.  
  
 Para obter uma lista de tópicos que explicam a algumas das tarefas comuns em projetos do Excel, consulte [tarefas comuns na programação do Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: Criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Personalizações em nível de documento do programa](../vsto/programming-document-level-customizations.md)   
 [Soluções do Excel](../vsto/excel-solutions.md)   
 [Passo a passo: Criar a primeira personalização no nível de documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Instruções passo a passo usando o Excel](../vsto/walkthroughs-using-excel.md)   
 [Visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md)   
 [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)  
