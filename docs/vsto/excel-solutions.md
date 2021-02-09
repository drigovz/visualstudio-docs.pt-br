---
title: Soluções do Excel
description: Saiba que você pode usar modelos de projeto para automatizar o Excel, estender recursos do Excel e personalizar a interface do usuário do Excel
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], application-level add-ins
- Office solutions [Office development in Visual Studio], Excel
- solutions [Office development in Visual Studio], Excel
- add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], about Excel solutions
- Excel [Office development in Visual Studio]
- documents [Office development in Visual Studio], Excel
- Office documents [Office development in Visual Studio, Excel
- projects [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Excel
- Office development in Visual Studio, Excel solutions
- document-level customizations [Office development in Visual Studio], Excel
- Office projects [Office development in Visual Studio], Excel
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3833ff549b2cceb3f783afc43a4f71dacc00ecb0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931273"
---
# <a name="excel-solutions"></a>Soluções do Excel
  O Visual Studio fornece modelos de projeto que você pode usar para criar personalizações em nível de documento e suplementos do VSTO para o Microsoft Office Excel. Você pode usar essas soluções para automatizar o Excel, estender recursos do Excel e personalizar a interface do usuário do Excel. Para obter mais informações sobre as diferenças entre as personalizações em nível de documento e os suplementos do VSTO, consulte [visão geral do desenvolvimento de soluções do Office &#40;&#41;do VSTO ](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Este tópico fornece as seguintes informações:

- [Automatize o Excel](#automating).

- [Desenvolva personalizações em nível de documento para o Excel](#doclevel).

- [Desenvolva suplementos do VSTO para Excel](#applevel).

- [Personalize a interface do usuário do Excel](#UI).

## <a name="automate-excel"></a><a name="automating"></a> Automatizar o Excel
 O modelo de objeto do Excel expõe muitos tipos que você pode usar para automatizar o Excel. Por exemplo, você pode criar gráficos programaticamente, Formatar planilhas e definir os valores de intervalos e células. Para obter mais informações, consulte [visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md).

 Ao desenvolver soluções do Excel no Visual Studio, você também pode usar *itens de host* e controles de *host* em suas soluções. Esses são objetos que estendem determinados objetos comumente usados no modelo de objeto do Excel, como os <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Range> objetos e. Os objetos estendidos se comportam como os objetos do Excel em que se baseiam, mas adicionam eventos adicionais e recursos de associação de dados aos objetos. Para obter mais informações, consulte [automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md).

## <a name="develop-document-level-customizations-for-excel"></a><a name="doclevel"></a> Desenvolver personalizações em nível de documento para o Excel
 Uma personalização em nível de documento para Microsoft Office Excel consiste em um assembly associado a uma pasta de trabalho específica. O assembly normalmente estende a pasta de trabalho Personalizando a interface do usuário e automatizando o Excel. Ao contrário de um suplemento do VSTO, que está associado ao próprio Excel, a funcionalidade que você implementa em uma personalização está disponível somente quando a pasta de trabalho associada está aberta no Excel.

 Para criar um projeto de personalização no nível do documento para o Excel, use a pasta de trabalho do Excel ou modelos de projeto de modelo do Excel na caixa de diálogo **novo projeto** do Visual Studio. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Para obter mais informações sobre como funcionam as personalizações em nível de documento, consulte [arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md).

### <a name="excel-customization-programming-model"></a>Modelo de programação de personalização do Excel
 Quando você cria um projeto de nível de documento para o Excel, o Visual Studio gera várias classes que são a base de sua solução: `ThisWorkbook` ,, `Sheet1` `Sheet2` e `Sheet3` . Essas classes representam a pasta de trabalho e planilhas associadas à sua solução e fornecem um ponto de partida para escrever seu código.

 Para obter mais informações sobre essas classes geradas e outros recursos que você pode usar em um projeto de nível de documento, consulte [programar personalizações em nível de documento](../vsto/programming-document-level-customizations.md).

## <a name="develop-vsto-add-ins-for-excel"></a><a name="applevel"></a> Desenvolver suplementos do VSTO para Excel
 Um suplemento do VSTO para Microsoft Office Excel consiste em um assembly que é carregado pelo Excel. O assembly normalmente estende o Excel Personalizando a interface do usuário e automatizando o Excel. Ao contrário de uma personalização em nível de documento, que é associada a uma pasta de trabalho específica, a funcionalidade implementada em um suplemento do VSTO não é restrita a nenhuma pasta de trabalho única.

 Para criar um projeto de suplemento do VSTO para Excel, use a pasta de trabalho do Excel ou modelos de projeto de modelo do Excel na caixa de diálogo **novo projeto** do Visual Studio. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Para obter informações gerais sobre como funcionam os suplementos do VSTO, consulte [arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md).

### <a name="excel-add-in-programming-model"></a>Modelo de programação de suplemento do Excel
 Quando você cria um projeto de suplemento do VSTO do Excel, o Visual Studio gera uma classe, chamada `ThisAddIn` , que é a base da sua solução. Essa classe fornece um ponto de partida para escrever seu código e também expõe o modelo de objeto do Excel para seu suplemento do VSTO.

 Para obter mais informações sobre a `ThisAddIn` classe e outros recursos do Visual Studio que você pode usar em um suplemento do VSTO, consulte [programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md).

## <a name="customize-the-user-interface-of-excel"></a><a name="UI"></a> Personalizar a interface do usuário do Excel
 Há várias maneiras diferentes de personalizar a interface do usuário do Excel. Algumas opções estão disponíveis para todos os tipos de projeto e outras opções estão disponíveis somente para suplementos do VSTO ou personalizações em nível de documento.

### <a name="options-for-all-project-types"></a>Opções para todos os tipos de projeto
 A tabela a seguir lista as opções de personalização disponíveis para as personalizações no nível do documento e os suplementos do VSTO.

|Tarefa|Para obter mais informações|
|----------|--------------------------|
|Personalize a faixa de faixas.|[Visão geral da faixa de faixas](../vsto/ribbon-overview.md)|
|Adicione controles de Windows Forms ou controles estendidos do Excel a uma planilha na pasta de trabalho personalizada para uma personalização em nível de documento ou em qualquer pasta de trabalho aberta para um suplemento do VSTO.|[Como: adicionar controles do Windows Forms a documentos do Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Como: adicionar controles de gráfico a planilhas](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Como adicionar controles ListObject a planilhas](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Como: adicionar controles NamedRange a planilhas](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|

### <a name="options-for-document-level-customizations"></a>Opções para personalizações em nível de documento
 A tabela a seguir lista as opções de personalização disponíveis apenas para personalizações em nível de documento.

|Tarefa|Para obter mais informações|
|----------|--------------------------|
|Adicione um painel Ações à pasta de trabalho.|[Visão geral do painel Ações](../vsto/actions-pane-overview.md)<br /><br /> [Como: adicionar um painel de ações a documentos do Word ou a pastas de trabalho do Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|Adicione controles de intervalo estendidos que são mapeados para nós XML para uma planilha.|[Como: adicionar controles XMLMappedRange a planilhas](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|

### <a name="options-for-vsto-add-ins"></a>Opções para suplementos do VSTO
 A tabela a seguir lista as opções de personalização disponíveis apenas para os suplementos do VSTO.

|Tarefa|Para obter mais informações|
|----------|--------------------------|
|Crie um painel de tarefas personalizado.|[Painéis de tarefas personalizados](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>Tópicos relacionados

| Title | Descrição |
| - | - |
| [Visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md) | Fornece uma visão geral dos tipos principais fornecidos pelo modelo de objeto do Excel. |
| [Automatizar o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md) | Fornece informações sobre objetos estendidos (fornecidos pelo [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ) que você pode usar em soluções do Excel. |
| [Globalização e localização de soluções do Excel](../vsto/globalization-and-localization-of-excel-solutions.md) | Contém informações sobre considerações especiais para soluções do Excel que serão executadas em computadores com configurações diferentes do inglês para o Windows. |
| [Visão geral dos controles de Windows Forms em documentos do Office](../vsto/windows-forms-controls-on-office-documents-overview.md) | Descreve como você pode adicionar controles de Windows Forms a planilhas do Excel. |
| [Walkthrough: criar sua primeira personalização em nível de documento para o Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md) | Demonstra como criar uma personalização básica no nível do documento para o Excel. |
| [Walkthrough: criar seu primeiro suplemento do VSTO para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md) | Demonstra como criar um suplemento do VSTO básico para Excel. |
| [Walkthrough: adicionar controles a uma planilha em tempo de execução no projeto de suplemento do VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) | Demonstra como adicionar um botão de Windows Forms, um <xref:Microsoft.Office.Tools.Excel.NamedRange> e um <xref:Microsoft.Office.Tools.Excel.ListObject> a uma planilha em tempo de execução usando um suplemento do VSTO. |
| [Entender a coautoria e os suplementos](./understanding-coauthoring-and-addins.md) | Descreve os ajustes que talvez você precise fazer em suas soluções para acomodar a coautoria. |
| [Excel 2010 no desenvolvimento do Office](/previous-versions/office/developer/office-2010/ee658205(v=office.14)) | Fornece links para artigos e documentação de referência sobre como desenvolver soluções do Excel. Eles não são específicos do desenvolvimento do Office usando o Visual Studio. |
