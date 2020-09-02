---
title: Propriedades em projetos do Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Trust Assemblies Location property
- Cache in Document property
- properties [Office development in Visual Studio]
- Namespace for Host Item property
- Office projects [Office development in Visual Studio], properties
- projects [Office development in Visual Studio], properties
- Value2 property
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9fc2a0774206eac0c9295a425d81555ffdd3cac8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62561353"
---
# <a name="properties-in-office-projects"></a>Propriedades em projetos do Office
  Há várias propriedades importantes que estão disponíveis para projetos do Office no Visual Studio. Essas propriedades podem ser acessadas na janela **Propriedades** .

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="namespace-for-host-item"></a>Namespace para o item de host
 Use o **namespace para a propriedade de item de host** para alterar o namespace para classes de item de host (por exemplo, as `ThisAddIn` `ThisWorkbook` classes, ou `ThisDocument` ) em projetos do Visual C#. Essa propriedade aparece na janela **Propriedades** quando você seleciona o nó de documento em um projeto de nível de documento (como *ExcelWorkbook1.xlsx* ou *WordDocument1.docx*) ou o nó de aplicativo em um projeto de suplemento do VSTO (como o Excel ou Word) no **Gerenciador de soluções**.

 Quando você cria um projeto do Office em Visual C#, os itens de host recebem um namespace com base no nome do projeto. É recomendável que você use o **namespace para a propriedade de item de host** para alterar o namespace em vez de editar os arquivos de código diretamente. Quando você usa essa propriedade, o namespace é alterado nos arquivos de código gerados (ocultos), bem como nos arquivos de código visíveis.

## <a name="cacheindocument"></a>CacheInDocument
 A propriedade **CacheInDocument** aparece na janela **Propriedades** para projetos de nível de documento quando você seleciona uma instância de a <xref:System.Data.DataSet> no designer do Visual Studio. Somente membros públicos podem ser armazenados em cache; Certifique-se de que a propriedade **modificadores** esteja definida como **pública** se você quiser armazenar em cache um <xref:System.Data.DataSet> .

 Essa propriedade usa um valor booliano:

- Selecione **true** para armazenar em cache o conjunto de armazenamento no documento.

- Selecione **falso** se você não quiser que o conjunto de um seja armazenado em cache no documento.

  Para obter mais informações sobre como armazenar dados em cache, consulte [dados armazenados em cache em personalizações em nível de documento](../vsto/cached-data-in-document-level-customizations.md).

## <a name="value2"></a>Value2
 A propriedade **value2** só está disponível para projetos de pasta de trabalho ou modelo do Excel. Ele aparece sob o nó de propriedade **DataBindings** na janela **Propriedades** quando você seleciona um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle no designer de planilha.

 Use a propriedade **value2** na janela **Propriedades** para associar a <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> Propriedade do <xref:Microsoft.Office.Tools.Excel.NamedRange> a um campo em sua fonte de dados.

## <a name="see-also"></a>Confira também
- [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)
- [Visão geral dos modelos do Office Project](../vsto/office-project-templates-overview.md)
- [Eventos em projetos do Office](../vsto/events-in-office-projects.md)
