---
title: A classe selecionada não pode ser excluída porque é usada como um tipo de retorno para um ou mais métodos DataContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf16fe7453388e19308ed603ee9dbbac207cec41
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667251"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>A classe selecionada não pode ser excluída porque é usada como um tipo de retorno para um ou mais métodos DataContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O tipo de retorno de um ou mais métodos de <xref:System.Data.Linq.DataContext> é a classe de entidade selecionada. Excluindo um classe de entidade que é usada como o tipo de retorno para um método de <xref:System.Data.Linq.DataContext> fará com que a compilação do projeto falhar. Para excluir a classe selecionada de entidade, identifica os métodos de <xref:System.Data.Linq.DataContext> que a usam e definem seus tipos de retorno para uma classe diferente de entidade.

 Para reverter os tipos de retorno dos métodos de <xref:System.Data.Linq.DataContext> para seus tipos originais gerados automaticamente, primeiro exclua o método <xref:System.Data.Linq.DataContext> do painel métodos e arraste o objeto de **Gerenciador de Servidores** /**Gerenciador de banco de dados** para o o/R Designer novamente.

### <a name="to-correct-this-error"></a>Para corrigir este erro

1. Identifique <xref:System.Data.Linq.DataContext> métodos que usam a classe Entity como um tipo de retorno, selecionando um método <xref:System.Data.Linq.DataContext> no painel métodos e inspecionando a propriedade **tipo de retorno** na janela **Propriedades** .

2. Definir **Tipo de Retorno** a uma classe diferente de entidade ou exclui o método de <xref:System.Data.Linq.DataContext> do painel métodos.

## <a name="see-also"></a>Consulte também
 [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [passo a passos: criando classes de LINQ to SQL (o-r designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [métodos DataContext (o/r designer)](../data-tools/datacontext-methods-o-r-designer.md) [como alterar o tipo de retorno de um método DataContext (o/r designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)
