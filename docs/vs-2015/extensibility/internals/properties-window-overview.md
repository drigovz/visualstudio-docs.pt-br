---
title: Visão geral da janela Propriedades | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fd4be229338d1a09c22b4d81384dc90f0544fa39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700749"
---
# <a name="properties-window-overview"></a>Visão geral da janela Propriedades
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A janela **Propriedades** é usada para exibir propriedades de objetos selecionados nos dois tipos principais de Windows disponíveis no ambiente de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] desenvolvimento integrado (IDE). Esses dois tipos de janelas são:  
  
- Janelas de ferramentas, como Gerenciador de Soluções, Modo de Exibição de Classe e pesquisador de objetos  
  
- Documente as janelas que contêm tais editores e designers como designer de formulários, editor de XML e editor de HTML  
  
## <a name="using-the-properties-window"></a>Usando a janela Propriedades  
 A janela **Propriedades** exibe as propriedades de um ou vários itens selecionados. Se vários itens forem selecionados, a interseção de todas as propriedades de todos os objetos selecionados será exibida.  
  
 Eventos relacionados a um objeto selecionado em uma janela de design de formulário ou em um editor de HTML usando metadados COM+ são exibidos na janela **Propriedades** . Por exemplo, você pode selecionar um botão e exibir seus eventos associados, como um `OnClick` evento, que pode ser vinculado a esse botão.  
  
 Os eventos exibidos na janela **Propriedades** são usados principalmente com objetos associados ao código. Se você estiver editando um formato de arquivo que não tem nada a ver com o código, não haverá nenhum evento. Os eventos são exibidos apenas na janela **Propriedades** quando há uma associação entre o código em execução e determinados eventos associados a objetos específicos. Um exemplo disso seria o código por trás de um objeto selecionado que é executado quando esse objeto é ativado.  
  
 A tabela a seguir lista as interfaces primárias usadas pela janela **Propriedades** .  
  
|Nome da Interface|Descrição|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Fornece uma lista de categorias para a janela **Propriedades** e mapeia cada propriedade para uma categoria.|  
|[Interface IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)|Expõe os métodos e as propriedades de um objeto para ferramentas de programação e outros aplicativos que dão suporte à automação.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Fornece botões de reticências (...) chamados *construtores* que abrem janelas de caixas de diálogo modais implementadas pelo próprio objeto. Usado quando um valor não é facilmente digitado pelo usuário em um campo de texto. Por exemplo, ele pode ser usado para abrir um seletor de cores que determina o valor RGB para você.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Fornece acesso a objetos usados para atualizar as informações exibidas na janela **Propriedades** . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> é implementado por VSPackages para cada janela que contém objetos selecionáveis com propriedades relacionadas a serem exibidas.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Fornece informações sobre o tipo de um objeto, como métodos de uma interface e os campos de uma estrutura.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Permite que o VSPackages receba notificações de eventos de seleção e recupere informações sobre a hierarquia de projeto atual, o item, o valor do elemento e o contexto da interface do usuário do comando.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Fornece o ambiente com acesso a várias seleções.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Usado para fornecer nomes localizados em algumas propriedades exibidas na janela **Propriedades** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Notifica o VSPackages registrado sobre alterações na seleção atual, no valor do elemento ou no contexto da interface do usuário do comando.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Notifica o ambiente de uma alteração na seleção atual e fornece acesso às informações de hierarquia e de item relacionadas à nova seleção.|  
  
 Para obter mais informações sobre `IDispatch` o, consulte a biblioteca MSDN.  
  
## <a name="see-also"></a>Consulte Também  
 [Estendendo propriedades](../../extensibility/internals/extending-properties.md)   
 [Interfaces e campos da janela Propriedades](../../extensibility/internals/properties-window-fields-and-interfaces.md)
