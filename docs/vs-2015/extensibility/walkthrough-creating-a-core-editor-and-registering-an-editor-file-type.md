---
title: 'Walkthrough: Criando um editor principal e registrando um tipo de arquivo do editor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 14296aa335ba6710d4d9eac8e5338af7463c0aac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687643"
---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>Passo a passo: Criar um editor principal e registrar um tipo de arquivo do editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tutorial demonstra como criar um VSPackage que inicia o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor de núcleo quando um arquivo com a extensão de nome de arquivo. MyExt é carregado.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para seguir este passo a passos, você deve instalar o SDK do Visual Studio. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Locais para o modelo de projeto de pacote do Visual Studio  
 O modelo de projeto de pacote do Visual Studio pode ser encontrado em três locais diferentes na caixa de diálogo **novo projeto** :  
  
1. Em extensibilidade de Visual Basic. O idioma padrão do projeto é Visual Basic.  
  
2. Em extensibilidade do C#. O idioma padrão do projeto é C#.  
  
3. Em outra extensibilidade de tipos de projeto. O idioma padrão do projeto é C++.  
  
### <a name="to-create-the-vspackage"></a>Para criar o VSPackage  
  
- Inicie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e crie um [!INCLUDE[csprcs](../includes/csprcs-md.md)] VSPackage chamado `MyPackage` , conforme descrito em [passo a passo: Criando um comando de menu VSPackage](https://msdn.microsoft.com/d699c149-5d1e-47ff-94c7-e1222af02c32).  
  
### <a name="to-add-the-editor-factory"></a>Para adicionar a fábrica do editor  
  
1. Clique com o botão direito do mouse no projeto **MyPackage** , aponte para **Adicionar** e clique em **classe**.  
  
2. Na caixa de diálogo **Adicionar novo item** , verifique se o modelo de **classe** está selecionado, digite `EditorFactory.cs` para o nome e clique em **Adicionar** para adicionar a classe ao seu projeto.  
  
     O arquivo EditorFactory.cs deve ser aberto automaticamente.  
  
3. Referencie os seguintes assemblies do seu código.  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    Imports Microsoft.VisualStudio  
    Imports Microsoft.VisualStudio.Shell  
    Imports Microsoft.VisualStudio.Shell.Interop  
    Imports Microsoft.VisualStudio.OLE.Interop  
    Imports Microsoft.VisualStudio.TextManager.Interop  
    Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
    ```  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
    ```  
  
4. Adicione um GUID à `EditorFactory` classe adicionando o `Guid` atributo imediatamente antes da declaração de classe.  
  
     Você pode gerar um novo GUID usando o programa guidgen.exe no prompt de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] comando ou clicando em **Criar GUID** no menu **ferramentas** . O GUID usado aqui é apenas um exemplo; Não o use em seu projeto.  
  
    ```vb  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```csharp  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5. Na definição de classe, adicione duas variáveis privadas para conter o pacote pai e um provedor de serviços.  
  
    ```vb  
    Class EditorFactory  
        Private parentPackage As Package  
        Private serviceProvider As IOleServiceProvider  
    ```  
  
    ```csharp  
    class EditorFactory  
    {  
        private Package parentPackage;  
        private IOleServiceProvider serviceProvider;  
    }  
  
    ```  
  
6. Adicione um construtor de classe pública que aceite um parâmetro do tipo <xref:Microsoft.VisualStudio.Shell.Package> :  
  
    ```vb  
    Public Sub New(ByVal parentPackage As Package)  
        Me.parentPackage = parentPackage  
    End Sub  
    ```  
  
    ```csharp  
    public EditorFactory(Package parentPackage)  
    {  
        this.parentPackage = parentPackage;  
    }  
    ```  
  
7. Modifique a `EditorFactory` declaração de classe para derivar da <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface.  
  
    ```vb  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```csharp  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8. Clique com o botão direito do mouse em <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> , clique em **implementar interface**e, em seguida, clique em **implementar interface explicitamente**.  
  
     Isso adiciona os quatro métodos que devem ser implementados na <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface.  
  
9. Substitua o conteúdo do método `IVsEditorFactory.Close` pelo código a seguir.  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. Substitua o conteúdo do `IVsEditorFactory.SetSite` pelo código a seguir.  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. Substitua o conteúdo do método `IVsEditorFactory.MapLogicalView` pelo código a seguir.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_NOTIMPL;  
    pbstrPhysicalView = null;   // We support only one view.  
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))  
    {  
        retval = VSConstants.S_OK;  
    }  
    return retval;  
    ```  
  
12. Substitua o conteúdo do método `IVsEditorFactory.CreateEditorInstance` pelo código a seguir.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_FAIL          
  
    ' Initialize these to empty to start with   
    ppunkDocView = IntPtr.Zero  
    ppunkDocData = IntPtr.Zero  
    pbstrEditorCaption = ""  
    pguidCmdUI = Guid.Empty  
    pgrfCDW = 0  
  
    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _  
    VSConstants.CEF_SILENT)) = 0 Then  
        Throw New ArgumentException("Only Open or Silent is valid")  
    End If  
    If punkDocDataExisting <> IntPtr.Zero Then  
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA  
    End If  
  
    ' Instantiate a text buffer of type VsTextBuffer.   
    ' Note: we only need an IUnknown (object) interface for   
    ' this invocation.   
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID  
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown  
    Dim pTextBuffer As Object = pTextBuffer = _  
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _  
    GetType(Object))  
  
    If Not pTextBuffer Is Nothing Then  
        ' "Site" the text buffer with the service provider we were   
        ' provided.   
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _  
        IObjectWithSite)  
        If Not textBufferSite Is Nothing Then  
            textBufferSite.SetSite(Me.serviceProvider)  
        End If  
  
        ' Instantiate a code window of type IVsCodeWindow.   
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID  
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID  
        Dim pCodeWindow As IVsCodeWindow = _  
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _  
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)  
        If Not pCodeWindow Is Nothing Then  
            ' Give the text buffer to the code window.   
            ' We are giving up ownership of the text buffer!   
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))  
  
            ' Now tell the caller about all this new stuff   
            ' that has been created.   
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)  
  
            ' Specify the command UI to use so keypresses are   
            ' automatically dealt with.   
            pguidCmdUI = VSConstants.GUID_TextEditorFactory  
  
            ' This caption is appended to the filename and   
            ' lets us know our invocation of the core editor   
            ' is up and running.   
            pbstrEditorCaption = " [MyPackage]"  
  
            retval = VSConstants.S_OK  
        End If  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_FAIL;  
  
    // Initialize these to empty to start with  
    ppunkDocView       = IntPtr.Zero;  
    ppunkDocData       = IntPtr.Zero;  
    pbstrEditorCaption = "";  
    pguidCmdUI         = Guid.Empty;   
    pgrfCDW            = 0;  
  
    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |   
          VSConstants.CEF_SILENT)) == 0)  
    {   
        throw new ArgumentException("Only Open or Silent is valid");  
    }  
    if (punkDocDataExisting != IntPtr.Zero)  
    {  
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;  
    }  
  
    // Instantiate a text buffer of type VsTextBuffer.  
    // Note: we only need an IUnknown (object) interface for   
    // this invocation.  
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;  
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;  
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(  
          ref clsidTextBuffer,  
          ref iidTextBuffer,  
          typeof(object));  
  
    if (pTextBuffer != null)  
    {  
        // "Site" the text buffer with the service provider we were  
        // provided.  
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;  
        if (textBufferSite != null)  
        {  
            textBufferSite.SetSite(this.serviceProvider);  
        }  
  
        // Instantiate a code window of type IVsCodeWindow.  
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;  
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;  
        IVsCodeWindow pCodeWindow =  
        (IVsCodeWindow)this.parentPackage.CreateInstance(   
              ref clsidCodeWindow,  
              ref iidCodeWindow,  
              typeof(IVsCodeWindow));  
        if (pCodeWindow != null)  
        {  
            // Give the text buffer to the code window.  
            // We are giving up ownership of the text buffer!  
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);  
  
            // Now tell the caller about all this new stuff   
            // that has been created.  
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);  
  
            // Specify the command UI to use so keypresses are   
            // automatically dealt with.  
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;  
  
            // This caption is appended to the filename and  
            // lets us know our invocation of the core editor   
            // is up and running.  
            pbstrEditorCaption = " [MyPackage]";  
  
            retval = VSConstants.S_OK;  
        }   
    }   
    return retval;   
    ```  
  
13. Compile o projeto e verifique se não há erros.  
  
### <a name="to-register-the-editor-factory"></a>Para registrar a fábrica do editor  
  
1. Em **Gerenciador de soluções**, clique duas vezes no arquivo Resources. resx para abri-lo na tabela de cadeias de caracteres, na qual a entrada **seqüência1 está** selecionada.  
  
2. Altere o nome do identificador para `IDS_EDITORNAME` e o texto para o **Editor myPackage.** Essa cadeia de caracteres será exibida como o nome do seu editor.  
  
3. Abra o arquivo VSPackage. resx e adicione uma nova cadeia de caracteres, defina o nome como **101** e o valor como `IDS_EDITORNAME` . Isso fornece ao pacote uma ID de recurso para acessar a cadeia de caracteres que você acabou de criar.  
  
    > [!NOTE]
    > Se o arquivo VSPackage. resx contiver outra cadeia de caracteres que o `name` atributo definiu como **101**, substitua outro valor numérico exclusivo, aqui e nas etapas a seguir.  
  
4. No **Gerenciador de soluções**, abra o arquivo MyPackagePackage.cs.  
  
     Este é o arquivo de pacote principal.  
  
5. Adicione os seguintes atributos de usuário logo antes do `Guid` atributo.  
  
    ```vb  
    <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
    <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
          ".myext", 32, NameResourceID:=101 )> _  
    ```  
  
    ```csharp  
    [ProvideEditorFactory(typeof(EditorFactory), 101)]  
    [ProvideEditorExtension(typeof(EditorFactory),   
          ".myext", 32, NameResourceID = 101)]   
    ```  
  
     O <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> atributo associa a extensão de arquivo. myext à sua fábrica de editor para que, sempre que um arquivo que tenha essa extensão seja carregado, a fábrica do editor seja invocada.  
  
6. Adicione uma variável particular à `MyPackage` classe, logo antes do Construtor, e dê a ela o tipo `EditorFactory` .  
  
    ```vb  
    Private editorFactory As EditorFactory  
    ```  
  
    ```csharp  
    private EditorFactory editorFactory;  
    ```  
  
7. Localize o `Initialize` método (talvez você precise abrir a `Package Members` região oculta) e adicione o código a seguir após a chamada para `base.Initialize()` .  
  
    ```vb  
    'Create our editor factory and register it.   
    Me.editorFactory = New EditorFactory(Me)  
    MyBase.RegisterEditorFactory(Me.editorFactory)  
    ```  
  
    ```csharp  
    // Create our editor factory and register it.  
    this.editorFactory = new EditorFactory(this);  
    base.RegisterEditorFactory(this.editorFactory);  
  
    ```  
  
8. Compile o programa e verifique se não há erros.  
  
     Essa etapa registra a fábrica do editor no hive experimental do registro para o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Se for solicitado que você substitua o arquivo Resource. h, clique em **OK**.  
  
9. Crie um arquivo de exemplo chamado textarquivo1. myext.  
  
10. Pressione **F5** para abrir uma instância do experimental [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
11. No experimental [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , no menu **arquivo** , aponte para **abrir** e clique em **arquivo**.  
  
12. Localize textarquivo1. myext e clique em **abrir**.  
  
     O arquivo agora deve ser carregado.  
  
## <a name="robust-programming"></a>Programação robusta  
 O [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor central lida com uma ampla variedade de tipos de arquivos baseados em texto e trabalha em conjunto com os serviços de linguagem para fornecer um rico grupo de recursos, como realce de sintaxe, correspondência de chaves e listas de conclusão de palavras e preenchimento de membros do IntelliSense. Se você estiver trabalhando com arquivos baseados em texto, poderá usar o editor principal junto com um serviço de idioma personalizado que dá suporte a seus tipos de arquivo específicos.  
  
 Um VSPackage pode invocar o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor central fornecendo uma fábrica de editor. Essa fábrica do editor é usada sempre que um arquivo associado a ele é carregado. Se o arquivo fizer parte de um projeto, o editor central será invocado automaticamente, a menos que seja substituído por seu VSPackage. No entanto, se o arquivo for carregado fora de um projeto, o editor principal deverá ser invocado explicitamente pelo seu VSPackage.  
  
 Para obter mais informações sobre o editor principal, consulte [dentro do editor principal](../extensibility/inside-the-core-editor.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Dentro do editor principal](../extensibility/inside-the-core-editor.md)   
 [Criando uma instância do editor principal usando a API herdada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
