---
title: Estendendo e personalizando janelas de ferramentas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b232fa1275bce453e3b32cea6a5ff37fdd501c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204539"
---
# <a name="extending-and-customizing-tool-windows"></a>Estendendo e personalizando as janelas de ferramentas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O Visual Studio fornece vários tipos diferentes de janelas, por exemplo, janelas de ferramentas, janelas de documentos e janelas de diálogo. Outras janelas, como a janela Propriedades, a janela de saída e a janela de Lista de Tarefas, são tipos de janelas de ferramentas.  
  
## <a name="tool-windows"></a>Janelas de ferramentas  
 As janelas de ferramentas do Visual Studio geralmente são janelas somente leitura que não são baseadas em arquivo. Nessas diferem das janelas de documentos, que exibem arquivos no modo de leitura/gravação. A **caixa de ferramentas**, **Gerenciador de soluções**, janela **Propriedades** e **navegador da Web** são exemplos de janelas de ferramentas.  
  
 Para descobrir como criar uma janela de ferramenta simples, consulte [adicionando uma janela de ferramentas](../extensibility/adding-a-tool-window.md).  
  
 Para registrar uma janela de ferramentas com o Visual Studio, consulte [registrando uma janela de ferramentas](../extensibility/registering-a-tool-window.md).  
  
 As janelas de ferramentas são de instância única por padrão, o que significa que apenas uma instância da janela de ferramentas pode ser aberta por vez. Depois que uma janela de ferramenta de instância única é aberta, ela permanece aberta até que o IDE seja fechado. Quando você fecha uma janela de ferramenta de instância única, apenas sua visibilidade é alterada. Você também pode criar janelas de ferramentas de várias instâncias, de modo que várias instâncias da janela possam ser abertas simultaneamente. Consulte [criando uma janela de ferramentas de várias instâncias](../extensibility/creating-a-multi-instance-tool-window.md) para obter mais informações.  
  
 As janelas de ferramentas podem ser *dinâmicas*, o que significa que elas ficam visíveis sempre que seu contexto de interface do usuário relacionado se aplica. O uso da visibilidade automática pode reduzir a desordem das janelas no IDE. Para obter mais informações, consulte [abrindo uma janela de ferramenta dinâmica](../extensibility/opening-a-dynamic-tool-window.md).  
  
 As janelas de ferramentas podem ser encaixadas, flutuantes ou tabuladas no quadro do documento. O quadro da janela de ferramentas é fornecido pelo IDE e é usado para controlar o tamanho, o local, o estado de encaixe e outras propriedades persistentes. O painel da janela de ferramentas exibe o conteúdo. O tamanho e o local padrão se aplicam somente quando a janela de ferramentas é aberta pela primeira vez; Depois disso, o estado da janela da ferramenta é persistido.  
  
 Os painéis da janela de ferramentas podem hospedar controles de usuário do WPF e barras de ferramentas de suporte. Você pode substituir a <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> propriedade para retornar o identificador do controle hospedado.  
  
 Você pode adicionar vários recursos diferentes às janelas de ferramentas. Por exemplo, você pode adicionar uma barra de ferramentas: [Adicionar uma barra de ferramentas a uma janela de ferramentas](../extensibility/adding-a-toolbar-to-a-tool-window.md) ou a um menu de atalho: [Adicionar um menu de atalho em uma janela de ferramentas](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Você pode adicionar um controle de pesquisa que permite pesquisar itens dentro de sua janela de ferramentas: [adicionando a pesquisa a uma janela de ferramentas](../extensibility/adding-search-to-a-tool-window.md).  
  
 Você pode assinar eventos de janela de ferramentas: [inscrevendo-se em um evento](../extensibility/subscribing-to-an-event.md).  
  
## <a name="extending-existing-tool-windows"></a>Estendendo janelas de ferramentas existentes  
 Você pode adicionar informações sobre a janela de ferramentas a uma nova página **Opções** e uma nova configuração na página **Propriedades** , gravar nas janelas **lista de tarefas** e **saída** . Para obter mais informações, consulte [estendendo as janelas Propriedades, lista de tarefas, saída e opções](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) e [estendendo as janelas Propriedades, lista de tarefas, saída e opções](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## <a name="modal-dialog-boxes"></a>Caixas de diálogo modais  
 Em uma extensão do Visual Studio, você deve criar caixas de diálogo modais derivando-as de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName> , o que permite controlá-las e o restante da interface do usuário. Para obter mais informações, consulte . [Criando e gerenciando caixas de diálogo modais](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Criar uma extensão com uma janela de ferramentas](../extensibility/creating-an-extension-with-a-tool-window.md)
