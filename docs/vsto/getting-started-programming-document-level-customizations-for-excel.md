---
title: 'Excel: introdução à programação de personalizações em nível de documento'
description: Saiba o que você precisa saber para começar a criar personalizações em nível de documento para Microsoft Office Excel usando o Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
ms.openlocfilehash: 1fb048fd015126e5438a007be1950cddffbac9e1
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846032"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Introdução à programação de personalizações em nível de documento para o Excel
  Se você estiver apenas começando a criar personalizações em nível de documento para Microsoft Office Excel usando o Visual Studio, aqui está o que você precisa saber.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-excel-work"></a>Entenda como as personalizações no nível do documento para o Excel funcionam
 Uma personalização no nível do documento para o Excel baseia-se em uma única pasta de trabalho. Para começar a usar a personalização, o usuário final abre a pasta de trabalho ou cria a pasta de trabalho a partir de um modelo do Excel. Os eventos na pasta de trabalho, por exemplo, digitando em células ou clicando em botões e itens de menu, podem chamar métodos de manipulação de eventos no assembly. Quando a pasta de trabalho é fechada, os recursos fornecidos pela personalização não estão mais disponíveis no Excel, somente no documento que as continha.

 Para obter mais informações, consulte [arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-excel"></a>Criar projetos de nível de documento para o Excel
 Para criar uma personalização em nível de documento para o Excel, use a pasta de trabalho do Excel ou o modelo de projeto de modelo do Excel na caixa de diálogo **novo projeto** . Esses modelos incluem referências de assembly e arquivos de projeto necessários.

 Para obter mais informações sobre como criar um projeto de nível de documento para o Excel, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Para obter mais informações sobre os modelos de projeto, consulte [visão geral dos modelos do Office Project](../vsto/office-project-templates-overview.md).

## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Programar pastas de trabalho do Excel usando itens de host e controles de host
 Os *itens de host* e os controles de *host* são classes que fornecem o modelo de programação para personalizações em nível de documento criadas usando o Visual Studio.

 Os itens de host fornecem um ponto de entrada para seu código e também podem atuar como contêineres para controles de host e controles de Windows Forms. Em projetos de nível de documento para Excel, esses itens de host são representados pelas `ThisWorkbook` `Sheet1` classes,, `Sheet2` e `Sheet3` .

 Os controles de host são baseados em objetos nativos do Excel, como os intervalos e objetos de lista. Os controles de host fornecem funcionalidade semelhante aos objetos nativos do Excel, mas também têm novos eventos, suporte ao designer e capacidade de vinculação de dados. Eles aparecem como objetos de primeira classe no código do projeto e no IntelliSense, o que torna mais fácil referir-se a objetos específicos diretamente em seu código sem precisar navegar pelo modelo de objeto do Excel.

 Para mais informações, consulte os seguintes tópicos:

- [Programar personalizações em nível de documento](../vsto/programming-document-level-customizations.md)

- [Automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)

- [Visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-excel"></a>Personalizar a interface do usuário do Excel
 A maioria das soluções Microsoft Office modifica a interface do usuário do aplicativo do Office para fornecer algum modo para os usuários interagirem com a solução. Há muitas maneiras pelas quais você pode modificar a interface do usuário do Excel usando uma personalização no nível do documento. Por exemplo, você pode adicionar controles à faixa de faixas ou pode exibir um painel Ações. Para obter mais informações, consulte [personalização da interface do usuário do Office](../vsto/office-ui-customization.md).

 Você também pode abrir a pasta de trabalho que está associada ao seu projeto diretamente no Visual Studio. Quando a pasta de trabalho estiver aberta no Visual Studio, você poderá modificar a pasta de trabalho usando a interface do usuário do Excel. Você também pode usar a pasta de trabalho como uma superfície de design, que permite arrastar controles para planilhas. Para obter mais informações, consulte [projetos do Office no ambiente do Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="use-data-binding"></a>Usar Associação de dados
 Os controles de host também estão na lista de controles que você pode arrastar da janela **fontes de dados** . Adicionar controles de host dessa maneira os associa automaticamente à fonte de dados que você configurou usando a janela. Sem escrever nenhum código, você pode exibir dados de bancos de dado, serviços Web e objetos comerciais. Para obter mais informações, consulte [associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Próximas etapas
 Para saber como criar uma personalização em nível de documento para o Excel, consulte [passo a passos: criar sua primeira personalização em nível de documento para o Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). Este tutorial apresenta as ferramentas de desenvolvimento do Office no Visual Studio e o modelo de programação para personalizações em nível de documento do Excel.

 Para obter uma lista de tópicos que orientam algumas das tarefas comuns em projetos do Excel, consulte [tarefas comuns na programação do Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Confira também
- [Como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programar personalizações em nível de documento](../vsto/programming-document-level-customizations.md)
- [Soluções do Excel](../vsto/excel-solutions.md)
- [Walkthrough: criar sua primeira personalização em nível de documento para o Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Passo a passos usando o Excel](../vsto/walkthroughs-using-excel.md)
- [Visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md)
- [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)
