---
title: Atualizar as regiões do formulário em projetos do Outlook que você migrar para o .NET Framework 4 ou o .NET Framework 4.5
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fed87ee8106c3e8a09c341b9de4709060627dac1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60048263"
---
# <a name="update-form-regions-in-outlook-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Atualizar as regiões do formulário em projetos do Outlook que você migrar para o .NET Framework 4 ou o .NET Framework 4.5
  Se a estrutura de destino de um projeto de suplemento do VSTO do Outlook com uma região de formulário for alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deve fazer algumas alterações no código de região de formulário gerado e a qualquer código que cria uma instância de determinadas classes de região de formulário em tempo de execução.

## <a name="update-the-generated-form-region-code"></a>Atualize o código de região de formulário gerado
 Se a estrutura de destino do projeto é alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deve alterar o código de região de formulário gerado. As alterações feitas são diferentes para regiões de formulário projetada no Visual Studio e o formulário de regiões que você importou do Outlook. Para obter mais informações sobre as diferenças entre esses tipos de regiões de formulário, consulte [regiões de formulário do Outlook criar](../vsto/creating-outlook-form-regions.md).

### <a name="to-update-the-generated-code-for-a-form-region-that-you-designed-in-visual-studio"></a>Para atualizar o código gerado para uma região de formulário projetada no Visual Studio

1. Abra o arquivo de code-behind de região de formulário no editor de códigos. Esse arquivo é denominado *YourFormRegion*. Designer.cs ou *YourFormRegion*. VB. Para ver esse arquivo em projetos do Visual Basic, clique o **Show All Files** botão na **Gerenciador de soluções**.

2. Modifique a declaração da classe de região de formulário para que ele deriva <xref:Microsoft.Office.Tools.Outlook.FormRegionBase> em vez de `Microsoft.Office.Tools.Outlook.FormRegionControl`.

3. Modifique o construtor da classe de região de formulário, conforme mostrado nos exemplos de código a seguir.

     O exemplo de código a seguir mostra o construtor de uma classe de região de formulário em um projeto que tem como alvo o .NET Framework 3.5.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(formRegion)
        Me.InitializeComponent()
    End Sub
    ```

    ```csharp
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(formRegion)
    {
        this.InitializeComponent();
    }
    ```

     O exemplo de código a seguir mostra o construtor de uma classe de região de formulário em um projeto que tem como alvo o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(Globals.Factory, formRegion)
        Me.InitializeComponent()
    End Sub
    ```

    ```csharp
    public FormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(Globals.Factory, formRegion)
    {
        this.InitializeComponent();
    }
    ```

4. Modifique a assinatura do `InitializeManifest` método conforme mostrado abaixo. Certifique-se de que você não modifique o código no método; Esse código representa as configurações de região de formulário que você aplicou no designer. Em projetos do Visual c#, você deve expandir a região chamada `Form Region Designer generated code` para ver esse método.

     O exemplo de código a seguir mostra a assinatura do `InitializeManifest` método em um projeto que tem como alvo o .NET Framework 3.5.

    ```vb
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest)

        ' Do not change code in this method.
    End Sub
    ```

    ```csharp
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest)
    {
        // Do not change code in this method.
    }
    ```

     O exemplo de código a seguir mostra a assinatura `InitializeManifest` método em um projeto que tem como alvo o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

    ```vb
    Private Shared Sub InitializeManifest(ByVal manifest As Microsoft.Office.Tools.Outlook.FormRegionManifest,
        ByVal factory As Microsoft.Office.Tools.Outlook.Factory)

        ' Do not change code in this method.
    End Sub
    ```

    ```csharp
    private static void InitializeManifest(Microsoft.Office.Tools.Outlook.FormRegionManifest manifest,
        Microsoft.Office.Tools.Outlook.Factory factory)
    {
        // Do not change code in this method.
    }
    ```

5. Adicione um novo item de região de formulário do Outlook ao seu projeto. Abra o arquivo code-behind para a nova região de formulário, localize o *YourNewFormRegion* `Factory` e `WindowFormRegionCollection` classes no arquivo e copie essas classes para a área de transferência.

6. Exclua a nova região de formulário adicionado ao seu projeto.

7. No arquivo code-behind da região do formulário que você está atualizando para trabalhar no projeto redirecionado, localize o *YourOriginalFormRegion* `Factory` e `WindowFormRegionCollection` classes e substituí-los com o código que você copiou das nova região do formulário.

8. No *YourNewFormRegion* `Factory` e `WindowFormRegionCollection` pesquisar todas as referências a classes, o *YourNewFormRegion* classe e altere cada referência para o  *YourOriginalFormRegion* classe em vez disso. Por exemplo, se a região do formulário que você está atualizando é denominado `SalesDataFormRegion` e a nova região de formulário que você criou na etapa 5 é denominada `FormRegion1`, altere todas as referências de `FormRegion1` para `SalesDataFormRegion`.

#### <a name="to-update-the-generated-code-for-a-form-region-that-you-imported-from-outlook"></a>Para atualizar o código gerado para uma região de formulário que você importou do Outlook

1. Abra o arquivo de code-behind de região de formulário no editor de códigos. Esse arquivo é denominado *YourFormRegion*. Designer.cs ou *YourFormRegion*. VB. Para ver esse arquivo em projetos do Visual Basic, clique o **Show All Files** botão na **Gerenciador de soluções**.

2. Modifique a declaração da classe de região de formulário para que ele deriva <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase> em vez de `Microsoft.Office.Tools.Outlook.ImportedFormRegion`.

3. Modifique o construtor da classe de região de formulário, conforme mostrado nos exemplos de código a seguir.

     O exemplo de código a seguir mostra o construtor de uma classe de região de formulário em um projeto que tem como alvo o .NET Framework 3.5.

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(formRegion)
    End Sub
    ```

    ```csharp
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(formRegion)
    {
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);
    }
    ```

     O exemplo de código a seguir mostra a assinatura do construtor de uma classe de região de formulário em um projeto que tem como alvo o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

    ```vb
    Public Sub New(ByVal formRegion As Microsoft.Office.Interop.Outlook.FormRegion)
        MyBase.New(Globals.Factory, formRegion)
    End Sub
    ```

    ```csharp
    public ImportedFormRegion1(Microsoft.Office.Interop.Outlook.FormRegion formRegion)
        : base(Globals.Factory, formRegion)
    {
        this.FormRegionShowing += new System.EventHandler(this.TaskFormRegion_FormRegionShowing);
        this.FormRegionClosed += new System.EventHandler(this.TaskFormRegion_FormRegionClosed);
    }
    ```

4. Para cada linha de código no `InitializeControls` método que inicializa um controle na classe de região de formulário, modifique o código conforme mostrado abaixo.

     O exemplo de código a seguir mostra como inicializar um controle em um projeto que tem como alvo o .NET Framework 3.5. Nesse código, o `GetFormRegionControl` método tem um parâmetro de tipo que especifica o tipo do controle que é retornado.

    ```vb
    Me.olkTextBox1 = Me.GetFormRegionControl(Of Microsoft.Office.Interop.Outlook.OlkTextBox)("OlkTextBox1")
    ```

    ```csharp
    this.olkTextBox1 = this.GetFormRegionControl<Microsoft.Office.Interop.Outlook.OlkTextBox>("OlkTextBox1");
    ```

     O exemplo de código a seguir mostra como inicializar um controle em um projeto que tem como alvo o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Nesse código, o <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase.GetFormRegionControl%2A> método não tem um parâmetro de tipo. Você deve converter o valor de retorno para o tipo do controle que você estiver inicializando.

    ```vb
    Me.olkTextBox1 = CType(GetFormRegionControl("OlkTextBox1"), Microsoft.Office.Interop.Outlook.OlkTextBox)
    ```

    ```csharp
    this.olkTextBox1 = (Microsoft.Office.Interop.Outlook.OlkTextBox)GetFormRegionControl("OlkTextBox1");
    ```

5. Adicione um novo item de região de formulário do Outlook ao seu projeto. Abra o arquivo code-behind para a nova região de formulário, localize o *YourNewFormRegion* `Factory` e `WindowFormRegionCollection` classes no arquivo e copie essas classes para a área de transferência.

6. Exclua a nova região de formulário adicionado ao seu projeto.

7. No arquivo code-behind da região do formulário que você está atualizando para trabalhar no projeto redirecionado, localize o *YourOriginalFormRegion* `Factory` e `WindowFormRegionCollection` classes e substituí-los com o código que você copiou das nova região do formulário.

8. No *YourNewFormRegion* `Factory` e `WindowFormRegionCollection` pesquisar todas as referências a classes, o *YourNewFormRegion* classe e altere cada referência para o  *YourOriginalFormRegion* classe em vez disso. Por exemplo, se a região do formulário que você está atualizando é denominado `SalesDataFormRegion` e a nova região de formulário que você criou na etapa 5 é denominada `FormRegion1`, altere todas as referências de `FormRegion1` para `SalesDataFormRegion`.

## <a name="instantiate-form-region-classes"></a>Instanciar classes de região de formulário
 Você deve modificar qualquer código que instancia dinamicamente determinadas classes de região do formulário. Em projetos direcionados ao .NET Framework 3.5, você pode instanciar classes de região de formulário como `Microsoft.Office.Tools.Outlook.FormRegionManifest` diretamente. Em projetos que segmentam o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou versões posteriores, essas classes são interfaces que você não pode instanciar diretamente.

 Se a estrutura de destino do seu projeto é alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deve instanciar as interfaces usando métodos que são fornecidos pelo `Globals.Factory` propriedade. Para obter mais informações sobre o `Globals.Factory` propriedade, consulte [Global de acesso a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md).

 A tabela a seguir lista os tipos de região de formulário e o método a ser usado para instanciar os tipos nos projetos que se destinam a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior.

|Tipo|Método de fábrica para usar|
|----------|---------------------------|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|

## <a name="see-also"></a>Consulte também
- [Migrar soluções do Office para o .NET Framework 4 ou posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)
