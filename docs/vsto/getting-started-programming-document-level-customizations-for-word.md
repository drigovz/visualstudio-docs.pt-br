---
title: Introdução à programação de personalizações em nível de documento para o Word
titleSuffix: ''
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
ms.openlocfilehash: f4cf54dcdd08e7c44e8318973a3653dbe9c5ea1b
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585661"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Introdução à programação de personalizações em nível de documento para o Word
  Se você estiver apenas começando a criar personalizações em nível de documento para Microsoft Office Word usando o Visual Studio, aqui está o que você precisa saber.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-word-work"></a>Entenda como as personalizações no nível do documento para o Word Work
 Cada personalização de palavra que você cria baseia-se em um único documento. Para começar a usar a personalização, o usuário final abre o documento ou cria o documento a partir de um modelo do Word. Os eventos no documento, por exemplo, mover o cursor para áreas específicas ou clicar em botões e itens de menu, podem chamar métodos de manipulação de eventos no assembly. Quando o documento é fechado, os recursos fornecidos pela personalização não estão mais disponíveis no Word.

 Para obter mais informações, consulte [arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-word"></a>Criar projetos de nível de documento para o Word
 Para criar uma personalização em nível de documento para o Word, use o documento do Word ou modelo de projeto de modelo do Word na caixa de diálogo **novo projeto** . Esses modelos incluem referências de assembly e arquivos de projeto necessários.

 Para obter mais informações sobre como criar um projeto de nível de documento para o Word, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Para obter mais informações sobre os modelos de projeto, consulte [visão geral dos modelos do Office Project](../vsto/office-project-templates-overview.md).

## <a name="program-word-documents-by-using-host-items-host-controls"></a>Documentos do Word do programa usando itens de host controles de host
 Os *itens de host* e os controles de *host* são classes que fornecem o modelo de programação para personalizações em nível de documento.

 Os itens de host fornecem um ponto de entrada para seu código e também podem atuar como contêineres para controles de host e controles de Windows Forms. Em projetos de nível de documento para o Word, o item de host é representado pela `ThisDocument` classe.

 Os controles de host são baseados em objetos nativos do Word, como controles de conteúdo, indicadores e nós XML. Os controles de host fornecem funcionalidade semelhante aos objetos nativos do Word, mas também têm novos eventos, suporte ao designer e capacidade de vinculação de dados. Eles aparecem como objetos de primeira classe no código do projeto e no IntelliSense, o que torna mais fácil referir-se a objetos específicos diretamente em seu código sem precisar navegar pelo modelo de objeto do Word.

 Para obter mais informações, consulte estes tópicos:

- [Programar personalizações em nível de documento](../vsto/programming-document-level-customizations.md)

- [Automatizar o Word usando objetos estendidos](../vsto/automating-word-by-using-extended-objects.md)

- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-word"></a>Personalizar a interface do usuário do Word
 A maioria das soluções Microsoft Office modifica a interface do usuário do aplicativo do Office para fornecer algum modo para os usuários interagirem com a solução. Há muitas maneiras pelas quais você pode modificar a interface do usuário do Word usando uma personalização no nível do documento. Por exemplo, você pode adicionar controles à faixa de e pode exibir um painel Ações. Para obter mais informações, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).

 Você também pode abrir o documento associado ao seu projeto diretamente no Visual Studio. Quando o documento estiver aberto no Visual Studio, você poderá modificar o documento usando a interface do usuário do Word. Você também pode usar o documento como uma superfície de design, o que permite arrastar controles para ele. Para obter mais informações, consulte [projetos do Office no ambiente do Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="bind-controls-to-data"></a>Associar controles a dados
 Os controles de conteúdo e o <xref:Microsoft.Office.Tools.Word.Bookmark> controle estão na lista de controles que você pode arrastar da janela **fontes de dados** . Adicionar controles de conteúdo e indicadores dessa forma os associa automaticamente à fonte de dados que você configurou usando a janela. Sem escrever nenhum código, você pode exibir dados de bancos de dado, serviços e objetos de negócios. Para obter mais informações, consulte [associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Próximas etapas
 Para saber como criar uma personalização em nível de documento para o Word, consulte [passo a passos: criar sua primeira personalização em nível de documento para o Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). Este tutorial apresenta as ferramentas de desenvolvimento do Office no Visual Studio e o modelo de programação para personalizações em nível de documento do Word.

 Para obter uma lista de tópicos que orientam algumas das tarefas comuns em projetos do Word, consulte [tarefas comuns na programação do Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Confira também
- [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programar personalizações em nível de documento](../vsto/programming-document-level-customizations.md)
- [Soluções do Word](../vsto/word-solutions.md)
- [Walkthrough: criar sua primeira personalização em nível de documento para o Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
- [Passo a passos usando o Word](../vsto/walkthroughs-using-word.md)
- [Visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md)
- [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)
