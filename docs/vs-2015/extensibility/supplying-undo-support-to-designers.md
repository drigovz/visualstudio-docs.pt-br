---
title: Fornecendo suporte de desfazer para designers | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6136caaec0cb8f0d79e3fb7b96245fc3fd070710
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675335"
---
# <a name="supplying-undo-support-to-designers"></a>Fornecendo suporte à função desfazer para designers
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Designers, como editores, normalmente precisam oferecer suporte a operações de desfazer para que os usuários possam reverter suas alterações recentes ao modificar um elemento de código.  
  
 A maioria dos designers implementados no Visual Studio têm suporte de desfazer automaticamente fornecido pelo ambiente.  
  
 Implementações de designer que precisam fornecer suporte para o recurso de desfazer:  
  
- Fornecer gerenciamento de desfazer implementando a classe base abstrata <xref:System.ComponentModel.Design.UndoEngine>  
  
- Forneça suporte a persistência e CodeDOM implementando as <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> <xref:System.ComponentModel.Design.IComponentChangeService> classes e.  
  
  Para obter mais informações sobre como escrever designers usando o [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , consulte [estendendo o suporte ao tempo de design](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
  O [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] fornece uma infraestrutura de desfazer padrão por:  
  
- Fornecer implementações de gerenciamento de desfazer por meio das <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> classes e.  
  
- Fornecendo suporte a persistência e CodeDOM por meio do padrão <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> e das <xref:System.ComponentModel.Design.IComponentChangeService> implementações.  
  
## <a name="obtaining-undo-support-automatically"></a>Obtendo suporte de desfazer automaticamente  
 Qualquer designer criado no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tem suporte automático e de desfazer completo se, o designer:  
  
- Usa uma <xref:System.Windows.Forms.Control> classe baseada em sua interface do usuário.  
  
- Emprega a geração de código baseado em CodeDOM padrão e o sistema de análise para a geração e persistência de código.  
  
     Para obter mais informações sobre como trabalhar com o suporte a CodeDOM do Visual Studio, consulte [geração e compilação de código-fonte dinâmico](https://msdn.microsoft.com/library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Quando usar o suporte de desfazer do designer explícito  
 Os designers devem fornecer seu próprio gerenciamento de desfazer se usarem uma interface gráfica do usuário, conhecida como adaptador de exibição, diferente daquele fornecido pelo <xref:System.Windows.Forms.Control> .  
  
 Um exemplo disso pode ser a criação de um produto com uma interface de design gráfico baseada na Web, em vez de uma [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] interface gráfica baseada em.  
  
 Nesses casos, seria necessário registrar esse adaptador de exibição no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usando <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> e fornecer gerenciamento de desfazer explícito.  
  
 Os designers precisam fornecer suporte a CodeDOM e persistência se não usarem o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modelo de geração de código fornecido no <xref:System.CodeDom> espaço de nome.  
  
## <a name="undo-support-features-of-the-designer"></a>Desfazer recursos de suporte do designer  
 O SDK do ambiente fornece implementações padrão de interfaces necessárias para fornecer suporte de desfazer que pode ser usado por designers que não usam <xref:System.Windows.Forms.Control> classes baseadas em suas interfaces de usuário ou o modelo CodeDOM e persistência padrão.  
  
 A <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe deriva da [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.ComponentModel.Design.UndoEngine> classe usando uma implementação da <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> classe para gerenciar operações de desfazer.  
  
 O Visual Studio fornece o seguinte recurso para o designer desfazer:  
  
- Funcionalidade de desfazer vinculada em vários designers.  
  
- As unidades filhas dentro de um designer podem interagir com seus pais implementando <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> em <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .  
  
  O SDK do ambiente fornece suporte a CodeDOM e persistência fornecendo:  
  
- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> como implementações do <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
  Um <xref:System.ComponentModel.Design.IComponentChangeService> fornecido pelo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] host de design ' '.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Usando os recursos do SDK do ambiente para fornecer suporte de desfazer  
 Para obter o suporte de desfazer, um objeto que implementa um designer deve:  
  
- Instancie e inicialize uma instância da <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe com uma <xref:System.IServiceProvider> implementação válida.  
  
- Essa <xref:System.IServiceProvider> classe deve fornecer os seguintes serviços:  
  
  - <xref:System.ComponentModel.Design.IDesignerHost>.  
  
  - <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
       Os designers [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que usam a serialização CodeDom podem optar <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> pelo uso fornecido com o [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] como sua implementação do <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .  
  
       Nesse caso, a <xref:System.IServiceProvider> classe fornecida para o <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Construtor deve retornar esse objeto como uma implementação da <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> classe.  
  
  - <xref:System.ComponentModel.Design.IComponentChangeService>  
  
       Os designers que usam o padrão <xref:System.ComponentModel.Design.DesignSurface> fornecido pelo host de design têm a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] garantia de ter uma implementação padrão da <xref:System.ComponentModel.Design.IComponentChangeService> classe.  
  
  Os designers que implementam um <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> mecanismo de desfazer baseado controlam automaticamente as alterações se:  
  
- As alterações de propriedade são feitas por meio do <xref:System.ComponentModel.TypeDescriptor> objeto.  
  
- <xref:System.ComponentModel.Design.IComponentChangeService> os eventos são gerados manualmente quando uma alteração desfeita é confirmada.  
  
- A modificação no designer foi criada no contexto de um <xref:System.ComponentModel.Design.DesignerTransaction> .  
  
- O designer opta por criar explicitamente unidades de desfazer usando a unidade de desfazer padrão fornecida por uma implementação <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> ou a implementação específica do Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> , que deriva de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> e também fornece uma implementação de <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> .  
  
## <a name="see-also"></a>Consulte Também  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Estendendo o suporte para tempo de design](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
