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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 19367f812a87d6aa585e123100f1d08144c57ff9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672368"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Estender a funcionalidade de um TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode estender a funcionalidade de um TableAdapter adicionando código ao arquivo de classe parcial do TableAdapter.

 O código que define um TableAdapter é regenerado quando qualquer alteração é feita no TableAdapter no **Designer de conjunto de dados**, ou quando um assistente modifica a configuração de um TableAdapter. Para impedir que seu código seja excluído durante a regeneração de um TableAdapter, adicione o código ao arquivo de classe parcial do TableAdapter.

 As classes parciais permitem que o código de uma classe específica seja dividido entre vários arquivos físicos. Para obter mais informações, consulte [parcial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) ou [parcial (tipo)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).

## <a name="locate-tableadapters-in-code"></a>Localizar TableAdapters no código
 Embora os TableAdapters sejam projetados com o **Designer de conjunto de dados**, as classes do TableAdapter geradas não são classes aninhadas de <xref:System.Data.DataSet>. Os TableAdapters estão localizados em um namespace com base no nome do DataSet associado do TableAdapter. Por exemplo, se seu aplicativo contiver um conjunto de um DataSet chamado `HRDataSet`, os TableAdapters estarão localizados no namespace `HRDataSetTableAdapters`. (A convenção de nomenclatura segue este padrão: *DatasetName* + `TableAdapters`).

 O exemplo a seguir pressupõe um TableAdapter chamado `CustomersTableAdapter`is em um projeto com `NorthwindDataSet`.

#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Para criar uma classe parcial para um TableAdapter

1. Adicione uma nova classe ao seu projeto acessando o menu **projeto** e selecionando**Adicionar classe**.

2. Nomeie a classe `CustomersTableAdapterExtended`.

3. Selecione **Adicionar**.

4. Substitua o código pelo namespace correto e o nome da classe parcial do seu projeto da seguinte maneira:

     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]

## <a name="see-also"></a>Consulte também
 [Preencher conjuntos de dados usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
