---
title: 'Como: registrar tipos de arquivo do editor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d22e61d88b5f6e3959a369f6957efbc824384b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204114"
---
# <a name="how-to-register-editor-file-types"></a>Como registrar tipos de arquivo do editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A maneira mais fácil de registrar tipos de arquivo do editor é usando os atributos de registro fornecidos como parte das [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] classes do MPF (estrutura de pacote gerenciada). Se você estiver implementando seu pacote em nativo [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , também poderá escrever um script de registro que registra seu editor e as extensões associadas.  
  
## <a name="registration-using-mpf-classes"></a>Registro usando classes do MPF  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>Para registrar tipos de arquivo do editor usando classes do MPF  
  
1. Forneça a <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> classe com os parâmetros apropriados para o seu editor na classe de seu VSPackage.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Em que ". Sample "é a extensão que é registrada para este editor e" 32 "é seu nível de prioridade.  
  
     O `projectGuid` é o GUID para diversos tipos de arquivo, definido em <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid> . O tipo de arquivo variado é fornecido, de modo que o arquivo resultante não fará parte do processo de compilação.  
  
     `TemplateDir` representa a pasta que contém os arquivos de modelo incluídos com a amostra do editor básico gerenciado.  
  
     `NameResourceID` é definido no arquivo Resources. h do projeto BasicEditorUI e identifica o editor como "meu editor".  
  
2. Substitua o método <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Na implementação do <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método, chame o <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> método e passe a instância da fábrica do editor, conforme demonstrado abaixo.  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     Essa etapa registra a fábrica do editor e as extensões de arquivo do editor.  
  
3. Cancele o registro das fábricas do editor.  
  
     As fábricas de editor são desregistradas automaticamente quando o VSPackage é Descartado. Se o objeto de fábrica do editor implementar a <xref:System.IDisposable> interface, seu `Dispose` método será chamado após o cancelamento do registro da fábrica com o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="registration-using-a-registry-script"></a>Registro usando um script de registro  
 Registrar fábricas de editor e tipos de arquivo em nativo [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] é feito usando um script de registro para gravar no registro do Windows, conforme ilustrado a seguir.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>Para registrar tipos de arquivo do editor usando um script de registro  
  
1. No script do registro, defina a fábrica do editor e a cadeia de caracteres do GUID de fábrica do editor, conforme mostrado na `GUID_BscEditorFactory` seção do script de registro a seguir. Além disso, defina a extensão e a prioridade da extensão do editor:  
  
    ```  
  
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions            {                val rtf = d 50            }  
        }  
    }  
    ```  
  
     A extensão de arquivo do editor neste exemplo é identificada como ". rtf" e sua prioridade é "50". As cadeias de caracteres GUID são definidas no arquivo Resource. h do projeto de exemplo BscEdit.  
  
2. Registre o VSPackage.  
  
3. Registre a fábrica do editor.  
  
     A fábrica do editor está registrada na <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> implementação.  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     As cadeias de caracteres GUID são definidas no arquivo Resource. h do projeto BscEdit.
