---
title: Adaptando o código herdado para o editor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb90723a72c10dbf6cfda5edd4aa68f71f1c6b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184917"
---
# <a name="adapting-legacy-code-to-the-editor"></a>Adaptar um código herdado para o Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O editor do Visual Studio tem muitos recursos que você pode acessar a partir de componentes de código existentes. As instruções a seguir mostram como adaptar um componente não MEF, por exemplo, um VSPackage, para consumir a funcionalidade do editor. As instruções também mostram como usar adaptadores para obter os serviços do editor em código gerenciado e não gerenciado.  
  
## <a name="editor-adapters"></a>Adaptadores do editor  
 Os adaptadores do editor, ou shims, são wrappers para objetos do editor que também expõem as classes e interfaces na <xref:Microsoft.VisualStudio.TextManager.Interop> API. Você pode usar os adaptadores para se mover entre os serviços que não são do editor, por exemplo, comandos do shell do Visual Studio e serviços do editor. (É assim que o editor está atualmente hospedado no Visual Studio.) Os adaptadores também permitem que o editor herdado e as extensões de serviço de linguagem funcionem corretamente no Visual Studio.  
  
## <a name="using-editor-adapters"></a>Usando adaptadores do editor  
 O <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> fornece métodos que alternam entre as novas interfaces do editor e as interfaces herdadas, além de métodos que criam adaptadores.  
  
 Se você estiver usando esse serviço em uma parte de componente do MEF, poderá importar o serviço da seguinte maneira.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 Se você quiser usar esse serviço em um componente não MEF, siga as instruções na seção "usando os serviços do editor do Visual Studio em um componente não MEF" mais adiante neste tópico.  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>Alternando entre a nova API do editor e a API herdada  
 Use os métodos a seguir para alternar entre um objeto do editor e uma interface herdada.  
  
|Método|Conversão|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|Converte um <xref:Microsoft.VisualStudio.Text.ITextBuffer> em um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|Converte um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> em um <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|Converte um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> em um <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|Converte um <xref:Microsoft.VisualStudio.Text.Editor.ITextView> em um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|Converte um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> em um <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
  
## <a name="creating-adapters"></a>Criando adaptadores  
 Use os métodos a seguir para criar adaptadores para interfaces herdadas.  
  
|Método|Conversão|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|Cria um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Cria um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> para um especificado <xref:Microsoft.VisualStudio.Utilities.IContentType> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|Cria um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|Cria um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Cria um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para um <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|Cria um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>Criando adaptadores em código não gerenciado  
 Todas as classes de adaptador são registradas para serem cocreatables locais e podem ser instanciadas usando a `VsLocalCreateInstance()` função.  
  
 Todos os adaptadores são criados usando os GUIDs que são definidos no arquivo vsshlids. h no.. Pasta \VisualStudioIntegration\Common\Inc\ da instalação do SDK do Visual Studio. Para criar uma instância de VsTextBufferAdapter, use o código a seguir.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>Criando adaptadores em código gerenciado  
 No código gerenciado, você pode Cocriar os adaptadores da mesma maneira que o descrito para código não gerenciado. Você também pode usar um serviço MEF que permite criar e interagir com adaptadores. Essa maneira de obter um adaptador permite um controle mais refinado do que quando você o cria.  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>Para criar um adaptador para IVsTextView  
  
1. Adicione uma referência a Microsoft.VisualStudio.Editor.dll. Verifique se `CopyLocal` está definido como `false`.  
  
2. Crie uma instância do, da seguinte <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> maneira.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3. Chame o método `CreateX()` .  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>Usando o editor do Visual Studio diretamente de código não gerenciado  
 O namespace Microsoft. VisualStudio. Platform. VSEditor e o namespace Microsoft. VisualStudio. Platform. VSEditor. Interop expõem interfaces que podem ser chamadas COM, como interfaces IVx *. Por exemplo, a interface Microsoft. VisualStudio. Platform. VSEditor. Interop. IVxTextBuffer é a versão COM da <xref:Microsoft.VisualStudio.Text.ITextBuffer> interface. No `IVxTextBuffer` , você pode obter acesso aos instantâneos de buffer, modificar o buffer, escutar eventos de alteração de texto no buffer e criar pontos de controle e intervalos. As etapas a seguir mostram como acessar um `IVxTextBuffer` de um `IVsTextBuffer` .  
  
#### <a name="to-get-an-ivxtextbuffer"></a>Para obter um IVxTextBuffer  
  
1. As definições para as interfaces IVx * estão no arquivo VSEditor. h no.. Pasta \VisualStudioIntegration\Common\Inc\ da instalação do SDK do Visual Studio.  
  
2. O código a seguir instancia um buffer de texto usando o `IVsUserData->GetData()` método. No código a seguir, `pData` é um ponteiro para um `IVsUserData` objeto.  
  
    ```  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>Usando os serviços do editor do Visual Studio em um componente não MEF  
 Se você tiver um componente de código gerenciado existente que não use o MEF e quiser usar os serviços do editor do Visual Studio, você deverá adicionar uma referência ao assembly que contém o ComponentModelHost VSPackage e obter seu serviço SComponentModel.  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>Para consumir componentes do editor do Visual Studio de um componente não MEF  
  
1. Adicione uma referência ao assembly Microsoft.VisualStudio.ComponentModelHost.dll no.. Pasta \Common7\IDE\ da instalação do Visual Studio. Verifique se `CopyLocal` está definido como `false`.  
  
2. Adicione um `IComponentModel` membro privado à classe na qual você deseja usar os serviços do editor do Visual Studio, da seguinte maneira.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3. Crie uma instância do modelo de componente no método de inicialização para seu componente.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4. Depois disso, você pode obter qualquer um dos serviços do editor do Visual Studio chamando o `IComponentModel.GetService<T>()` método para o serviço desejado.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```
