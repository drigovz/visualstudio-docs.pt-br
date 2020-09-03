---
title: 'Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2054a55f0633d5d4add51fee2e933d9f4d829fcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609975"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Como atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os procedimentos armazenados podem ser adicionados ao Designer Relacional de Objetos e executados como métodos típicos do <xref:System.Data.Linq.DataContext>. Eles também podem ser usados para substituir o [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] comportamento de tempo de execução padrão que executa inserções, atualizações e exclusões quando as alterações são salvas de classes de entidade em um banco de dados (por exemplo, ao chamar o <xref:System.Data.Linq.DataContext.SubmitChanges%2A> método).

> [!NOTE]
> Se seu procedimento armazenado retornar valores que precisem ser reenviados ao cliente (por exemplo, valores calculados no procedimento armazenado), crie parâmetros de saída em seus procedimentos armazenados. Se você não pode usar parâmetros de saída, escreva uma implementação de método parcial em vez de depender das substituições geradas pelo Designer Relacional de Objetos. Os membros mapeados para os valores gerados por banco de dados precisam ser definidos para valores apropriados após a conclusão com êxito de operações INSERT ou UPDATE. Para obter mais informações, consulte [responsabilidades do desenvolvedor ao substituir o comportamento padrão](https://msdn.microsoft.com/library/c6909ddd-e053-46a8-980c-0e12a9797be1).

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] manipula automaticamente valores gerados pelo banco de dados para identidade (incremento automático), ROWGUIDCOL (GUID gerado pelo banco de dados) e colunas de carimbo de data/hora. Os valores gerados pelo banco de dados em outros tipos de coluna resultarão inesperadamente em um valor nulo. Para retornar os valores gerados pelo banco de dados, você deve definir manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> como `true` e <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> como um dos seguintes: <xref:System.Data.Linq.Mapping.AutoSync> , <xref:System.Data.Linq.Mapping.AutoSync> ou <xref:System.Data.Linq.Mapping.AutoSync> .

## <a name="configuring-the-update-behavior-of-an-entity-class"></a>Configurando o comportamento de atualização de uma classe de entidade
 Por padrão, a lógica para atualizar um banco de dados (inserções, atualizações e exclusões), com alterações que foram feitas nos dados em classes de entidade [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)], é fornecida em runtime pelo [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]. O tempo de execução cria comandos de inserção, atualização e exclusão padrão baseados no esquema da tabela (a coluna e as informações de chave primária). Quando o comportamento padrão não é desejado, você pode configurar o comportamento de atualização atribuindo procedimentos armazenados específicos para executar as inserções, atualizações e exclusões necessárias para manipular os dados em sua tabela. Você também pode fazer isso quando o comportamento padrão não é gerado, por exemplo, quando as classes de entidade mapeiam para as exibições. Finalmente, você pode substituir o comportamento de atualização padrão quando o banco de dados exige o acesso à tabela através de procedimentos armazenados.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Para atribuir procedimentos armazenados para substituir o comportamento padrão de uma classe de entidade

1. Abra o arquivo **LINQ to SQL** no designer. (Clique duas vezes no arquivo .dbml em **Gerenciador de Soluções**.)

2. Em **Gerenciador de servidores** / **Gerenciador de banco de dados**, expanda **procedimentos armazenados** e localize os procedimentos armazenados que você deseja usar para os comandos inserir, atualizar e/ou excluir da classe de entidade.

3. Arraste o procedimento armazenado para o Designer Relacional de Objetos.

     O procedimento armazenado é adicionado ao painel de métodos como um método <xref:System.Data.Linq.DataContext>. Para obter mais informações, consulte [métodos DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4. Selecione a classe de entidade para a qual você deseja usar o procedimento armazenado para executar atualizações.

5. Na janela **Propriedades**, selecione o comando a ser substituído (**Insert**, **Update** ou **Delete**).

6. Clique nas reticências (...) ao lado das palavras **Usar Runtime** para abrir a caixa de diálogo **Configurar Comportamento**.

7. Selecione **Personalizar**.

8. Selecione o procedimento armazenado desejado na lista **Personalizar**.

9. Inspecione a lista de **Argumentos de Método** e de **Propriedades de Classe** para verificar se **Argumentos de Método** é mapeado para **Propriedades de Classe** apropriado. Mapeie os argumentos do método original (Original_*ArgumentName*) para as propriedades originais (*PropertyName* (original)) para os comandos Update e Delete.

    > [!NOTE]
    > Por padrão, os argumentos do método são mapeados para as propriedades de classe quando os nomes coincidem. Se os nomes de propriedade forem modificados, não haverá mais correspondência entre a tabela e a classe de entidade. Talvez seja necessário selecionar a propriedade de classe equivalente para mapeamento se o designer não puder determinar o mapeamento correto.

10. Clique em **OK** ou em **Aplicar**.

    > [!NOTE]
    > Você pode continuar a configurar o comportamento para cada combinação de classe/comportamento quando você clica em **Aplicar** depois de cada alteração. Se você alterar a classe ou o comportamento antes de clicar em **aplicar**, uma caixa de diálogo de aviso que fornece uma oportunidade para aplicar todas as alterações será exibida.

     Para reverter o uso da lógica de tempo de execução padrão para atualizações, clique nas reticências ao lado do comando Inserir, atualizar ou excluir na janela **Propriedades** e, em seguida, selecione **usar tempo de execução** na caixa de diálogo **Configurar comportamento** .

## <a name="see-also"></a>Consulte Também
 Instruções [de LINQ to SQL nos métodos de DataContext do Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [(o/r designer)](../data-tools/datacontext-methods-o-r-designer.md) [Walkthrough: criação de classes de LINQ to SQL (o-r designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [operações de inserção, atualização e exclusão](https://msdn.microsoft.com/library/26a43a4f-83c9-4732-806d-bb23aad0ff6b)
