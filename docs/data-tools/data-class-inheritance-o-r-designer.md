---
title: Herança de classe de dados (Designer Relacional de Objetos)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7cb47913f2b14867be4dcc8f98688ab2d2a858d9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648549"
---
# <a name="data-class-inheritance-or-designer"></a>Herança de classe de dados (Designer Relacional de Objetos)

Assim como outros objetos, LINQ to SQL classes podem usar a herança e serem derivadas de outras classes. Em código, você pode especificar relações de herança entre objetos declarando uma classe que herda de outra. Em uma base de dados, as relações de herança são criadas de várias maneiras. O **Object Relational Designer** (**o/R Designer**) dá suporte ao conceito de herança de tabela única, pois ela geralmente é implementada em sistemas relacionais.

A herança de tabela única, há uma única tabela de base de dados que contém colunas para ambos base e classes derivadas. Com dados relacionais, uma coluna de discriminador contém o valor que determina qual classe qualquer determinado registro pertence. Por exemplo, considere uma tabela `Persons` que contém todos os empregados por uma empresa. Algumas pessoas são funcionários e algumas pessoas são gerentes. A tabela `Persons` contém uma coluna chamada `Type` que tem um valor de 1 para gerentes e um valor de 2 para funcionários. A coluna `Type` é a coluna discriminadora. Nesse cenário, você pode criar uma subclasse de Employees e preencher a classe somente com registros que tenham um valor de `Type` de 2.

Quando você configura a herança na classe entidade usando [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], arraste a única tabela que contém os dados de herança no designer duas vezes: uma vez para cada classe na hierarquia de herança. Após adicionar tabelas ao designer, conectar-las com um item de herança da caixa de ferramentas de **Object Relational Designer** e então defina as quatro propriedades de herança na janela **Propriedades**.

## <a name="inheritance-properties"></a>Propriedades de herança

A seguinte tabela lista as propriedades de herança e suas descrições:

|propriedade|Descrição|
|--------------|-----------------|
|**Propriedade Discriminatória**|A propriedade (mapeado para a coluna) que determina qual classe ao registro atual pertence.|
|**Valor discriminatório da classe base**|O valor (na coluna designada como a **propriedade discriminatória**) que determina que um registro é a classe base.|
|**Valor discriminatório da classe derivada**|O valor (na propriedade designada como a **propriedade discriminatória**) que determina que um registro é da classe derivada.|
|**Padrão de Herança**|A classe que é populada quando o valor na propriedade designada como a **Propriedade discriminadora** não corresponde ao **valor discriminador da classe base** ou ao **valor discriminador da classe derivada**.|

Criar um modelo de objeto que usar herança e corresponde a dados relacionais pode ser um pouco confuso. Este tópico fornece informações sobre os conceitos básicos e as propriedades individuais que são necessários configurando a herança. Os tópicos a seguir fornecem uma explicação mais clara de como configurar a herança com o o **/R Designer**.

|Tópico|Descrição|
|-----------|-----------------|
|[Como configurar a herança usando o Designer Relacional de Objetos](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Descreve como configurar classes de entidade que usam herança de tabela única usando o o **/R Designer**.|
|[Passo a passo: criando classes LINQ to SQL usando a herança de tabela única (Designer Relacional de Objetos)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Fornece instruções passo a passo sobre como configurar classes de entidade que usam herança de tabela única usando o o **/R Designer**.|

## <a name="see-also"></a>Consulte também

- [Ferramentas do LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Passo a passo: criando classes LINQ to SQL (Designer Relacional de Objetos)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Passo a passo: criando classes LINQ to SQL usando a herança de tabela única (Designer Relacional de Objetos)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Introdução](/dotnet/framework/data/adonet/sql/linq/getting-started)