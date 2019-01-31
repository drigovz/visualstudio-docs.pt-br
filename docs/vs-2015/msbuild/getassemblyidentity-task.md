---
title: Tarefa GetAssemblyIdentity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetAssemblyIdentity
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GetAssemblyIdentity task
- GetAssemblyIdentity task [MSBuild]
ms.assetid: a977e072-37ad-4941-84a6-32a4483be55d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b91510d5b9a896c25c8c96f75767cf8e04183973
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790120"
---
# <a name="getassemblyidentity-task"></a>Tarefa GetAssemblyIdentity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Recupera as identidades do assembly dos arquivos especificados e gera como saída as informações de identidade.  
  
## <a name="task-parameters"></a>Parâmetros da tarefa  
 A tabela a seguir descreve os parâmetros da tarefa `GetAssemblyIdentity`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`Assemblies`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém as identidades de assembly recuperadas.|  
|`AssemblyFiles`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica os arquivos dos quais recuperar identidades.|  
  
## <a name="remarks"></a>Comentários  
 Os itens gerados como saída pelo parâmetro `Assemblies` contêm entradas de metadados do item chamadas `Version`, `PublicKeyToken` e `Culture`.  
  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir recupera a identidade dos arquivos especificados no item `MyAssemblies` e, em seguida, os gera como saída no item `MyAssemblyIdentities`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="File1.dll;File2.dll" />  
    </ItemGroup>  
  
    <Target Name="RetrieveIdentities>  
        <GetAssemblyIdentity  
            AssemblyFiles="@(MyAssemblies)"  
            <Output  
                TaskParameter="Assemblies"  
                ItemName="MyAssemblyIdentities"  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
