---
title: 'Checklist: Criando um serviço de linguagem legado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11785dab63cbb6a95ab2d34c5edbfb4525ebf34c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709785"
---
# <a name="checklist-create-a-legacy-language-service"></a>Checklist: Crie um serviço de idioma legado
A lista de verificação a seguir resume as etapas básicas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que você deve tomar para criar um serviço de idioma para o editor principal. Para integrar seu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]serviço de idioma, você deve criar um avaliador de expressão de depuração. Para obter mais informações, consulte [Escreva um avaliador](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) de expressão CLR na [extensibilidade do depurador visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="steps-to-create-a-language-service"></a>Etapas para criar um serviço de idioma

1. Implemente a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.

    - Em seu VSPackage, <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> implemente a interface para fornecer o serviço de idioma.

    - Disponibilize seu serviço de idiomas para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> ambiente de desenvolvimento integrado (IDE) em sua implementação.

2. Implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> a interface na classe principal de serviço de idiomas.

     A <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface é o ponto de partida da interação entre o editor principal e o serviço de idiomas.

### <a name="optional-features"></a>Recursos opcionais
 Os seguintes recursos são opcionais e podem ser implementados em qualquer ordem. Esses recursos aumentam a funcionalidade do seu serviço de idiomas.

- Coloração de sintaxe

  Implemente a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. Sua implementação desta interface deve ser que as informações do analisador retornem as informações de cor apropriadas.

  O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> retorna a interface. Uma instância de colorrizador separada é criada para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> cada buffer de texto, então você deve implementar a interface separadamente. Para obter mais informações, consulte [Coloração sintaxe em um serviço de linguagem legado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).

- Janela de código

  Implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> a interface para permitir que o serviço de idioma suma notificação de quando uma nova janela de código for criada.

  O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> retorna a interface. O serviço de idiomas pode então adicionar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>ui especial à janela de código em . O serviço de idiomas também pode fazer qualquer processamento <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>especial, como adicionar um filtro de exibição de texto em .

- Filtro de visualização de texto

  Para fornecer a conclusão da declaração do IntelliSense em um serviço de idioma, você deve interceptar alguns dos comandos que a exibição de texto manteria de outra forma. Para interceptar esses comandos, complete as seguintes etapas:

  - Implementar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> para participar da cadeia de comando e lidar com os comandos do editor.

  - Ligue <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> para o método <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> e passe em sua implementação.

  - Chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> o método quando você se separar da exibição para que esses comandos não sejam mais passados para você.

  Os comandos que devem ser manuseados dependem dos serviços prestados. Para obter mais informações, consulte [Comandos importantes para filtros de serviço de idioma .](../../extensibility/internals/important-commands-for-language-service-filters.md)

  > [!NOTE]
  > A <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interface deve ser implementada no <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> mesmo objeto que a interface.

- Conclusão da instrução

  Implemente a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.

  Apoie o comando de conclusão <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>de declaração (ou seja, ) e chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface, passando pela <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interface. Para obter mais informações, consulte [Conclusão da declaração em um serviço de idioma legado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).

- Dicas de método

  Implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> a interface para fornecer dados para a janela de ponta do método.

  Instale o filtro de exibição de texto para lidar com os comandos adequadamente, para que você saiba quando mostrar uma janela de dica de dados do método. Para obter mais informações, consulte [Parameter Info em um serviço de idioma legado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).

- Marcadores de erro

  Implemente a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.

  Crie os objetos de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> marcador de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> erro que <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> implementam a interface e chamem o método, passando pela interface do objeto marcador de erro.

  Normalmente, cada marcador de erro gerencia um item na janela da lista de tarefas.

- Itens da lista de tarefas

  Implemente uma classe de <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> item de tarefa que forneça a interface.

  Implemente uma classe <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> de provedor <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> de tarefas que forneça a interface e a interface.

  Implemente uma classe de enumeradores de tarefas que forneça a <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> interface.

  Registre o provedor de tarefas <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> com o método da lista de tarefas.

  Obtenha <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> a interface ligando para o provedor de <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>serviços do idioma com o GUID de serviço.

  Crie objetos de item de tarefa e chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> método na <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interface quando houver tarefas novas ou atualizadas.

- Itens de tarefa de comentário

  Use <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> e a interface para obter os tokens da tarefa de comentário.

  Obtenha <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> uma interface <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> do serviço.

  Obtenha <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> a partir do método.

  Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> a interface para ouvir alterações na lista de tokens.

- Estrutura de tópicos

  Existem várias opções para apoiar o delineamento. Por exemplo, você pode oferecer suporte ao comando **'Colapso às Definições',** fornecer regiões de contorno controladas pelo editor ou oferecer suporte a regiões controladas pelo cliente. Para obter mais informações, consulte [Como: Fornecer suporte de delineamento expandido em um serviço de idioma legado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).

- Registro de serviços de idiomas

  Para obter mais informações sobre como registrar um serviço de idioma, consulte [Registrar um serviço de idioma legado](../../extensibility/internals/registering-a-legacy-language-service2.md) e gerenciar [vspackages](../../extensibility/managing-vspackages.md).

- Ajuda sensível ao contexto

  Forneça contexto ao editor de uma das seguintes maneiras:

  - Forneça contexto para marcadores de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> texto implementando a interface.

  - Forneça todo o contexto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> do usuário implementando a interface.

## <a name="see-also"></a>Confira também
- [Desenvolva um serviço de linguagem legado](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Escreva um avaliador de expressão CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
