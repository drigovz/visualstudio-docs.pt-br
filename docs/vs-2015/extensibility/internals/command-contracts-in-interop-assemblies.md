---
title: Contratos de comando em assemblies de interoperabilidade | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 50d48d3a8ff55559cce1c3a40142e31b8eebd85f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195129"
---
# <a name="command-contracts-in-interop-assemblies"></a>Contratos de comando em assemblies de interoperabilidade
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O contrato básico para manipular comandos por meio da <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface é que o ambiente chama o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método para determinar se o comando tem suporte e, se houver suporte, para determinar seu estado e texto. Em seguida, o ambiente chama o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método para executar o comando.  
  
 O <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método é tratado de forma idêntica para todos os comandos. Uma comunicação adicional, se necessário (por exemplo, com listas suspensas), é gerenciada chamando o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> método com os parâmetros apropriados. A interpretação desses parâmetros depende do comando especificado.  
  
 Se o destino do comando retornar valores no parâmetro de saída, o chamador será sempre responsável por liberar todos os recursos que foram alocados. Como esse parâmetro é uma variante, limpar a variante libera os recursos.  
  
 Nos casos em que os comandos devem operar em uma janela de hierarquia, a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface deve ser usada. A <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interface tem um contrato semelhante com métodos semelhantes: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> .  
  
## <a name="see-also"></a>Consulte Também  
 [Como VSPackages adicionar elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Roteamento de comandos em VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Implementação](../../extensibility/internals/command-implementation.md)
