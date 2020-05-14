---
title: Comandos e menus que usam montagens interop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6c381abe9b4c6ea2a58342e185d7427fa56a180
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709482"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Comandos e menus que usam conjuntos Interop
Um VSPackage que implementa comandos de menu e barra de ferramentas usando conjuntos Interop deve:

- Informe [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado (IDE) sobre os comandos que suporta e se eles estão habilitados atualmente.

- Aderir às regras (contrato) para manusear comandos.

- Implemente explicitamente o manuseio de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> comando usando a interface ou a interface.

  A seção a seguir descreve como fazer essas tarefas.

## <a name="in-this-section"></a>Nesta seção
- [Determine o status do comando usando conjuntos Interop](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 Descreve como um VSPackage notifica o IDE sobre quais comandos ele suporta e se eles estão habilitados no momento.

- [Contratos de comando em assembléias interop](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Fornece uma definição do contrato de comando básico usado por todos os VSPackages implementando comandos usando conjuntos Interop.

- [Implementação de comando](../../extensibility/internals/command-implementation.md)

 Fornece uma visão geral de como um VSPackage implementa um comando.

- [Registre os manipuladores de comando de montagem Interop](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 Descreve as entradas de registro necessárias para notificar o IDE de que um VSPackage fornece um manipulador de comando.

## <a name="related-sections"></a>Seções relacionadas
- [Disponibilidade de comando](../../extensibility/internals/command-availability.md)

 Descreve critérios usados pelo IDE para determinar quais comandos VSPackage estão disponíveis e qual objeto os lida.

- [Como o VSPackages adiciona elementos de interface de usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Fornece detalhes sobre como criar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] uma ui que usa suporte a comandos.

- [Roteamento de comando em VSPacotes](../../extensibility/internals/command-routing-in-vspackages.md)

 Uma visão geral do processo usado para relacionar um objeto com a solicitação de comando correta.
