---
title: Gerenciamento de desfazer e refazer, usando a API herdada | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: adf6a2405ae3d3408f9cf04199ba05dff9232326
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856435"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>Gerenciar desfazer e refazer, usando a API herdada
Editores devem oferecer suporte a operações de desfazer que permitem aos usuários reverter suas alterações recentes, ao modificar o código. A maioria dos editores implementados nos [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] pode ter suporte de desfazer automaticamente fornecido pelo ambiente de desenvolvimento integrado (IDE).

## <a name="in-this-section"></a>Nesta seção
- [Como: Implementar o gerenciamento de desfazer](../extensibility/how-to-implement-undo-management.md) fornece a capacidade de desfazer para editores com único ou vários modos de exibição.

- [Como: Limpar a pilha de desfazer](../extensibility/how-to-clear-the-undo-stack.md) descreve como limpar uma pilha de desfazer.

- [Como: Use o gerenciamento de desfazer vinculado](../extensibility/how-to-use-linked-undo-management.md) Incorporates vinculado desfazer gerenciamento em seu editor.

## <a name="reference"></a>Referência
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> Fornece gerenciamento de desfazer para um editor que dá suporte a vários modos de exibição.
