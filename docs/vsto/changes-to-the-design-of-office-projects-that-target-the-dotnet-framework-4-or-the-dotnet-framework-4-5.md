---
title: Alterações de design em projetos do Office direcionados .NET Framework
description: Saiba mais sobre as alterações introduzidas no Visual Studio para o design de projetos do Office direcionados para o .NET Framework 4 ou posterior.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio 2010, what's new
- what's new [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2bb8f6064bd2c2df55c7d0cf8fea1e25c513da0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903788"
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>Alterações no design de projetos do Office direcionados para o .NET Framework 4 ou o .NET Framework 4,5
  A partir do [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] , o Visual Studio introduziu algumas alterações no design de projetos do Office direcionados para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior. Se você estiver familiarizado com projetos do Office em versões anteriores do Visual Studio, deve estar ciente dessas alterações antes de desenvolver projetos do Office direcionados a essas versões do .NET Framework 4,0 ou posterior. Por padrão, todos os projetos que você cria usando o Visual Studio 2013 ou posterior direcionam o .NET Framework 4,0 ou posterior.

 As seções a seguir descrevem essas alterações de design do Office Project.

## <a name="understand-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Entenda o design baseado em interface do tempo de execução das ferramentas do Visual Studio 2010 para Office
 Quando você desenvolve um projeto do Office direcionado [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] para o ou posterior, a maioria dos tipos que você usa no Visual Studio 2010 Tools for Office Runtime são interfaces. Essa é uma alteração importante das versões anteriores do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , onde esses tipos são classes. Por exemplo, quando você direciona o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, os <xref:Microsoft.Office.Tools.Excel.Worksheet> <xref:Microsoft.Office.Tools.Word.Document> tipos e são interfaces em vez de classes. Para obter mais informações, consulte [visão geral do ferramentas do Visual Studio para Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

 Para qualquer tipo que você possa instanciar diretamente nas versões anteriores do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , agora você usa métodos do `Globals.Factory` objeto para obter instâncias desses tipos. Por exemplo, para obter um objeto que implemente a interface <xref:Microsoft.Office.Tools.Excel.SmartTag>, use o método `Globals.Factory.CreateSmartTag`. Para mais informações, consulte os seguintes tópicos:

- [Atualize os projetos do Excel e do Word que você migra para o .NET Framework 4 ou o .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Atualize as personalizações da faixa de na de projetos do Office que você migra para o .NET Framework 4 ou o .NET Framework 4,5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [Atualize as regiões de formulário nos projetos do Outlook que você migra para o .NET Framework 4 ou o .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

### <a name="new-base-classes-in-office-projects"></a>Novas classes base em projetos do Office
 O novo design baseado em interface do Visual Studio 2010 Tools for Office Runtime afeta as classes geradas em projetos do Office, como `ThisDocument` , `ThisWorkbook` e `ThisAddIn` . Em projetos do Office que visam o .NET Framework 3,5 e as versões anteriores do Framework, essas classes geradas derivam de classes no, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] como, `Microsoft.Office.Tools.Word.Document` `Microsoft.Office.Tools.Excel.Worksheet` e `Microsoft.Office.Tools.AddIn` . Em projetos direcionados para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, essas [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] classes agora são interfaces. Portanto, as classes geradas em projetos do Office não podem mais derivar sua implementação deles. Em vez disso, as classes geradas derivam de novas classes base, como <xref:Microsoft.Office.Tools.Word.DocumentBase> , <xref:Microsoft.Office.Tools.Excel.WorksheetBase> e <xref:Microsoft.Office.Tools.AddInBase> . Para obter mais informações, consulte [programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md) e [programar personalizações em nível de documento](../vsto/programming-document-level-customizations.md).

 As classes base não fazem parte do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] redistribuível. Em vez disso, eles são definidos em assemblies de utilitários incluídos no Visual Studio. Esses assemblies são copiados para a pasta de saída quando você cria projetos do Office e deve ser implantado com sua solução. Para obter mais informações sobre os assemblies de utilitários, consulte [assemblies no ferramentas do Visual Studio para o tempo de execução do Office](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).

## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>Alterações significativas em projetos do Office que são redirecionados para o .NET Framework 4
 A tabela a seguir lista as principais alterações que você pode encontrar em projetos do Office que são redirecionados para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior. Para obter mais detalhes, consulte [migrar soluções do Office para o .NET Framework 4 ou posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

|Alteração interruptiva|Consequência|
|---------------------|-----------------|
|O <xref:System.Security.SecurityTransparentAttribute> não é mais usado nem tem suporte em projetos do Office.|Você deve remover esse atributo do arquivo de código AssemblyInfo em projetos do Office que você atualiza do Visual Studio 2008. Para obter mais informações, consulte [as alterações necessárias para executar projetos do Office que você migra para o .NET Framework 4 ou o .NET Framework 4,5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|O **ExcelLocale1033Attribute** não é mais usado ou tem suporte em projetos do Excel.|Você deve remover esse atributo do arquivo de código *AssemblyInfo* em projetos do Excel. Para obter mais informações, consulte [Atualizar projetos do Excel e do Word que você migra para o .NET Framework 4 ou o .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|O modelo de programação dos itens de projeto da **faixa de Ribbon (Visual Designer)** foi alterado.|Você deve modificar o arquivo code-behind para qualquer item da faixa de bits em seu projeto. Você também deve modificar qualquer código que instancie os controles da faixa de forma em tempo de execução, manipule os eventos da faixa de forma ou defina a posição de um componente da faixa de medida programaticamente. Para obter mais informações, consulte [atualizar as personalizações da faixa de forma em projetos do Office que você migra para o .NET Framework 4 ou o .NET Framework 4,5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md).|
|O modelo de programação das regiões de formulário do Outlook foi alterado.|Você deve modificar o arquivo code-behind para qualquer região de formulário em seu projeto e qualquer código que instancie determinadas classes de região de formulário em tempo de execução. Para obter mais informações, consulte [atualizar regiões de formulário em projetos do Outlook que você migra para o .NET Framework 4 ou o .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|O modelo de programação para marcas inteligentes no Excel e em projetos do Word foi alterado. As marcas inteligentes foram preteridas no [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] e [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Se sua solução usar marcas inteligentes, ocorrerão erros quando você compilar o projeto. Como as marcas inteligentes são preteridas no [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] e no [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] , você deve remover as marcas antes de poder testar e depurar a solução no [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] ou posterior.|
|A sintaxe dos `GetVstoObject` métodos e `HasVstoObject` foi alterada|Você deve passar o `Globals.Factory` objeto para esses métodos ao acessá-los em objetos nativos dos pias (assemblies de interoperabilidade) primários, ou pode acessar esses métodos no objeto que é retornado pela `Globals.Factory` propriedade em seu projeto. Para obter mais informações, consulte [Atualizar projetos do Excel e do Word que você migra para o .NET Framework 4 ou o .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|Os eventos dos controles de conteúdo do Word estão associados a novos delegados.|Você deve modificar qualquer código que manipule eventos de controles de conteúdo do Word para especificar os novos delegados. Para obter mais informações, consulte [Atualizar projetos do Excel e do Word que você migra para o .NET Framework 4 ou o .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|As `OLEObject` classes e foram `OLEControl` renomeadas.|Você deve modificar qualquer código que use instâncias dessas classes para usar <xref:Microsoft.Office.Tools.Excel.ControlSite> ou <xref:Microsoft.Office.Tools.Word.ControlSite> objetos. Para obter mais informações, consulte [Atualizar projetos do Excel e do Word que você migra para o .NET Framework 4 ou o .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).|
|As classes de item de host, como `ThisWorkbook` `Sheet` *n*, `ThisDocument` e `ThisAddIn` não fornecem mais um `Dispose` método que você pode substituir.|Você deve mover qualquer código no `Dispose` método override para o `Shutdown` manipulador de eventos na classe de item de host, por exemplo, `ThisAddIn_Shutdown` e remover a `Dispose` substituição do método da classe de item de host.|

## <a name="see-also"></a>Confira também
- [Migrar soluções do Office para o .NET Framework 4 ou posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [O que há de novo no desenvolvimento do Office](/previous-versions/86bkz018(v=vs.110))
- [Visão geral do Ferramentas do Visual Studio para Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)