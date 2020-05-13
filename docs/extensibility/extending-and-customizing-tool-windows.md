---
title: Ampliação e Personalização de ferramentas Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76c094ec73a69baa46a5e8313dd26febd57e5887
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711812"
---
# <a name="extend-and-customize-tool-windows"></a>Estender e personalizar janelas de ferramentas
O Visual Studio fornece vários tipos diferentes de janelas, como janelas de ferramentas, janelas de documentos e janelas de diálogo. Outras janelas, como a janela **Propriedades,** a janela **Saída** e a janela **Lista de tarefas,** são tipos de janelas de ferramentas.

## <a name="tool-windows"></a>Janelas da ferramenta
 As janelas de ferramentas do Visual Studio geralmente são janelas somente leitura que não são baseadas em arquivos. Neste, eles diferem das janelas de documentos, que exibem arquivos no modo de leitura e gravação. A **caixa de ferramentas,** **o Solution Explorer,** a janela **Propriedades** e o Navegador **da Web** são exemplos de janelas de ferramentas.

 Para descobrir como criar uma janela de ferramenta simples, consulte [Adicionar uma janela de ferramenta](../extensibility/adding-a-tool-window.md).

 Para registrar uma janela de ferramenta com o Visual Studio, consulte [Registrar uma janela de ferramenta](../extensibility/registering-a-tool-window.md).

 As janelas de ferramenta são de instância única por padrão, o que significa que apenas uma instância da janela da ferramenta pode ser aberta por vez. Depois que uma janela de ferramenta de instância única é aberta, ela permanece aberta até que o IDE seja fechado. Quando você fecha uma janela de ferramenta de instância única, apenas sua visibilidade muda. Você também pode criar janelas de ferramentas de várias instâncias, de tal forma que várias instâncias da janela podem ser abertas simultaneamente. Consulte [Criar uma janela de ferramenta de várias instâncias](../extensibility/creating-a-multi-instance-tool-window.md) para obter mais informações.

 As janelas de ferramentas podem ser *dinâmicas,* o que significa que elas são visíveis sempre que seu contexto de interface do usuário relacionado se aplica. O uso da visibilidade automática pode reduzir a desordem das janelas no IDE. Para obter mais informações, consulte [Abrir uma janela dinâmica de ferramentas](../extensibility/opening-a-dynamic-tool-window.md).

 As janelas da ferramenta podem ser encaixadas, flutuantes ou guiadas no quadro do documento. A moldura da janela da ferramenta é fornecida pelo IDE e é usada para controlar o tamanho, localização, estado de acoplamento e outras propriedades persistentes. O painel da janela da ferramenta exibe o conteúdo. O tamanho e o local padrão só se aplicam quando a janela da ferramenta é aberta pela primeira vez; depois disso, o estado da janela da ferramenta é persistido.

 Os painéis de janela da ferramenta podem hospedar controles do usuário WPF e barras de ferramentas de suporte. Você pode substituir <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> a propriedade para devolver a alça do controle hospedado.

 Você pode adicionar muitos recursos diferentes às janelas de ferramentas. Por exemplo, você pode adicionar uma barra de ferramentas: [Adicione uma barra de ferramentas a uma janela de ferramenta](../extensibility/adding-a-toolbar-to-a-tool-window.md) ou a um menu de atalho: Adicione um menu de atalho em uma janela de [ferramenta](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Você pode adicionar um controle de pesquisa que permite pesquisar itens dentro da janela da ferramenta: [Adicione pesquisa a uma janela de ferramenta](../extensibility/adding-search-to-a-tool-window.md).

 Você pode se inscrever em eventos de janela de ferramentas: [Inscreva-se em um evento](../extensibility/subscribing-to-an-event.md).

## <a name="extend-existing-tool-windows"></a>Estender as janelas de ferramentas existentes
 Você pode adicionar informações sobre a janela da ferramenta a uma nova página **de Opções** e uma nova configuração na página **Propriedades,** escrever nas janelas **Lista de tarefas** e **saída.** Para obter mais informações, consulte [Estender as janelas Propriedades, Lista de Tarefas, Saída e Opções](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).

## <a name="modal-dialog-boxes"></a>Caixas de diálogo modais
 Em uma extensão do Visual Studio, você deve <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>criar caixas de diálogo modais, derivando-as, o que permite controlá-las e o resto da ui. Para obter mais informações, consulte [Criar e gerenciar caixas de diálogo modais](../extensibility/creating-and-managing-modal-dialog-boxes.md).

## <a name="see-also"></a>Confira também
- [Crie uma extensão com uma janela de ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md)
- [Ampliar projetos](../extensibility/extending-projects.md)
- [Ampliar soluções](../extensibility/extending-solutions.md)
