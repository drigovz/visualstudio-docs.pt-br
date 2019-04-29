---
title: Herança de classe de dados (Designer Relacional de Objetos)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a8df3d39e44bf1d40f3abfd4d6218d2c9a72b690
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567800"
---
# <a name="data-class-inheritance-or-designer"></a>Herança de classe de dados (Designer Relacional de Objetos)

Como outros objetos, classes LINQ to SQL pode usar a herança e ser derivado de outras classes. Em código, você pode especificar relações de herança entre objetos declarando uma classe que herda de outra. Em uma base de dados, as relações de herança são criadas de várias maneiras. O **Object Relational Designer** (**Relational Designer**) suporta o conceito de herança de tabela única como geralmente é implementado em sistemas relacionais.

A herança de tabela única, há uma única tabela de base de dados que contém colunas para ambos base e classes derivadas. Com dados relacionais, uma coluna de discriminador contém o valor que determina qual classe qualquer determinado registro pertence. Por exemplo, considere um `Persons` tabela que contém todos empregado por uma empresa. Algumas pessoas são funcionários e algumas pessoas são gerentes. O `Persons` tabela contém uma coluna denominada `Type` que tem um valor de 1 para gerentes e um valor de 2 para funcionários. O `Type` coluna é a coluna de discriminador. Nesse cenário, você pode criar uma subclasse de funcionários e preencher a classe com apenas os registros que têm um `Type` valor 2.

Quando você configura a herança na classe entidade usando [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], arraste a única tabela que contém os dados de herança no designer duas vezes: uma vez para cada classe na hierarquia de herança. Após adicionar tabelas ao designer, conectar-las com um item de herança da caixa de ferramentas de **Object Relational Designer** e então defina as quatro propriedades de herança na janela **Propriedades**.

## <a name="inheritance-properties"></a>Propriedades de herança

A seguinte tabela lista as propriedades de herança e suas descrições:

|Propriedade|Descrição|
|--------------|-----------------|
|**Propriedade Discriminatória**|A propriedade (mapeado para a coluna) que determina qual classe ao registro atual pertence.|
|**Valor discriminatório da classe base**|O valor (na coluna designada como a **propriedade discriminatória**) que determina que um registro é a classe base.|
|**Valor discriminatório da classe derivada**|O valor (na propriedade designada como a **propriedade discriminatória**) que determina que um registro é da classe derivada.|
|**Padrão de Herança**|A classe que é preenchida quando o valor na propriedade designada como o **propriedade discriminatória** não corresponder a **valor Discriminatório da classe Base** ou o **classe derivada Valor Discriminatório**.|

Criar um modelo de objeto que usar herança e corresponde a dados relacionais pode ser um pouco confuso. Este tópico fornece informações sobre os conceitos básicos e as propriedades individuais que são necessários configurando a herança. Os tópicos a seguir fornecem uma explicação mais claro de como configurar a herança com o **Relational Designer**.

|Tópico|Descrição|
|-----------|-----------------|
|[Como: Configurar a herança usando o Designer Relacional de Objetos](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Descreve como configurar classes de entidade que usam herança de tabela única usando o **Relational Designer**.|
|[Passo a passo: Criando classes LINQ to SQL usando a herança de tabela única (Designer Relacional de Objetos)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Fornece instruções passo a passo sobre como configurar classes de entidade que usam herança de tabela única usando o **Relational Designer**.|

## <a name="see-also"></a>Consulte também

- [Ferramentas do LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Passo a passo: Criando o LINQ para SQL classes (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Passo a passo: Criando classes LINQ to SQL usando a herança de tabela única (Designer Relacional de Objetos)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Introdução](/dotnet/framework/data/adonet/sql/linq/getting-started)