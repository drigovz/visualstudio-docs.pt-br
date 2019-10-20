---
title: Usar DataRelation para criar relações entre conjuntos de os
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c9fab55c020894fe87ec4dc1c31137fb7e38c204
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648249"
---
# <a name="create-relationships-between-datasets"></a>Criar relações entre conjuntos de dados
DataSets que contêm tabelas de dados relacionadas usam <xref:System.Data.DataRelation> objetos para representar uma relação pai/filho entre as tabelas e retornar registros relacionados uns dos outros. Adicionar tabelas relacionadas a conjuntos de dados usando o **Assistente de configuração de fonte de dados**ou o **Designer de conjunto de dados**, cria e configura o objeto de <xref:System.Data.DataRelation> para você.

O objeto <xref:System.Data.DataRelation> executa duas funções:

- Ele pode disponibilizar os registros relacionados a um registro com o qual você está trabalhando. Ele fornecerá registros filho se você estiver em um registro pai (<xref:System.Data.DataRow.GetChildRows%2A>) e um registro pai se estiver trabalhando com um registro filho (<xref:System.Data.DataRow.GetParentRow%2A>).

- Ele pode impor restrições para a integridade referencial, como excluir registros filho relacionados quando você exclui um registro pai.

É importante entender a diferença entre uma junção verdadeira e a função de um objeto <xref:System.Data.DataRelation>. Em uma junção verdadeira, os registros são tirados das tabelas pai e filho e colocados em um único conjunto de registros simples. Quando você usa um objeto <xref:System.Data.DataRelation>, nenhum novo conjunto de registros é criado. Em vez disso, a DataRelation acompanha a relação entre as tabelas e mantém os registros pai e filho sincronizados.

## <a name="datarelation-objects-and-constraints"></a>Objetos e restrições de DataRelation
Um objeto <xref:System.Data.DataRelation> também é usado para criar e impor as seguintes restrições:

- Uma restrição UNIQUE, que garante que uma coluna na tabela não contenha duplicatas.

- Uma restrição FOREIGN-KEY, que pode ser usada para manter a integridade referencial entre uma tabela pai e filho em um conjunto de um DataSet.

As restrições que você especificar em um objeto <xref:System.Data.DataRelation> são implementadas criando automaticamente objetos apropriados ou definindo propriedades. Se você criar uma restrição FOREIGN-KEY usando o objeto <xref:System.Data.DataRelation>, as instâncias da classe <xref:System.Data.ForeignKeyConstraint> serão adicionadas à propriedade <xref:System.Data.DataRelation.ChildKeyConstraint%2A> do objeto de <xref:System.Data.DataRelation>.

Uma restrição UNIQUE é implementada simplesmente definindo a propriedade <xref:System.Data.DataColumn.Unique%2A> de uma coluna de dados como `true` ou adicionando uma instância da classe <xref:System.Data.UniqueConstraint> à propriedade <xref:System.Data.DataRelation.ParentKeyConstraint%2A> do objeto <xref:System.Data.DataRelation>. Para obter informações sobre como suspender restrições em um conjunto de dados, consulte [desativar restrições ao preencher um conjunto de](../data-tools/turn-off-constraints-while-filling-a-dataset.md)dados.

### <a name="referential-integrity-rules"></a>Regras de integridade referencial
Como parte da restrição FOREIGN-KEY, você pode especificar regras de integridade referencial que são aplicadas em três pontos:

- Quando um registro pai é atualizado

- Quando um registro pai é excluído

- Quando uma alteração é aceita ou rejeitada

As regras que você pode fazer são especificadas na enumeração <xref:System.Data.Rule> e estão listadas na tabela a seguir.

|Regra de restrição FOREIGN-KEY|Ação|
| - |------------|
|<xref:System.Data.Rule.Cascade>|A alteração (Update ou Delete) feita no registro pai também é feita em registros relacionados na tabela filho.|
|<xref:System.Data.Rule.SetNull>|Os registros filho não são excluídos, mas a chave estrangeira nos registros filho é definida como <xref:System.DBNull>. Com essa configuração, os registros filho podem ser deixados como "órfãos", ou seja, não têm relação com os registros pai. **Observação:** O uso dessa regra pode resultar em dados inválidos na tabela filho.|
|<xref:System.Data.Rule.SetDefault>|A chave estrangeira nos registros filho relacionados é definida com seu valor padrão (conforme estabelecido pela propriedade de <xref:System.Data.DataColumn.DefaultValue%2A> da coluna).|
|<xref:System.Data.Rule.None>|Nenhuma alteração é feita em registros filho relacionados. Com essa configuração, os registros filho podem conter referências a registros pai inválidos.|

Para obter mais informações sobre atualizações em tabelas de DataSet, consulte [salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md).

### <a name="constraint-only-relations"></a>Relações somente de restrição
Ao criar um objeto de <xref:System.Data.DataRelation>, você tem a opção de especificar que a relação seja usada somente para impor restrições, ou seja, ela também não será usada para acessar registros relacionados. Você pode usar essa opção para gerar um conjunto de registros que seja um pouco mais eficiente e que contenha menos métodos do que um com a funcionalidade de registros relacionados. No entanto, você não poderá acessar os registros relacionados. Por exemplo, uma relação somente de restrição impede que você exclua um registro pai que ainda tem registros filho, e você não pode acessar os registros filho por meio do pai.

## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>Criando manualmente uma relação de dados no Designer de Conjunto de Dados
Quando você cria tabelas de dados usando as ferramentas de design de dados no Visual Studio, as relações são criadas automaticamente se as informações podem ser coletadas da origem dos seus dados. Se você adicionar tabelas de dados manualmente a partir da guia **DataSet** da **caixa de ferramentas**, talvez seja necessário criar a relação manualmente. Para obter informações sobre como criar objetos de <xref:System.Data.DataRelation> de forma programática, consulte [adicionando DataRelations](/dotnet/framework/data/adonet/dataset-datatable-dataview/adding-datarelations).

As relações entre tabelas de dados aparecem como linhas na **Designer de conjunto de dados**, com um glifo de chave e infinito, que ilustra o aspecto de um para muitos da relação. Por padrão, o nome da relação não aparece na superfície de design.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-a-relationship-between-two-data-tables"></a>Para criar uma relação entre duas tabelas de dados

1. Abra o conjunto de dados no **Designer de Conjunto de Dados**. Para obter mais informações, consulte [Walkthrough: Criando um conjunto de dados no designer de conjunto de dados](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Arraste um objeto **relation** da caixa de ferramentas **DataSet** para a tabela de dados filho na relação.

     A caixa de diálogo **relação** é aberta, preenchendo a caixa **tabela filho** com a tabela na qual você arrastou o objeto de **relação** .

3. Selecione a tabela pai na caixa **tabela pai** . A tabela pai contém registros no lado "um" de uma relação um-para-muitos.

4. Verifique se a tabela filho correta é exibida na caixa **tabela filho** . A tabela filho contém registros no lado "muitos" de uma relação um-para-muitos.

5. Digite um nome para a relação na caixa **nome** ou deixe o nome padrão com base nas tabelas selecionadas. Este é o nome do objeto de <xref:System.Data.DataRelation> real no código.

6. Selecione as colunas que unem as tabelas nas listas **colunas de chave** e **colunas de chave estrangeira** .

7. Selecione se deseja criar uma relação, uma restrição ou ambas.

8. Marque ou desmarque a caixa de **relação aninhada** . A seleção dessa opção define a propriedade <xref:System.Data.DataRelation.Nested%2A> como `true` e faz com que as linhas filhas da relação sejam aninhadas dentro da coluna pai quando essas linhas são gravadas como dados XML ou sincronizadas com <xref:System.Xml.XmlDataDocument>. Para obter mais informações, consulte [aninhando DataRelations](/dotnet/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations).

9. Defina as regras a serem impostas quando você estiver fazendo alterações em registros nessas tabelas. Para obter mais informações, consulte <xref:System.Data.Rule>.

10. Clique em **OK** para criar a relação. Uma linha de relação aparece no designer entre as duas tabelas.

#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Para exibir um nome de relação no Designer de Conjunto de Dados

1. Abra o conjunto de dados no **Designer de Conjunto de Dados**. Para obter mais informações, consulte [Walkthrough: Criando um conjunto de dados no designer de conjunto de dados](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. No menu **dados** , selecione o comando **Mostrar rótulos de relação** para exibir o nome da relação. Limpe esse comando para ocultar o nome da relação.

## <a name="see-also"></a>Consulte também

- [Criar e configurar conjuntos de dados no Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)