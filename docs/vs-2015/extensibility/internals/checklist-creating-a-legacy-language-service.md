---
title: 'Lista de verificação: Criando um serviço de idioma herdado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b79afe64aafac473d4fe5d22464998d0c2f0537
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838660"
---
# <a name="checklist-creating-a-legacy-language-service"></a>Lista de verificação: Criando um serviço de linguagem herdado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A lista de verificação a seguir resume as etapas básicas que você deve executar para criar um serviço de idioma para o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] editor principal. Para integrar seu serviço de idioma no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , você deve criar um avaliador de expressão de depuração. Para obter mais informações, consulte [escrevendo um avaliador de expressão CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) na [extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="steps-for-creating-a-language-service"></a>Etapas para criar um serviço de idioma  
  
1. Implemente a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  
  
    - Em seu VSPackage, implemente a <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interface para fornecer o serviço de linguagem.  
  
    - Disponibilize seu serviço de linguagem para o ambiente de desenvolvimento integrado (IDE) em sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementação.  
  
2. Implemente a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface na classe de serviço do idioma principal.  
  
     A <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interface é o ponto de partida de interação entre o editor principal e o serviço de linguagem.  
  
### <a name="optional-features"></a>Recursos opcionais  
 Os recursos a seguir são opcionais e podem ser implementados em qualquer ordem. Esses recursos aumentam a funcionalidade do seu serviço de idioma.  
  
- Coloração de sintaxe  
  
   Implemente a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. A implementação dessa interface deve que as informações do analisador retornem as informações de cor apropriadas.  
  
   O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> método retorna a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interface. Uma instância Colorizer separada é criada para cada buffer de texto, portanto, você deve implementar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interface separadamente. Para obter mais informações, consulte [cores de sintaxe em um serviço de linguagem herdado](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
- Janela de código  
  
   Implemente a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interface para habilitar o serviço de linguagem a receber notificação de quando uma nova janela de código for criada.  
  
   O <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> método retorna a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> interface. O serviço de linguagem pode então adicionar uma interface do usuário especial à janela de código no <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> . O serviço de linguagem também pode fazer qualquer processamento especial, como adicionar um filtro de exibição de texto no <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A> .  
  
- Filtro de exibição de texto  
  
   Para fornecer a conclusão da instrução IntelliSense em um serviço de idioma, você deve interceptar alguns dos comandos que o modo de exibição de texto trataria de outra forma. Para interceptar esses comandos, conclua as seguintes etapas:  
  
  - Implemente <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> para participar da cadeia de comandos e manipule os comandos do editor.  
  
  - Chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método e passe sua <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementação.  
  
  - Chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> método ao desanexar da exibição para que esses comandos não sejam mais passados para você.  
  
    Os comandos que devem ser manipulados dependem dos serviços fornecidos. Para obter mais informações, consulte [importantes comandos para filtros de serviço de linguagem](../../extensibility/internals/important-commands-for-language-service-filters.md).  
  
  > [!NOTE]
  > A <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> interface deve ser implementada no mesmo objeto que a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface.  
  
- Conclusão da instrução  
  
   Implemente a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.  
  
   Dê suporte ao comando de conclusão de instrução (ou seja, <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> ) e chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface, passando a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interface. Para obter mais informações, consulte [conclusão de instrução em um serviço de linguagem herdado](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).  
  
- Dicas de método  
  
   Implemente a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interface para fornecer dados para a janela de dica do método.  
  
   Instale o filtro de exibição de texto para manipular comandos adequadamente, para que você saiba quando mostrar uma janela de dica de dados de método. Para obter mais informações, consulte [informações de parâmetro em um serviço de linguagem herdado](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).  
  
- Marcadores de erro  
  
   Implemente a interface <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.  
  
   Crie os objetos de marcador de erro que implementam a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface e chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> método, passando a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> interface do objeto marcador de erro.  
  
   Normalmente, cada marcador de erro gerencia um item na janela de lista de tarefas.  
  
- Itens de Lista de Tarefas  
  
   Implemente uma classe de item de tarefa fornecendo a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> interface.  
  
   Implemente uma classe de provedor de tarefas que forneça a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> interface e a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> interface.  
  
   Implemente uma classe de enumerador de tarefa que forneça a <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> interface.  
  
   Registre o provedor de tarefas com o método da lista de tarefas <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> .  
  
   Obtenha a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interface chamando o provedor de serviços do serviço de linguagem com o GUID do serviço <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> .  
  
   Crie objetos de item de tarefa e chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> método na <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> interface quando houver tarefas novas ou atualizadas.  
  
- Itens de tarefa de comentário  
  
   Use a <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interface e a <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interface para obter os tokens de tarefa de comentário.  
  
   Obtenha uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> interface do <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> serviço.  
  
   Obtenha a <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> interface do <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> método.  
  
   Implemente a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> interface para escutar alterações na lista de tokens.  
  
- Estrutura de tópicos  
  
   Há várias opções para dar suporte a estrutura de tópicos. Por exemplo, você pode dar suporte ao comando **recolher para definições** , fornecer regiões de estrutura de tópicos controladas por editor ou dar suporte a regiões controladas pelo cliente. Para obter mais informações, consulte [como fornecer suporte expandido à estrutura de tópicos em um serviço de linguagem herdado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).  
  
- Registro do serviço de idioma  
  
   Para obter mais informações sobre como registrar um serviço de linguagem, consulte [registrando um serviço de linguagem herdado](../../extensibility/internals/registering-a-legacy-language-service2.md) e [Gerenciando VSPackages](../../extensibility/managing-vspackages.md).  
  
- Ajuda contextual  
  
   Forneça o contexto para o editor de uma das seguintes maneiras:  
  
  - Forneça o contexto para marcadores de texto implementando a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interface.  
  
  Forneça todo o contexto do usuário implementando a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interface.  
  
## <a name="see-also"></a>Consulte Também  
 [Desenvolvendo um serviço de linguagem herdado](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Escrevendo um avaliador de expressão do CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
