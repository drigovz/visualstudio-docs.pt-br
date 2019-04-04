---
title: Classe ContingentProperties - membros internos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f6778aef90361a7751ccd744fcf93822f8f97db
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922602"
---
# <a name="contingentproperties-class---internal-members"></a>Classe ContingentProperties – membros internos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Contém propriedades adicionais para um <xref:System.Threading.Tasks.Task> objeto.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib (em mscorlib. dll)  
  
 Porque você não pode acessar esses membros internos do .NET Framework, a sintaxe a seguir é fornecida em comum Intermediate Language (CIL).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## <a name="members"></a>Membros  
  
### <a name="fields"></a>Campos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[m_children](../../extensibility/debugger/m-children-field.md)|A lista de tarefas filho que estão registrados com essa tarefa.|  
  
## <a name="remarks"></a>Comentários  
 O .NET Framework inicializa os campos dessa classe somente quando eles forem necessários.  
  
## <a name="see-also"></a>Consulte também  
 [Elementos internos de extensões paralelas para o .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
