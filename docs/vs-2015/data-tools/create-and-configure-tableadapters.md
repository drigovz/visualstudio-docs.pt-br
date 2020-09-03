---
title: Criar e configurar TableAdapters | Microsoft Docs
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
- table adapters, creating
- creating TableAdapters
- data [Visual Studio], creating data components
- data [Visual Studio], TableAdapters
- data [Visual Studio], creating table adapters
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9a2136960dfcbbbcf63fbefeb16d527793d4b939
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72631034"
---
# <a name="create-and-configure-tableadapters"></a>Criar e configurar TableAdapters
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os TableAdapters fornecem comunicação entre o aplicativo e um banco de dados. Eles se conectam ao banco de dados, executam consultas ou procedimentos armazenados, e retornam uma nova tabela data ou preenchem um existente <xref:System.Data.DataTable> com os dados retornados. Os TableAdapters também podem enviar dados atualizados do seu aplicativo de volta para o banco de dados.

 Os TableAdapters são criados para você quando você executa uma das seguintes ações:

- Execute o [Assistente de configuração da fonte de dados](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) e selecione o tipo de fonte de dados do **banco** de dados ou do **serviço Web** .

- Arraste objetos de banco de dados de [Gerenciador de servidores](https://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) para o **Designer de conjunto de dados**.

  Você pode criar um novo TableAdapter e configurá-lo com uma fonte de dados arrastando um TableAdapter da caixa de ferramentas para uma região vazia na superfície de **Designer de conjunto de dados** .

  Para obter uma introdução aos TableAdapters, consulte [preencher conjuntos de valores usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="use-the-tableadapter-configuration-wizard"></a>Usar o assistente de configuração do TableAdapter
 Execute o **Assistente de configuração do TableAdapter** para criar ou editar TableAdapters e suas tabelas de tabela associadas. Você pode configurar um TableAdapter existente clicando com o botão direito do mouse nele na **Designer de conjunto de dados**.

 ![Assistente de configuração do adaptador de tabela raddata](../data-tools/media/raddata-table-adapter-configuration-wizard.png "Assistente de configuração do adaptador de tabela raddata")

 Se você arrastar um novo TableAdapter da caixa de ferramentas quando o **Designer de conjunto de dados** estiver em foco, o assistente solicitará que você especifique a fonte de dados à qual o TableAdapter deve se conectar e que tipo de comandos ele deve usar para se comunicar com o Database, instruções SQL ou procedimentos armazenados. Você não verá isso se estiver configurando um TableAdapter que já está associado a uma fonte de dados.

- O uso da opção **criar métodos para enviar atualizações diretamente para o banco de dados** é equivalente a definir a `GenerateDBDirectMethods` propriedade como true. A opção fica não disponível quando a instrução SQL original não fornecer informações suficientes ou a consulta não for uma consulta atualizável. Essa situação pode ocorrer, por exemplo, em consultas de **junção** e consultas que retornam um único valor (escalar).

- Você tem a opção de criar um novo procedimento armazenado no banco de dados subjacente se tiver as permissões corretas para o banco de dados. Se você não tiver essas permissões, isso não será uma opção.

- Você também pode optar por executar procedimentos armazenados existentes para os comandos **Select**, **Insert**, **Update**e **delete** do TableAdapter. O procedimento armazenado que é atribuído ao comando **Update** , por exemplo, é executado quando o `TableAdapter.Update()` método é chamado.

     Mapear parâmetros desde o procedimento armazenado selecionado até as colunas correspondentes na tabela de dados. Por exemplo, se o procedimento armazenado aceitar um parâmetro chamado `@CompanyName` que ele passa para a `CompanyName` coluna na tabela, defina a **coluna de origem** do `@CompanyName` parâmetro como `CompanyName` .

    > [!NOTE]
    > O procedimento armazenado atribuído ao comando SELECT é executado chamando-se o método do TableAdapter que você nomeou na próxima etapa do assistente. O método padrão é `Fill` , portanto, o código que é normalmente usado para executar o procedimento SELECT é `TableAdapter.Fill(tableName)` . Se você alterar o nome padrão de `Fill` , substitua `Fill` pelo nome que você atribui e substitua "TableAdapter" pelo nome real do TableAdapter (por exemplo, `CustomersTableAdapter` ).

- As **Opções avançadas** no assistente permitem que você gere instruções INSERT, Update e DELETE com base na instrução SELECT definida na página **gerar instruções SQL** . Use a simultaneidade otimista e especifique se deseja atualizar a tabela de dados após a execução das instruções INSERT e UPDATE.

## <a name="configure-a-tableadapters-fill-method"></a>Configurar o método Fill de um TableAdapter
 Às vezes, você pode querer alterar o esquema da tabela do TableAdapter. Para fazer isso, modifique o método principal do TableAdapter `Fill` . Os TableAdapters são criados com um `Fill` método primário que define o esquema da tabela de dados associada. O `Fill` método principal é baseado na consulta ou no procedimento armazenado que você inseriu quando configurou originalmente o TableAdapter. Ele é o primeiro método (mais alto) na tabela de dados no designer de DataSet.

 ![TableAdapter com várias consultas](../data-tools/media/tableadapter.gif "TableAdapter")

 As alterações feitas no método Main do TableAdapter `Fill` são refletidas no esquema da tabela de dados associada. Por exemplo, remover uma coluna da consulta no `Fill` método Main também remove a coluna da tabela de dados associada. Além disso, remover a coluna do `Fill` método Main remove a coluna de quaisquer consultas adicionais para esse TableAdapter.

 Você pode usar o assistente de configuração de consulta do TableAdapter para criar e editar consultas adicionais para o TableAdapter. Essas consultas adicionais devem estar em conformidade com o esquema de tabela, a menos que elas retornem um valor escalar.  As consultas adicionais têm nomes que você especifica (por exemplo, `CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, "Seattle")` .)

#### <a name="to-start-the-tableadapter-query-configuration-wizard-with-a-new-query"></a>Para iniciar o assistente de configuração de consulta do TableAdapter com uma nova consulta

1. Abra o conjunto de dados no **Designer de Conjunto de Dados**.

2. Se você estiver criando uma nova consulta, arraste um objeto de **consulta** da guia **DataSet** da **caixa de ferramentas** para um <xref:System.Data.DataTable> ou selecione **Adicionar consulta** no menu de atalho do TableAdapter. Você também pode arrastar um objeto de **consulta** para uma área vazia da **Designer de conjunto de dados**, que cria um TableAdapter sem um associado <xref:System.Data.DataTable> . Essas consultas só podem retornar valores únicos (escalares) ou executar comandos UPDATE, INSERT ou DELETE no banco de dados.

3. Na tela **escolher sua conexão de dados** , selecione ou crie a conexão que será usada pela consulta.

    > [!NOTE]
    > Essa tela só aparece quando o designer não pode determinar a conexão apropriada a ser usada ou quando não há conexões disponíveis.

4. Na tela **escolher um tipo de comando** , selecione um dos seguintes métodos de busca de dados do banco de dados:

    - O **uso de instruções SQL** permite que você digite uma instrução SQL para selecionar os dados do banco de dado.

    - **Criar novo procedimento armazenado** permite que o assistente crie um novo procedimento armazenado (no banco de dados) com base na instrução SELECT especificada.

    - O **uso de procedimentos armazenados existentes** permite que você execute um procedimento armazenado existente ao executar a consulta.

#### <a name="to-start-the-tableadapter-query-configuration-wizard-on-an-existing-query"></a>Para iniciar o assistente de configuração de consulta do TableAdapter em uma consulta existente

- Se você estiver editando uma consulta TableAdapter existente, clique com o botão direito do mouse na consulta e escolha **Configurar** no menu de atalho.

    > [!NOTE]
    > Clicar com o botão direito do mouse na consulta principal de um TableAdapter reconfigura o TableAdapter e o <xref:System.Data.DataTable> esquema. No entanto, clicar com o botão direito do mouse em uma consulta adicional em um TableAdapter apenas configurará a consulta selecionada. O **Assistente de configuração do TableAdapter** reconfigura a definição do TableAdapter, enquanto o assistente de configuração de consulta do TableAdapter reconfigura a consulta selecionada apenas.

#### <a name="to-add-a-global--query-to-a-tableadapter"></a>Para adicionar uma consulta global a um TableAdapter

- *Consultas globais* são consultas SQL que retornam um único valor (escalar) ou nenhum valor. Normalmente, as funções globais executam operações de banco de dados, como inserções, atualizações, exclusões. Eles também agregam informações, como uma contagem de clientes em uma tabela ou os encargos totais de todos os itens em uma ordem específica.

     Você adiciona consultas globais arrastando um objeto de **consulta** da guia **DataSet** da **caixa de ferramentas** para uma área vazia da **Designer de conjunto de dados**.

- Forneça uma consulta que execute a tarefa desejada, por exemplo, `SELECT COUNT(*) AS CustomerCount FROM Customers` .

    > [!NOTE]
    > Arrastar um objeto de **consulta** diretamente para o **Designer de conjunto de dados** cria um método que retorna apenas um valor escalar (único). Embora a consulta ou o procedimento armazenado selecionado possa retornar mais de um único valor, o método criado pelo assistente retornará apenas um único valor. Por exemplo, a consulta pode retornar a primeira coluna da primeira linha dos dados retornados.

## <a name="see-also"></a>Consulte Também
 [Preencher conjuntos de dados usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
