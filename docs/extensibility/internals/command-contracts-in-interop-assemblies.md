---
title: Contratos de Comando em Montagens Interop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f20a4f479d62cd1b64c3b13ff6e1a949656a668
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709681"
---
# <a name="command-contracts-in-interop-assemblies"></a>Contratos de comando em assembléias interop
O contrato básico para manusear comandos através <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> da interface é que o ambiente chama o método para determinar se o comando é suportado e, se é suportado, para determinar seu estado e texto. Em seguida, o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> ambiente chama o método para executar o comando.

 O <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método é tratado de forma idêntica para todos os comandos. A comunicação adicional, se necessária (por exemplo, com listas <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> paradas), é gerenciada ligando para o método com parâmetros apropriados. A interpretação desses parâmetros depende do comando especificado.

 Se o destino de comando retornar valores no parâmetro de saída, o chamador é sempre responsável por liberar todos os recursos que foram alocados. Como este parâmetro é uma variante, limpar a variante libera os recursos.

 Nos casos em que os comandos devem <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> operar dentro de uma janela de hierarquia, a interface deve ser usada. A <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface tem um contrato semelhante <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>com métodos semelhantes: e .

## <a name="see-also"></a>Confira também
- [Como o VSPackages adiciona elementos de interface de usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Roteamento de comando em VSPacotes](../../extensibility/internals/command-routing-in-vspackages.md)
- [Implementação de comando](../../extensibility/internals/command-implementation.md)
