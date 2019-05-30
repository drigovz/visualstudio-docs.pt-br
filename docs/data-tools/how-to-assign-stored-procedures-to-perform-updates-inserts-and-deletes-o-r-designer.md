---
title: Use os procedimentos armazenados em LINQ to SQL para atualizar dados (O/R Designer)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 58dfb1016097429eeab10c3b50262adc7015e818
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260799"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Como: Atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)

Os procedimentos armazenados podem ser adicionados ao **Designer Relacional de Objetos** e executados como métodos típicos do <xref:System.Data.Linq.DataContext>. Eles também podem ser usados para substituir o padrão LINQ ao comportamento de tempo de execução do SQL que executa inserções, atualizações e exclusões quando alterações são salvas de classes de entidade para um banco de dados (por exemplo, ao chamar o <xref:System.Data.Linq.DataContext.SubmitChanges%2A> método).

> [!NOTE]
> Se seu procedimento armazenado retornar valores que precisem ser reenviados ao cliente (por exemplo, valores calculados no procedimento armazenado), crie parâmetros de saída em seus procedimentos armazenados. Se você não pode usar parâmetros de saída, escreva uma implementação de método parcial em vez de depender das substituições geradas pelo Designer Relacional de Objetos. Os membros mapeados para os valores gerados por banco de dados precisam ser definidos para valores apropriados após a conclusão com êxito de operações INSERT ou UPDATE. Para obter mais informações, consulte [responsabilidades do desenvolvedor em Substituir padrão comportamento](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior).

> [!NOTE]
> O LINQ to SQL lida com valores de banco de dados gerado automaticamente para a identidade (incremento automático), rowguidcol (GUID gerado por banco de dados) e colunas de carimbo de hora. Os valores gerados pelo banco de dados em outros tipos de coluna resultarão inesperadamente em um valor nulo. Para retornar os valores gerados pelo banco de dados, você deve definir manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> à **verdadeira** e <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> para um dos seguintes: [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>), ou [AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="configure-the-update-behavior-of-an-entity-class"></a>Configurar o comportamento de atualização de uma classe de entidade

Por padrão, a lógica para atualizar um banco de dados (inserções, atualizações e exclusões) com as alterações feitas aos dados em LINQ para classes de entidade do SQL é fornecida pelo LINQ to SQL de tempo de execução. O tempo de execução cria comandos padrão INSERT, UPDATE e DELETE que se baseiam no esquema da tabela (as informações de coluna e chave primária). Quando o comportamento padrão não for desejado, você pode configurar o comportamento de atualização atribuindo procedimentos armazenados específicos para executar as inserções, atualizações e exclusões necessárias para manipular os dados em sua tabela. Você também pode fazer isso quando o comportamento padrão não é gerado, por exemplo, quando as classes de entidade mapeiam para as exibições. Finalmente, você pode substituir o comportamento de atualização padrão quando o banco de dados exige o acesso à tabela através de procedimentos armazenados.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Para atribuir procedimentos armazenados para substituir o comportamento padrão de uma classe de entidade

1. Abra o arquivo **LINQ to SQL** no designer. (Clique duas vezes no arquivo **.dbml** em **Gerenciador de Soluções**.)

2. Em **Gerenciador de Servidores** ou **Gerenciador de Banco de Dados**, expanda **Procedimentos Armazenados** e localize os procedimentos armazenados a serem usados com os comandos Insert, Update e/ou Delete da classe de entidade.

3. Arraste o procedimento armazenado para o **Designer Relacional de Objetos**.

     O procedimento armazenado é adicionado ao painel de métodos como um método <xref:System.Data.Linq.DataContext>. Para obter mais informações, consulte [métodos de DataContext (Designer relacional de objetos)](../data-tools/datacontext-methods-o-r-designer.md).

4. Selecione a classe de entidade para a qual você deseja usar o procedimento armazenado para executar atualizações.

5. Na janela **Propriedades**, selecione o comando a ser substituído (**Insert**, **Update** ou **Delete**).

6. Clique nas reticências (...) ao lado das palavras **Usar Tempo de Execução** para abrir a caixa de diálogo **Configurar Comportamento**.

7. Selecione **Personalizar**.

8. Selecione o procedimento armazenado desejado na lista **Personalizar**.

9. Inspecione a lista de **Argumentos de Método** e de **Propriedades de Classe** para verificar se **Argumentos de Método** é mapeado para **Propriedades de Classe** apropriado. Mapeie os argumentos de método originais (`Original_<ArgumentName>`) para as propriedades originais (`<PropertyName> (Original)`) para o `Update` e `Delete` comandos.

    > [!NOTE]
    > Por padrão, os argumentos do método são mapeados para as propriedades de classe quando os nomes coincidem. Se os nomes de propriedade forem modificados, não haverá mais correspondência entre a tabela e a classe de entidade. Talvez seja necessário selecionar a propriedade de classe equivalente para mapeamento se o designer não puder determinar o mapeamento correto.

10. Clique em **OK** ou em **Aplicar**.

    > [!NOTE]
    > Você pode continuar a configurar o comportamento para cada combinação de classe e o comportamento desde que você clique em **aplicar** após cada alteração. Se você alterar a classe ou o comportamento antes de clicar em **aplicar**, uma caixa de diálogo de aviso é exibida e fornece a você uma oportunidade para aplicar suas alterações.

Para voltar a usar a lógica padrão em tempo de execução para atualizações, clique nas reticências ao lado do comando **Insert**, **Update** ou **Delete**, na janela **Propriedades**, e selecione **Usar tempo de execução** na caixa de diálogo **Configurar Comportamento**.

## <a name="see-also"></a>Consulte também

- [Ferramentas do LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Métodos DataContext](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Inserir, atualizar e excluir operações (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)
