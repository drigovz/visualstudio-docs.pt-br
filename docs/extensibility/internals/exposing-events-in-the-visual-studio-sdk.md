---
title: Expondo Eventos no Estúdio Visual SDK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48f1e0ea0dcd07bbc26fc89d5c61a6a5941d4727
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708481"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Expor eventos no Visual Studio SDK
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]permite que você origem eventos usando automação. Recomendamos que você origem em eventos para projetos e itens de projeto.

 Os eventos são recuperados por <xref:EnvDTE.DTEClass.Events%2A> consumidores <xref:EnvDTE.DTEClass.GetObject%2A> de automação `GetObject("EventObjectName")`do objeto ou (por exemplo, ). O ambiente `IDispatch::Invoke` chama `DISPATCH_METHOD` usando `DISPATCH_PROPERTYGET` o ou bandeiras para retornar um evento.

 O processo a seguir explica como os eventos específicos do VSPackage são retornados.

1. O ambiente começa.

2. Ele lê do registro todos os nomes de valor sob as chaves **Automação,** **AutomaçãoEventos**e **AutomaçãoPropriedades** de todos os VSPackages, e armazena esses nomes em uma tabela.

3. Um consumidor de automação chama, neste exemplo, `DTE.Events.AutomationProjectsEvents` ou `DTE.Events.AutomationProjectItemsEvents`.

4. O ambiente encontra o parâmetro de string na tabela e carrega o VSPackage correspondente.

5. O ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> chama o método usando o nome aprovado na chamada; neste exemplo, `AutomationProjectsEvents` `AutomationProjectItemsEvents`ou .

6. O VSPackage cria um objeto raiz `get_AutomationProjectsEvents` que `get_AutomationProjectItemEvents` tem métodos como e, em seguida, retorna um ponteiro IDispatch para o objeto.

7. O ambiente chama o método apropriado com base no nome passado para a chamada de automação.

8. O `get_` método cria outro objeto de evento baseado `IConnectionPointContainer` em `IConnectionPoint` IDispatch que `IDispatchpointer` implementa a interface e a interface e retorna um para o objeto.

   Para expor um evento usando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> automação, você deve responder e observar as strings que você adiciona ao registro. Na amostra do Projeto Básico, as strings são *BscProjectsEvents* e *BscProjectItemsEvents*.

## <a name="registry-entries-from-the-basic-project-sample"></a>Inscrições de registro da amostra do Projeto Básico
 Esta seção mostra onde adicionar valores de eventos de automação ao registro.

 **[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Pacotes\\<PkgGUID\>\AutomationEvents]**

 **AutomationProjectEvents** = `AutomationProjectEvents` Retorna o objeto.

 **AutomationProjectItemEvents** = `AutomationProjectItemsEvents` Retorna o objeto.

|Nome|Type|Intervalo|Descrição|
|----------|----------|-----------|-----------------|
|Padrão (@)|REG_SZ|Não usado|Não utilizado. Você pode usar o campo de dados para documentação.|
|*AutomaçãoProjetosEventos*|REG_SZ|Nome do objeto do evento.|Apenas o nome chave é relevante. Você pode usar o campo de dados para documentação.<br /><br /> Este exemplo vem da amostra do Projeto Básico.|
|*AutomaçãoProjectItemEvents*|REG_SZ|Nome do objeto do evento|Apenas o nome chave é relevante. Você pode usar o campo de dados para documentação.<br /><br /> Este exemplo vem da amostra do Projeto Básico.|

 Quando qualquer um de seus objetos de evento for solicitado por um consumidor de automação, crie um objeto raiz que tenha métodos para qualquer evento que seu VSPackage suporte. O ambiente chama `get_` o método apropriado neste objeto. Por exemplo, `DTE.Events.AutomationProjectsEvents` se for `get_AutomationProjectsEvents` chamado, o método no objeto raiz é invocado.

 ![Eventos do projeto Visual Studio](../../extensibility/internals/media/projectevents.gif "Eventos de Projetos") Modelo de automação para eventos

 A `CProjectEventsContainer` classe representa o objeto de origem de `CProjectItemsEventsContainer` *BscProjectsEvents*e representa o objeto de origem de *BscProjectItemsEvents*.

 Na maioria dos casos, você deve retornar um novo objeto para cada solicitação de evento, porque a maioria dos objetos de evento leva um objeto de filtro. Ao disparar seu evento, verifique este filtro para verificar se o manipulador de eventos está sendo chamado.

 *AutomationEvents.h* e *AutomationEvents.cpp* contêm declarações e implementações das classes na tabela a seguir.

|Classe|Descrição|
|-----------|-----------------|
|`CAutomationEvents`|Implementa um objeto raiz de `DTE.Events` evento, recuperado do objeto.|
|`CProjectsEventsContainer` e `CProjectItemsEventsContainer`|Implemente os objetos de origem do evento que disparam os eventos correspondentes.|

 O exemplo de código a seguir mostra como responder a uma solicitação de um objeto de evento.

```cpp
STDMETHODIMP CVsPackage::GetAutomationObject(
    /* [in]  */ LPCOLESTR       pszPropName,
    /* [out] */ IDispatch **    ppIDispatch)
{
    ExpectedPtrRet(ppIDispatch);
    *ppIDispatch = NULL;

    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)
        //Is the requested name our Projects object?
    {
        return GetAutomationProjects(ppIDispatch);
        // Gets our Projects object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)
        //Is the requested name our ProjectsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectEvents object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectItemsEvents object.
    }
    return E_INVALIDARG;
}
```

 No `g_wszAutomationProjects` código acima, está o nome da sua coleção de projetos (*FigProjectsEvents*) `g_wszAutomationProjectsEvents` e*FigProjectsEvents* `g_wszAutomationProjectItemsEvents` *(FigProjectItemEvents)* são os nomes dos eventos de projetos e itens de projeto que são originados da sua implementação do VSPackage.

 Os objetos de evento são recuperados `DTE.Events` do mesmo local central, o objeto. Dessa forma, todos os objetos de evento são agrupados para que um usuário final não precise navegar por todo o modelo de objeto para encontrar um evento específico. Isso também permite que você forneça seus objetos VSPackage específicos, em vez de exigir que você implemente seu próprio código para eventos em todo o sistema. No entanto, para o usuário final, `ProjectItem` que deve encontrar um evento para sua interface, não está imediatamente claro de onde esse objeto de evento é recuperado.

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
