---
title: A classe selecionada não pode ser excluída porque ele é usado como um tipo de retorno para um ou mais métodos DataContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 03e1df5398b4a23a1633d4a0fa92fe0bedb830f6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686621"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>A classe selecionada não pode ser excluída porque é usada como um tipo de retorno para um ou mais métodos DataContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O tipo de retorno de um ou mais métodos de <xref:System.Data.Linq.DataContext> é a classe de entidade selecionada. Excluindo um classe de entidade que é usada como o tipo de retorno para um método de <xref:System.Data.Linq.DataContext> fará com que a compilação do projeto falhar. Para excluir a classe selecionada de entidade, identifica os métodos de <xref:System.Data.Linq.DataContext> que a usam e definem seus tipos de retorno para uma classe diferente de entidade.  
  
 Para reverter os tipos de retorno de <xref:System.Data.Linq.DataContext> métodos para seus tipos gerados automaticamente originais, primeiro exclua os <xref:System.Data.Linq.DataContext> método a partir do painel de métodos e, em seguida, arraste o objeto de **Gerenciador de servidores** / **Gerenciador de banco de dados** para o O/R Designer novamente.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Identificar <xref:System.Data.Linq.DataContext> métodos que usam a classe de entidade como um tipo de retorno selecionando um <xref:System.Data.Linq.DataContext> método nos métodos de painel e inspecionando a **tipo de retorno** propriedade no **propriedades** janela .  
  
2. Definir **Tipo de Retorno** a uma classe diferente de entidade ou exclui o método de <xref:System.Data.Linq.DataContext> do painel métodos.  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Passo a passo: Criando Classes LINQ to SQL (Object Relational Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Métodos de DataContext (Designer relacional de objetos)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Como: Alterar o tipo de retorno de um método DataContext (Designer Relacional de Objetos)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)
