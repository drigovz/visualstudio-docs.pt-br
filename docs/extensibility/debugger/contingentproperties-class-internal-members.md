---
title: Classe ContingentProperties - membros internos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7b9775ed74e7ae81768f180e596f171b2c99cba
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344314"
---
# <a name="contingentproperties-class---internal-members"></a>Classe ContingentProperties - membros internos
Contém propriedades adicionais para um <xref:System.Threading.Tasks.Task> objeto.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Assembly:** mscorlib (em mscorlib. dll)

 Porque você não pode acessar esses membros internos do .NET Framework, a sintaxe a seguir é fornecida em comum Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxe

```csharp
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
- [Elementos internos de extensões paralelas para o .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)