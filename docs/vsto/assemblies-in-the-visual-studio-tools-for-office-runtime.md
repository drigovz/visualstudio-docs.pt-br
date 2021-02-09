---
title: Assemblies no Ferramentas do Visual Studio para o tempo de execução do Office
description: Saiba que o Visual Studio adiciona automaticamente referências ao Ferramentas do Visual Studio para assemblies de tempo de execução do Office.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 600408231e5085009e5edc546535ca8e5110fc6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882551"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Assemblies no Ferramentas do Visual Studio para o tempo de execução do Office
  Quando você cria um projeto do Office, o Visual Studio adiciona automaticamente referências aos [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] assemblies que são usados para o tipo de projeto e o .NET Framework de destino do projeto. Há diferentes assemblies nas extensões do Office para o .NET Framework 3,5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e [!INCLUDE[net_v45](includes/net-v45-md.md)] . Para obter mais informações sobre as extensões do Office, consulte [visão geral do ferramentas do Visual Studio for Office Runtime](visual-studio-tools-for-office-runtime-overview.md).

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-net_v45"></a>Assemblies nas extensões do Office para o .NET Framework 4 e o [!INCLUDE[net_v45](includes/net-v45-md.md)]
 A tabela a seguir lista os assemblies incluídos nas extensões do Office para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e o [!INCLUDE[net_v45](includes/net-v45-md.md)] . Para obter a documentação sobre os namespaces e tipos nesses assemblies, consulte [referência gerenciada &#40;desenvolvimento do Office no Visual Studio&#41;](managed-reference-office-development-in-visual-studio.md).

|Nome do assembly|Descrição|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.dll|O fornece os seguintes tipos:<br /><br /> -Tipos para criação de personalizações da faixa de tipos e marcas inteligentes. **Observação:**      Marcas inteligentes são preteridas no [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] e no [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />-Tipos para a criação de painéis de ações em personalizações em nível de documento e painéis de tarefas personalizados em suplementos do VSTO.|
|Microsoft.Office.Tools.Excel.dll|Fornece interfaces que representam itens de host e controles de host para projetos do Excel e tipos de suporte. Para obter mais informações, consulte [automatizar o Excel usando objetos estendidos](automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.dll|Fornece tipos que você pode usar para criar regiões de formulário personalizadas nos suplementos do VSTO do Outlook.|
|Microsoft.Office.Tools.Word.dll|Fornece interfaces que representam itens de host e controles de host para projetos do Word e tipos de suporte. Para obter mais informações, consulte [automatizar o Word usando objetos estendidos](automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v4.0.Framework.dll|O fornece os seguintes tipos:<br /><br /> -Exceções que podem ser geradas pelo Ferramentas do Visual Studio para o tempo de execução do Office.<br />-Atributos que você pode usar ao criar regiões de formulário do Outlook.|
|Microsoft.Office.Tools.dll|Fornece tipos que fazem parte do Ferramentas do Visual Studio para a infraestrutura de tempo de execução do Office e não se destinam a serem usados diretamente do seu código.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|O fornece os seguintes tipos:<br /><br /> -O <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributo e a <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interface, que você pode usar para armazenar em cache objetos de dados em uma personalização em nível de documento. Para obter mais informações, consulte [armazenar dados em cache](caching-data.md).<br />-A <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> interface, que pode ser implementada para executar etapas de instalação adicionais como a etapa final do instalador do ClickOnce para uma solução do Office. Para obter mais informações, consulte [implantar uma solução do Office usando o ClickOnce](deploying-an-office-solution-by-using-clickonce.md).<br />-Exceções que podem ser geradas pelo Ferramentas do Visual Studio para o tempo de execução do Office.<br />-Outros tipos que fazem parte do Ferramentas do Visual Studio para a infraestrutura de tempo de execução do Office e não se destinam a serem usados diretamente do seu código.|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|O fornece os seguintes tipos:<br /><br /> -A <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe, que você pode usar para anexar assemblies de personalização a documentos e acessar os dados armazenados em cache em documentos. Para obter mais informações, consulte [gerenciar documentos em um servidor usando a classe ServerDocument](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Várias classes que representam a hierarquia de dados armazenados em cache em uma personalização em nível de documento. Para obter mais informações, consulte [acessar dados em documentos no servidor](accessing-data-in-documents-on-the-server.md).|

 Projetos que visam o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou o [!INCLUDE[net_v45](includes/net-v45-md.md)] também referenciam os seguintes assemblies. Esses assemblies não fazem parte do [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] redistribuível. Em vez disso, eles são assemblies dependentes que devem ser implantados com sua solução. Por padrão, eles são copiados para a pasta de saída de compilação do seu projeto (a propriedade **Copy local** para esses assemblies é definida como **true**). Se você implantar seu projeto usando o ClickOnce, esses assemblies serão incluídos no pacote gerado.

|Nome do assembly|Descrição|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|Fornece as classes base para a `ThisAddIn` classe gerada no VSTO Add-In projetos e a classe da faixa de Ribbon gerada em todos os projetos.|
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|O fornece os seguintes tipos:<br /><br /> -Classes base para as classes geradas `ThisWorkbook` e `Sheet` em projetos de nível de documento para Excel.<br />-Windows Forms controles que você pode usar em planilhas em projetos do Excel.|
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Fornece classes base para as `ThisAddIn` classes de região gerada e de formulário nos projetos do Outlook.|
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|O fornece os seguintes tipos:<br /><br /> -Classes base para a `ThisDocument` classe gerada em projetos de nível de documento para o Word.<br />-Windows Forms controles que você pode usar em documentos em projetos do Word.|

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>Assemblies nas extensões do Office para o .NET Framework 3,5
 A tabela a seguir lista os assemblies que estão incluídos nas extensões do Office para o .NET Framework 3,5. Para obter a documentação sobre os namespaces e as classes nesses assemblies, consulte a seção de referência a seguir na documentação do Visual Studio 2008: [http://go.microsoft.com/fwlink/?LinkId=160658](managed-reference-office-development-in-visual-studio.md) .

|Nome do assembly|Descrição|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v9.0.dll|O fornece os seguintes tipos:<br /><br /> -A classe base Microsoft. Office. Tools. AddIn para os suplementos do VSTO.<br />-Classes para criação de personalizações da faixa de e de marcas inteligentes. **Observação:**      Marcas inteligentes são preteridas no [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] e no [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />-Classes para a criação de painéis de ações em personalizações em nível de documento e painéis de tarefas personalizados em suplementos do VSTO.|
|Microsoft.Office.Tools.Excel.v9.0.dll|Fornece itens de host e controles de host para soluções do Excel. Para obter mais informações, consulte [automatizar o Excel usando objetos estendidos](automating-excel-by-using-extended-objects.md).|
|Microsoft.Office.Tools.Outlook.v9.0.dll|Fornece classes que você pode usar para criar regiões de formulário personalizadas nos suplementos do VSTO do Outlook.|
|Microsoft.Office.Tools.Word.v9.0.dll|Fornece itens de host e controles de host para soluções do Word. Para obter mais informações, consulte [automatizar o Word usando objetos estendidos](automating-word-by-using-extended-objects.md).|
|Microsoft.Office.Tools.v9.0.dll|O fornece os seguintes tipos:<br /><br /> -A classe [RemoteBindableComponent](/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) , que fornece os recursos de vinculação de dados para controles de host em personalizações em nível de documento.<br />-Outros tipos que fazem parte do Ferramentas do Visual Studio para a infraestrutura de tempo de execução do Office e não se destinam a serem usados diretamente do seu código.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|O fornece os seguintes tipos:<br /><br /> -O <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> atributo e a <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> interface, que você pode usar para armazenar em cache objetos de dados em uma personalização em nível de documento. Para obter mais informações, consulte [armazenar dados em cache](caching-data.md).<br />-Exceções que podem ser geradas pelo Ferramentas do Visual Studio para o tempo de execução do Office.<br />-Outros tipos que fazem parte do Ferramentas do Visual Studio para a infraestrutura de tempo de execução do Office e não se destinam a serem usados diretamente do seu código.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|Fornece a <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> interface, que pode ser implementada para executar etapas de instalação adicionais como a etapa final do instalador do ClickOnce para uma solução do Office. Para obter mais informações, consulte [implantação avançada da solução Office](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100)).|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|O fornece os seguintes tipos:<br /><br /> -A <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> classe, que você pode usar para anexar programaticamente assemblies de personalização a documentos e acessar os dados armazenados em cache em documentos. Para obter mais informações, consulte [gerenciar documentos em um servidor usando a classe ServerDocument](managing-documents-on-a-server-by-using-the-serverdocument-class.md).<br />-Várias classes que representam a hierarquia de dados armazenados em cache em uma personalização em nível de documento. Para obter mais informações, consulte [acessar dados em documentos no servidor](accessing-data-in-documents-on-the-server.md).|
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|O fornece os seguintes tipos:<br /><br /> -As classes Microsoft. VisualStudio. Tools. Office. Runtime. Security. AddInSecurityEntry e Microsoft. VisualStudio. Tools. Office. Runtime. Security. conclusionlist, que você pode usar para criar entradas de lista de inclusão de usuário para conceder confiança às soluções do Office direcionadas ao .NET Framework 3,5.<br />-Outros tipos que fazem parte do Ferramentas do Visual Studio para a infraestrutura de tempo de execução do Office e não se destinam a serem usados diretamente do seu código.|

## <a name="see-also"></a>Confira também
- [Visão geral do Ferramentas do Visual Studio para Office Runtime](visual-studio-tools-for-office-runtime-overview.md)
- [Ferramentas do Visual Studio para cenários de instalação do Office Runtime](visual-studio-tools-for-office-runtime-installation-scenarios.md)
