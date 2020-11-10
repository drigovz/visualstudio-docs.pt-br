---
title: Como estender o código gerado pelo Designer Relacional de Objetos
description: Examine como estender O código gerado por Object Relational Designer (O/R Designer). Adicione código a uma classe de entidade. Adicione código a um DataContext.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7d3468bbc3e3a1f1250cf2c679087b9606b87a18
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434916"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Como estender o código gerado pelo Designer Relacional de Objetos
O código gerado pelo o **/R Designer** é regenerado quando são feitas alterações nas classes de entidade e outros objetos na superfície do designer. Devido a essa regeneração de código, qualquer código que você adicionar ao código gerado seja substituído normalmente quando o código de regenerados de designer. O o **/R Designer** fornece a capacidade de gerar arquivos de classe parciais nos quais você pode adicionar código que não é substituído. Um exemplo de adição de seu próprio código ao código gerado pelo o **/R Designer** é adicionar validação de dados a classes LINQ to SQL (entidade). Para obter mais informações, consulte [como: Adicionar validação a classes de entidade](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Adicionar código a uma classe de entidade

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Para criar uma classe parcial e adicione o código para uma classe de entidade

1. Abra ou crie um novo arquivo de classes de LINQ to SQL (arquivo **. dbml** ) no o **/R Designer**. (Clique duas vezes no arquivo **. dbml** em **Gerenciador de soluções** ou **Gerenciador de banco de dados**.)

2. No **Designer Relacional de Objetos** , clique com o botão direito do mouse na classe para qual você deseja adicionar validação e clique em **Exibir Código**.

     O editor de códigos abre com uma classe parcial para a classe de entidade selecionada.

3. Adicione o código na declaração de classe parcial para a classe de entidade.

## <a name="add-code-to-a-datacontext"></a>Adicionar código a um DataContext

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Para criar uma classe parcial e adicione o código a um DataContext

1. Abra ou crie um novo arquivo de classes de LINQ to SQL (arquivo **. dbml** ) no o **/R Designer**. (Clique duas vezes no arquivo **. dbml** em **Gerenciador de soluções** ou **Gerenciador de banco de dados**.)

2. No o **/R Designer** , clique com o botão direito do mouse em uma área vazia no designer e clique em **Exibir código**.

     O editor de códigos abre com uma classe parcial para o DataContext.

3. Adicione o código na declaração de classe parcial para o DataContext.

## <a name="see-also"></a>Confira também

- [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Passo a passo: criando classes LINQ to SQL (Designer Relacional de Objetos)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
