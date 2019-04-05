---
title: 'Como: Registrar uma biblioteca com o Gerenciador de objetos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6be7c1fc8f615ccbf29b8c085fecf6f4d6689404
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58928276"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Como: Registrar uma biblioteca com o Gerenciador de Objetos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Navegação de símbolos de ferramentas, tais como **Class View**, **Pesquisador de objetos**, **Pesquisador de chamadas** e **Find Symbol Results**, que você possa exibir símbolos em seu projeto ou em componentes externos. Os símbolos incluir namespaces, classes, interfaces, métodos e outros elementos de linguagem. As bibliotecas de acompanhar esses símbolos e expô-los para o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Gerenciador de objeto que preenche as ferramentas com os dados.  
  
 O Gerenciador de objetos controla de todas as bibliotecas disponíveis. Cada biblioteca deve registrar com o Gerenciador de objetos antes de fornecer os símbolos para as ferramentas de navegação de símbolo.  
  
 Normalmente, você registra uma biblioteca quando é carregado um VSPackage. No entanto, ele pode ser feito em outro momento, conforme necessário. Você cancelar o registro a biblioteca quando o VSPackage é desligado.  
  
 Para registrar uma biblioteca, use o <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> método. No caso de biblioteca de código gerenciado, use o <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> método.  
  
 Para cancelar o registro de uma biblioteca, use o <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> método.  
  
 Para obter uma referência para o Gerenciador de objetos <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, passe o <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> ID ao serviço `GetService` método.  
  
## <a name="registering-and-unregistering-a-library-with-the-object-manager"></a>Registrar e cancelar o registro de uma biblioteca com o Gerenciador de objetos  
  
#### <a name="to-register-a-library-with-the-object-manager"></a>Para registrar uma biblioteca com o Gerenciador de objetos  
  
1.  Crie uma biblioteca.  
  
    ```vb  
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing  
    Private m_nLibraryCookie As UInteger = 0  
    ' Create Library.  
    m_CallBrowserLibrary = New CallBrowser.Library()  
    ```  
  
    ```csharp  
    private CallBrowser.Library m_CallBrowserLibrary = null;  
    private uint m_nLibraryCookie = 0;  
    // Create Library.  
    m_CallBrowserLibrary = new CallBrowser.Library();  
  
    ```  
  
2.  Obtenha uma referência a um objeto do <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> de tipo e chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> método.  
  
    ```vb  
    Private Sub RegisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            Throw New Exception("Library already registered with Object Manager")  
        End If  
  
        ' Obtain a reference to IVsObjectManager2 type object.  
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
        If objManager Is Nothing Then  
            Throw New NullReferenceException("GetService failed for SVsObjectManager")  
        End If  
  
        Try  
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)  
        Catch e As Exception  
            ' Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message)  
            Throw  
        End Try  
    End Sub  
    ```  
  
    ```csharp  
    private void RegisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
            throw new Exception("Library already registered with Object Manager");  
  
        // Obtain a reference to IVsObjectManager2 type object.  
        IVsObjectManager2 objManager =   
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
        if (objManager == null)  
            throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
        try  
        {  
            int hr =   
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,   
                                                 out m_nLibraryCookie);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
        }  
        catch (Exception e)  
        {  
            // Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message);  
            throw;  
        }  
    }  
  
    ```  
  
#### <a name="to-unregister-a-library-with-the-object-manager"></a>Para cancelar o registro de uma biblioteca com o Gerenciador de objetos  
  
1.  Obtenha uma referência a um objeto do <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> de tipo e chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> método.  
  
    ```vb  
    Private Sub UnregisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            ' Obtain a reference to IVsObjectManager2 type object.  
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
            If objManager Is Nothing Then  
                Throw New NullReferenceException("GetService failed for SVsObjectManager")  
            End If  
  
            Try  
                objManager.UnregisterLibrary(m_nLibraryCookie)  
            Catch e As Exception  
                ' Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message)  
                Throw  
            Finally  
                m_nLibraryCookie = 0  
            End Try  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UnregisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
        {  
            // Obtain a reference to IVsObjectManager2 type object.  
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
            if (objManager == null)  
                throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
            try  
            {  
                objManager.UnregisterLibrary(m_nLibraryCookie);  
            }  
            catch (Exception e)  
            {  
                // Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message);  
                throw;  
            }  
            finally  
            {  
                m_nLibraryCookie = 0;  
            }  
        }  
    }  
  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Extensibilidade do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-extensibility.md)   
 [Suporte a ferramentas de navegação de símbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Como: Expor listas de símbolos fornecidos pela biblioteca para o Gerenciador de objetos](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
