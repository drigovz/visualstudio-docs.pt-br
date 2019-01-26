---
title: Começar a programar personalizações no nível de documento para Word
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0b8ac2efc6627eae017c7154743091b7682dc8ac
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869194"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Começar a programar personalizações no nível de documento para Word
  Se você estiver apenas começando criar personalizações em nível de documento para o Microsoft Office Word usando o Visual Studio, aqui está o que você precisa saber.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## <a name="understand-how-document-level-customizations-for-word-work"></a>Entender as personalizações no nível do documento como para o trabalho do Word  
 Cada personalização do Word que você cria é baseada em torno de um único documento. Para começar a usar a personalização, o usuário final abre o documento ou cria o documento de um modelo do Word. Eventos no documento, por exemplo, mover o cursor para áreas específicas ou clicar em botões e itens de menu, podem chamar métodos de manipulação de eventos no assembly. Quando o documento é fechado, os recursos fornecidos pela personalização não estão mais disponíveis no Word.  
  
 Para obter mais informações, consulte [arquitetura de personalizações no nível do documento](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="create-document-level-projects-for-word"></a>Criar projetos de nível de documento para Word  
 Para criar uma personalização no nível de documento para Word, use o modelo de projeto de documento do Word ou o modelo do Word na **novo projeto** caixa de diálogo. Esses modelos incluem referências de assembly necessárias e os arquivos de projeto.  
  
 Para obter mais informações sobre como criar um projeto de nível de documento para Word, consulte [como: Criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Para obter mais informações sobre os modelos de projeto, consulte [visão geral de modelos de projeto do Office](../vsto/office-project-templates-overview.md).  
  
## <a name="program-word-documents-by-using-host-items-host-controls"></a>Documentos do Word programa por meio de controles de host de itens de host  
 *Itens de host* e *hospedar controles* são classes que fornecem o modelo de programação para personalizações no nível do documento.  
  
 Itens de host fornecem um ponto de entrada para seu código, e pode também atuam como contêineres para controles dos Windows Forms e controles de host. Em projetos de nível de documento para Word, o item de host é representado pelo `ThisDocument` classe.  
  
 Controles de host se baseiam em objetos nativos do Word, como controles de conteúdo, indicadores e nós XML. Controles de host fornecem funcionalidade semelhante aos objetos nativos do Word, mas também têm novos eventos, o suporte do designer e o recurso de vinculação de dados. Eles são exibidos como objetos de primeira classe no código do seu projeto e no IntelliSense, o que torna mais fácil para se referir a objetos específicos diretamente no seu código sem precisar navegar no modelo de objeto do Word.  
  
 Para mais informações, consulte os seguintes tópicos:  
  
-   [Personalizações em nível de documento do programa](../vsto/programming-document-level-customizations.md)  
  
-   [Automatizar o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [Visão geral dos controles de host e de itens de host](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customize-the-user-interface-of-word"></a>Personalizar a interface do usuário do Word  
 A maioria das soluções do Microsoft Office modificar a interface do usuário (IU) do aplicativo do Office para fornecer aos usuários interagir com a solução de alguma maneira. Há muitas maneiras em que você pode modificar a interface do usuário do Word por meio de uma personalização no nível de documento. Por exemplo, você pode adicionar controles à faixa de opções, e você pode exibir um painel de ações. Para obter mais informações, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).  
  
 Você também pode abrir o documento que está associado com seu projeto diretamente no Visual Studio. Quando o documento é aberto no Visual Studio, você pode modificar o documento usando a interface de usuário do Word. Você também pode usar o documento como uma superfície de design, que permite que você arrastar controles para ele. Para obter mais informações, consulte [projetos do Office no ambiente do Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="bind-controls-to-data"></a>Associar controles a dados  
 Os controles de conteúdo e o <xref:Microsoft.Office.Tools.Word.Bookmark> controle estão na lista de controles que você pode arrastar as **fontes de dados** janela. Adicionando controles de conteúdo e indicadores desta forma automaticamente associa-os à fonte de dados que você configurou usando a janela. Sem escrever nenhum código, você pode exibir dados de bancos de dados, serviços e objetos comerciais. Para obter mais informações, consulte [ligar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Próximas etapas  
 Para saber como criar uma personalização no nível de documento para Word, consulte [passo a passo: Criar a primeira personalização no nível de documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). Este passo a passo apresenta a você as ferramentas de desenvolvimento do Office no Visual Studio e o modelo de programação para personalizações de nível de documento do Word.  
  
 Para obter uma lista de tópicos que explicam a algumas das tarefas comuns em projetos do Word, consulte [tarefas comuns na programação do Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: Criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Personalizações em nível de documento do programa](../vsto/programming-document-level-customizations.md)   
 [Soluções do Word](../vsto/word-solutions.md)   
 [Passo a passo: Criar a primeira personalização no nível de documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [Instruções passo a passo usando o Word](../vsto/walkthroughs-using-word.md)   
 [Visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md)   
 [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)  
