---
title: Gerenciando desfazer e refazer usando a API herdada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c2133c75b32e56c1a054740bd829bd04cac97cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194364"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Gerenciamento de desfazer e refazer usando a API herdada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os editores devem oferecer suporte a operações de desfazer que permitem que os usuários revertam suas alterações recentes quando modificam o código. A maioria dos editores implementados no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e no [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] pode ter o suporte de desfazer automaticamente fornecido pelo IDE (ambiente de desenvolvimento integrado).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como implementar o gerenciamento de desfazer](../extensibility/how-to-implement-undo-management.md)  
 Fornece funcionalidade de desfazer para editores com uma ou várias exibições.  
  
 [Como limpar a pilha de desfazer](../extensibility/how-to-clear-the-undo-stack.md)  
 Descreve como limpar uma pilha de desfazer.  
  
 [Como usar o gerenciamento de desfazer vinculado](../extensibility/how-to-use-linked-undo-management.md)  
 Incorpora o gerenciamento de desfazer vinculado ao seu editor.  
  
## <a name="reference"></a>Referência  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Fornece gerenciamento de desfazer para um editor que dá suporte a várias exibições.  
  
## <a name="related-sections"></a>Seções relacionadas
