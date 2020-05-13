---
title: 'Como: Cadastrar uma Biblioteca com o Gerenciador de Objetos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4bd1032d2ba67a0c0f3338560a80038ed3215531
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707936"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Como: Registrar uma biblioteca com o gerenciador de objetos
As ferramentas de navegação por símbolos, como **Exibição de Classe,** **Navegador de Objeto,** **Navegador de Chamadas** e Resultados de Símbolos de **Encontrar,** permitem que você visualize símbolos em seu projeto ou em componentes externos. Os símbolos incluem namespaces, classes, interfaces, métodos e outros elementos linguísticos. As bibliotecas rastreiam esses símbolos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e os expõem ao gerenciador de objetos que preenche as ferramentas com os dados.

 O gerenciador de objetos mantém o controle de todas as bibliotecas disponíveis. Cada biblioteca deve registrar-se com o gerenciador de objetos antes de fornecer símbolos para as ferramentas de navegação de símbolos.

 Normalmente, você registra uma biblioteca quando um VSPackage é carregado. No entanto, pode ser feito em outro momento, conforme necessário. Você desregistra a biblioteca quando o VSPackage é desligado.

 Para registrar uma biblioteca, use o <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> método. Para uma biblioteca de código <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> gerenciada, use o método.

 Para cancelar o registro <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> de uma biblioteca, use o método.

 Para obter uma referência ao <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>gerenciador <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> de objetos, passe o ID de serviço para `GetService` o método.

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>Registre e desregistre uma biblioteca com o gerenciador de objetos

### <a name="to-register-a-library-with-the-object-manager"></a>Para registrar uma biblioteca com o gerenciador de objetos

1. Crie uma biblioteca.

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

2. Obtenha uma referência a <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> um objeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> do tipo e chame o método.

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

### <a name="to-unregister-a-library-with-the-object-manager"></a>Para desregistrar uma biblioteca com o gerenciador de objetos

1. Obtenha uma referência a <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> um objeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> do tipo e chame o método.

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

## <a name="see-also"></a>Confira também
- [Extensibilidade do serviço de linguagem legado](../../extensibility/internals/legacy-language-service-extensibility.md)
- [Suporte a ferramentas de navegação por símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Como: Expor listas de símbolos fornecidos pela biblioteca ao gerenciador de objetos](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
