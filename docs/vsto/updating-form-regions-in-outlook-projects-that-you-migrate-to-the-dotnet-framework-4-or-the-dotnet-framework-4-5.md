---
title: Atualizar as regiões de formulário do Outlook quando migradas para o .NET Framework 4,5
description: Você deve modificar seu código se a estrutura de destino de um projeto de suplemento do VSTO do Outlook com uma região de formulário for alterada para o .NET Framework 4 ou posterior.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 15b212a8b7dde85e66b18b78d356bdb31c62836a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921890"
---
# <a name="update-outlook-form-regions-when-migrated-to-net-framework-45"></a>Atualizar as regiões de formulário do Outlook quando migradas para o .NET Framework 4,5

  Se a estrutura de destino de um projeto de suplemento do VSTO do Outlook com uma região de formulário for alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deverá fazer algumas alterações no código de região de formulário gerado e em qualquer código que instancie determinadas classes de região de formulário em tempo de execução.

## <a name="update-the-generated-form-region-code"></a>Atualizar o código de região do formulário gerado
 Se a estrutura de destino do projeto for alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deverá alterar o código de região do formulário gerado. As alterações feitas são diferentes para as regiões de formulário que você criou no Visual Studio e nas regiões de formulário que você importou do Outlook. Para obter mais informações sobre as diferenças entre esses tipos de regiões de formulário, consulte [criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md).

### <a name="to-update-the-generated-code-for-a-form-region-that-you-designed-in-visual-studio"></a>Para atualizar o código gerado para uma região de formulário que você criou no Visual Studio

1. Abra o arquivo code-behind da região do formulário no editor de código. Esse arquivo é denominado *YourFormRegion*. Designer.cs ou *YourFormRegion*. Designer. vb. Para ver esse arquivo em projetos Visual Basic, clique no botão **Mostrar todos os arquivos** em **Gerenciador de soluções**.

2. Modifique a declaração da classe de região do formulário para que ela seja derivada de <xref:Microsoft.Office.Tools.Outlook.FormRegionBase> em vez de `Microsoft.Office.Tools.Outlook.FormRegionControl` .

3. Modifique o construtor da classe de região do formulário, conforme mostrado nos exemplos de código a seguir.

     O exemplo de código a seguir mostra o construtor de uma classe de região de formulário em um projeto que tem como destino o .NET Framework 3,5.

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

     O exemplo de código a seguir mostra o construtor de uma classe de região de formulário em um projeto que tem como destino o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

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

4. Modifique a assinatura do `InitializeManifest` método, conforme mostrado abaixo. Certifique-se de não modificar o código no método; Esse código representa as configurações de região de formulário que você aplicou no designer. Em projetos do Visual C#, você deve expandir a região nomeada `Form Region Designer generated code` para ver esse método.

     O exemplo de código a seguir mostra a assinatura do `InitializeManifest` método em um projeto que tem como destino o .NET Framework 3,5.

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

     O exemplo de código a seguir mostra o método de assinatura `InitializeManifest` em um projeto que tem como destino o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

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

5. Adicione um novo item de região de formulário do Outlook ao seu projeto. Abra o arquivo code-behind para a nova região de formulário, localize o *YourNewFormRegion* `Factory` e as `WindowFormRegionCollection` classes no arquivo e copie essas classes para a área de transferência.

6. Exclua a nova região de formulário que você adicionou ao seu projeto.

7. No arquivo code-behind da região do formulário que você está atualizando para funcionar no projeto redirecionado, localize o *YourOriginalFormRegion* `Factory` e as `WindowFormRegionCollection` classes e substitua-os pelo código que você copiou da nova região do formulário.

8. No *YourNewFormRegion* `Factory` e nas `WindowFormRegionCollection` classes, pesquise todas as referências à classe *YourNewFormRegion* e altere cada referência para a classe *YourOriginalFormRegion* em vez disso. Por exemplo, se a região de formulário que você está atualizando for nomeada `SalesDataFormRegion` e a nova região de formulário criada na etapa 5 for denominada `FormRegion1` , altere todas as referências de `FormRegion1` para `SalesDataFormRegion` .

#### <a name="to-update-the-generated-code-for-a-form-region-that-you-imported-from-outlook"></a>Para atualizar o código gerado para uma região de formulário que você importou do Outlook

1. Abra o arquivo code-behind da região do formulário no editor de código. Esse arquivo é denominado *YourFormRegion*. Designer.cs ou *YourFormRegion*. Designer. vb. Para ver esse arquivo em projetos Visual Basic, clique no botão **Mostrar todos os arquivos** em **Gerenciador de soluções**.

2. Modifique a declaração da classe de região do formulário para que ela seja derivada de <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase> em vez de `Microsoft.Office.Tools.Outlook.ImportedFormRegion` .

3. Modifique o construtor da classe de região do formulário, conforme mostrado nos exemplos de código a seguir.

     O exemplo de código a seguir mostra o construtor de uma classe de região de formulário em um projeto que tem como destino o .NET Framework 3,5.

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

     O exemplo de código a seguir mostra a assinatura do construtor de uma classe de região de formulário em um projeto que tem como destino o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

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

4. Para cada linha de código no `InitializeControls` método que inicializa um controle na classe de região do formulário, modifique o código conforme mostrado abaixo.

     O exemplo de código a seguir mostra como inicializar um controle em um projeto que tem como alvo o .NET Framework 3,5. Nesse código, o `GetFormRegionControl` método tem um parâmetro de tipo que especifica o tipo do controle retornado.

    ```vb
    Me.olkTextBox1 = Me.GetFormRegionControl(Of Microsoft.Office.Interop.Outlook.OlkTextBox)("OlkTextBox1")
    ```

    ```csharp
    this.olkTextBox1 = this.GetFormRegionControl<Microsoft.Office.Interop.Outlook.OlkTextBox>("OlkTextBox1");
    ```

     O exemplo de código a seguir mostra como inicializar um controle em um projeto que tem como destino o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Nesse código, o <xref:Microsoft.Office.Tools.Outlook.ImportedFormRegionBase.GetFormRegionControl%2A> método não tem um parâmetro de tipo. Você deve converter o valor de retorno no tipo do controle que está inicializando.

    ```vb
    Me.olkTextBox1 = CType(GetFormRegionControl("OlkTextBox1"), Microsoft.Office.Interop.Outlook.OlkTextBox)
    ```

    ```csharp
    this.olkTextBox1 = (Microsoft.Office.Interop.Outlook.OlkTextBox)GetFormRegionControl("OlkTextBox1");
    ```

5. Adicione um novo item de região de formulário do Outlook ao seu projeto. Abra o arquivo code-behind para a nova região de formulário, localize o *YourNewFormRegion* `Factory` e as `WindowFormRegionCollection` classes no arquivo e copie essas classes para a área de transferência.

6. Exclua a nova região de formulário que você adicionou ao seu projeto.

7. No arquivo code-behind da região do formulário que você está atualizando para funcionar no projeto redirecionado, localize o *YourOriginalFormRegion* `Factory` e as `WindowFormRegionCollection` classes e substitua-os pelo código que você copiou da nova região do formulário.

8. No *YourNewFormRegion* `Factory` e nas `WindowFormRegionCollection` classes, pesquise todas as referências à classe *YourNewFormRegion* e altere cada referência para a classe *YourOriginalFormRegion* em vez disso. Por exemplo, se a região de formulário que você está atualizando for nomeada `SalesDataFormRegion` e a nova região de formulário criada na etapa 5 for denominada `FormRegion1` , altere todas as referências de `FormRegion1` para `SalesDataFormRegion` .

## <a name="instantiate-form-region-classes"></a>Instanciar classes de região de formulário
 Você deve modificar qualquer código que instancie dinamicamente determinadas classes de região de formulário. Em projetos que visam o .NET Framework 3,5, você pode instanciar classes de região de formulário, como `Microsoft.Office.Tools.Outlook.FormRegionManifest` diretamente. Em projetos direcionados para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, essas classes são interfaces que você não pode instanciar diretamente.

 Se a estrutura de destino do seu projeto for alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deverá instanciar as interfaces usando métodos fornecidos pela `Globals.Factory` propriedade. Para obter mais informações sobre a `Globals.Factory` propriedade, consulte [acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md).

 A tabela a seguir lista os tipos de região de formulário e o método a ser usado para instanciar os tipos em projetos direcionados para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior.

|Tipo|Método de fábrica a ser usado|
|----------|---------------------------|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionCustomAction>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionCustomAction%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionInitializingEventArgs%2A>|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest>|<xref:Microsoft.Office.Tools.Outlook.Factory.CreateFormRegionManifest%2A>|

## <a name="see-also"></a>Confira também
- [Migrar soluções do Office para o .NET Framework 4 ou posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Criar regiões de formulário do Outlook](../vsto/creating-outlook-form-regions.md)
