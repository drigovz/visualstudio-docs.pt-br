---
title: Campo m_children | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a681f3a58fddbb136383a1259aa5e4c0c3b96b69
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49289621"
---
# <a name="mchildren-field"></a>Campo m_children
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A lista de tarefas filho que estão registrados com essa tarefa.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib. dll)  
  
 Porque você não pode acessar esse membro interno do .NET Framework, a sintaxe a seguir é fornecida em comum Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Comentários  
 Enquanto a tarefa está em execução, somente o thread que executa a tarefa deve acessar essa matriz.  
  
 Se a tarefa for concluída, outros threads podem acessar este campo desde que eles não adiciona nada a ele ou remover nada dela.  
  
## <a name="see-also"></a>Consulte também  
 [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)

