---
title: Gerenciando a caixa de ferramentas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Toolbox [Visual Studio SDK], automatic tab selection
- Toolbox [Visual Studio SDK], managing
ms.assetid: 3b052047-f6db-46dd-b3bf-da1c348ee410
caps.latest.revision: 33
manager: jillfra
ms.openlocfilehash: 5eeb5d06b0e689391f450fec8744fa58a41f4508
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681537"
---
# <a name="managing-the-toolbox"></a>Gerenciando a caixa de ferramentas
O [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] permite que um VSPackage, como um editor ou designer, gerencie a associação e a aparência da **caixa de ferramentas**.  
  
 Além disso, a própria **caixa de ferramentas** pode ser gerenciada usando a automação. Para obter mais informações sobre como gerenciar uma caixa de ferramentas por meio de automação, consulte [como controlar a caixa de ferramentas](https://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599).  
  
## <a name="automatic-toolbox-tab-selection"></a>Seleção automática da guia caixa de ferramentas  
 Uma determinada guia ou categoria da **caixa de ferramentas** pode ser automaticamente ativada com base em qual editor ou designer está ativo no momento. Por exemplo, se um designer de formulários estiver ativado, talvez você queira que a guia **todos os Windows Forms** selecionada.  
  
 Esse suporte é limitado a editores e designers que exigem:  
  
1. A implementação de um objeto de fábrica para fornecer instâncias do editor ou designer. Para obter mais informações sobre como implementar um objeto de criação de designer ou editor, consulte [fábricas de editor](../extensibility/editor-factories.md).  
  
2. Registro da guia caixa de ferramentas que será ativada automaticamente se o editor ou o designer estiver presente.  
  
## <a name="controlling-the-toolbox"></a>Controlando a caixa de ferramentas  
 Complementar o suporte à automação, o [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] fornece as seguintes interfaces para fornecer VSPackages maior controle sobre como a **caixa de ferramentas** é gerenciada.  
  
|Interface|Descrição|  
|---------------|-----------------|  
|<xref:System.Drawing.Design.IToolboxService>|Permite que os aplicativos gerenciem, adicionem e removam <xref:System.Drawing.Design.ToolboxItem> objetos da **caixa de ferramentas**. Também habilita a configuração de categorias de aparência e **caixa de ferramentas** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2>|Permite que os aplicativos gerenciem, adicionem e removam controles de **caixa de ferramentas** baseados em ativos, bem como configurem categorias e aparência da **caixa de ferramentas** .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3>|Estende a funcionalidade encontrada no <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> fornecendo suporte completo para persistência e localização.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox4>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox5>||  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox6>||  
  
 Há vários pontos importantes a ter em mente ao trabalhar com essas interfaces:  
  
- <xref:System.Drawing.Design.IToolboxService> está disponível somente para VSPackages com base em estrutura de pacote gerenciado.  
  
- Os controles não podem ser adicionados diretamente à **caixa de ferramentas** usando <xref:System.Drawing.Design.IToolboxService> .  
  
- Um VSPackage deve ser usado <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> para adicionar controles ou hospedar o controle em um controle de wrapper que deriva de <xref:System.Windows.Forms.AxHost> .  
  
   O Visual Studio fornece a `Aximp.exe` ferramenta para automatizar a disposição de um controle ActiveX em um controle derivado de <xref:System.Windows.Forms.AxHost> . Para obter mais informações, consulte [Aximp.exe (Windows Forms importador de controle ActiveX)](https://msdn.microsoft.com/library/482c0d83-7144-4497-b626-87d2351b78d0).  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> são interfaces baseadas em com disponíveis por meio de assemblies de interoperabilidade.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> deriva de <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox> e implementa todos os seus métodos.  
  
   Os objetos obtêm apenas uma instância do <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> não deriva de <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> e não implementa seus métodos.  
  
   Os objetos que precisam de funcionalidade em ambas as interfaces devem obter instâncias de ambas as interfaces do ambiente.  
  
- Ao trabalhar com <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> , as informações sobre os nomes canônicos (não traduzidos) de guias são manipuladas pelos <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.GetIDOfTab%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3.SetIDOfTab%2A> métodos e.  
  
- Ao usar <xref:System.Drawing.Design.IToolboxService> o, cabe ao implementador gerenciar informações localizadas, como nomes de categorias.  
  
  Use o mecanismo de configurações para permitir que os usuários salvem as configurações de **caixa de ferramentas** acessadas por usuários no comando de **configurações de importação/exportação** , encontradas no menu **ferramentas** do IDE. Para obter mais informações sobre como usar configurações, consulte [estendendo configurações e opções de usuário](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Estendendo a caixa de ferramentas](../misc/extending-the-toolbox.md)