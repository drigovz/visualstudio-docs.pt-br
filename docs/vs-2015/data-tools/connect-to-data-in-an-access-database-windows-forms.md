---
title: Conectar-se a dados em um Access Database (Windows Forms) | Microsoft Docs
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
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8426e9fcaa29bef36b6701c78d622f6f42fd1171
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651141"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Conectar-se a dados em um banco de dados do Access (Windows Forms)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode se conectar a um banco de dados do Access (um arquivo. MDF ou. accdb) usando o Visual Studio. Depois de definir a conexão, os dados são exibidos na janela **Fontes de Dados**. Nela, é possível arrastar tabelas ou exibições para os formulários.

## <a name="prerequisites"></a>Pré-requisitos
 Para usar esses procedimentos, você precisa de um projeto de aplicativo Windows Forms e de um banco de dados do Access (arquivo. accdb) ou de um banco de dados do Access 2000 – 2003 (arquivo. mdb). Siga o procedimento correspondente ao tipo de arquivo.

## <a name="creating-the-dataset-for-an-accdb-file"></a>Criando o Conjunto de Dados para um arquivo .accdb
 Você pode se conectar a bancos de dados criados por meio do Access 2013, do Office 365, do Access 2010 ou do Access 2007 usando o procedimento a seguir.

#### <a name="to-create-the-dataset"></a>Para criar o conjunto de dados

1. Abra o aplicativo do Windows Forms ao qual você deseja conectar dados.

2. No menu **Exibir** , selecione **outras**  >  **fontes de dados**do Windows.

     ![Exibir outras fontes de dados do Windows](../data-tools/media/viewdatasources.png "ViewDataSources")

3. Na janela **Fontes de Dados**, clique em **Adicionar Nova Fonte de Dados**.

     ![Adicionar nova fonte de dados](../data-tools/media/dataaddnewdatasource.png "dataAddNewDataSource")

4. Selecione **banco** de dados na página **escolher um tipo de fonte de dado** e, em seguida, selecione **Avançar**.

5. Selecione **DataSet** na página **escolher um modelo de banco de dados** e, em seguida, selecione **Avançar**.

6. Na página **Escolha a Conexão de Dados**, selecione **Nova Conexão** para configurar uma nova conexão de dados.

7. Altere a **fonte de dados** para **.NET Framework provedor de dados para OLE DB**.

     ![Alterar Provedor de Dados para OLE DB](../data-tools/media/datachangedatasourceoledb.png "dataChangeDataSourceOLEDB")

    > [!IMPORTANT]
    > Embora uma fonte de dados do **Microsoft Access Database File (OLE DB)** possa parecer com a escolha certa, você usa esse tipo de fonte de dados somente para arquivos de banco de dado. mdb.

8. No **provedor OLE DB**, selecione **Microsoft Office 12,0 acesso Mecanismo de Banco de Dados provedor de OLE DB**.

     ![Provedor de OLE DB Microsoft Office acesso 12,0](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")

9. Em **nome do servidor ou arquivo**, especifique o caminho e o nome do arquivo. accdb ao qual você deseja se conectar e, em seguida, selecione **OK**.

    > [!NOTE]
    > Se o arquivo de banco de dados tiver um nome de usuário e uma senha, especifique-os antes de selecionar **OK**.

10. Selecione **Avançar** na página **escolher sua conexão de dados** .

11. Selecione **Avançar** na página **salvar cadeia de conexão no arquivo de configuração do aplicativo** .

12. Expanda o nó **Tabelas** na página **Escolher Objetos do Banco de Dados**.

13. Selecione quaisquer tabelas ou exibições desejadas no conjunto de seus conjuntos de seus e, em seguida, selecione **concluir**.

     O Conjunto de Dados é adicionado ao projeto e as tabelas e as exibições são mostradas na janela **Fontes de Dados**.

## <a name="creating-the-dataset-for-an-mdb-file"></a>Criando o conjunto de um arquivo. mdb
 Você cria o conjunto de dados executando o **Assistente de Configuração de Fonte de Dados**.

#### <a name="to-create-the-dataset"></a>Para criar o conjunto de dados

1. Abra o aplicativo do Windows Forms ao qual você deseja conectar dados.

2. No menu **Exibir** , selecione **outras**  >  **fontes de dados**do Windows.

     ![Exibir outras fontes de dados do Windows](../data-tools/media/viewdatasources.png "ViewDataSources")

3. Na janela **Fontes de Dados**, clique em **Adicionar Nova Fonte de Dados**.

4. Selecione **banco** de dados na página **escolher um tipo de fonte de dado** e, em seguida, selecione **Avançar**.

5. Selecione **DataSet** na página **escolher um modelo de banco de dados** e, em seguida, selecione **Avançar**.

6. Na página **Escolha a Conexão de Dados**, selecione **Nova Conexão** para configurar uma nova conexão de dados.

7. Se a fonte de dados não for um **arquivo de banco de dado do Microsoft Access (OLE DB)**, selecione **alterar** para abrir a caixa de diálogo **Alterar fonte de dados** e selecione o arquivo de banco de dado **do Microsoft Access**e, em seguida, selecione **OK**.

8. No **nome do arquivo de banco de dados**, especifique o caminho e o nome do arquivo. mdb ao qual você deseja se conectar e, em seguida, selecione **OK**.

     ![Adicionar arquivo de banco de dados de acesso de conexão](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")

9. Selecione **Avançar** na página **escolher sua conexão de dados** .

10. Selecione **Avançar** na página **salvar cadeia de conexão no arquivo de configuração do aplicativo** .

11. Expanda o nó **Tabelas** na página **Escolher Objetos do Banco de Dados**.

12. Selecione quaisquer tabelas ou exibições desejadas no conjunto de seus conjuntos de seus e, em seguida, selecione **concluir**.

     O Conjunto de Dados é adicionado ao projeto e as tabelas e as exibições são mostradas na janela **Fontes de Dados**.

## <a name="security"></a>Segurança
 O armazenamento das informações confidenciais (como uma senha) pode afetar a segurança do aplicativo. O uso da Autenticação do Windows (também conhecida como segurança integrada) é uma maneira mais segura de controlar o acesso a um banco de dados. Para obter mais informações, consulte [protegendo informações de conexão](https://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).

## <a name="next-steps"></a>Próximas etapas
 O conjunto de dados que você acabou de criar agora está disponível na janela **Data Sources** . Agora é possível realizar qualquer uma das seguintes tarefas:

- Selecione os itens na janela **fontes de dados** e arraste-os para o formulário (consulte [associar controles de Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).

- Abra a fonte de dados no Designer de Conjunto de Dados para adicionar ou editar os objetos que constituem o conjunto de dados.

- Adicione a lógica de validação para o <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> evento ou das tabelas de dados no DataSet (consulte [Validate data in](../data-tools/validate-data-in-datasets.md)DataSets).

## <a name="see-also"></a>Consulte Também

 [Preparando seu aplicativo para receber](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [controles de ligação de dados para dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md) [Validando](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e) [orientações](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4) de dados de dados