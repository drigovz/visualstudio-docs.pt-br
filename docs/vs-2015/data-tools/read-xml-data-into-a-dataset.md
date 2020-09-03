---
title: Ler dados XML em um DataSet | Microsoft Docs
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
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c34fb87c02ff60d9b28c43130d6fbf3a12e70349
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652900"
---
# <a name="read-xml-data-into-a-dataset"></a>Ler dados XML em um conjunto de dados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O ADO.NET fornece métodos simples para trabalhar com dados XML. Neste tutorial, você cria um aplicativo do Windows que carrega dados XML em um DataSet. Em seguida, o DataSet é exibido em um <xref:System.Windows.Forms.DataGridView> controle. Por fim, um esquema XML baseado no conteúdo do arquivo XML é exibido em uma caixa de texto.

 Este passo a passos consiste em cinco etapas principais:

1. Crie um novo projeto

2. Criando um arquivo XML a ser lido no conjunto de

3. Criar a interface do usuário

4. Criando o conjunto de um, lendo o arquivo XML e exibindo-o em um <xref:System.Windows.Forms.DataGridView> controle

5. Adicionando código para exibir o esquema XML com base no arquivo XML em um <xref:System.Windows.Forms.TextBox> controle

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes daqueles descritos na ajuda, dependendo das configurações ativas ou da edição que você está usando. Para alterar as configurações, no menu  **ferramentas** , selecione**importar e exportar configurações**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-new-project"></a>Criar um novo projeto
 Nesta etapa, você cria um projeto do Visual Basic ou do Visual C# que contém este passo a passos.

#### <a name="to-create-the-new-windows-project"></a>Para criar o novo projeto do Windows

1. No menu **arquivo** , crie um novo projeto.

2. Dê ao projeto o nome de `ReadingXML`.

3. Selecione **aplicativo do Windows**e, em seguida, selecione **OK**. Para obter mais informações, consulte [aplicativos cliente](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     O projeto **ReadingXML** é criado e adicionado ao **Gerenciador de soluções**.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Gerar o arquivo XML a ser lido no conjunto de
 Como este passo a passos se concentra na leitura de dados XML em um conjunto, o conteúdo de um arquivo XML é fornecido.

#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>Para criar o arquivo XML que será lido no conjunto de

1. No menu **projeto** , selecione**Adicionar novo item**.

2. Selecione **arquivo XML**, nomeie o arquivo `authors.xml` e, em seguida, selecione **Adicionar**.

     O arquivo XML é carregado no designer e está pronto para edição.

3. Cole o código a seguir no editor abaixo da declaração XML:

    ```xml
    <Authors_Table>
      <authors>
        <au_id>172-32-1176</au_id>
        <au_lname>White</au_lname>
        <au_fname>Johnson</au_fname>
        <phone>408 496-7223</phone>
        <address>10932 Bigge Rd.</address>
        <city>Menlo Park</city>
        <state>CA</state>
        <zip>94025</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>213-46-8915</au_id>
        <au_lname>Green</au_lname>
        <au_fname>Margie</au_fname>
        <phone>415 986-7020</phone>
        <address>309 63rd St. #411</address>
        <city>Oakland</city>
        <state>CA</state>
        <zip>94618</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>238-95-7766</au_id>
        <au_lname>Carson</au_lname>
        <au_fname>Cheryl</au_fname>
        <phone>415 548-7723</phone>
        <address>589 Darwin Ln.</address>
        <city>Berkeley</city>
        <state>CA</state>
        <zip>94705</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>267-41-2394</au_id>
        <au_lname>Hunter</au_lname>
        <au_fname>Anne</au_fname>
        <phone>408 286-2428</phone>
        <address>22 Cleveland Av. #14</address>
        <city>San Jose</city>
        <state>CA</state>
        <zip>95128</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>274-80-9391</au_id>
        <au_lname>Straight</au_lname>
        <au_fname>Dean</au_fname>
        <phone>415 834-2919</phone>
        <address>5420 College Av.</address>
        <city>Oakland</city>
        <state>CA</state>
        <zip>94609</zip>
        <contract>true</contract>
      </authors>
    </Authors_Table>
    ```

4. No menu **arquivo** , selecione**salvar authors.xml**.

## <a name="create-the-user-interface"></a>Criar a interface do usuário
 A interface do usuário para esse aplicativo consiste no seguinte:

- Um <xref:System.Windows.Forms.DataGridView> controle que exibe o conteúdo do arquivo XML como dados.

- Um <xref:System.Windows.Forms.TextBox> controle que exibe o esquema XML para o arquivo XML.

- Dois <xref:System.Windows.Forms.Button> controles.

  - Um botão lê o arquivo XML no conjunto de e o exibe no <xref:System.Windows.Forms.DataGridView> controle.

  - Um segundo botão extrai o esquema do conjunto de um, e por meio de um <xref:System.IO.StringWriter> exibe-o no <xref:System.Windows.Forms.TextBox> controle.

#### <a name="to-add-controls-to-the-form"></a>Para adicionar controles ao formulário

1. Abra `Form1` no modo Design.

2. Na **caixa de ferramentas**, arraste os seguintes controles para o formulário:

    - Um <xref:System.Windows.Forms.DataGridView> controle

    - Um <xref:System.Windows.Forms.TextBox> controle

    - Dois <xref:System.Windows.Forms.Button> controles

3. Defina as seguintes propriedades:

    |Control|Propriedade|Configuração|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multilinha**|`true`|
    ||**ScrollBars**|**Vertical**|
    |`Button1`|**Nome**|`ReadXmlButton`|
    ||**Text**|`Read XML`|
    |`Button2`|**Nome**|`ShowSchemaButton`|
    ||**Text**|`Show Schema`|

## <a name="create-the-dataset-thatreceives-the-xml-data"></a>Criar a thatreceives do conjunto de dados XML
 Nesta etapa, você cria um novo conjunto de uma chamada `authors` . Para obter mais informações sobre conjuntos de dados, consulte [ferramentas de DataSet no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

#### <a name="to-create-a-new-dataset-that--receives-the-xml-data"></a>Para criar um novo DataSet que recebe os dados XML

1. Em **Gerenciador de soluções**, selecione o arquivo de origem para o **Form1**e, em seguida, selecione o botão **Designer de exibição** na barra de ferramentas **Gerenciador de soluções** .

2. Na [caixa de ferramentas, guia Data](../ide/reference/toolbox-data-tab.md), arraste um **conjunto** de dados para **Form1**.

3. Na caixa de diálogo **Adicionar conjunto** de texto, selecione **conjunto de tipos não tipado**e, em seguida, selecione **OK**.

     **DataSet1** é adicionado à bandeja de componentes.

4. Na janela **Propriedades** , defina o **nome** e <xref:System.Data.DataSet.DataSetName%2A> as propriedades para `AuthorsDataSet` .

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>Criar o manipulador de eventos para ler o arquivo XML no conjunto de
 O botão **ler XML** lê o arquivo XML no conjunto de os. Em seguida, ele define as propriedades no <xref:System.Windows.Forms.DataGridView> controle que a associa ao conjunto de linhas.

#### <a name="to-add-code-to-the-readxmlbutton_click-event-handler"></a>Para adicionar código ao manipulador de eventos ReadXmlButton_Click

1. Em **Gerenciador de soluções**, selecione **Form1**e, em seguida, selecione o botão **Designer de exibição** na barra de ferramentas **Gerenciador de soluções** .

2. Selecione o botão **ler XML** .

     O **Editor de código** é aberto no `ReadXmlButton_Click` manipulador de eventos.

3. Digite o seguinte código no `ReadXmlButton_Click` manipulador de eventos:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#2)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#2)]

4. No `ReadXMLButton_Click` código do manipulador de eventos, altere a `filepath =` entrada para o caminho correto.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Criar o manipulador de eventos para exibir o esquema na caixa de texto
 O botão **Mostrar esquema** cria um <xref:System.IO.StringWriter> objeto que é preenchido com o esquema e é exibido no <xref:System.Windows.Forms.TextBox> controle.

#### <a name="to-add-code-to-the-showschemabutton_click-event-handler"></a>Para adicionar código ao manipulador de eventos ShowSchemaButton_Click

1. Em **Gerenciador de soluções**, selecione **Form1**e, em seguida, selecione o botão **Designer de exibição** .

2. Selecione o botão **Mostrar esquema** .

     O **Editor de código** é aberto no `ShowSchemaButton_Click` manipulador de eventos.

3. Digite o código a seguir no `ShowSchemaButton_Click` manipulador de eventos.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#3)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#3)]

## <a name="test-the-form"></a>Testar o formulário

Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.

1. Selecione **F5** para executar o aplicativo.

2. Selecione o botão **ler XML** .

     O DataGridView exibe o conteúdo do arquivo XML.

3. Selecione o botão **Mostrar esquema** .

     A caixa de texto exibe o esquema XML para o arquivo XML.

## <a name="next-steps"></a>Próximas etapas

Este tutorial ensina os conceitos básicos da leitura de um arquivo XML em um conjunto de um, bem como a criação de um esquema com base no conteúdo do arquivo XML. Aqui estão algumas tarefas que você pode fazer em seguida:

- Edite os dados no DataSet e grave-os de volta como XML. Para obter mais informações, consulte <xref:System.Data.DataSet.WriteXml%2A>.

- Edite os dados no DataSet e grave-os em um banco de dados.

## <a name="see-also"></a>Consulte Também
 [Orientações de dados](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4) [acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md) [preparando seu aplicativo para receber](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [ferramentas XML de dados no Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)
