---
title: Atualizar personalizações da faixa de das de projetos do Office migradas para o .NET Framework 4, 4,5
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
ms.openlocfilehash: c7d7ab5755f592e57e76dcd68f3dcb9dc2a7eab9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71254359"
---
# <a name="update-ribbon-customizations-in-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Atualize as personalizações da faixa de na de projetos do Office que você migra para o .NET Framework 4 ou o .NET Framework 4,5
  Se o seu projeto contiver uma personalização da faixa de opções que foi criada usando o item de projeto **da faixa de opções (Visual Designer)** , você deverá fazer as seguintes alterações no código do projeto se a estrutura de destino for alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior.

- Modifique o código da faixa de Ribbon gerado.

- Modifique qualquer código que instancie os controles da faixa de forma em tempo de execução, lide com os eventos da faixa de forma ou defina a posição de um componente da faixa de uma das

## <a name="update-the-generated-ribbon-code"></a>Atualizar o código da faixa de Ribbon gerado
 Se a estrutura de destino do seu projeto for alterada para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deverá alterar o código gerado para o item da faixa de opções executando as etapas a seguir. Os arquivos de código que você precisa atualizar dependem da linguagem de programação e de como você criou o projeto:

- Em projetos Visual Basic ou em projetos do Visual C# que você criou em [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] ou [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] Execute todas as etapas no arquivo code-behind da faixa de opções (*YourRibbonItem*. Designer.cs ou *YourRibbonItem*. Designer. vb). Para ver o arquivo code-behind em projetos Visual Basic, clique no botão **Mostrar todos os arquivos** em **Gerenciador de soluções**.

- Em projetos do Visual C# que você criou no Visual Studio 2008 e, em seguida, atualizado para [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] o, execute as duas primeiras etapas no arquivo de código da faixa de bits (*YourRibbonItem*. cs ou *YourRibbonItem*. vb) e execute as etapas restantes no arquivo code-behind da faixa de bits.

### <a name="to-change-the-generated-ribbon-code"></a>Para alterar o código da faixa de Ribbon gerado

1. Modifique a declaração da classe Ribbon para que ela seja derivada de <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> em vez de `Microsoft.Office.Tools.Ribbon.OfficeRibbon` .

2. Modifique o construtor da classe Ribbon, conforme mostrado abaixo. Se você tiver adicionado qualquer um de seus próprios códigos ao construtor, não altere seu código. Em projetos Visual Basic, modifique somente o construtor sem parâmetros. Ignore o outro construtor.

     O exemplo de código a seguir mostra o construtor padrão de uma classe da faixa de opções em um projeto que tem como alvo o .NET Framework 3,5.

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
    End Sub
    ```

    ```csharp
    public Ribbon1()
    {
        InitializeComponent();
    }
    ```

     O exemplo de código a seguir mostra o construtor padrão de uma classe da faixa de opções em um projeto que tem como destino o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior.

    ```vb
    Public Sub New()
        MyBase.New(Globals.Factory.GetRibbonFactory())
        InitializeComponent()
    End Sub
    ```

    ```csharp
    public Ribbon1()
        : base(Globals.Factory.GetRibbonFactory())
    {
        InitializeComponent();
    }
    ```

3. No `InitializeComponent` método, modifique qualquer código que construa um controle da faixa de forma para que o código use um dos métodos auxiliares do <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> objeto.

    > [!NOTE]
    > Em projetos do Visual C#, você deve expandir a região nomeada `Component Designer generated code` para ver o `InitializeComponent` método.

     Por exemplo, suponha que o arquivo contém a linha de código a seguir que instancia um <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> nome `button1` em um projeto que se destina ao .NET Framework 3,5.

    ```vb
    Me.button1 = New Microsoft.Office.Tools.Ribbon.RibbonButton()
    ```

    ```csharp
    this.button1 = new Microsoft.Office.Tools.Ribbon.RibbonButton();
    ```

     Em um projeto que tem como alvo o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deve usar o código a seguir em vez disso.

    ```vb
    Me.button1 = Me.Factory.CreateRibbonButton()
    ```

    ```csharp
    this.button1 = this.Factory.CreateRibbonButton();
    ```

     Para obter uma lista completa dos métodos auxiliares para os controles da faixa de faixas, consulte [instanciar controles da faixa](#ribboncontrols)de medida.

4. Em projetos do Visual C#, modifique qualquer linha de código no `InitializeComponent` método que usa um <xref:System.EventHandler%601> delegado para usar um delegado de faixa de uma específico.

     Por exemplo, suponha que o arquivo contém a linha de código a seguir que manipula o <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> evento em um projeto que tem como alvo o .NET Framework 3,5.

    \<CodeContentPlaceHolder>8 </CodeContentPlaceHolder> em um projeto direcionado para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deve usar o código a seguir em vez disso.

    \<CodeContentPlaceHolder>9 </CodeContentPlaceHolder> para obter uma lista completa dos delegados da faixa de faixas, consulte [manipular eventos da faixa](#ribbonevents)de medida.

5. Em projetos Visual Basic, localize a `ThisRibbonCollection` classe no final do arquivo. Modifique a declaração dessa classe para que ela não herde mais de `Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection` .

## <a name="instantiate-ribbon-controls"></a><a name="ribboncontrols"></a> Instanciar controles da faixa de faixas
 Você deve modificar qualquer código que instancie dinamicamente os controles da faixa de forma. Em projetos direcionados para o .NET Framework 3,5, os controles da faixa de tipos são classes que você pode instanciar diretamente em determinados cenários. Em projetos direcionados para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, esses controles são interfaces que você não pode instanciar diretamente. Você deve criar os controles usando métodos que são fornecidos pelo <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> objeto.

 Existem duas maneiras de acessar o objeto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>:

- Usando a propriedade Factory da classe Ribbon. Use essa abordagem no código na classe Ribbon.

- Usando o método `Globals.Factory.GetRibbonFactory`. Use essa abordagem no código fora da classe Ribbon. Para obter mais informações sobre a classe Globals, consulte [acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md).

  O exemplo de código a seguir demonstra como criar um <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> em uma classe de faixa de opções em um projeto direcionado para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior.

\<CodeContentPlaceHolder>10 </CodeContentPlaceHolder> 
 \<CodeContentPlaceHolder> 11 </CodeContentPlaceHolder> a tabela a seguir lista os controles que você pode criar programaticamente e o método a ser usado para criar os controles em projetos direcionados para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior.

|Control|Método RibbonFactory para usar no [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e em projetos posteriores|
|-------------| - |
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButton%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButtonGroup%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonCheckBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonComboBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDialogLauncher%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>:|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDown%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDownItem>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDownItem%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonEditBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGallery%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGroup%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonLabel%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonManager>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonManager%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonMenu%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSeparator%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSplitButton%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonTab%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonToggleButton%2A>|

## <a name="handle-ribbon-events"></a><a name="ribbonevents"></a> Manipular eventos da faixa de das
 Você deve modificar qualquer código que manipule eventos de controles da faixa de faixas. Em projetos que visam o .NET Framework 3,5, esses eventos são tratados pelo <xref:System.EventHandler%601> delegado genérico. Em projetos direcionados [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] para o ou posterior, esses eventos agora são tratados por outros delegados.

 A tabela a seguir lista os eventos da faixa de opções e os delegados associados a eles em projetos direcionados para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior.

|Evento|Delegar para usar no [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] e projetos posteriores|
|-----------| - |
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage> evento em uma classe de faixa de Ribbon gerada|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|

## <a name="set-the-position-of-a-ribbon-component-programmatically"></a>Definir a posição de um componente da faixa de forma programaticamente
 Você deve modificar qualquer código que defina a posição de grupos de faixas de faixa, guias ou controles. Em projetos que visam o .NET Framework 3,5, você pode usar `AfterOfficeId` os `BeforeOfficeId` métodos e da `Microsoft.Office.Tools.Ribbon.RibbonPosition` classe estática para atribuir a `Position` propriedade de um grupo, guia ou controle. Em projetos direcionados para o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou posterior, você deve acessar esses métodos usando a <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A> propriedade fornecida pelo <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> objeto.

 Existem duas maneiras de acessar o objeto <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>:

- Usando a propriedade `Factory` da classe Ribbon. Use essa abordagem no código na classe Ribbon.

- Usando o método `Globals.Factory.GetRibbonFactory`. Use essa abordagem no código fora da classe Ribbon. Para obter mais informações sobre a classe Globals, consulte [acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md).

  O exemplo de código a seguir demonstra como definir a `Position` propriedade de uma guia em uma classe da faixa de opções em um projeto que tem como alvo o .NET Framework 3,5.

```vb
Me.tab1.Position = RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = RibbonPosition.AfterOfficeId("TabHome");
```

 O exemplo de código a seguir demonstra a mesma tarefa em um projeto que tem como destino o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] .

```vb
Me.tab1.Position = Me.Factory.RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = this.Factory.RibbonPosition.AfterOfficeId("TabHome");
```

## <a name="see-also"></a>Confira também
- [Migrar soluções do Office para o .NET Framework 4 ou posterior](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Designer de faixa de das](../vsto/ribbon-designer.md)
