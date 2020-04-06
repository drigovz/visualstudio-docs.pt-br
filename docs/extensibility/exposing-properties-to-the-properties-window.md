---
title: Expondo Propriedades à Janela propriedades | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f84962628ae550676e2c2eeb10c0f3baeca1bb58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711823"
---
# <a name="expose-properties-to-the-properties-window"></a>Expor propriedades à janela Propriedades

Este passo a passo expõe as propriedades públicas de um objeto à janela **Propriedades.** As alterações que você faz nessas propriedades são refletidas na janela **Propriedades.**

## <a name="prerequisites"></a>Pré-requisitos

A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="expose-properties-to-the-properties-window"></a>Expor propriedades à janela Propriedades

Nesta seção, você cria uma janela de ferramenta personalizada e exibe as propriedades públicas do objeto painel de janela associado na janela **Propriedades.**

### <a name="to-expose-properties-to-the-properties-window"></a>Para expor propriedades à janela Propriedades

1. Toda extensão do Visual Studio começa com um projeto de implantação vsix, que conterá os ativos de extensão. Crie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] um projeto `MyObjectPropertiesExtension`VSIX chamado . Você pode encontrar o modelo de projeto VSIX na caixa de diálogo **Projeto Novo** procurando por "vsix".

2. Adicione uma janela de ferramenta adicionando um `MyToolWindow`modelo de item de janela de ferramenta personalizado chamado . No **Solution Explorer,** clique com o botão direito do mouse no nó do projeto e **selecione Adicionar** > **novo item**. Na **caixa de diálogo Adicionar novo item,** vá para A > **Extensibilidade** de **Itens Visuais C#** e selecione **Janela de ferramenta personalizada**. No **campo Nome** na parte inferior da caixa de diálogo, altere o nome do arquivo para *MyToolWindow.cs*. Para obter mais informações sobre como criar uma janela de ferramenta personalizada, consulte [Criar uma extensão com uma janela de ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Abra *MyToolWindow.cs* e adicione a seguinte declaração usando:

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. Agora adicione os seguintes campos à `MyToolWindow` classe.

   ```csharp
   private ITrackSelection trackSel;
   private SelectionContainer selContainer;

   ```

5. Adicione o código a seguir à classe `MyToolWindow` .

   ```csharp
   private ITrackSelection TrackSelection
   {
       get
       {
           if (trackSel == null)
               trackSel =
                  GetService(typeof(STrackSelection)) as ITrackSelection;
           return trackSel;
       }
   }

   public void UpdateSelection()
   {
       ITrackSelection track = TrackSelection;
       if (track != null)
           track.OnSelectChange((ISelectionContainer)selContainer);
   }

   public void SelectList(ArrayList list)
   {
       selContainer = new SelectionContainer(true, false);
       selContainer.SelectableObjects = list;
       selContainer.SelectedObjects = list;
       UpdateSelection();
   }

   public override void OnToolWindowCreated()
   {
       ArrayList listObjects = new ArrayList();
       listObjects.Add(this);
       SelectList(listObjects);
   }
   ```

    A `TrackSelection` propriedade `GetService` usa `STrackSelection` para obter um <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> serviço, que fornece uma interface. O `OnToolWindowCreated` manipulador `SelectList` de eventos e o método juntos criam uma lista de objetos selecionados que contém apenas o próprio objeto do painel de janela da ferramenta. O `UpdateSelection` método diz à janela **Propriedades** para exibir as propriedades públicas do painel da janela da ferramenta.

6. Compile o projeto e comece a depuração. A instância experimental do Visual Studio deve aparecer.

7. Se a janela **Propriedades** não estiver visível, abra-a pressionando **F4**.

8. Abra a janela **MyToolWindow.** Você pode encontrá-lo no **View** > **Other Windows**.

    A janela se abre e as propriedades públicas do painel de janela aparecem na janela **Propriedades.**

9. Altere a **propriedade Legenda** na janela **Propriedades** para Propriedades do **Meu Objeto**.

     A legenda da janela MyToolWindow muda de acordo.

## <a name="expose-tool-window-properties"></a>Expor propriedades da janela da ferramenta

Nesta seção, você adiciona uma janela de ferramenta e expõe suas propriedades. As alterações que você faz nas propriedades são refletidas na janela **Propriedades.**

### <a name="to-expose-tool-window-properties"></a>Para expor as propriedades da janela da ferramenta

1. Abra *MyToolWindow.cs*e adicione a propriedade pública `MyToolWindow` booleana IsChecked à classe.

    ```csharp
    [Category("My Properties")]
    [Description("MyToolWindowControl properties")]
    public bool IsChecked
    {
        get {
            if (base.Content == null)  return false;
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;
        }
        set {
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;
        }
    }
    ```

     Esta propriedade obtém seu estado a partir da caixa de seleção WPF que você criará mais tarde.

2. Abra *MyToolWindowControl.xaml.cs* e substitua o construtor MyToolWindowControl pelo seguinte código.

    ```vb
    private MyToolWindow pane;
    public MyToolWindowControl(MyToolWindow pane)
    {
        InitializeComponent();
        this.pane = pane;
        checkBox.IsChecked = false;
    }
    ```

     Isso `MyToolWindowControl` dá acesso `MyToolWindow` ao painel.

3. Em *MyToolWindow.cs,* `MyToolWindow` mude o construtor da seguinte forma:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. Alterar para a visualização de design do MyToolWindowControl.

5. Exclua o botão e adicione uma caixa de seleção da caixa de **ferramentas** ao canto superior esquerdo.

6. Adicione os eventos verificados e não verificados. Selecione a caixa de seleção na exibição de design. Na janela **Propriedades,** clique no botão manipuladores de eventos (no canto superior direito da janela **Propriedades).** Encontre **Verificação** e digite **checkbox_Checked** na caixa de texto, em seguida, encontre **Desmarcado** e digite **checkbox_Unchecked** na caixa de texto.

7. Adicione os manipuladores de eventos da caixa de seleção:

    ```csharp
    private void checkbox_Checked(object sender, RoutedEventArgs e)
    {
        pane.IsChecked = true;
        pane.UpdateSelection();
    }
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)
    {
        pane.IsChecked = false;
        pane.UpdateSelection();
    }
    ```

8. Compile o projeto e comece a depuração.

9. No caso experimental, abra a janela **MyToolWindow.**

     Procure as propriedades da janela na janela **Propriedades.** A propriedade **IsChecked** aparece na parte inferior da janela, na categoria **Minhas propriedades.**

10. Verifique a caixa de seleção na janela **MyToolWindow.** **IsChecked** na **janela Propriedades** altera em **True**. Limpe a caixa de seleção na janela **MyToolWindow.** **IsChecked** in the **Properties** window changes to **False**. Alterar o valor de **IsChecked** na janela **Propriedades.** A caixa de seleção na janela **MyToolWindow** muda para corresponder ao novo valor.

    > [!NOTE]
    > Se você tiver que descartar um objeto exibido na `OnSelectChange` janela `null` **Propriedades,** ligue com um recipiente de seleção primeiro. Depois de descartar a propriedade ou objeto, você pode <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> mudar <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> para um contêiner de seleção que tenha atualizado e listado.

## <a name="change-selection-lists"></a>Alterar listas de seleção

 Nesta seção, você adiciona uma lista de seleção para uma classe de propriedade básica e usa a interface da janela da ferramenta para escolher qual lista de seleção exibir.

### <a name="to-change-selection-lists"></a>Para alterar listas de seleção

1. Abra *MyToolWindow.cs* e adicione `Simple`uma classe pública chamada .

    ```csharp
    public class Simple
    {
        private string someText = "";

        [Category("My Properties")]
        [Description("Simple Properties")]
        [DisplayName("My Text")]
        public string SomeText
        {
            get { return someText; }
            set { someText = value; }
        }

        [Category("My Properties")]
        [Description("Read-only property")]
        public bool ReadOnly
        {
            get { return false; }
        }
    }
    ```

2. Adicione `SimpleObject` uma propriedade `MyToolWindow` à classe, além de dois métodos para alternar `Simple` a seleção da janela **Propriedades** entre o painel de janela e o objeto.

    ```csharp
    private Simple simpleObject = null;
    public Simple SimpleObject
    {
        get
        {
            if (simpleObject == null) simpleObject = new Simple();
            return simpleObject;
        }
    }

    public void SelectSimpleList()
    {
        ArrayList listObjects = new ArrayList();
        listObjects.Add(SimpleObject);
        SelectList(listObjects);
    }

    public void SelectThisList()
    {
        ArrayList listObjects = new ArrayList();
        listObjects.Add(this);
        SelectList(listObjects);
    }
    ```

3. Em *MyToolWindowControl.cs,* substitua os manipuladores da caixa de seleção por estas linhas de código:

    ```csharp
    private void checkbox_Checked(object sender, RoutedEventArgs e)
     {
        pane.IsChecked = true;
        pane.SelectSimpleList();
        pane.UpdateSelection();
    }
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)
    {
        pane.IsChecked = false;
        pane.SelectThisList();
        pane.UpdateSelection();
    }
    ```

4. Compile o projeto e comece a depuração.

5. No caso experimental, abra a janela **MyToolWindow.**

6. Selecione a caixa de seleção na janela **MyToolWindow.** A **Properties** janela Propriedades `Simple` exibe as propriedades do objeto, **SomeText** e **ReadOnly**. Desmarque a caixa de seleção. As propriedades públicas da janela aparecem na janela **Propriedades.**

    > [!NOTE]
    > O nome de exibição de **SomeText** é **Meu Texto**.

## <a name="best-practice"></a>Melhor prática

Neste passo a <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> passo, é implementado para que a coleta de objetos selecionáveis e a coleção de objetos selecionados sejam a mesma coleção. Apenas o objeto selecionado aparece na lista Do Navegador de Propriedades. Para obter uma implementação mais completa do ISelectionContainer, consulte as amostras Reference.ToolWindow.

As janelas de ferramentas do Visual Studio persistem entre as sessões do Visual Studio. Para obter mais informações sobre a <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>persistência do estado da janela da ferramenta, consulte .

## <a name="see-also"></a>Confira também

- [Estender propriedades e a janela Propriedade](../extensibility/extending-properties-and-the-property-window.md)
