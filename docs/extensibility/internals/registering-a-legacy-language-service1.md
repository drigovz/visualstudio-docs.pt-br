---
title: Registrando um serviço de idioma legado1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], registering
ms.assetid: d33b08af-09e0-4c79-87b2-5536b27fbacf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91776382fff1818986049558c9d86e8fce4d0dd7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705899"
---
# <a name="registering-a-legacy-language-service"></a>Registrar um serviço de linguagem herdado
No mpf (framework de pacote gerenciado), o serviço de idiomaé oferecido por um VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (ver [VSPackages](../../extensibility/internals/vspackages.md)) e é registrado adicionando chaves de registro e entradas. Este processo de registro é feito em parte durante a instalação e em parte em tempo de execução.

## <a name="register-the-language-service-by-using-attributes"></a>Registre o serviço de idioma usando atributos
 Os seguintes atributos são usados para registrar um serviço de idioma.

- <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageExtensionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute>

- <xref:Microsoft.VisualStudio.Shell.ProvideLanguageEditorOptionPageAttribute>

  Esses atributos são explicados abaixo

### <a name="provideserviceattribute"></a>ProvideServiceAttribute
 Este atributo registra seu serviço de idioma como um serviço.

### <a name="example"></a>Exemplo

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideServiceAttribute(typeof(TestLanguageService),
                             ServiceName = "Test Language Service")]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageserviceattribute"></a>ProvideLanguageServiceAttribute
 Este atributo registra seu serviço de idioma especificamente como um serviço de idiomas. Ele permite definir opções que especificam os recursos que seu serviço de idioma oferece. O exemplo mostra um subconjunto das opções que um serviço de idioma pode fornecer. Para obter o conjunto completo <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>de opções de serviço de idioma, consulte .

### <a name="example"></a>Exemplo

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageServiceAttribute(typeof(TestLanguageService),
                             "Test Language",
                             106,             // resource ID of localized language name
                             CodeSense = true,             // Supports IntelliSense
                             RequestStockColors = false,   // Supplies custom colors
                             EnableCommenting = true,      // Supports commenting out code
                             EnableAsyncCompletion = true  // Supports background parsing
                             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageextensionattribute"></a>ProvideLanguageExtensionAttribute
 Este atributo associa seu serviço de idioma a uma extensão de arquivo. Sempre que um arquivo com essa extensão é carregado, em qualquer projeto, seu serviço de idioma é iniciado e usado para exibir o conteúdo do arquivo.

### <a name="example"></a>Exemplo

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageExtensionAttribute(typeof(TestLanguageService),
                                       ".Testext")]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguagecodeexpansionattribute"></a>FornecerLanguageCodeExpansionAttribute
 Este atributo registra um local a partir do qual os modelos de expansão de código ou trechos são obtidos. Essas informações são usadas pelo **Navegador Code Snippets** e pelo editor quando um trecho de código é inserido no arquivo de origem.

### <a name="example"></a>Exemplo

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageCodeExpansionAttribute(
             typeof(TestLanguageService),
             "Test Language", // Name of language used as registry key.
             106,           // Resource ID of localized name of language service.
             "testlanguage",  // language key used in snippet templates.
             @"%InstallRoot%\Test Language\SnippetsIndex.xml",  // Path to snippets index
             SearchPaths = @"%InstallRoot%\Test Language\Snippets\%LCID%\Snippets\;" +
                           @"%TestDocs%\Code Snippets\Test Language\Test Code Snippets"
             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

### <a name="providelanguageeditoroptionpageattribute"></a>FornecerLanguageEditorPáginadepáginadedo
 Este atributo registra uma página de propriedade a ser exibida na caixa de diálogo **Opções** na categoria **Editor de texto.** Use um desses atributos para cada página a ser exibida para o seu serviço de idioma. Se você precisar organizar suas páginas em uma estrutura de árvore, use atributos adicionais para definir cada nó da árvore.

### <a name="example"></a>Exemplo
 Este exemplo mostra duas páginas de propriedade, **Opções** e **Recuse,** e um nó que contém a segunda página de propriedade.

```csharp
using Microsoft.VisualStudio.Shell;

namespace TestLanguagePackage
{
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             "Options",      // Registry key name for property page
             "#242",         // Localized name of property page
             OptionPageGuid = "{A2FE74E1-FFFF-3311-4342-123052450768}"  // GUID of property page
             )]
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             "Advanced",     // Registry key name for node
             "#243",         // Localized name of node
             )]
    [ProvideLanguageEditorOptionPageAttribute(
             "Test Language",  // Registry key name for language
             @"Advanced\Indenting",     // Registry key name for property page
             "#244",         // Localized name of property page
             OptionPageGuid = "{A2FE74E2-FFFF-3311-4342-123052450768}"  // GUID of property page
             )]

    public class TestLanguagePackage : Package
    {
    }
}
```

## <a name="proffer-the-language-service-at-run-time"></a>Ofereça o Serviço de Idiomas em tempo de execução
 Quando o pacote de idiomas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] estiver carregado, você deve dizer que seu serviço de idioma está pronto. Você faz isso oferecendo o serviço. Isso é feito <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> no método. Além disso, você precisa iniciar um temporizador que ligue seu serviço de idioma durante períodos ociosos para que o análise de fundo possa ser realizado. Este temporizador ocioso também é usado <xref:Microsoft.VisualStudio.Package.DocumentProperties> para atualizar propriedades de documentos se você tiver implementado alguma através da classe. Para suportar um temporizador, seu <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent> pacote deve <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponent.FDoIdle%2A> implementar a interface (apenas o método precisa ser totalmente implementado; os demais métodos podem retornar valores padrão).

### <a name="example"></a>Exemplo
 Este exemplo mostra uma abordagem típica para oferecer um serviço e fornecer um temporizador ocioso.

```csharp

using System;
using System.Runtime.InteropServices;
using System.ComponentModel.Design;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.OLE.Interop;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    [Microsoft.VisualStudio.Shell.ProvideService(typeof(TestLanguageService))]
    [Microsoft.VisualStudio.Shell.ProvideLanguageExtension(typeof(TestLanguageService), ".testext")]
    [Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(TestLanguageService), "Test Language", 0,
        AutoOutlining = true,
        EnableCommenting = true,
        MatchBraces = true,
        ShowMatchingBrace = true)]
    [Guid("00000000-0000-0000-0000-00000000000")] //provide a unique GUID for the package

    public class TestLanguagePackage : Package, IOleComponent
    {
        private uint m_componentID;

        protected override void Initialize()
        {
            base.Initialize();  // required

            // Proffer the service.
            IServiceContainer serviceContainer = this as IServiceContainer;
            TestLanguageService langService      = new TestLanguageService();
            langService.SetSite(this);
            serviceContainer.AddService(typeof(TestLanguageService),
                                        langService,
                                        true);

            // Register a timer to call our language service during
            // idle periods.
            IOleComponentManager mgr = GetService(typeof(SOleComponentManager))
                                       as IOleComponentManager;
            if (m_componentID == 0 && mgr != null)
            {
                OLECRINFO[] crinfo = new OLECRINFO[1];
                crinfo[0].cbSize            = (uint)Marshal.SizeOf(typeof(OLECRINFO));
                crinfo[0].grfcrf            = (uint)_OLECRF.olecrfNeedIdleTime |
                                              (uint)_OLECRF.olecrfNeedPeriodicIdleTime;
                crinfo[0].grfcadvf          = (uint)_OLECADVF.olecadvfModal |
                                              (uint)_OLECADVF.olecadvfRedrawOff |
                                              (uint)_OLECADVF.olecadvfWarningsOff;
                crinfo[0].uIdleTimeInterval = 1000;
                int hr = mgr.FRegisterComponent(this, crinfo, out m_componentID);
            }
        }

        protected override void Dispose(bool disposing)
        {
            if (m_componentID != 0)
            {
                IOleComponentManager mgr = GetService(typeof(SOleComponentManager))
                                           as IOleComponentManager;
                if (mgr != null)
                {
                    int hr = mgr.FRevokeComponent(m_componentID);
                }
                m_componentID = 0;
            }

            base.Dispose(disposing);
        }

        #region IOleComponent Members

        public int FDoIdle(uint grfidlef)
        {
            bool bPeriodic = (grfidlef & (uint)_OLEIDLEF.oleidlefPeriodic) != 0;
            // Use typeof(TestLanguageService) because we need to
            // reference the GUID for our language service.
            LanguageService service = GetService(typeof(TestLanguageService))
                                      as LanguageService;
            if (service != null)
            {
                service.OnIdle(bPeriodic);
            }
            return 0;
        }

        public int FContinueMessageLoop(uint uReason,
                                        IntPtr pvLoopData,
                                        MSG[] pMsgPeeked)
        {
            return 1;
        }

        public int FPreTranslateMessage(MSG[] pMsg)
        {
            return 0;
        }

        public int FQueryTerminate(int fPromptUser)
        {
            return 1;
        }

        public int FReserved1(uint dwReserved,
                              uint message,
                              IntPtr wParam,
                              IntPtr lParam)
        {
            return 1;
        }

        public IntPtr HwndGetWindow(uint dwWhich, uint dwReserved)
        {
            return IntPtr.Zero;
        }

        public void OnActivationChange(IOleComponent pic,
                                       int fSameComponent,
                                       OLECRINFO[] pcrinfo,
                                       int fHostIsActivating,
                                       OLECHOSTINFO[] pchostinfo,
                                       uint dwReserved)
        {
        }

        public void OnAppActivate(int fActive, uint dwOtherThreadID)
        {
        }

        public void OnEnterState(uint uStateID, int fEnter)
        {
        }

        public void OnLoseActivation()
        {
        }

        public void Terminate()
        {
        }

        #endregion
    }
}
```
