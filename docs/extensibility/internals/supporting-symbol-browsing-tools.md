---
title: Suporte a ferramentas de navegação por símbolos | Microsoft Docs
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4998e47ccd6f99df2710833c18975d57e3bb92f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704774"
---
# <a name="supporting-symbol-browsing-tools"></a>Suporte a ferramentas de navegação de símbolo
**As**ferramentas Object Browser , **Class View,** **Call Browser** e Find **Symbol Results** fornecem recursos de navegação de símbolos no Visual Studio. Essas ferramentas exibem visões hierárquicas de símbolos e mostram as relações entre os símbolos na árvore. Os símbolos podem representar namespaces, objetos, classes, membros de classe e outros elementos linguísticos contidos em vários componentes. Os componentes incluem projetos do Visual Studio, componentes externos do .NET Framework e bibliotecas tipo (.tlb). Para obter mais informações, consulte [Visualizando a estrutura do código](../../ide/viewing-the-structure-of-code.md).

## <a name="symbol-browsing-libraries"></a>Bibliotecas de navegação por símbolos
 Como um implementador de idiomas, você pode estender os recursos de navegação de símbolos do Visual Studio criando bibliotecas que rastreiam os símbolos em seus componentes e fornecem as listas de símbolos para o gerenciador de objetos do Visual Studio através de um conjunto de interfaces. Uma biblioteca é <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> descrita pela interface. O gerenciador de objetos Visual Studio responde a solicitações de novos dados das ferramentas de navegação de símbolos, obtendo os dados das bibliotecas e organizando-os. Posteriormente, preenche ou atualiza as ferramentas com os dados solicitados. Para obter uma referência ao gerenciador de <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> objetos visual `GetService` studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>passe o ID de serviço para o método.

 Cada biblioteca deve se registrar com o gerenciador de objetos Visual Studio, que coleta as informações em todas as bibliotecas. Para registrar uma biblioteca, ligue para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> método. Dependendo de qual ferramenta inicia a solicitação, o gerenciador de objetos do Visual Studio encontra a biblioteca apropriada e solicita dados. Os dados viajam entre as [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] bibliotecas e o gerenciador <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> de objetos em listas de símbolos descritos pela interface.

 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerenciador de objetos é responsável por atualizar periodicamente as ferramentas de navegação de símbolos para refletir os dados mais atuais contidos nas bibliotecas.

 O diagrama abaixo contém uma amostra de elementos-chave do processo de solicitações/troca de dados entre uma biblioteca e o gerenciador de objetos do Visual Studio. As interfaces no diagrama são parte de um aplicativo de código gerenciado.

 ![Fluxo de dados entre uma biblioteca e o gerenciador de objetos](../../extensibility/internals/media/callbrowserdiagram.gif "Diagrama de navegador de chamadas")

 Para fornecer as listas de símbolos ao gerenciador de objetos do Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> primeiro você deve registrar a biblioteca com o gerenciador de objetos do Visual Studio, chamando o método. Depois que a biblioteca é registrada, o gerenciador de objetos do Visual Studio solicita certas informações sobre as capacidades da biblioteca. Por exemplo, ele solicita as bandeiras da <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> biblioteca <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> e categorias suportadas chamando os métodos. Em algum momento, quando uma das ferramentas solicita dados dessa biblioteca, o gerenciador de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> objetos solicita a lista de símbolos de nível superior chamando o método. Em resposta, a biblioteca fabrica uma lista de símbolos e expõe-o ao gerenciador de objetos do Visual Studio através da <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> interface. O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerenciador de objetos determina quantos itens <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> estão na lista chamando o método. Todas as solicitações a seguir referem-se a um determinado item da lista e fornecem o número do índice do item em cada solicitação. O gerenciador de objetos Visual Studio passa a coletar as informações sobre o tipo, a acessibilidade e outras propriedades do item, chamando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> método.

 Ele determina o nome do item <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> chamando o método e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> solicita as informações do ícone chamando o método. O ícone é exibido à esquerda do nome do item e mostra o tipo do item, a acessibilidade e outras propriedades.

 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerenciador <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> de objetos chama o método para determinar se um determinado item da lista é expansível e tem itens infantis. Se a UI enviar uma solicitação para expandir um elemento, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> gerenciador de objetos solicitará a lista filho de símbolos chamando o método. O processo continua com diferentes partes da árvore sendo construídas sob demanda.

> [!NOTE]
> Para implementar um provedor de <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> símbolo <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> de código nativo, use as interfaces e interfaces.

## <a name="see-also"></a>Confira também
- [Como registrar uma biblioteca com o Gerenciador de Objetos](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [Como expor listas de símbolos fornecidos pela biblioteca ao Gerenciador de Objetos](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [Como identificar símbolos em uma biblioteca](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
