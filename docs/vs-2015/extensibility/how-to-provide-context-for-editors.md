---
title: 'Como: fornecer contexto para editores | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 11a98599a9812cd00650d113170ff55c01ac44db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838433"
---
# <a name="how-to-provide-context-for-editors"></a>Como fornecer contexto para editores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para um editor, o contexto é ativo somente quando o editor tem foco ou tem foco imediatamente antes de o foco ser movido para uma janela de ferramenta. Você pode fornecer contexto para um editor fazendo o seguinte:  
  
1. Crie um recipiente de contexto.  
  
2. Publique o recipiente de contexto no identificador do elemento de seleção (SEID).  
  
3. Manter o contexto na bolsa.  
  
   Essas tarefas são cobertas pelos procedimentos a seguir. Para obter mais informações sobre como fornecer contexto, consulte **programação robusta** mais adiante neste tópico.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Para criar um recipiente de contexto para um editor ou um designer  
  
1. Chame `QueryService` na sua <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interface para o <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> serviço.  
  
     Um ponteiro para a <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> interface é retornado.  
  
2. Chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> método para criar um novo contexto ou recipiente de subcontexto.  
  
     Um ponteiro para a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> interface é retornado.  
  
3. Chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> método para adicionar atributos, palavras-chave de pesquisa ou palavras-chave F1 ao recipiente de contexto ou subcontexto.  
  
4. Se você estiver criando um recipiente de subcontexto, chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> método para vincular o recipiente de subcontexto ao recipiente de contexto pai.  
  
5. Chamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> para receber notificação quando a janela de **Ajuda dinâmica** estiver prestes a ser atualizada.  
  
     Fazer com que a janela de **Ajuda dinâmica** chame seu editor quando ele estiver pronto para atualização lhe dá a oportunidade de atrasar a alteração do contexto até que ocorra a atualização. Isso pode melhorar o desempenho porque permite atrasar os algoritmos demorados da execução até que o tempo ocioso do sistema esteja disponível.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Para publicar o recipiente de contexto no SEID  
  
1. Chame `QueryService` no <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> serviço para retornar um ponteiro para a <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interface.  
  
2. Chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> , especificando um `elementid` valor de identificador (parâmetro) de elemento de SEID_UserContext para indicar que você está passando o contexto para o nível global.  
  
3. Quando o editor ou o designer se torna ativo, os valores em seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> objeto são propagados para a seleção global. Você só precisa concluir esse processo uma vez por sessão e, em seguida, armazenar o ponteiro para o contexto global criado quando você chamou <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> .  
  
### <a name="to-maintain-the-context-bag"></a>Para manter o recipiente de contexto  
  
1. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> para garantir que a janela de **Ajuda dinâmica** chame o editor ou designer antes de atualizar.  
  
     Para cada recipiente de contexto que foi chamado <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> depois que o recipiente de contexto é criado e implementado <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate> , o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> para notificar o provedor de contexto que o recipiente de contexto será atualizado. Você pode usar essa chamada para alterar os atributos e as palavras-chave no recipiente de contexto, e em qualquer supercontexto, antes que a atualização da janela de **Ajuda dinâmica** ocorra.  
  
2. Chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> no recipiente de contexto para indicar que o editor ou designer tem um novo contexto.  
  
     Quando a janela de **Ajuda dinâmica** chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> para indicar que está atualizando, o editor ou o designer pode atualizar o contexto adequadamente para o recipiente de contexto pai e qualquer supercontexto no momento.  
  
    > [!NOTE]
    > O `SetDirty` sinalizador é definido automaticamente para `true` sempre que o contexto é adicionado ou removido do recipiente de contexto. A janela de **Ajuda dinâmica** só chamará <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> o recipiente de contexto se o `SetDirty` sinalizador for definido como `true` . Ele é redefinido para `false` após a atualização.  
  
3. Chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> para adicionar contexto à coleção de contexto ativa ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> para remover o contexto.  
  
## <a name="robust-programming"></a>Programação robusta  
 Se você estiver escrevendo seu próprio editor, deverá concluir todos os três procedimentos neste tópico para fornecer contexto para o editor.  
  
> [!NOTE]
> Para ativar corretamente um editor ou uma janela de designer e garantir que o roteamento de comandos seja atualizado corretamente, você deve chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> no componente para torná-lo a janela de foco.  
  
 O SEID é uma coleção de propriedades que são alteradas com base na seleção. As informações de SEID estão disponíveis por meio da seleção global. A seleção global é conectada a eventos disparados pela <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> interface e tem uma lista de tudo o que está selecionado (editor atual, janela de ferramentas atual, hierarquia atual e assim por diante).  
  
 Para editores e designers, em que o contexto pode ser alterado sempre que o cursor se move em uma palavra, é ineficiente atualizar constantemente o recipiente de contexto. Para tornar a atualização mais eficiente sempre que detectar o cursor em movimento dentro da janela Editor ou designer, você pode chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> . Isso permite que você mantenha as alterações de contexto até que haja tempo ocioso e o serviço de contexto do IDE envie notificação ao editor ou ao designer que a janela de **Ajuda dinâmica** está atualizando. Essa abordagem é usada no procedimento "para manter o recipiente de contexto" neste tópico.  
  
 Depois de fornecer o contexto para atividades no editor ou designer, você deve fornecer uma palavra-chave F1 específica para permitir que os usuários obtenham ajuda para o próprio editor ou designer.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>
