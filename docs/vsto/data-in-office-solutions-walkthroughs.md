---
title: Orientações sobre os dados nas soluções do Office
description: Saiba como trabalhar com dados em personalizações em nível de documento e suplementos do VSTO para o Microsoft Word e o Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], walkthroughs
- walkthroughs [Office development in Visual Studio], data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4736b357017f5ff5244af8f078457b0289994e98
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962411"
---
# <a name="data-in-office-solutions-walkthroughs"></a>Orientações sobre os dados nas soluções do Office
  As orientações a seguir demonstram como trabalhar com dados em personalizações em nível de documento e suplementos do VSTO para Microsoft Office Word e Microsoft Office Excel.

## <a name="bind-controls-to-data"></a>Associar controles a dados
- [Walkthrough: vinculação de dados simples em um projeto de nível de documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) Demonstra como associar um único campo de dados em um banco de dado SQL Server a um <xref:Microsoft.Office.Tools.Excel.NamedRange> em uma personalização em nível de documento para o Excel.

- [Walkthrough: ligação de dados complexa em um projeto de nível de documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) Demonstra como associar uma tabela em um banco de dados SQL Server a um <xref:Microsoft.Office.Tools.Excel.ListObject> em uma personalização em nível de documento para o Excel.

- [Walkthrough: vinculação de dados simples no projeto de suplemento do VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) Demonstra como associar um único campo de dados em um banco de dado SQL Server a um <xref:Microsoft.Office.Tools.Word.RichTextContentControl> em um suplemento do VSTO para Word.

- [Walkthrough: ligação de dados complexa no projeto de suplemento do VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) Demonstra como associar uma tabela em um banco de dados SQL Server a um <xref:Microsoft.Office.Tools.Excel.ListObject> em um suplemento do VSTO para Excel.

- [Walkthrough: associar dados a controles em um painel de ações do Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md) Demonstra como adicionar controles associados a uma fonte de dados a um painel de ações no Excel.

- [Walkthrough: associar dados a controles em um painel de ações do Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md) Demonstra como associar controles em um painel ações aos dados. Os controles demonstram uma relação mestre/detalhes entre tabelas em um banco de dados SQL Server.

- [Walkthrough: associar controles de conteúdo a partes XML personalizadas](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md) Demonstra como associar controles de conteúdo em um documento do Word a dados XML armazenados no documento.

## <a name="cache-data-in-document-level-solutions"></a>Armazenar dados em cache em soluções de nível de documento
- [Walkthrough: criar uma relação de detalhes mestre usando um conjunto de um DataSet armazenado em cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md) Demonstra como criar uma relação mestre/detalhes em uma planilha e armazenar os dados em cache para que a solução possa ser usada offline.

- [Walkthrough: inserir dados em uma pasta de trabalho em um servidor](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md) Demonstra como inserir dados em um DataSet que é armazenado em cache em uma Microsoft Office pasta de trabalho do Excel sem iniciar o Excel.

- [Walkthrough: recuperar dados armazenados em cache de uma pasta de trabalho em um servidor](../vsto/walkthrough-retrieving-cached-data-from-a-workbook-on-a-server.md) Demonstra como recuperar dados de um DataSet que é armazenado em cache em uma Microsoft Office pasta de trabalho do Excel sem iniciar o Excel.

- [Walkthrough: alterar os dados armazenados em cache em uma pasta de trabalho em um servidor](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md) Demonstra como modificar um conjunto de armazenamento armazenado em cache em uma Microsoft Office pasta de trabalho do Excel sem iniciar o Excel.

## <a name="see-also"></a>Confira também
- [Passo a passos usando o Word](../vsto/walkthroughs-using-word.md)
- [Passo a passos usando o Excel](../vsto/walkthroughs-using-excel.md)
- [Passo a passos de personalização da interface do usuário do Office](../vsto/office-ui-customization-walkthroughs.md)
- [Orientações de segurança e implantação](../vsto/security-and-deployment-walkthroughs.md)
- [Exemplos de desenvolvimento do Office](../vsto/office-development-samples.md)
- [Introdução &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Tarefas comuns na programação do Office](../vsto/common-tasks-in-office-programming.md)
- [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)
