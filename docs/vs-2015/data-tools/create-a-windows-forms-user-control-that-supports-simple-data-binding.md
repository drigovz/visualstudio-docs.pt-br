---
title: Criar um controle de usuário Windows Forms que dá suporte à vinculação de dados simples | Microsoft Docs
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
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bf30a38384863c9ba5a8af35af3326a51058d831
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668767"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados simples
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao exibir dados em formulários nos aplicativos do Windows, você poderá escolher os controles existentes da **Caixa de Ferramentas** ou criar controles personalizados se o aplicativo exigir alguma funcionalidade que não esteja disponível nos controles padrão. Este passo a passo mostra como criar um controle que implementa o <xref:System.ComponentModel.DefaultBindingPropertyAttribute>. Os controles que implementam o <xref:System.ComponentModel.DefaultBindingPropertyAttribute> contêm uma propriedade que pode ser associada a dados. Tais controles são semelhantes a um <xref:System.Windows.Forms.TextBox> ou <xref:System.Windows.Forms.CheckBox>.

 Para obter mais informações sobre a criação de controles, consulte [desenvolvendo Windows Forms controles em tempo de design](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).

 Ao criar controles para uso em cenários de vinculação de dados, você deve implementar um dos seguintes atributos de vinculação de dados:

|Uso de atributo de vinculação de dados|
|-----------------------------------|
|Implemente o <xref:System.ComponentModel.DefaultBindingPropertyAttribute> em controles simples, como um <xref:System.Windows.Forms.TextBox>, que exibe uma única coluna (ou propriedade) de dados. (Esse processo é descrito nesta página de passo a passo.)|
|Implemente o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.DataGridView> que exibe listas (ou tabelas) de dados. Para obter mais informações, consulte [criar um Windows Forms controle de usuário que dá suporte à ligação de dados complexa](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implemente o <xref:System.ComponentModel.LookupBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.ComboBox>que exibe listas (ou tabelas) de dados, mas também precisa apresentar uma única coluna ou propriedade. Para obter mais informações, consulte [criar um Windows Forms controle de usuário que dá suporte à vinculação de dados de pesquisa](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 Este passo a passo cria um controle simples que exibe dados de uma única coluna em uma tabela. Este exemplo usa a coluna `Phone` da tabela `Customers` do banco de dados de exemplo Northwind. O controle de usuário simples exibirá os números de telefone dos clientes em um formato de número de telefone padrão, usando um <xref:System.Windows.Forms.MaskedTextBox> e definindo a máscara como um número de telefone.

 Durante este passo a passo, você aprenderá a:

- Crie um novo **aplicativo do Windows**.

- Adicionar um novo **Controle de Usuário** ao projeto.

- Projetar visualmente o controle do usuário.

- Implementar o atributo `DefaultBindingProperty`.

- Crie um conjunto de dados com o assistente de **configuração de fonte de dados** .

- Definir a coluna **Telefone** na janela **Fontes de Dados** para usar o novo controle.

- Criar um formulário para exibir dados no novo controle.

## <a name="prerequisites"></a>Prerequisites
 Para concluir este passo a passo, você precisará de:

- Acesso ao banco de dados de exemplo Northwind.

## <a name="create-a-windows-application"></a>Criar um aplicativo do Windows
 A primeira etapa é criar um **aplicativo do Windows**.

#### <a name="to-create-the-new-windows-project"></a>Para criar o novo projeto do Windows

1. No Visual Studio, no menu **arquivo** , crie um novo **projeto**.

2. Nomeie o projeto **SimpleControlWalkthrough**.

3. Selecione **aplicativo do Windows** e clique em **OK**. Para obter mais informações, consulte [aplicativos cliente](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     O projeto **SimpleControlWalkthrough** é criado e adicionado ao **Gerenciador de Soluções**.

## <a name="add-a-user-control-to-the-project"></a>Adicionar um controle de usuário ao projeto
 Este tutorial cria um controle vinculável de dados simples de um **controle de usuário**, portanto, adicione um item de controle de **usuário** ao projeto **SimpleControlWalkthrough** .

#### <a name="to-add-a-user-control-to-the-project"></a>Para adicionar um controle de usuário ao projeto

1. No menu **Projeto**, escolha **Adicionar Controle do Usuário**.

2. Digite `PhoneNumberBox` na área nome e clique em **Adicionar**.

     O controle **PhoneNumberBox** é adicionado ao **Gerenciador de Soluções** e abre no designer.

## <a name="design-the-phonenumberbox-control"></a>Criar o controle PhoneNumberBox
 Este passo a passo expande o <xref:System.Windows.Forms.MaskedTextBox> existente para criar o controle `PhoneNumberBox`.

#### <a name="to-design-the-phonenumberbox-control"></a>Para projetar o controle PhoneNumberBox

1. Arraste um <xref:System.Windows.Forms.MaskedTextBox> da **Caixa de Ferramentas** para a superfície de design do controle de usuário.

2. Selecione a smart tag no <xref:System.Windows.Forms.MaskedTextBox> que você acabou de arrastar e selecione **Definir Máscara**.

3. Selecione **Número do telefone** na caixa de diálogo **Máscara de Entrada** e clique em **OK** para configurar a máscara.

## <a name="add-the-required-data-binding-attribute"></a>Adicionar o atributo de associação de dados necessário
 Para controles simples que suportam associação de dados, implemente o <xref:System.ComponentModel.DefaultBindingPropertyAttribute>.

#### <a name="to-implement-the-defaultbindingproperty-attribute"></a>Para implementar o atributo DefaultBindingProperty

1. Alterne o controle `PhoneNumberBox` para exibição de código. (No menu **Exibir**, escolha **Código**.)

2. Substitua o código no `PhoneNumberBox` pelo seguinte:

     [!code-csharp[VbRaddataDisplaying#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/PhoneNumberBox.cs#3)]
     [!code-vb[VbRaddataDisplaying#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/PhoneNumberBox.vb#3)]

3. No menu **Compilação**, escolha **Compilar Solução**.

## <a name="create-a-data-source-from-your-database"></a>Criar uma fonte de dados do seu banco de dados
 Esta etapa usa o **Assistente de Configuração de Fonte de Dados** para criar uma fonte de dados com base na tabela `Customers` no banco de dados de exemplo Northwind. É preciso ter acesso ao banco de dados de exemplo Northwind para criar a conexão.

#### <a name="to-create-the-data-source"></a>Para criar a fonte de dados

1. No menu **Dados**, clique em **Mostrar Fontes de Dados**.

2. Na janela **Fontes de Dados**, selecione **Adicionar Nova Fonte de Dados** para iniciar o assistente de **Configuração de Fonte de Dados**.

3. Na página **Escolher um Tipo de Fonte de Dados**, selecione **Banco de Dados** e clique em **Avançar**.

4. Na página **Escolha a Conexão de Dados**, faça o seguinte:

    - Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-o.

    - Selecione **Nova Conexão** para inicializar a caixa de diálogo **Adicionar/Modificar Conexão**.

5. Se o banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **Avançar**.

6. Na página **salvar cadeia de conexão no arquivo de configuração do aplicativo** , clique em **Avançar**.

7. Na página **escolher seus objetos de banco de dados** , expanda o nó **tabelas** .

8. Selecione a tabela `Customers` e clique em **Concluir**.

     O **NorthwindDataSet** é adicionado ao projeto e a tabela `Customers` aparece na janela **Fontes de Dados**.

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>Definir a coluna de telefone para usar o controle PhoneNumberBox
 Na janela **Fontes de Dados**, você pode definir o controle a ser criado antes de arrastar itens para seu formulário.

#### <a name="to-set-the-phone-column-to-bind-to-the-phonenumberbox-control"></a>Para definir a coluna telefone para se associar ao controle PhoneNumberBox

1. Abra **Form1** no designer.

2. Expanda o nó **Clientes** na janela **Fontes de Dados**.

3. Clique na seta suspensa no nó **Clientes** e escolha **Detalhes** na lista de controle.

4. Clique na seta suspensa na coluna **Telefone** e escolha **Personalizar**.

5. Selecione **PhoneNumberBox** na lista de **Controles Associados** na caixa de diálogo **Opções de Personalização da Interface do Usuário de Dados**.

6. Clique na seta suspensa na coluna **Telefone** e escolha **PhoneNumberBox**.

## <a name="addcontrols-to-the-form"></a>Addcontroles para o formulário
 É possível criar controles de associação de dados ao arrastar itens da janela **Fontes de Dados** para o formulário.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Para criar controles de associação de dados no formulário

- Arraste o nó **clientes** principais da janela **fontes de dados** para o formulário e verifique se o controle de `PhoneNumberBox` é usado para exibir os dados na coluna `Phone`.

     Os controles de associação de dados com rótulos descritivos são exibidos no formulário, juntamente com uma faixa de ferramentas (<xref:System.Windows.Forms.BindingNavigator>) para registros de navegação. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator> são exibidos na bandeja de componentes.

## <a name="run-the-application"></a>Executar o aplicativo

#### <a name="to-run-the-application"></a>Para executar o aplicativo

- Pressione F5 para executar o aplicativo.

## <a name="next-steps"></a>Próximas etapas
 Dependendo dos requisitos do aplicativo, existem várias etapas que você pode realizar após criar um controle com suporte a associação de dados. Algumas etapas seguintes típicas incluem:

- Colocando os controles personalizados em uma biblioteca de controles para que você possa reutilizá-los em outros aplicativos.

- Criando controles que suportam cenários de associação de dados mais complexos. Para obter mais informações, consulte [criar um Windows Forms controle de usuário que dá suporte à vinculação de dados complexa](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) e [criar um controle de usuário de Windows Forms que dá suporte à vinculação de dados de pesquisa](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Consulte também
 [Associar controles de Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [defina o controle a ser criado ao arrastar da janela fontes de dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
