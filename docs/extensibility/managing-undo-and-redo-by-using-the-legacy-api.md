---
title: Gerenciamento de desfazer e refazer, usando a API herdada | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8a93b4fd12cd9a0bd2e5a5f3c70486e370545a9
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747643"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>Gerenciar desfazer e refazer, usando a API herdada
Editores devem oferecer suporte a operações de desfazer que permitem aos usuários reverter suas alterações recentes, ao modificar o código. A maioria dos editores implementados nos [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e o .NET Framework podem ter suporte de desfazer automaticamente fornecido pelo ambiente de desenvolvimento integrado (IDE).

## <a name="in-this-section"></a>Nesta seção
- [Como: Implementar o gerenciamento de desfazer](../extensibility/how-to-implement-undo-management.md) fornece a capacidade de desfazer para editores com único ou vários modos de exibição.

- [Como: Limpar a pilha de desfazer](../extensibility/how-to-clear-the-undo-stack.md) descreve como limpar uma pilha de desfazer.

- [Como: Use o gerenciamento de desfazer vinculado](../extensibility/how-to-use-linked-undo-management.md) Incorporates vinculado desfazer gerenciamento em seu editor.

## <a name="reference"></a>Referência
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> Fornece gerenciamento de desfazer para um editor que dá suporte a vários modos de exibição.
