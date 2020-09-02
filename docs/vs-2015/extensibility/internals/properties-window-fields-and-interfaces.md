---
title: Propriedades e interfaces campos de janela | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b58314d64536ecf33cc5589609ee5524a9352629
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700818"
---
# <a name="properties-window-fields-and-interfaces"></a>Interfaces e campos da janela Propriedades
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O modelo de seleção para determinar quais informações são exibidas na janela **Propriedades** baseia-se na janela que tem o foco no IDE. Cada janela e objeto dentro da janela selecionada podem ter seu objeto de contexto de seleção enviado por push para o contexto de seleção global. O ambiente atualiza o contexto de seleção global com valores de um quadro de janela quando essa janela tem o foco. Quando o foco muda, o contexto de seleção é alterado.  
  
## <a name="tracking-selection-in-the-ide"></a>Controlando a seleção no IDE  
 O quadro de janela ou site, pertencente ao IDE, tem um serviço chamado <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . As etapas a seguir mostram como uma alteração em uma seleção, causada pelo usuário que está alterando o foco para outra janela aberta ou selecionando um item de projeto diferente no **Gerenciador de soluções**, é implementada para alterar o conteúdo exibido na janela **Propriedades** .  
  
1. O objeto criado por seu VSPackage que está no local na janela selecionada chama <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> para ter <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Invoke <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
2. O contêiner de seleção, fornecido pela janela selecionada, cria seu próprio <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objeto. Quando a seleção é alterada, o VSPackage chama <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> para notificar quaisquer ouvintes no ambiente, incluindo a janela **Propriedades** da alteração. Ele também fornece acesso a informações de hierarquia e de item relacionadas à nova seleção.  
  
3. Chamar <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> e passar os itens de hierarquia selecionados no `VSHPROPID_BrowseObject` parâmetro popula o <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> objeto.  
  
4. Um objeto derivado da [interface IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) é retornado para <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> o item solicitado e o ambiente o encapsula em um <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (consulte a etapa a seguir). Se a chamada falhar, o ambiente fará uma segunda chamada para `IVsHierarchy::GetProperty` , passando-o para o contêiner de seleção <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> que o item ou itens de hierarquia fornece.  
  
    O projeto VSPackage não cria <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> porque a janela VSPackage fornecida pelo ambiente que a implementa (por exemplo, **Gerenciador de soluções**) constrói <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> em seu nome.  
  
5. O ambiente invoca os métodos de <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> para obter os objetos com base na `IDispatch` interface para preencher a janela **Propriedades** .  
  
   Quando um valor na janela **Propriedades** é alterado, VSPackages implementa `IVsTrackSelectionEx::OnElementValueChangeEx` e `IVsTrackSelectionEx::OnSelectionChangeEx` relata a alteração para o valor do elemento. Em seguida, o ambiente invoca <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> ou <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> mantém as informações exibidas na janela **Propriedades** sincronizadas com os valores de propriedade. Para obter mais informações, consulte [atualizando valores de propriedade na janela Propriedades](../../misc/updating-property-values-in-the-properties-window.md).  
  
   Além de selecionar um item de projeto diferente em **Gerenciador de soluções** para exibir as propriedades relacionadas a esse item, você também pode escolher um objeto diferente de dentro de uma janela de formulário ou de documento usando a lista suspensa disponível na janela **Propriedades** . Para obter mais informações, consulte [lista de objetos da janela de propriedades](../../extensibility/internals/properties-window-object-list.md).  
  
   Você pode alterar a maneira como as informações são exibidas na grade da janela **Propriedades** de ordem alfabética para categórica e, se disponíveis, você também pode abrir uma página de propriedades para um objeto selecionado clicando nos botões apropriados na janela **Propriedades** . Para obter mais informações, consulte [botões da janela de propriedades](../../extensibility/internals/properties-window-buttons.md) e páginas de [Propriedades](../../extensibility/internals/property-pages.md).  
  
   Por fim, a parte inferior da janela **Propriedades** também contém uma descrição do campo selecionado na grade da janela **Propriedades** . Para obter mais informações, consulte [obtendo descrições de campo na janela Propriedades](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Estendendo propriedades](../../extensibility/internals/extending-properties.md)
