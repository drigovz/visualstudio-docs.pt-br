---
title: Ativação in-loco | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - in-place view activation
ms.assetid: 7d316945-06e0-4d8e-ba3a-0ef96fc75399
caps.latest.revision: 26
manager: jillfra
ms.openlocfilehash: 192274d087731f68cb7e01c1da20e80cbfef0360
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802929"
---
# <a name="in-place-activation"></a>Ativação in-loco
Se a exibição do editor hospedar ActiveX ou outros controles ativos, você deverá implementar a exibição do editor como um controle ActiveX ou um objeto de dados do documento ativo usando o modelo de ativação in-loco.  
  
## <a name="support-for-menus-toolbars-and-commands"></a>Suporte para menus, barras de ferramentas e comandos  
 O Visual Studio permite que a exibição do editor use os menus e as barras de ferramentas do IDE. Essas extensões são conhecidas como *componentes no local OLE*. Para obter mais informações, consulte o <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> e o <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> .  
  
 Se você implementar um controle ActiveX, poderá hospedar outros objetos incorporados. Se você implementar um objeto de dados de documento, o quadro de janela restringirá sua capacidade de usar controles ActiveX.  
  
> [!NOTE]
> As <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> interfaces e permitem uma separação de dados e exibição. No entanto, o Visual Studio não oferece suporte a essa funcionalidade, e essas interfaces são usadas apenas para representar o objeto de exibição de documento.  
  
 Os editores que usam o <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> serviço podem fornecer o menu, a barra de ferramentas e a integração de comandos chamando os métodos da <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interface implementada pelo <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> serviço. Os editores também podem oferecer outras funcionalidades do Visual Studio, como o controle de seleção e o gerenciamento de desfazer. Para obter mais informações, consulte [criando editores e designers personalizados](../extensibility/creating-custom-editors-and-designers.md).  
  
## <a name="objects-and-interfaces-used"></a>Objetos e interfaces usados  
 Os objetos usados para criar a ativação in-loco são mostrados na ilustração a seguir.  
  
 ![No editor de ativação&#45;local](../misc/media/vsinplaceactivationeditor.gif "vsInPlaceActivationEditor")  
Editor de ativação in-loco  
  
> [!NOTE]
> Dos objetos neste desenho, somente o `CYourEditorFactory` objeto é necessário para criar um editor padrão. Se você estiver criando um editor personalizado, não será necessário implementá-lo <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> porque seu editor provavelmente terá seu próprio mecanismo de persistência privado. Para obter mais informações, consulte [criando editores e designers personalizados](../extensibility/creating-custom-editors-and-designers.md).  
  
 Todas as interfaces implementadas para criar um editor de ativação in-loco são mostradas no único `CYourEditorDocument` objeto, mas essa configuração dá suporte apenas a uma exibição única de dados de documento. Para obter mais informações sobre como dar suporte a várias exibições de seus dados de documento, consulte [dando suporte a exibições de vários documentos](../extensibility/supporting-multiple-document-views.md).  
  
|Interface|Tipo de objeto|Uso|  
|---------------|--------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|Visualizar|Permite que objetos VSPackage in-loco operem como componentes totalmente integrados do IDE usando o <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> serviço. Esse serviço integra os menus, as barras de ferramentas e os comandos do objeto no IDE e emite notificações de alterações de estado.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>|Visualizar|Principal significa por meio do qual um objeto incorporado fornece funcionalidade básica para seu contêiner e se comunica com ele.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>|Visualizar|Gerencia a ativação e a desativação de objetos in-loco e determina a quantidade do objeto in-loco que deve estar visível.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceObject>|Visualizar|Fornece um canal direto de comunicação entre um objeto no local, a janela de quadro externa do aplicativo associado e a janela do documento no aplicativo que contém o objeto inserido.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>|Visualizar|Implementa um objeto ActiveX. Observe que os métodos de <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> e `T:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView` que separa dados de documento e exibição não são usados no IDE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Exibição/dados|Habilita o objeto de dados do documento ou o objeto de exibição de documento ou ambos para participar da manipulação de comandos.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Visualizar|Habilita atualizações da barra de status.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Visualizar|Permite adicionar itens à caixa de ferramentas.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Dados|Envia a notificação de alterações para o arquivo editado. (Essa interface é opcional.)|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Dados|Usado para habilitar o recurso salvar como para um tipo de arquivo.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Dados|Habilita a persistência para o documento. Para arquivos somente leitura, chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SetDocDataReadOnly%2A> para fornecer o ícone de "bloqueio" que indica arquivos somente leitura.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Dados|Determina se as alterações nos dados do documento devem ser ignoradas.|