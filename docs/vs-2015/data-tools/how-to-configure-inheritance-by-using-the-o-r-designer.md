---
title: 'Como: configurar a herança usando o-R Designer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f8c08546fdf96c755b3adb80021ab7269509739
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654701"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Como configurar a herança usando o Designer Relacional de Objetos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) suporta o conceito de herança de tabela única como geralmente é implementado em sistemas relacionais. Na herança de tabela única, há uma única tabela de banco de dados que contém campos para informações pai e informações filho. Com os dados relacionais, uma coluna de discriminador contém o valor que determina qual classe qualquer registro pertence.

 Por exemplo, considere pessoas a tabela que contém todos empregado por uma empresa. Algumas pessoas são funcionários e algumas pessoas são gerentes. A tabela de pessoas contém uma coluna chamada `EmployeeType` que tenha um valor de 1 para gerentes e um valor de 2 para funcionários; esta é a coluna de discriminador. Nesse cenário, você pode criar uma subclasse de funcionários e preencher a classe com apenas os registros que têm um valor de `EmployeeType` de 2. Você pode também remover colunas que não se aplicam de cada uma das classes.

 Criar um modelo de objeto que usar herança (e corresponde a dados relacionais) pode ser um pouco confuso. O procedimento a seguir descreve as etapas necessárias para configurar a herança com object relational Designer de Objetos. Após as etapas genéricos sem se referir a uma tabela existente e colunas pode ser difícil, para uma explicação passo a passo que usa dados é fornecido. Para obter instruções passo a passo detalhadas sobre como configurar a herança usando o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , consulte [Walkthrough: criando Classes de LINQ to SQL usando herança de tabela única (o/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

### <a name="to-create-inherited-data-classes"></a>Para criar classes de dados herdadas

1. Abra o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] adicionando um item de **Classes de LINQ to SQL** a um projeto existente Visual Basic ou C#.

2. Arraste a tabela que você deseja usar como a classe base em [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

3. Arraste uma segunda cópia da tabela para a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] e renomeie-a. Esta é a classe derivada, ou subclasse.

4. Clique na guia **Herança** no **Object Relational Designer** da **Caixa de Ferramentas** e em seguida, clique na subclasse (a tabela que você renomeou) e conecta-se a classe base.

    > [!NOTE]
    > Clique no item de **Herança** em **Caixa de Ferramentas** e solte o botão do mouse, clique na segunda cópia de classe que você criou na etapa 3 e depois clique na primeira classe que você criou na etapa 2. A seta na linha de herança irá apontar para a primeira classe.

5. Em cada classe, excluir todas as propriedades do objeto que você não deseja que apareça e que não são usadas para associações. Você receberá um erro se tentar excluir as propriedades de objeto usadas para associações: [a propriedade \<property name> não pode ser excluída porque está participando da \<association name> Associação ](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    > Como uma classe derivada herda as propriedades definidas na sua classe base, as mesmas colunas não podem ser definidas em cada classe. (As colunas são implementadas como propriedades.) Você pode habilitar a criação de colunas na classe derivada definindo o modificador de herança na propriedade na classe base. Para obter mais informações, consulte [não está na compilação: substituindo Propriedades e métodos](https://msdn.microsoft.com/2167e8f5-1225-4b13-9ebd-02591ba90213).

6. Selecione a linha de herança em [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

7. Na janela **Propriedades** , defina a **Propriedade discriminador** como o nome da coluna que é usado para distinguir os registros em suas classes.

8. Defina a propriedade **Valor Discriminatório da Classe Derivada** para o valor no banco de dados que designa o registro como o tipo herdado. (Esse é o valor que são armazenados na coluna de discriminador e que é usado para designar a classe herdada.)

9. Defina a propriedade **valor do discriminador de classe base** como o valor que designa o registro como um tipo base. (Esse é o valor que são armazenados na coluna de discriminador e que é usado para designar a classe base.)

10. Opcionalmente, você pode também definir a propriedade de **Padrão de Herança** para designar um tipo em uma hierarquia de herança que é usada para carregar as linhas que não correspondem nenhum código de herança definido. Em outras palavras, se um registro tiver um valor em sua coluna discriminadora que não corresponda ao valor no **valor discriminador da classe derivada** ou nas propriedades do **valor discriminador da classe base** , o registro será carregado no tipo designado como **padrão de herança**.

## <a name="see-also"></a>Consulte Também
 [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [passo a passos: criando classes de LINQ to SQL (O-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [pavimentar o que há de novo para o desenvolvimento de aplicativos de dados no Visual Studio 2012](https://msdn.microsoft.com/3d50d68f-5f44-4915-842f-6d42fce793f1) [acessando dados no visual studio](../data-tools/accessing-data-in-visual-studio.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [explicação: Criando classes de LINQ to SQL usando herança de tabela única (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) [não está no Build: herança em Visual Basic](https://msdn.microsoft.com/e5e6e240-ed31-4657-820c-079b7c79313c) [herança](https://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)
