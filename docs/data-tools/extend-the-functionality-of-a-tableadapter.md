---
title: Estender a funcionalidade de um TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d0ec905670c72ff7c2c5f5d94c9f5189241daebb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60100008"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Estender a funcionalidade de um TableAdapter

Você pode estender a funcionalidade de um TableAdapter, adicionando código ao arquivo de classe parcial do TableAdapter.

O código que define um TableAdapter é regenerado quando alterações são feitas no TableAdapter na **Dataset Designer**, ou quando um assistente modifica a configuração de um TableAdapter. Para impedir que seu código seja excluído durante a regeneração de um TableAdapter, adicione código ao arquivo de classe parcial do TableAdapter.

Classes parciais permitem que o código para uma classe específica a ser dividido entre vários arquivos físicos. Para obter mais informações, consulte [parcial](/dotnet/visual-basic/language-reference/modifiers/partial) ou [partial (tipo)](/dotnet/csharp/language-reference/keywords/partial-type).

## <a name="locate-tableadapters-in-code"></a>Localize os TableAdapters no código

Enquanto TableAdapters são criados com o **Dataset Designer**, as classes TableAdapter geradas não são classes aninhadas do <xref:System.Data.DataSet>. TableAdapters estão localizados em um namespace com base no nome do conjunto de dados associado do TableAdapter. Por exemplo, se seu aplicativo contém um conjunto de dados denominado `HRDataSet`, os TableAdapters deve estar localizado no `HRDataSetTableAdapters` namespace. (A convenção de nomenclatura segue este padrão: *DatasetName* + `TableAdapters`).

O exemplo a seguir pressupõe um TableAdapter nomeado `CustomersTableAdapter`está em um projeto com `NorthwindDataSet`.

### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Para criar uma classe parcial para um TableAdapter

1. Adicione uma nova classe ao seu projeto, vá para o **Project** menu e selecionando **Adicionar classe**.

2. Nomeie a classe `CustomersTableAdapterExtended`.

3. Selecione **Adicionar**.

4. Substitua o código com o namespace correto e o nome de classe parcial para o seu projeto da seguinte maneira:

     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]

## <a name="see-also"></a>Consulte também

- [Preencher conjuntos de dados usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)