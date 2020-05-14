---
title: 'Como: Identificar símbolos em uma biblioteca | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fe920fabd05a875b336467fbba16e4229fa9613
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708012"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Como: Identificar símbolos em uma biblioteca
Ferramentas de navegação por símbolos exibem visões hierárquicas de símbolos. Os símbolos representam namespaces, objetos, classes, membros de classe e outros elementos linguísticos.

 Cada símbolo na hierarquia pode ser identificado pelas informações de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] navegação passadas pela biblioteca de símbolos ao gerenciador de objetos através das seguintes interfaces:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 A localização do símbolo na hierarquia distingue um símbolo. Ele permite que ferramentas de navegação de símbolos naveguem até um símbolo específico. O caminho único e totalmente qualificado para o símbolo determina a localização. Cada elemento no caminho é um nó. O caminho começa com o nó de nível superior e termina com o símbolo específico. Por exemplo, se o método M1 é um membro da classe C1 e C1 está no namespace N1, o caminho completo do método M1 é N1. C1. M1. Este caminho contém três nós: N1, C1 e M1.

 As informações de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] navegação permitem que o gerenciador de objetos localize, selecione e mantenha os símbolos selecionados na hierarquia. Permite navegar de uma ferramenta de navegação para outra. Ao usar **o Object Browser** [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] para navegar símbolos em um projeto, você pode clicar com o botão direito do mouse em um método e iniciar a ferramenta **Navegador de chamadas** para exibir o método em um gráfico de chamadas.

 Duas formas descrevem a localização do símbolo. A forma canônica é baseada no caminho totalmente qualificado do símbolo. Representa uma posição única do símbolo na hierarquia. É independente da ferramenta de navegação de símbolos. Para obter as informações do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] formulário canônico, o gerenciador de objetos chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> o método. O formulário de apresentação descreve a localização do símbolo dentro de uma ferramenta específica de navegação de símbolos. A posição do símbolo é relativa à posição de outros símbolos na hierarquia. Um determinado símbolo pode ter vários caminhos de apresentação, mas apenas um caminho canônico. Por exemplo, se a classe C1 for herdada da classe C2 e ambas as classes estiverem no namespace N1, o **Navegador de Objeto** exibe a seguinte árvore hierárquica:

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 O caminho canônico da classe C2, neste exemplo, é N1 + C2. O caminho de apresentação do C2 inclui os nodos C1 e "Bases e Interfaces": N1 + C1 + "Bases e Interfaces" + C2.

 Para obter as informações do formulário <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> de apresentação, o gerenciador de objetos chama o método.

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>Obter informações de formulários canônicos e de apresentação

1. Implementar o método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> .

     O gerenciador de objetos chama este método para obter a lista de nódulos contidos no caminho canônico do símbolo.

    ```vb
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)
        Return 0
    End Function
    ```

    ```csharp
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)
    {
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =
            new CallBrowserEnumNavInfoNodes(m_strMethod);
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);
        return 0;
    }

    ```

2. Implementar o método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> .

     O gerenciador de objetos chama este método para obter a lista de nós contidos no caminho de apresentação do símbolo.

## <a name="see-also"></a>Confira também
- [Suporte a ferramentas de navegação por símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Como: Registrar uma biblioteca com o gerenciador de objetos](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Como: Expor listas de símbolos fornecidos pela biblioteca ao gerenciador de objetos](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
