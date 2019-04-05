---
title: Salvar um conjunto de dados como XML | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 49fb600b2c27725eb6fe888aa2a41a6b19c123b0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58927241"
---
# <a name="save-a-dataset-as-xml"></a>Salvar um conjunto de dados como XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Os dados XML em um conjunto de dados podem ser acessados chamando os métodos XML disponíveis no conjunto de dados. Para salvar os dados em formato XML, você pode chamar o <xref:System.Data.DataSet.GetXml%2A> método ou o <xref:System.Data.DataSet.WriteXml%2A> método de um <xref:System.Data.DataSet>.  
  
 Chamar o <xref:System.Data.DataSet.GetXml%2A> método retorna uma cadeia de caracteres que contém os dados de todas as tabelas de dados no conjunto de dados que está formatado como XML.  
  
 Chamar o <xref:System.Data.DataSet.WriteXml%2A> método envia os dados formatados em XML para um arquivo que você especifica.  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Para salvar os dados em um conjunto de dados como XML em uma variável  
  
-   O <xref:System.Data.DataSet.GetXml%2A> método retorna um <xref:System.String>. Isso significa que você declare uma variável do tipo <xref:System.String> e atribua a ele os resultados do <xref:System.Data.DataSet.GetXml%2A> método.  
  
     [!code-csharp[VbRaddataSaving#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#12)]
     [!code-vb[VbRaddataSaving#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#12)]  
  
### <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Para salvar os dados em um conjunto de dados como XML em um arquivo  
  
-   O <xref:System.Data.DataSet.WriteXml%2A> método tem várias sobrecargas. O código a seguir mostra como salvar os dados em um arquivo. Declare uma variável e atribuí-lo em um caminho válido para salvar o arquivo.  
  
     [!code-csharp[VbRaddataSaving#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#13)]
     [!code-vb[VbRaddataSaving#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>Consulte também  
 [Salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md)
