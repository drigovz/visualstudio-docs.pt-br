---
title: Algoritmo de Roteamento de Comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af8d3e53e09214ce36a80ca18856085dfb2bb746
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709543"
---
# <a name="command-routing-algorithm"></a>Algoritmo de roteamento de comando
No Visual Studio, os comandos são manuseados por vários componentes diferentes. Os comandos são roteados do contexto mais interno, que se baseia na seleção atual, para o contexto mais externo (também conhecido como global). Para obter mais informações, consulte [disponibilidade de comando](../../extensibility/internals/command-availability.md).

## <a name="order-of-command-resolution"></a>Ordem de resolução de comando
 Os comandos são transmitidos pelos seguintes níveis de contexto de comando:

1. Complementos: O ambiente primeiro oferece o comando para quaisquer complementos que estejam presentes.

2. Comandos prioritários: Estes comandos <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>são registrados usando . Eles são chamados para cada comando no Visual Studio, e são chamados na ordem em que foram registrados.

3. Comandos do menu de contexto: Um comando localizado em um menu de contexto é oferecido primeiro ao destino de comando que é fornecido ao menu de contexto e, depois disso, ao roteamento típico.

4. Metas de comando de conjunto de ferramentas: Esses <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>alvos de comando são registrados quando você chama . O `pCmdTarget` parâmetro pode `null`ser. Se não `null`for, então este destino de comando é usado para atualizar quaisquer comandos localizados na barra de ferramentas que você está configurando. Se o shell estiver configurando sua barra de ferramentas, ela passa o quadro da janela como o `pCmdTarget` de modo que todas as atualizações para os comandos em sua barra de ferramentas fluam através do quadro da janela, mesmo quando não está em foco.

5. Janela da ferramenta: O Tool <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Windows, que normalmente implementa a interface, também deve implementar a interface para que o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Visual Studio possa obter o alvo de comando quando a janela da ferramenta estiver na janela ativa. No entanto, se a janela da ferramenta que tem foco <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> for a janela **Projeto,** então o comando será encaminhado para a interface que é o pai comum dos itens selecionados. Se essa seleção abranger vários projetos, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> o comando será encaminhado para a hierarquia. A <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> contém <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> os métodos análogos aos comandos correspondentes na <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface.

6. Janela do documento: Se `RouteToDocs` o comando tiver o sinalizador definido em seu arquivo *.vsct,* o Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> procurará um destino de comando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> no objeto <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> de exibição de documento, que é uma instância de uma interface ou uma instância de um objeto de documento (tipicamente uma interface ou uma interface). Se o objeto de exibição de documento não suportar <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> o comando, o Visual Studio encaminha o comando para a interface que é retornada. (Esta é uma interface opcional para objetos de dados de documentos.)

7. Hierarquia atual: A hierarquia atual pode ser o projeto que possui a janela de documento ativa ou a hierarquia selecionada no **Solution Explorer**. O Visual Studio <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> procura a interface que é implementada na hierarquia atual ou ativa. A hierarquia deve suportar comandos válidos sempre que a hierarquia estiver ativa, mesmo que uma janela de documento de um item de projeto tenha foco. No entanto, os comandos que se aplicam apenas <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> quando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> **Solution Explorer** tem foco devem ser suportados usando a interface e seus métodos.

     **Os**comandos Cut , **Copy**, **Paste**, **Delete,** **Rename**, **Enter**e **DoubleClick** requerem um manuseio especial. Para obter informações sobre como lidar com **comandos** <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> Excluir e **Remover** em hierarquias, consulte a interface.

8. Global: Se um comando não tiver sido manipulado pelos contextos mencionados anteriormente, o Visual Studio tentará encaminhá-lo para o VSPackage que possui um comando que implementa a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Se o VSPackage ainda não tiver sido carregado, ele não <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> será carregado quando o Visual Studio chamar o método. O VSPackage só é <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> carregado quando o método é chamado.

## <a name="see-also"></a>Confira também
- [Design de comando](../../extensibility/internals/command-design.md)
