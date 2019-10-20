---
title: Salvar um DataSet como XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e64c3c17934e5cdc5d6ca1f510c7164b86a77c1a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652858"
---
# <a name="save-a-dataset-as-xml"></a>Salvar um conjunto de dados como XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os dados XML em um DataSet podem ser acessados chamando os métodos XML disponíveis no conjunto de dados. Para salvar os dados em formato XML, você pode chamar o método <xref:System.Data.DataSet.GetXml%2A> ou o método <xref:System.Data.DataSet.WriteXml%2A> de um <xref:System.Data.DataSet>.

 Chamar o método <xref:System.Data.DataSet.GetXml%2A> retorna uma cadeia de caracteres que contém os dados de todas as tabelas de dados no DataSet formatados como XML.

 Chamar o método <xref:System.Data.DataSet.WriteXml%2A> envia os dados formatados em XML para um arquivo que você especificar.

### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Para salvar os dados em um DataSet como XML em uma variável

- O método <xref:System.Data.DataSet.GetXml%2A> retorna um <xref:System.String>. isso significa que você declara uma variável do tipo <xref:System.String> e atribui a ela os resultados do método <xref:System.Data.DataSet.GetXml%2A>.

     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]

### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Para salvar os dados em um DataSet como XML em um arquivo

- O método <xref:System.Data.DataSet.WriteXml%2A> tem várias sobrecargas. O código a seguir mostra como salvar os dados em um arquivo. Declare uma variável e atribua um caminho válido para salvar o arquivo.

     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]

## <a name="see-also"></a>Consulte também
 [Salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md)
