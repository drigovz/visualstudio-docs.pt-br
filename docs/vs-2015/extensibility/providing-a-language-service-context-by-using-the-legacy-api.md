---
title: Fornecendo um contexto de serviço de linguagem usando a API herdada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - language service context
ms.assetid: daa2df22-9181-4bad-b007-a7d40302bce1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4471b71b612008ba7d0733c92286415cd3c3f6b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193879"
---
# <a name="providing-a-language-service-context-by-using-the-legacy-api"></a>Fornecer um contexto de serviço de linguagem usando a API herdada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Há duas opções para um serviço de linguagem fornecer o contexto do usuário usando o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principal: forneça o contexto do marcador de texto ou forneça todo o contexto do usuário. As diferenças entre cada um são descritas aqui.  
  
 Para obter mais informações sobre como fornecer contexto a um serviço de linguagem que está conectado ao seu próprio editor, consulte [como: fornecer contexto para editores](../extensibility/how-to-provide-context-for-editors.md).  
  
## <a name="provide-text-marker-context-to-the-editor"></a>Fornecer contexto de marcador de texto para o editor  
 Para fornecer contexto para erros de compilador indicados por marcadores de texto no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principal, implemente a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interface. Nesse cenário, o serviço de idioma fornece contexto somente quando o cursor está em um marcador de texto. Isso permite que o editor forneça a palavra-chave no cursor para a janela de **Ajuda dinâmica** sem atributos.  
  
## <a name="provide-all-user-context-to-the-editor"></a>Fornecer todo o contexto do usuário para o editor  
 Se você estiver criando um serviço de linguagem e estiver usando o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor de núcleo, poderá implementar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interface para fornecer contexto para o serviço de idioma.  
  
 Para a implementação do `IVsLanguageContextProvider` , um recipiente de contexto (coleção) é anexado ao editor, que é responsável por atualizar o recipiente de contexto. Quando a janela de **Ajuda dinâmica** chama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.Update%2A> interface nesse recipiente de contexto no tempo ocioso, o recipiente de contexto consulta o editor em busca de uma atualização. Em seguida, o editor notifica o serviço de linguagem que ele deve atualizar o editor e passa um ponteiro para o recipiente de contexto. Isso é feito chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider.UpdateLanguageContext%2A> método do editor para o serviço de idioma. Usando o ponteiro para o recipiente de contexto, o serviço de linguagem agora pode adicionar e remover atributos e palavras-chave. Para obter mais informações, consulte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>.  
  
 Há duas maneiras diferentes de implementar `IVsLanguageContextProvider` :  
  
- Fornecer uma palavra-chave para o recipiente de contexto  
  
   Quando o editor é chamado para atualizar o recipiente de contexto, passe as palavras-chave e os atributos apropriados e, em seguida, retorne `S_OK` . Esse valor de retorno instrui o editor a reter a palavra-chave e o contexto de atributo em vez de fornecer a palavra-chave no cursor para o recipiente de contexto.  
  
- Obter a palavra-chave da palavra-chave no cursor  
  
   Quando o editor é chamado para atualizar o recipiente de contexto, passe os atributos apropriados e, em seguida, retorne `E_FAIL` . Esse valor de retorno instrui o editor a manter seus atributos no recipiente de contexto, mas atualizar o recipiente de contexto com a palavra-chave no cursor.  
  
  O diagrama a seguir demonstra como o contexto é fornecido para um serviço de linguagem que implementa o `IVsLanguageContextProvider` .  
  
  ![Gráfico de LangServiceImplementation2](../extensibility/media/vslanguageservice2.gif "vsLanguageService2")  
  Contexto para um serviço de idioma  
  
  Como você pode ver no diagrama, o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor de texto principal tem um recipiente de contexto anexado a ele. Este recipiente de contexto aponta para três pacotes de subcontextos separados: serviço de idioma, editor padrão e marcador de texto. Os pacotes de subcontexto do serviço de idioma e do marcador de texto contêm atributos e palavras-chave para o serviço de idioma se a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> interface for implementada e marcadores de texto se a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> interface for implementada. Se você não implementar nenhuma dessas interfaces, o editor fornecerá contexto para a palavra-chave no cursor no recipiente de subcontexto do editor padrão.  
  
## <a name="context-guidelines-for-editors-and-designers"></a>Diretrizes de contexto para editores e designers  
 Designers e editores devem fornecer uma palavra-chave geral para a janela Editor ou designer. Isso é feito para que um tópico de ajuda genérico, mas apropriado, seja exibido para o designer ou editor quando um usuário pressionar F1. Um editor deve, além disso, fornecer a palavra-chave Current no cursor ou fornecer um termo-chave com base na seleção atual. Isso é feito para garantir que um tópico da ajuda para o elemento Text ou UI apontado ou selecionado seja exibido quando o usuário pressionar F1. Um designer fornece contexto para um item selecionado em um designer, como um botão em um formulário. Editores e designers também devem se conectar a um serviço de linguagem, conforme descrito em [princípios de serviço de linguagem herdado](../extensibility/internals/legacy-language-service-essentials.md).
