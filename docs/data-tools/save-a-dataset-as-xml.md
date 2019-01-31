---
title: Salvar um conjunto de dados como XML
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: c1eff1b80807b040bd50d7e4e5f2045c73c46929
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011813"
---
# <a name="save-a-dataset-as-xml"></a>Salvar um conjunto de dados como XML

Acesse os dados XML em um conjunto de dados chamando os métodos XML disponíveis no conjunto de dados. Para salvar os dados em formato XML, você pode chamar o <xref:System.Data.DataSet.GetXml%2A> método ou o <xref:System.Data.DataSet.WriteXml%2A> método de um <xref:System.Data.DataSet>.

Chamar o <xref:System.Data.DataSet.GetXml%2A> método retorna uma cadeia de caracteres que contém os dados de todas as tabelas de dados no conjunto de dados que está formatado como XML.

Chamar o <xref:System.Data.DataSet.WriteXml%2A> método envia os dados formatados em XML para um arquivo que você especifica.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>Para salvar os dados em um conjunto de dados como XML em uma variável

- O método <xref:System.Data.DataSet.GetXml%2A> retorna um <xref:System.String>. Declare uma variável do tipo <xref:System.String> e atribua a ele os resultados do <xref:System.Data.DataSet.GetXml%2A> método.

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>Para salvar os dados em um conjunto de dados como XML em um arquivo

- O <xref:System.Data.DataSet.WriteXml%2A> método tem várias sobrecargas. Declare uma variável e atribuí-lo em um caminho válido para salvar o arquivo. O código a seguir mostra como salvar os dados em um arquivo:

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>Consulte também

- [Salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md)