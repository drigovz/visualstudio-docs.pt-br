---
title: Classe Propriedades Contingentes - Membros Internos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6441cafcc34a06464061b41691ea5faa32fc359
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739107"
---
# <a name="contingentproperties-class---internal-members"></a>Classe ContingentProperties - membros internos
Contém propriedades adicionais para um <xref:System.Threading.Tasks.Task> objeto.

 **Espaço de nome:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montagem:** mscorlib (in mscorlib.dll)

 Como você não pode acessar esses membros internos do Quadro .NET, a seguinte sintaxe é fornecida na Linguagem Intermediária Comum (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>Membros

### <a name="fields"></a>Campos

|Nome|Descrição|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|A lista de tarefas infantis registradas nesta tarefa.|

## <a name="remarks"></a>Comentários
 O Quadro .NET inicializa os campos desta classe somente quando necessário.

## <a name="see-also"></a>Confira também
- [Internos de extensão paralelas para o Quadro .NET](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
