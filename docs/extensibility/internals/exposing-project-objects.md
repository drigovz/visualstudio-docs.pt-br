---
title: Expondo Objetos de Projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81446fa582524872b03199ae707f658776787961
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708477"
---
# <a name="expose-project-objects"></a>Expor objetos do projeto

Os tipos de projetos personalizados podem fornecer objetos de automação para permitir o acesso ao projeto usando interfaces de automação. Espera-se que cada tipo <xref:EnvDTE.Project> de projeto forneça <xref:EnvDTE.Solution>o objeto de automação padrão que é acessado a partir de , que contém uma coleção de todos os projetos que estão abertos no IDE. Espera-se que cada item do projeto <xref:EnvDTE.ProjectItem> seja exposto `Project.ProjectItems`por um objeto acessado com . Além desses objetos de automação padrão, os projetos podem optar por oferecer objetos de automação específicos do projeto.

Você pode criar objetos de automação personalizados de nível raiz que `DTE.<customObjectName>` `DTE.GetObject("<customObjectName>")`você pode acessar vinculados tardiamente a partir do objeto DTE raiz usando ou . Por exemplo, o Visual C++ cria uma coleção de projetos c++ `DTE.GetObject("VCProjects")`específica do projeto chamada *VCProjects* que você pode acessar usando `DTE.VCProjects` ou . Você também pode `Project.Object`criar um , que é `Project.CodeModel`único para o tipo de projeto, a , `ProjectItem`que pode `ProjectItem.Object` ser `ProjectItem.FileCodeModel`consultado para o seu objeto mais derivado, e um , que expõe e a .

É uma convenção comum para projetos exporem uma coleção de projetos personalizada e específica do projeto. Por exemplo, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] cria uma coleção de projetos c++ específica que você pode acessar usando `DTE.VCProjects` ou `DTE.GetObject("VCProjects")`. Você também pode `Project.Object`criar um , que é `Project.CodeModel`único para o tipo de projeto, a `ProjectItem`, que `ProjectItem.Object`pode ser `ProjectItem.FileCodeModel`consultado para o seu objeto mais derivado, a , que expõe , e a .

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Para contribuir com um objeto específico do VSPackage para um projeto

1. Adicione as teclas apropriadas ao arquivo *.pkgdef* do seu VSPackage.

     Por exemplo, aqui estão as configurações *.pkgdef* para o projeto de idioma C++:

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. Implemente o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> código no método, como no exemplo a seguir.

    ```cpp
    STDMETHODIMP CVsPackage::GetAutomationObject(
    /* [in]  */ LPCOLESTR       pszPropName,
    /* [out] */ IDispatch **    ppIDispatch)
    {
    ExpectedPtrRet(pszPropName);
    ExpectedPtrRet(ppIDispatch);
    *ppIDispatch = NULL;

        if (m_fZombie)
            return E_UNEXPECTED;

        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)
        {
            return GetAutomationProjects(ppIDispatch);
        }
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)
        {
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);
        }
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)
        {
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);
        }
        return E_INVALIDARG;
    }
    ```

     No código, `g_wszAutomationProjects` está o nome da sua coleção de projetos. O `GetAutomationProjects` método cria um objeto `Projects` que implementa a interface e retorna um `IDispatch` ponteiro para o objeto de chamada, como mostrado no exemplo de código a seguir.

    ```cpp
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)
    {
        ExpectedPtrRet(ppIDispatch);
        *ppIDispatch = NULL;

        if (!m_srpAutomationProjects)
        {
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);
            IfFailRet(hr);
            ExpectedExprRet(m_srpAutomationProjects != NULL);
        }
        return m_srpAutomationProjects.CopyTo(ppIDispatch);
    }
    ```

     Escolha um nome único para o seu objeto de automação. Os conflitos de nome são imprevisíveis, e colisões fazem com que um nome de objeto conflitante seja arbitrariamente descartado se vários tipos de projeto usarem o mesmo nome. Você deve incluir seu nome corporativo ou algum aspecto único de seu nome de produto no nome do objeto de automação.

     O `Projects` objeto de coleta personalizado é um ponto de entrada de conveniência para a parte restante do seu modelo de automação de projetos. Seu objeto de projeto <xref:EnvDTE.Solution> também está acessível a partir da coleção do projeto. Depois de criar as entradas de código e `Projects` registro apropriadas que fornecem aos consumidores objetos de coleta, sua implementação deve fornecer objetos padrão restantes para o modelo do projeto. Para obter mais informações, consulte [A modelagem do Projeto](../../extensibility/internals/project-modeling.md).

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
