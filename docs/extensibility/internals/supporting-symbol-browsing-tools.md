---
title: Suporte a ferramentas de navegação de símbolo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 87612ebc9bbcaf14bdf25d91a4e5dbe018c22143
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428767"
---
# <a name="supporting-symbol-browsing-tools"></a>Suporte a ferramentas de navegação de símbolo
**Pesquisador de objetos**, **Class View**, **Pesquisador de chamadas** e **Find Symbol Results** ferramentas fornecem recursos no Visual Studio de navegação de símbolo. Essas ferramentas exibem modos de exibição de árvore hierárquica de símbolos e mostram as relações entre os símbolos na árvore. Os símbolos podem representar namespaces, objetos, classes, membros de classe e outros elementos de linguagem contidos em vários componentes. Os componentes incluem projetos do Visual Studio, externos [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] componentes e bibliotecas de tipos (. tlb). Para obter mais informações, consulte [Exibindo a estrutura do código](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Bibliotecas de navegação de símbolo
 Como um implementador de linguagem, você pode estender os recursos de navegação de símbolo do Visual Studio com a criação de bibliotecas que acompanhe os símbolos em seus componentes e fornecem as listas de símbolos para o Gerenciador de objetos do Visual Studio por meio de um conjunto de interfaces. Uma biblioteca é descrita pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> interface. O Gerenciador de objetos do Visual Studio responde a solicitações de novos dados das ferramentas de navegação de símbolo, obtendo os dados de bibliotecas e organizando-os. Posteriormente, ele preenche ou atualiza as ferramentas com os dados solicitados. Para obter uma referência para o Gerenciador de objetos do Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, passe o <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> ID ao serviço o `GetService` método.

 Cada biblioteca deve registrar com o Gerenciador de objetos do Visual Studio, que coleta as informações em todas as bibliotecas. Para registrar uma biblioteca, chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> método. Dependendo de qual ferramenta inicia a solicitação, o Gerenciador de objetos do Visual Studio localiza a biblioteca apropriada e solicita dados. Os dados são transmitidos entre as bibliotecas e o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gerenciador de objetos em listas de símbolos descritos pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interface.

 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gerenciador de objetos é responsável por atualizar periodicamente ferramentas de navegação de símbolo para refletir os dados mais atuais contidos nas bibliotecas.

 O diagrama a seguir contém uma amostra dos principais elementos do processo de troca de solicitações/dados entre uma biblioteca e o Gerenciador de objetos do Visual Studio. As interfaces no diagrama são parte de um aplicativo de código gerenciado.

 ![Fluxo de dados entre uma biblioteca e o Gerenciador de objetos](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Para fornecer as listas de símbolos para o Gerenciador de objetos do Visual Studio, você deve primeiro registrar a biblioteca com o Gerenciador de objetos do Visual Studio, chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> método. Depois que a biblioteca for registrada, o Gerenciador de objetos do Visual Studio solicita determinadas informações sobre os recursos da biblioteca. Por exemplo, ele solicita os sinalizadores de biblioteca e suporte para categorias, chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> métodos. Em algum momento, quando uma das ferramentas solicita dados desta biblioteca, o Gerenciador de objetos solicita a lista de nível superior de símbolos chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> método. Em resposta, a biblioteca fabrica uma lista de símbolos e o expõe para o Gerenciador de objetos do Visual Studio por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interface. O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gerenciador de objeto determina quantos itens estão na lista, chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> método. Todas as solicitações seguintes se relacionam a um determinado item na lista e fornecem o número de índice do item em cada solicitação. O Gerenciador de objetos do Visual Studio continua a coletar as informações sobre o tipo, a acessibilidade e outras propriedades do item chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> método.

 Ele determina o nome do item chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> método e solicita as informações de ícone chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> método. O ícone é exibido à esquerda do nome do item e descreve o tipo de item, a acessibilidade e outras propriedades.

 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chamadas de Gerenciador de objeto o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> método para determinar se um determinado item de lista é expansível e tem itens filhos. Se a interface do usuário envia uma solicitação para expandir um elemento, o Gerenciador de objetos solicita a lista de filhos de símbolos chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> método. O processo continua com diferentes partes da árvore que está sendo criada sob demanda.

> [!NOTE]
> Para implementar um provedor de símbolos de código nativo, use o <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> interfaces.

## <a name="see-also"></a>Consulte também
- [Como: registrar uma biblioteca com o Gerenciador de Objetos](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Como: expor listas de símbolos fornecidos pela biblioteca ao Gerenciador de Objetos](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Como: identificar símbolos em uma biblioteca](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)