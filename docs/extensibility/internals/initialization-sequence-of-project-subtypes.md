---
title: Sequência de inicialização dos subtipos do projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05a3c312f61dd2b2c63c3f38ef8bac2203b326db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707625"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Sequência de inicialização de subtipos de projeto
O ambiente constrói um projeto chamando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>implantação da fábrica de projetos básicos de . A construção de um subtipo de projeto começa quando o ambiente determina que a lista GUID do tipo de projeto para a extensão de um arquivo de projeto não está vazia. A extensão do arquivo do projeto [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] o GUIA do projeto especificam se o projeto é um ou tipo de projeto. Por exemplo, a extensão .vbproj e {F184B08F-C81C-45F6-A57F-5ABD9991F28F} identificam um [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projeto.

## <a name="environments-initialization-of-project-subtypes"></a>Inicialização do Meio Ambiente dos Subtipos do Projeto
 O procedimento a seguir detalha a seqüência de inicialização de um sistema de projeto agregado por vários subtipos de projeto.

1. O ambiente chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>projeto base de , e enquanto o projeto analisa seu arquivo de `null`projeto, ele descobre que a lista de GUIDs do tipo de projeto agregado não é . O projeto descontinua diretamente a criação de seu projeto.

2. O projeto `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> solicita o serviço para criar um subtipo <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> de projeto usando a implementação do método pelo ambiente. Dentro deste método, o ambiente faz chamadas de função <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> recursivas para suas implementações e <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> métodos enquanto ele está andando na lista de GUIDs do tipo projeto, começando com o subtipo de projeto mais externo.

     A seguir, detalha as etapas de inicialização.

    1. A implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> método pelo `HrCreateInnerProj` ambiente chama o método com a seguinte declaração de função:

         \<CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Quando esta função é chamada pela primeira vez, ou seja, para `pOuter` `pOwner` o subtipo `null` de projeto externo, os `IUnknown` parâmetros e são passados como e a função define o subtipo de projeto mais externo para `pOuter`.

    2. Em seguida, `HrCreateInnerProj` as chamadas de ambiente funcionam com o segundo tipo de projeto GUID na lista. Este GUID corresponde ao segundo subtipo de projeto interno que avança em direção ao projeto base na seqüência de agregação.

    3. O `pOuter` agora está `IUnknown` apontando para o subtipo `HrCreateInnerProj` de projeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> mais externo, e chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>sua implementação de seguido por uma chamada para sua implementação de . No <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> método que você `IUnknown` passa no controle do `pOuter`subtipo de projeto externo, . O projeto próprio (subtipo de projeto interno) precisa criar seu objeto de projeto agregado aqui. Na <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> implementação do método você `IUnknown` passa em um ponteiro para o projeto interno que está sendo agregado. Esses dois métodos criam o objeto de agregação, e suas implementações precisam seguir as regras de agregação do COM para garantir que um subtipo de projeto não acabe segurando uma contagem de referência para si mesmo.

    4. `HrCreateInnerProj`chama sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>implementação de . Nesse método, o subtipo do projeto faz seu trabalho de inicialização. Você pode, por exemplo, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>registrar eventos de solução em .

    5. `HrCreateInnerProj`é chamado de recursivamente até que o último GUID (o projeto base) da lista seja alcançado. Para cada uma dessas chamadas, os passos, c a d, são repetidos. `pOuter`aponta para o subtipo `IUnknown` de projeto mais externo para cada nível de agregação.

## <a name="example"></a>Exemplo

O exemplo a seguir detalha o processo programático <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> em uma representação aproximada do método como ele é implementado pelo ambiente. O código é apenas um exemplo; não se destina a ser compilado, e toda verificação de erro foi removida para maior clareza.

```cpp
HRESULT CreateAggregateProject
(
    LPCOLESTR lpstrGuids,
    LPCOLESTR pszFilename,
    LPCOLESTR pszLocation,
    LPCOLESTR pszName,
    VSCREATEPROJFLAGS grfCreateFlags,
    REFIID iidProject,
    void **ppvProject)
{
    HRESULT hr = NOERROR;
    CComPtr<IUnknown> srpunkProj;
    CComPtr<IVsAggregatableProject> srpAggProject;
    CComBSTR bstrGuids = lpstrGuids;
    BOOL fCanceled = FALSE;
    *ppvProject = NULL;

    HrCreateInnerProj(
         bstrGuids, NULL, NULL, pszFilename, pszLocation,
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);
    srpunkProj->QueryInterface(
        IID_IVsAggregatableProject, (void **)&srpAggProject));
    srpAggProject->OnAggregationComplete();
    srpunkProj->QueryInterface(iidProject, ppvProject);
}

HRESULT HrCreateInnerProj
(
    WCHAR *pwszGuids,
    IUnknown *pOuter,
    IVsAggregatableProject *pOwner,
    LPCOLESTR pszFilename,
    LPCOLESTR pszLocation,
    LPCOLESTR pszName,
    VSCREATEPROJFLAGS grfCreateFlags,
    IUnknown **ppInner,
    BOOL *pfCanceled
)
{
    HRESULT hr = NOERROR;
    CComPtr<IUnknown> srpInner;
    CComPtr<IVsAggregatableProject> srpAggInner;
    CComPtr<IVsProjectFactory> srpProjectFactory;
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;
    GUID guid = GUID_NULL;
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');
    WCHAR wszText[_MAX_PATH+150] = L"";

    if (pwszNextGuids)
    {
        *pwszNextGuids++ = 0;
    }

    CLSIDFromString(pwszGuids, &guid);
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(
        guid, &srpProjectFactory);
    srpProjectFactory->QueryInterface(
        IID_IVsAggregatableProjectFactory,
        (void **)&srpAggPF);
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);
    srpInner->QueryInterface(
        IID_IVsAggregatableProject, (void **)&srpAggInner);

    if (pOwner)
    {
        IfFailGo(pOwner->SetInnerProject(srpInner));
    }

    if (pwszNextGuids)
    {
        CComPtr<IUnknown> srpNextInner;
        HrCreateInnerProj(
            pwszNextGuids, pOuter ? pOuter : srpInner,
            srpAggInner, pszFilename, pszLocation, pszName,
            grfCreateFlags, &srpNextInner, pfCanceled);
    }

    return srpAggInner->InitializeForOuter(
        pszFilename, pszLocation, pszName, grfCreateFlags,
        IID_IUnknown, (void **)ppInner, pfCanceled);
}
```

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [Subtipos de projeto](../../extensibility/internals/project-subtypes.md)
