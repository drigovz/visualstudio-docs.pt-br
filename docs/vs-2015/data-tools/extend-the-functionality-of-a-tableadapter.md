---
title: Estender a funcionalidade de um TableAdapter | Microsoft Docs
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
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bbba71e6c1e636abe160036f10c1de1d11004a65
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58923948"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Estender a funcionalidade de um TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Você pode estender a funcionalidade de um TableAdapter, adicionando código ao arquivo de classe parcial do TableAdapter.  
  
 O código que define um TableAdapter é regenerado quando alterações são feitas no TableAdapter na **Dataset Designer**, ou quando um assistente modifica a configuração de um TableAdapter. Para impedir que seu código seja excluído durante a regeneração de um TableAdapter, adicione código ao arquivo de classe parcial do TableAdapter.  
  
 Classes parciais permitem que o código para uma classe específica a ser dividido entre vários arquivos físicos. Para obter mais informações, consulte [parcial](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) ou [partial (tipo)](http://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).  
  
## <a name="locate-tableadapters-in-code"></a>Localize os TableAdapters no código  
 Enquanto TableAdapters são criados com o **Dataset Designer**, as classes TableAdapter geradas não são classes aninhadas do <xref:System.Data.DataSet>. TableAdapters estão localizados em um namespace com base no nome do conjunto de dados associado do TableAdapter. Por exemplo, se seu aplicativo contém um conjunto de dados denominado `HRDataSet`, os TableAdapters deve estar localizado no `HRDataSetTableAdapters` namespace. (A convenção de nomenclatura segue este padrão: *DatasetName* + `TableAdapters`).  
  
 O exemplo a seguir pressupõe um TableAdapter nomeado `CustomersTableAdapter`está em um projeto com `NorthwindDataSet`.  
  
#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Para criar uma classe parcial para um TableAdapter  
  
1.  Adicione uma nova classe ao seu projeto, vá para o **Project** menu e selecionando**Adicionar classe**.  
  
2.  Nomeie a classe `CustomersTableAdapterExtended`.  
  
3.  Selecione **Adicionar**.  
  
4.  Substitua o código com o namespace correto e o nome de classe parcial para o seu projeto da seguinte maneira:  
  
     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Preencher conjuntos de dados usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
