---
title: Criar um aplicativo de dados simples usando ADO.NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
caps.latest.revision: 46
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b524c9d630f30edd226265ac150ef7ec4f6c60d8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651068"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Criar um aplicativo de dados simples usando o ADO.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando você cria um aplicativo que manipula dados em um banco de dado, executa tarefas básicas, como definir cadeias de conexão, inserir dados e executar procedimentos armazenados. Ao seguir este tópico, você pode descobrir como interagir com um banco de dados de dentro de um aplicativo simples Windows Forms "formulários por data" usando C# Visual ou Visual Basic e ADO.net.  Todas as tecnologias de dados do .NET, incluindo conjuntos, LINQ to SQL e Entity Framework, por fim, executam etapas muito semelhantes às mostradas neste artigo.

 Este artigo demonstra uma maneira simples de obter dados de um banco de dado de maneira muito rápida. Se seu aplicativo precisar modificar dados de maneiras não triviais e atualizar o banco de dado, você deverá considerar o uso de Entity Framework e o uso da vinculação de dados para sincronizar automaticamente os controles de interface do usuário com as alterações nos dados subjacentes.

> [!IMPORTANT]
> Para manter o código simples, ele não inclui manipulação de exceção pronta para produção.

 **Neste tópico**

- [Configurar o banco de dados de exemplo](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_setupthesampledatabase)

- [Criar os formulários e adicionar controles](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_createtheformsandaddcontrols)

- [Armazenar a cadeia de conexão](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_storetheconnectionstring)

- [Recuperar a cadeia de conexão](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_retrievetheconnectionstring)

- [Escreva o código para os formulários](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_writethecodefortheforms)

- [Testar seu aplicativo](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_testyourapplication)

## <a name="prerequisites"></a>Prerequisites
 Para criar o aplicativo, você precisará de:

- Visual Studio Community Edition.

- LocalDB do SQL Server Express.

- O pequeno banco de dados de exemplo que você cria seguindo as etapas em [criar um banco de dados SQL usando um script](../data-tools/create-a-sql-database-by-using-a-script.md).

- A cadeia de conexão do banco de dados depois de configurado. Você pode encontrar esse valor abrindo **pesquisador de objetos do SQL Server**, abrindo o menu de atalho para o banco de dados, selecionando **Propriedades**e, em seguida, rolando para a propriedade **ConnectionString** .

  Este tópico pressupõe que você esteja familiarizado com a funcionalidade básica do IDE do Visual Studio e pode criar um aplicativo Windows Forms, adicionar formulários a esse projeto, colocar botões e outros controles nesses formulários, definir propriedades desses controles e codificar eventos simples . Se você não estiver familiarizado com essas tarefas, sugerimos que você conclua o [introdução C# com Visual e Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) antes de iniciar este tópico.

## <a name="BKMK_setupthesampledatabase"></a>Configurar o banco de dados de exemplo
 O banco de dados de exemplo para este passo a passos consiste nas tabelas Customer e Orders. As tabelas não contêm dados inicialmente, mas você adicionará dados quando executar o aplicativo que você criará. O banco de dados também tem cinco procedimentos armazenados simples. [Criar um banco de dados SQL usando um script](../data-tools/create-a-sql-database-by-using-a-script.md) contém um script TRANSACT-SQL que cria as tabelas, as chaves primária e estrangeira, as restrições e os procedimentos armazenados.

## <a name="BKMK_createtheformsandaddcontrols"></a>Criar os formulários e adicionar controles

1. Crie um projeto para um aplicativo Windows Forms e nomeie-o SimpleDataApp.

    O Visual Studio cria o projeto e vários arquivos, incluindo um Windows Form vazio chamado Form1.

2. Adicione dois formulários do Windows ao seu projeto para que ele tenha três formulários e dê a eles os seguintes nomes:

   - Navegação

   - NewCustomer

   - FillOrCancel

3. Para cada formulário, adicione as caixas de texto, os botões e outros controles que aparecem nas ilustrações a seguir. Para cada controle, defina as propriedades que as tabelas descrevem.

   > [!NOTE]
   > A caixa de grupo e os controles de rótulo adicionam clareza, mas não são usados no código.

   **Formulário de navegação**

   ![Caixa de diálogo de navegação](../data-tools/media/simpleappnav.png "SimpleAppNav")

|Controles para o formulário de navegação|Propriedades|
|--------------------------------------|----------------|
|Botão|Nome = btnGoToAdd|
|Botão|Nome = btnGoToFillOrCancel|
|Botão|Nome = btnExit|

 **Formulário NewCustomer**

 ![Adicionar um novo cliente e fazer um pedido](../data-tools/media/simpleappnewcust.png "SimpleAppNewCust")

|Controles para o formulário NewCustomer|Propriedades|
|---------------------------------------|----------------|
|TextBox|Nome = txtCustomerName|
|TextBox|Nome = txtCustomerID<br /><br /> ReadOnly = true|
|Botão|Nome = btnCreateAccount|
|NumericUpdown|DecimalPlaces = 0<br /><br /> Máximo = 5000<br /><br /> Nome = numOrderAmount|
|DateTimePicker|Formato = curto<br /><br /> Nome = dtpOrderDate|
|Botão|Nome = btnPlaceOrder|
|Botão|Nome = btnAddAnotherAccount|
|Botão|Nome = btnAddFinish|

 **Formulário FillOrCancel**

 ![preencher ou cancelar pedidos](../data-tools/media/simpleappcancelfill.png "SimpleAppCancelFill")

|Controles para o formulário FillOrCancel|Propriedades|
|----------------------------------------|----------------|
|TextBox|Nome = txtOrderID|
|Botão|Nome = btnFindByOrderID|
|DateTimePicker|Formato = curto<br /><br /> Nome = dtpFillDate|
|DataGridView|Nome = dgvCustomerOrders<br /><br /> ReadOnly = true<br /><br /> RowHeadersVisible = False|
|Botão|Nome = btnCancelOrder|
|Botão|Nome = btnFillOrder|
|Botão|Nome = btnFinishUpdates|

## <a name="BKMK_storetheconnectionstring"></a>Armazenar a cadeia de conexão
 Quando seu aplicativo tenta abrir uma conexão com o banco de dados, seu aplicativo deve ter acesso à cadeia de conexão. Para evitar inserir a cadeia de caracteres manualmente em cada formulário, armazene a cadeia de caracteres no arquivo de configuração do aplicativo em seu projeto e crie um método que retorne a cadeia de caracteres quando o método for chamado de qualquer formulário em seu aplicativo.

 Você pode encontrar a cadeia de conexão no **pesquisador de objetos do SQL Server** clicando com o botão direito do mouse no banco de dados, selecionando **Propriedades**e localizando a propriedade ConnectionString. Use CTRL + A para selecionar a cadeia de caracteres.

1. Em **Gerenciador de soluções**, selecione o nó **Propriedades** no projeto e, em seguida, selecione **configurações. configurações**.

2. Na coluna **nome** , digite `connString`.

3. Na lista **tipo** , selecione **(cadeia de conexão)** .

4. Na lista **escopo** , selecione **aplicativo**.

5. Na coluna **valor** , insira sua cadeia de conexão (sem aspas externas) e, em seguida, salve as alterações.

> [!NOTE]
> Em um aplicativo real, você deve armazenar a cadeia de conexão com segurança, conforme descrito em [cadeias de conexão e arquivos de configuração](https://msdn.microsoft.com/library/37df2641-661e-407a-a3fb-7bf9540f01e8).

## <a name="BKMK_retrievetheconnectionstring"></a>Recuperar a cadeia de conexão

1. Na barra de menus, selecione **projeto**  > **Adicionar referência**e, em seguida, adicione uma referência a System. Configuration. dll.

2. Na barra de menus, selecione **projeto**  > **Adicionar classe** para adicionar um arquivo de classe ao seu projeto e, em seguida, nomeie o arquivo `Utility`.

     O Visual Studio cria o arquivo e o exibe em **Gerenciador de soluções**.

3. No arquivo do utilitário, substitua o código do espaço reservado pelo código a seguir. Observe os comentários numerados (prefixados com o util-) que identificam as seções do código. A tabela que segue o código chama pontos-chave.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    //Util-1 More namespaces.
    using System.Configuration;

    namespace SimpleDataApp
    {
        internal class Utility
        {

            //Get the connection string from App config file.
            internal static string GetConnectionString()
            {
                //Util-2 Assume failure.
                string returnValue = null;

                //Util-3 Look for the name in the connectionStrings section.
                ConnectionStringSettings settings =
                ConfigurationManager.ConnectionStrings["SimpleDataApp.Properties.Settings.connString"];

                //If found, return the connection string.
                if (settings != null)
                    returnValue = settings.ConnectionString;

                return returnValue;
            }
        }
    }
    ```

    ```vb
    Imports System
    Imports System.Collections.Generic
    Imports System.Linq
    Imports System.Text
    Imports System.Threading.Tasks
    ' Util-1 More namespaces.
    Imports System.Configuration

    Namespace SimpleDataApp
        Friend Class Utility

            ' Get connection string from App config file.
            Friend Shared Function GetConnectionString() As String

                ' Util-2 Assume failure.
                Dim returnValue As String = Nothing

                ' Util-3 Look for the name in the connectionStrings section.
                Dim settings As ConnectionStringSettings = ConfigurationManager.ConnectionStrings("SimpleDataApp.My.MySettings.connString")

                ' If found, return the connection string.
                If settings IsNot Nothing Then
                    returnValue = settings.ConnectionString
                End If

                Return returnValue
            End Function
        End Class
    End Namespace
    ```

    |Comentário|Descrição|
    |-------------|-----------------|
    |Util-1|Adicione o namespace `System.Configuration`.|
    |Util-2|Defina uma variável, `returnValue` e inicialize-a para `null` (C#) ou `Nothing` (Visual Basic).|
    |Util-3|Embora você tenha inserido `connString` como o nome da cadeia de conexão na janela **Propriedades** , você deve especificar `"SimpleDataApp.Properties.Settings.connString"` (C#) ou `"SimpleDataApp.My.MySettings.connString"` (Visual Basic) no código.|

## <a name="BKMK_writethecodefortheforms"></a>Escreva o código para os formulários
 Esta seção contém breves visões gerais do que cada formulário faz e mostra o código que cria os formulários. Comentários numerados identificam as seções do código.

### <a name="navigation-form"></a>Formulário de navegação
 O formulário de navegação é aberto quando você executa o aplicativo. O botão **Adicionar uma conta** abre o formulário NewCustomer. O botão **preencher ou cancelar pedidos** abre o formulário FillOrCancel. O botão **sair** fecha o aplicativo.

#### <a name="make-the-navigation-form-the-startup-form"></a>Tornar o formulário de navegação o formulário de inicialização
 Se você estiver usando C#o, em **Gerenciador de Soluções**, abra Program.cs e altere a linha de `Application.Run` para esta: `Application.Run(new Navigation());`

 Se você estiver usando Visual Basic, em **Gerenciador de soluções**, abra a janela **Propriedades** , selecione a guia **aplicativo** e, em seguida, selecione **SimpleDataApp. Navigation** na lista **formulário de inicialização** .

#### <a name="create-event-handlers"></a>Criar manipuladores de eventos
 Clique duas vezes nos três botões no formulário para criar métodos de manipulador de eventos vazios.

#### <a name="create-code-for-navigation"></a>Criar código para navegação
 No formulário de navegação, substitua o código existente pelo código a seguir.

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace SimpleDataApp
{
    public partial class Navigation : Form
    {
        public Navigation()
        {
            InitializeComponent();
        }

        //Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.
        private void btnGoToAdd_Click(object sender, EventArgs e)
        {
            Form frm = new NewCustomer();
            frm.Show();
        }

        //Open the FillorCancel form as a dialog box.
        private void btnGoToFillOrCancel_Click(object sender, EventArgs e)
        {
            Form frm = new FillOrCancel();
            frm.ShowDialog();
        }

        //Close the application, not just the Navigation form.
        private void btnExit_Click(object sender, EventArgs e)
        {
            this.Close();
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports System.ComponentModel
Imports System.Data
Imports System.Drawing
Imports System.Linq
Imports System.Text
Imports System.Threading.Tasks
Imports System.Windows.Forms

Namespace SimpleDataApp
    Partial Public Class Navigation
        Inherits Form
        Public Sub New()
            InitializeComponent()
        End Sub

        ' Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.
        Private Sub btnGoToAdd_Click() Handles btnGoToAdd.Click
            Dim frm As Form = New NewCustomer()
            frm.Show()
        End Sub

        ' Open the FillorCancel form as a dialog box.
        Private Sub btnGoToFillOrCancel_Click() Handles btnGoToFillOrCancel.Click
            Dim frm As Form = New FillOrCancel()
            frm.ShowDialog()
        End Sub

        ' Close the application, not just the Navigation form.
        Private Sub btnExit_Click() Handles btnExit.Click
            Me.Close()
        End Sub
    End Class
End Namespace

```

### <a name="newcustomer-form"></a>Formulário NewCustomer
 Quando você insere um nome de cliente e, em seguida, seleciona o botão **criar conta** , o formulário NewCustomer cria uma conta de cliente e SQL Server retorna um valor de identidade como o novo número da conta. Em seguida, faça um pedido para a nova conta especificando uma quantidade e uma data de pedido e selecionando o botão **fazer pedido** .

#### <a name="create-event-handlers"></a>Criar manipuladores de eventos
 Crie um manipulador de eventos de clique vazio para cada botão no formulário.

#### <a name="create-code-for-newcustomer"></a>Criar código para NewCustomer
 Adicione o código a seguir ao formulário NewCustomer. Percorra cada bloco de código usando os comentários numerados e a tabela após o código.

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
//NC-1 More namespaces.
using System.Data.SqlClient;
using System.Configuration;

namespace SimpleDataApp
{
    public partial class NewCustomer : Form
    {
        //NC-2 Storage for IDENTITY values returned from database.
        private int parsedCustomerID;
        private int orderID;

        //NC-3 Specify a connection string.
        string connstr = SimpleDataApp.Utility.GetConnectionString();

        public NewCustomer()
        {
            InitializeComponent();
        }

        //NC-4 Create account.
        private void btnCreateAccount_Click(object sender, EventArgs e)
        {
            //NC-5 Set up and run stored procedure only if Customer Name is present.
            if (isCustomerName())
            {

                //NC-6 Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //NC-7 Create a SqlCommand, and identify it as a stored procedure.
                SqlCommand cmdNewCustomer = new SqlCommand("Sales.uspNewCustomer", conn);
                cmdNewCustomer.CommandType = CommandType.StoredProcedure;

                //NC-8 Add input parameter from the stored procedure and specify what to use as its value.
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerName", SqlDbType.NVarChar, 40));
                cmdNewCustomer.Parameters["@CustomerName"].Value = txtCustomerName.Text;

                //NC-9 Add output parameter.
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));
                cmdNewCustomer.Parameters["@CustomerID"].Direction = ParameterDirection.Output;

                //NC-10 try-catch-finally
                try
                {
                    //NC-11 Open the connection.
                    conn.Open();

                    //NC-12 Run the stored procedure.
                    cmdNewCustomer.ExecuteNonQuery();

                    //NC-13 Customer ID is an IDENTITY value from the database.
                    this.parsedCustomerID = (int)cmdNewCustomer.Parameters["@CustomerID"].Value;
                    this.txtCustomerID.Text = Convert.ToString(parsedCustomerID);

                }
                catch
                {
                    //NC-14 A simple catch.

                    MessageBox.Show("Customer ID was not returned. Account could not be created.");
                }
                finally
                {
                    //NC-15 Close the connection.
                    conn.Close();
                }
            }
        }

        //NC-16 Verify that Customer Name is present.
        private bool isCustomerName()
        {
            if (txtCustomerName.Text == "")
            {
                MessageBox.Show("Please enter a name.");
                return false;
            }
            else
            {
                return true;
            }
        }

        //NC-17 Place order.
        private void btnPlaceOrder_Click(object sender, EventArgs e)
        {
            //NC-18 Set up and run stored procedure only if required input is present.
            if (isPlaceOrderReady())
            {
                // Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //NC-19 Create SqlCommand and identify it as a stored procedure.
                SqlCommand cmdNewOrder = new SqlCommand("Sales.uspPlaceNewOrder", conn);
                cmdNewOrder.CommandType = CommandType.StoredProcedure;

                //NC-20 @CustomerID, which was an output parameter from uspNewCustomer.
                cmdNewOrder.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));
                cmdNewOrder.Parameters["@CustomerID"].Value = this.parsedCustomerID;

                //NC-21 @OrderDate.
                cmdNewOrder.Parameters.Add(new SqlParameter("@OrderDate", SqlDbType.DateTime, 8));
                cmdNewOrder.Parameters["@OrderDate"].Value = dtpOrderDate.Value;

                //NC-22 @Amount.
                cmdNewOrder.Parameters.Add(new SqlParameter("@Amount", SqlDbType.Int));
                cmdNewOrder.Parameters["@Amount"].Value = numOrderAmount.Value;

                //NC-23 @Status. For a new order, the status is always O (open).
                cmdNewOrder.Parameters.Add(new SqlParameter("@Status", SqlDbType.Char, 1));
                cmdNewOrder.Parameters["@Status"].Value = "O";

                //NC-24 Add return value for stored procedure, which is orderID.
                cmdNewOrder.Parameters.Add(new SqlParameter("@RC", SqlDbType.Int));
                cmdNewOrder.Parameters["@RC"].Direction = ParameterDirection.ReturnValue;

                //try-catch-finally
                try
                {
                    //Open connection.
                    conn.Open();

                    //Run the stored procedure.
                    cmdNewOrder.ExecuteNonQuery();

                    //NC-25 Display the order number.
                    this.orderID = (int)cmdNewOrder.Parameters["@RC"].Value;
                    MessageBox.Show("Order number " + this.orderID + " has been submitted.");
                }
                catch
                {
                    //A simple catch.
                    MessageBox.Show("Order could not be placed.");
                }
                finally
                {
                    //Close connection.
                    conn.Close();
                }
            }
        }

        //NC-26 Verify that order data is ready.
        private bool isPlaceOrderReady()
        {
            // Verify that CustomerID is present.
            if (txtCustomerID.Text == "")
            {
                MessageBox.Show("Please create customer account before placing order.");
                return false;
            }

            // Verify that Amount isn't 0.
            else if ((numOrderAmount.Value < 1))
            {
                MessageBox.Show("Please specify an order amount.");
                return false;
            }
            else
            {
                // Order can be submitted.
                return true;
            }
        }

        //NC-27 Reset the form for another new account.
        private void btnAddAnotherAccount_Click(object sender, EventArgs e)
        {
            this.ClearForm();
        }

        //NC-28 Clear values from controls.
        private void ClearForm()
        {
            txtCustomerName.Clear();
            txtCustomerID.Clear();
            dtpOrderDate.Value = DateTime.Now;
            numOrderAmount.Value = 0;
            this.parsedCustomerID = 0;
        }

        //NC-29 Close the form.
        private void btnAddFinish_Click(object sender, EventArgs e)
        {
            this.Close();
        }

    }
}

```

```vb
Imports System
Imports System.Collections.Generic
Imports System.ComponentModel
Imports System.Data
Imports System.Drawing
Imports System.Linq
Imports System.Text
Imports System.Threading.Tasks
Imports System.Windows.Forms
' NC-1 More namespaces.
Imports System.Data.SqlClient
Imports System.Configuration

Namespace SimpleDataApp
    Partial Public Class NewCustomer
        Inherits Form

        ' NC-2 Storage for IDENTITY values returned from database.
        Private parsedCustomerID As Integer
        Private orderID As Integer

        ' NC-3 Specify a connection string.
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()

        Public Sub New()
            InitializeComponent()
        End Sub

        ' NC-4 Create account.
        Private Sub btnCreateAccount_Click() Handles btnCreateAccount.Click

            ' NC-5 Set up and run stored procedure only if Customer Name is present.
            If isCustomerName() Then

                ' NC-6 Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' NC-7 Create a SqlCommand, and identify it as a stored procedure.
                Dim cmdNewCustomer As New SqlCommand("Sales.uspNewCustomer", conn)
                cmdNewCustomer.CommandType = CommandType.StoredProcedure

                ' NC-8 Add input parameter from the stored procedure and specify what to use as its value.
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerName", SqlDbType.NVarChar, 40))
                cmdNewCustomer.Parameters("@CustomerName").Value = txtCustomerName.Text

                ' NC-9 Add output parameter.
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))
                cmdNewCustomer.Parameters("@CustomerID").Direction = ParameterDirection.Output

                ' NC-10 try-catch-finally
                Try
                    ' NC-11 Open the connection.
                    conn.Open()

                    ' NC-12 Run the stored procedure.
                    cmdNewCustomer.ExecuteNonQuery()

                    ' NC-13 Customer ID is an IDENTITY value from the database.
                    Me.parsedCustomerID = CInt(cmdNewCustomer.Parameters("@CustomerID").Value)
                    Me.txtCustomerID.Text = Convert.ToString(parsedCustomerID)

                Catch
                    ' NC-14 A simple catch.
                    MessageBox.Show("Customer ID was not returned. Account could not be created.")
                Finally
                    ' NC-15 Close the connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' NC-16 Verify that Customer Name is present.
        Private Function isCustomerName() As Boolean
            If txtCustomerName.Text = "" Then
                MessageBox.Show("Please enter a name.")
                Return False
            Else
                Return True
            End If
        End Function

        ' NC-17 Place order.
        Private Sub btnPlaceOrder_Click() Handles btnPlaceOrder.Click

            ' NC-18 Set up and run stored procedure only if necessary input is present.
            If isPlaceOrderReady() Then

                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' NC-19 Create SqlCommand and identify it as a stored procedure.
                Dim cmdNewOrder As New SqlCommand("Sales.uspPlaceNewOrder", conn)
                cmdNewOrder.CommandType = CommandType.StoredProcedure

                ' NC-20 @CustomerID, which was an output parameter from uspNewCustomer.
                cmdNewOrder.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))
                cmdNewOrder.Parameters("@CustomerID").Value = Me.parsedCustomerID

                ' NC-21 @OrderDate.
                cmdNewOrder.Parameters.Add(New SqlParameter("@OrderDate", SqlDbType.DateTime, 8))
                cmdNewOrder.Parameters("@OrderDate").Value = dtpOrderDate.Value

                ' NC-22 @Amount.
                cmdNewOrder.Parameters.Add(New SqlParameter("@Amount", SqlDbType.Int))
                cmdNewOrder.Parameters("@Amount").Value = numOrderAmount.Value

                ' NC-23 @Status. For a new order, the status is always O (open).
                cmdNewOrder.Parameters.Add(New SqlParameter("@Status", SqlDbType.[Char], 1))
                cmdNewOrder.Parameters("@Status").Value = "O"

                ' NC-24 Add return value for stored procedure, which is orderID.
                cmdNewOrder.Parameters.Add(New SqlParameter("@RC", SqlDbType.Int))
                cmdNewOrder.Parameters("@RC").Direction = ParameterDirection.ReturnValue

                ' try-catch-finally
                Try
                    ' Open connection.
                    conn.Open()

                    ' Run the stored procedure.
                    cmdNewOrder.ExecuteNonQuery()

                    ' NC-25 Display the order number.
                    Me.orderID = CInt(cmdNewOrder.Parameters("@RC").Value)
                    MessageBox.Show("Order number " & (Me.orderID).ToString & " has been submitted.")

                Catch
                    ' A simple catch.
                    MessageBox.Show("Order could  not be placed.")

                Finally
                    ' Close connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' NC-26 Verify that order data is ready.
        Private Function isPlaceOrderReady() As Boolean

            ' Verify that CustomerID is present.
            If txtCustomerID.Text = "" Then
                MessageBox.Show("Please create customer account before placing order.")
                Return False

                ' Verify that Amount isn't 0.
            ElseIf (numOrderAmount.Value < 1) Then

                MessageBox.Show("Please specify an order amount.")
                Return False
            Else
                ' Order can be submitted.
                Return True
            End If
        End Function

        ' NC-27 Reset the form for another new account.
        Private Sub btnAddAnotherAccount_Click() Handles btnAddAnotherAccount.Click
            Me.ClearForm()
        End Sub

        ' NC-28 Clear values from controls.
        Private Sub ClearForm()
            txtCustomerName.Clear()
            txtCustomerID.Clear()
            dtpOrderDate.Value = DateTime.Now
            numOrderAmount.Value = 0
            Me.parsedCustomerID = 0
        End Sub

        ' NC-29 Close the form.
        Private Sub btnAddFinish_Click() Handles btnAddFinish.Click
            Me.Close()
        End Sub

    End Class
End Namespace
```

|Comentário|Descrição|
|-------------|-----------------|
|NC-1|Adicione `System.Data.SqlClient` e `System.Configuration` à lista de namespaces.|
|NC-2|Declare as variáveis `parsedCustomerID` e `orderID`, que você usará mais tarde.|
|NC-3|Chame o método `GetConnectionString` para obter a cadeia de conexão do arquivo de configuração de aplicativo e armazene o valor na variável de cadeia de caracteres `connstr`.|
|NC-4|Adicione código ao manipulador de eventos de clique para o botão de `btnCreateAccount`.|
|NC-5|Encapsule a chamada para `isCustomerName` em volta do código do evento de clique para que `uspNewCustomer` seja executado somente se um nome de cliente estiver presente.|
|NC-6|Crie um objeto de `SqlConnection` (`conn`) e passe a cadeia de conexão em `connstr`.|
|NC-7|Crie um objeto de `SqlCommand`, `cmdNewCustomer`.<br /><br /> -Especifique `Sales.uspNewCustomer` como o procedimento armazenado a ser executado.<br />-Use a propriedade `CommandType` para especificar que o comando é um procedimento armazenado.|
|NC-8|Adicione o parâmetro de entrada `@CustomerName` do procedimento armazenado.<br /><br /> -Adicione o parâmetro à coleção de `Parameters`.<br />-Use a enumeração `SqlDbType` para especificar o tipo de parâmetro como nvarchar (40).<br />-Especifique `txtCustomerName.Text` como a origem.|
|NC-9|Adicione o parâmetro de saída do procedimento armazenado.<br /><br /> -Adicione o parâmetro à coleção de `Parameters`.<br />-Use `ParameterDirection.Output` para identificar o parâmetro como saída.|
|NC-10|Adicione um bloco try-catch-finally para abrir a conexão, executar o procedimento armazenado, tratar exceções e, em seguida, fechar a conexão.|
|NC-11|Abra a conexão (`conn`) que você criou em NC-6.|
|NC-12|Use o método `ExecuteNonQuery` para `cmdNewCustomer` para executar o procedimento armazenado `Sales.uspNewCustomer`. Esse procedimento armazenado executa uma instrução `INSERT`, não uma consulta.|
|NC-13|O valor de `@CustomerID` é retornado como um valor de identidade do banco de dados. Como é um número inteiro, você precisará convertê-lo em uma cadeia de caracteres para exibi-lo na caixa de texto **ID do cliente** .<br /><br /> -Você declarou `parsedCustomerID` em NC-2.<br />-Armazene o valor de `@CustomerID` no `parsedCustomerID` para uso posterior.<br />-Converta a ID do cliente retornada em uma cadeia de caracteres e insira-a em `txtCustomerID.Text`.|
|NC-14|Para este exemplo, adicione uma cláusula catch simples (não de qualidade de produção).|
|NC-15|Sempre feche uma conexão depois de terminar de usá-la, para que ela possa ser liberada para o pool de conexões. Confira [SQL Server pooling de conexão (ADO.net)](https://msdn.microsoft.com/library/8xx3tyca\(l=en-us,v=VS.110\).aspx).|
|NC-16|Defina um método para verificar se um nome de cliente está presente.<br /><br /> -Se a caixa de texto estiver vazia, exiba uma mensagem e retorne `false`, pois um nome é necessário para criar a conta.<br />-Se a caixa de texto não estiver vazia, retorne `true`.|
|NC-17|Adicione código ao manipulador de eventos de clique para o botão de `btnPlaceOrder`.|
|NC-18|Encapsule a chamada para `isPlaceOrderReady` em relação ao código do evento `btnPlaceOrder_Click` para que `uspPlaceNewOrder` não seja executado se a entrada necessária não estiver presente.|
|NC-19 até NC-25|Essas seções de código se assemelham ao código que você adicionou para o manipulador de eventos `btnCreateAccount_Click`.<br /><br /> -NC-19. Crie o objeto `SqlCommand`, `cmdNewOrder` e especifique `Sales.uspPlaceOrder` como o procedimento armazenado.<br />-NC-20 por meio de NC-23 são os parâmetros de entrada para o procedimento armazenado.<br />-NC-24. `@RC` conterá um valor de retorno que é a ID de ordem gerada do banco de dados. A direção deste parâmetro é especificada como `ReturnValue`.<br />-NC-25. Armazene o valor da ID do pedido na variável `orderID` que você declarou em NC-2 e exiba o valor em uma caixa de mensagem.|
|NC-26|Defina um método para verificar se existe uma ID de cliente e se um valor foi especificado em `numOrderAmount`.|
|NC-27|Chame o método `ClearForm` no manipulador de eventos de clique `btnAddAnotherAccount`.|
|NC-28|Crie o método `ClearForm` para limpar os valores do formulário se desejar adicionar outro cliente.|
|NC29|Feche o formulário NewCustomer e retorne o foco para o formulário de navegação.|

### <a name="fillorcancel-form"></a>Formulário FillOrCancel
 O formulário FillorCancel executa uma consulta para retornar um pedido quando você insere uma ID do pedido e seleciona o botão **Localizar ordem** . A linha retornada aparece em uma grade de dados somente leitura. Você pode marcar a ordem como cancelada (X) se selecionar o botão **Cancelar pedido** , ou pode marcar a ordem como preenchida (F) se você selecionar o botão **ordem de preenchimento** . Se você selecionar o botão **Localizar ordem** novamente, a linha atualizada será exibida.

#### <a name="create-event-handlers"></a>Criar manipuladores de eventos
 Crie manipuladores de eventos de clique vazios para os quatro botões no formulário.

#### <a name="create-code-for-fillorcancel"></a>Criar código para FillOrCancel
 Adicione o código a seguir ao formulário FillOrCancel. Percorra os blocos de código usando os comentários numerados e a tabela que segue o código.

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
//FC-1 More namespaces.
using System.Text.RegularExpressions;
using System.Data.SqlClient;
using System.Configuration;

namespace SimpleDataApp
{
    public partial class FillOrCancel : Form
    {
        //FC-2 Storage for OrderID.
        private int parsedOrderID;

        //FC-3 Specify a connection string.
        string connstr = SimpleDataApp.Utility.GetConnectionString();

        public FillOrCancel()
        {
            InitializeComponent();
        }

        //FC-4 Find an order.
        private void btnFindByOrderID_Click(object sender, EventArgs e)
        {
            //FC-5 Prepare the connection and the command.
            if (isOrderID())
            {
                //Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //Define a query string that has a parameter for orderID.
                string sql = "select * from Sales.Orders where orderID = @orderID";

                //Create a SqlCommand object.
                SqlCommand cmdOrderID = new SqlCommand(sql, conn);

                //Define the @orderID parameter and its value.
                cmdOrderID.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));
                cmdOrderID.Parameters["@orderID"].Value = parsedOrderID;

                //try-catch-finally
                try
                {
                    //FC-6 Run the command and display the results.
                    //Open the connection.
                    conn.Open();

                    //Run the command by using SqlDataReader.
                    SqlDataReader rdr = cmdOrderID.ExecuteReader();

                    //Create a data table to hold the retrieved data.
                    DataTable dataTable = new DataTable();

                    //Load the data from SqlDataReader into the data table.
                    dataTable.Load(rdr);

                    //Display the data from the data table in the data grid view.
                    this.dgvCustomerOrders.DataSource = dataTable;

                    //Close the SqlDataReader.
                    rdr.Close();
                }
                catch
                {
                    //A simple catch.
                    MessageBox.Show("The requested order could not be loaded into the form.");
                }
                finally
                {
                    //Close the connection.
                    conn.Close();
                }
            }
        }

        //FC-7 Cancel an order.
        private void btnCancelOrder_Click(object sender, EventArgs e)
        {
            //Set up and run stored procedure only if OrderID is ready.
            if (isOrderID())
            {
                //Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                // Create command and identify it as a stored procedure.
                SqlCommand cmdCancelOrder = new SqlCommand("Sales.uspCancelOrder", conn);
                cmdCancelOrder.CommandType = CommandType.StoredProcedure;

                cmdCancelOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));
                cmdCancelOrder.Parameters["@orderID"].Value = parsedOrderID;

                // try-catch-finally
                try
                {
                    // Open the connection.
                    conn.Open();

                    // Run the cmdCancelOrder command.
                    cmdCancelOrder.ExecuteNonQuery();
                }
                // A simple catch.
                catch
                {
                    MessageBox.Show("The cancel operation was not completed.");
                }
                finally
                {
                    //Close connection.
                    conn.Close();
                }
            }
        }

        //FC-8 Fill an order.
        private void btnFillOrder_Click(object sender, EventArgs e)
        {
            //Set up and run stored procedure only if OrderID is ready.
            if (isOrderID())
            {
                //Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //Create command and identify it as a stored procedure.
                SqlCommand cmdFillOrder = new SqlCommand("Sales.uspFillOrder", conn);
                cmdFillOrder.CommandType = CommandType.StoredProcedure;

                // Add input parameter from the stored procedure.
                cmdFillOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));
                cmdFillOrder.Parameters["@orderID"].Value = parsedOrderID;

                //Add the second input parameter.
                cmdFillOrder.Parameters.Add(new SqlParameter("@FilledDate", SqlDbType.DateTime, 8));
                cmdFillOrder.Parameters["@FilledDate"].Value = dtpFillDate.Value;

                //try-catch-finally
                try
                {
                    //Open the connection.
                    conn.Open();

                    //Run the cmdFillOrder command.
                    cmdFillOrder.ExecuteNonQuery();
                }
                catch
                {
                    //A simple catch.
                    MessageBox.Show("The fill operation was not completed.");
                }
                finally
                {
                    //Close the connection.
                    conn.Close();
                }
            }
        }

        //FC-9 Verify that OrderID is ready.
        private bool isOrderID()
        {

            //Check for input in the Order ID text box.
            if (txtOrderID.Text == "")
            {
                MessageBox.Show("Please specify the Order ID.");
                return false;
            }

            // Check for characters other than integers.
            else if (Regex.IsMatch(txtOrderID.Text, @"^\D*$"))
            {
               //Show message and clear input.
                MessageBox.Show("Please specify integers only.");
                txtOrderID.Clear();
                return false;
            }
            else
            {
                //Convert the text in the text box to an integer to send to the database.
                parsedOrderID = Int32.Parse(txtOrderID.Text);
                return true;
            }
        }

        //Close the form.
        private void btnFinishUpdates_Click(object sender, EventArgs e)
        {
            this.Close();
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports System.ComponentModel
Imports System.Data
Imports System.Drawing
Imports System.Linq
Imports System.Text
Imports System.Threading.Tasks
Imports System.Windows.Forms
' FC-1 More namespaces.
Imports System.Text.RegularExpressions
Imports System.Data.SqlClient
Imports System.Configuration

Namespace SimpleDataApp
    Partial Public Class FillOrCancel
        Inherits Form
        ' FC-2 Storage for OrderID.
        Private parsedOrderID As Integer

        ' FC-3 Specify a connection string.
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()

        Public Sub New()
            InitializeComponent()
        End Sub

        ' FC-4 Find an order.
        Private Sub btnFindByOrderID_Click() Handles btnFindByOrderID.Click

            ' FC-5 Prepare the connection and the command.

            If isOrderID() Then
                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' Define the query string that has a parameter for orderID.
                Dim sql As String = "select * from Sales.Orders where orderID = @orderID"

                ' Create a SqlCommand object.
                Dim cmdOrderID As New SqlCommand(sql, conn)

                ' Define the @orderID parameter and its value.
                cmdOrderID.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))
                cmdOrderID.Parameters("@orderID").Value = parsedOrderID

                ' try-catch-finally
                Try
                    ' FC-6 Run the command and display the results.
                    ' Open connection.
                    conn.Open()

                    ' Run the command by using SqlDataReader.
                    Dim rdr As SqlDataReader = cmdOrderID.ExecuteReader()

                    ' Create a data table to hold the retrieved data.
                    Dim dataTable As New DataTable()

                    ' Load the data from SqlDataReader into the data table.
                    dataTable.Load(rdr)

                    ' Display the data from the data table in the data grid view.
                    Me.dgvCustomerOrders.DataSource = dataTable

                    ' Close the SqlDataReader.
                    rdr.Close()
                Catch
                    ' A simple catch.
                    MessageBox.Show("The requested order could not be loaded into the form.")
                Finally
                    ' Close the connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' FC-7 Cancel an order.
        Private Sub btnCancelOrder_Click() Handles btnCancelOrder.Click

            ' Set up and run stored procedure only if OrderID is ready.
            If isOrderID() Then

                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' Create the command and identify it as a stored procedure.
                Dim cmdCancelOrder As New SqlCommand("Sales.uspCancelOrder", conn)
                cmdCancelOrder.CommandType = CommandType.StoredProcedure

                ' Add input parameter from the stored procedure.
                cmdCancelOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))
                cmdCancelOrder.Parameters("@orderID").Value = parsedOrderID

                ' try-catch-finally
                Try
                    ' Open the connection.
                    conn.Open()

                    ' Run the cmdCancelOrder command.
                    cmdCancelOrder.ExecuteNonQuery()
                Catch
                    ' A simple catch.
                    MessageBox.Show("The cancel operation was not completed.")
                Finally
                    ' Close connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' FC-8 Fill an order.
        Private Sub btnFillOrder_Click() Handles btnFillOrder.Click

            ' Set up and run stored procedure only if OrderID is ready.
            If isOrderID() Then

                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' Create command and identify it as a stored procedure.
                Dim cmdFillOrder As New SqlCommand("Sales.uspFillOrder", conn)
                cmdFillOrder.CommandType = CommandType.StoredProcedure

                ' Add input parameter from the stored procedure.
                cmdFillOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))
                cmdFillOrder.Parameters("@orderID").Value = parsedOrderID

                ' Add second input parameter.
                cmdFillOrder.Parameters.Add(New SqlParameter("@FilledDate", SqlDbType.DateTime, 8))
                cmdFillOrder.Parameters("@FilledDate").Value = dtpFillDate.Value

                ' try-catch-finally
                Try
                    ' Open the connection.
                    conn.Open()

                    ' Run the cmdFillOrder command.
                    cmdFillOrder.ExecuteNonQuery()
                Catch
                    ' A simple catch.
                    MessageBox.Show("The fill operation was not completed.")
                Finally
                    ' Close the connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' FC-9 Verify that OrderID is ready.
        Private Function isOrderID() As Boolean

            ' Check for input in the Order ID text box.
            If txtOrderID.Text = "" Then
                MessageBox.Show("Please specify the Order ID.")
                Return False

                ' Check for characters other than integers.
            ElseIf Regex.IsMatch(txtOrderID.Text, "^\D*$") Then

                ' Show message and clear input.
                MessageBox.Show("Please specify integers only.")
                txtOrderID.Clear()
                Return False

            Else
                ' Convert the text in the text box to an integer to send to the database.
                parsedOrderID = Int32.Parse(txtOrderID.Text)
                Return True

            End If
        End Function

        ' Close the form.
        Private Sub btnFinishUpdates_Click() Handles btnFinishUpdates.Click
            Me.Close()
        End Sub
    End Class
End Namespace
```

|Comentário|Descrição|
|-------------|-----------------|
|FC-1|Adicione `System.Data.SqlClient`, `System.Configuration` e `System.Text.RegularExpressions` à lista de namespaces.|
|FC-2|Declare a variável `parsedOrderID`.|
|FC-3|Chame o método `GetConnectionString` para obter a cadeia de conexão do arquivo de configuração de aplicativo e armazene o valor na variável de cadeia de caracteres `connstr`.|
|FC-4|Adicione código ao manipulador de eventos de clique para `btnFindOrderByID`.|
|FC-5|Essas tarefas são necessárias antes de tentar executar uma instrução SQL ou um procedimento armazenado.<br /><br /> -Criar um objeto de `SqlConnection`.<br />-Defina a instrução SQL ou especifique o nome do procedimento armazenado. (Nesse caso, você executará uma instrução `SELECT`.)<br />-Criar um objeto de `SqlCommand`.<br />-Defina quaisquer parâmetros para a instrução SQL ou procedimento armazenado.|
|FC-6|Esse código usa `SqlDataReader` e `DataTable` para recuperar e exibir o resultado da consulta.<br /><br /> -Abra a conexão.<br />-Crie um objeto `SqlDataReader`, `rdr`, executando o método `ExecuteReader` para `cmdOrderID`.<br />-Crie um objeto `DataTable` para manter os dados recuperados.<br />-Carregue os dados do objeto `SqlDataReader` no objeto `DataTable`.<br />-Exiba os dados no modo de exibição de grade de dados especificando `DataTable` como `DataSource` para a exibição de grade de dados.<br />-Fechar `SqlDataReader`.|
|FC-7|Adicione código ao manipulador de eventos de clique para `btnCancelOrder`. Esse código executa o procedimento armazenado `Sales.uspCancelOrder`.|
|FC-8|Adicione código ao manipulador de eventos de clique para `btnFillOrder`. Esse código executa o procedimento armazenado `Sales.uspFillOrder`.|
|FC-9|Crie um método para verificar se `OrderID` está pronto para enviar como um parâmetro para o objeto `SqlCommand`.<br /><br /> -Verifique se uma ID foi inserida no `txtOrderID`.<br />-Use `Regex.IsMatch` para definir uma verificação simples para caracteres não inteiros.<br />-Você declarou a variável `parsedOrderID` em FC-2.<br />-Se a entrada for válida, converta o texto em um inteiro e armazene o valor na variável `parsedOrderID`.<br />-Encapsula o método `isOrderID` em relação ao `btnFindByOrderID`, `btnCancelOrder` e `btnFillOrder` clique em manipuladores de eventos.|

## <a name="BKMK_testyourapplication"></a>Testar seu aplicativo
 Selecione a tecla F5 para compilar e testar seu aplicativo depois de codificar cada manipulador de eventos de clique e depois de concluir a codificação.
