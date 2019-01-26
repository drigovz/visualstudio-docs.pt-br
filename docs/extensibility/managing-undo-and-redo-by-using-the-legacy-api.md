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
ms.openlocfilehash: c43dc4892f1cf2a938a4ed29fc68bc55e99cc05e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948122"
---
# <a name="manage-undo-and-redo-by-using-the-legacy-api"></a>Gerenciar desfazer e refazer, usando a API herdada
Editores devem oferecer suporte a operações de desfazer que permitem aos usuários reverter suas alterações recentes, ao modificar o código. A maioria dos editores implementados nos [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] pode ter suporte de desfazer automaticamente fornecido pelo ambiente de desenvolvimento integrado (IDE).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Implementar o gerenciamento de desfazer](../extensibility/how-to-implement-undo-management.md)  
 Fornece a capacidade de desfazer para editores com único ou vários modos de exibição.  
  
 [Como: Limpar a pilha de desfazer](../extensibility/how-to-clear-the-undo-stack.md)  
 Descreve como limpar uma pilha de desfazer.  
  
 [Como: Use o gerenciamento de desfazer vinculado](../extensibility/how-to-use-linked-undo-management.md)  
 Incorpora o gerenciamento de desfazer vinculado em seu editor.  
  
## <a name="reference"></a>Referência  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Fornece gerenciamento de desfazer para um editor que dá suporte a vários modos de exibição.  
