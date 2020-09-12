---
title: A classe selecionada não pode ser excluída
description: A classe selecionada não pode ser excluída porque é usada como um tipo de retorno para um ou mais métodos DataContext
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 24b8e933d8a5d6002ba2ae7b035c5e9e3ee52630
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036191"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>A classe selecionada não pode ser excluída porque é usada como um tipo de retorno para um ou mais métodos DataContext

O tipo de retorno de um ou mais métodos de <xref:System.Data.Linq.DataContext> é a classe de entidade selecionada. A exclusão de uma classe de entidade usada como o tipo de retorno para um <xref:System.Data.Linq.DataContext> método faz com que a compilação do projeto falhe. Para excluir a classe selecionada de entidade, identifica os métodos de <xref:System.Data.Linq.DataContext> que a usam e definem seus tipos de retorno para uma classe diferente de entidade.

Para reverter os tipos de retorno de métodos de <xref:System.Data.Linq.DataContext> para seus tipos gerados automaticamente de original, primeiro excluir o método de <xref:System.Data.Linq.DataContext> do painel **Métodos** e arraste então o objeto de **Gerenciador de Servidores**/**Gerenciador de Banco de Dados** no **Designer Relacional de Objetos** novamente.

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Identifica os métodos de <xref:System.Data.Linq.DataContext> que usam a classe de entidade como um tipo de retorno selecionando um método de <xref:System.Data.Linq.DataContext> no painel **Métodos** e inspecionando a propriedade de **Tipo de Retorno** na janela **Propriedades**.

2. Definir **Tipo de Retorno** a uma classe diferente de entidade ou exclui o método de <xref:System.Data.Linq.DataContext> do painel métodos.

## <a name="see-also"></a>Confira também

- [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
