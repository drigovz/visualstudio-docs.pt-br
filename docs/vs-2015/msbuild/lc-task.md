---
title: Tarefa LC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#LC
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, LC task
- LC task [MSBuild]
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6470125656debf420990ed9b471a5303f66d5712
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59654904"
---
# <a name="lc-task"></a>Tarefa LC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Encapsula LC.exe, que gera um arquivo .license de um arquivo .licx. Para obter mais informações sobre LC.exe, consulte [Lc.exe (Compilador de Licença)](http://msdn.microsoft.com/library/2de803b8-495e-4982-b209-19a72aba0460).  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `LC`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`LicenseTarget`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> obrigatório.<br /><br /> Especifica o executável para o qual os arquivos .licenses são gerados.|  
|`NoLogo`|Parâmetro `Boolean` opcional.<br /><br /> Suprime a exibição do banner de inicialização da Microsoft.|  
|`OutputDirectory`|Parâmetro `String` opcional.<br /><br /> Especifica o diretório no qual os arquivos .licenses de saída devem ser colocados.|  
|`OutputLicense`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica o nome do arquivo .licenses. Se você não especificar um nome, o nome do arquivo .licx será usado e o arquivo .licenses será colocado no diretório contendo o arquivo .licx.|  
|`ReferencedAssemblies`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica os componentes referenciados a carregar ao gerar o arquivo .license.|  
|`SdkToolsPath`|Parâmetro `String` opcional.<br /><br /> Especifica o caminho para as ferramentas do SDK, por exemplo, resgen.exe.|  
|`Sources`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica os itens contendo os componentes licenciados para incluir no arquivo .licenses. Para obter mais informações, consulte a documentação da opção `/complist` em [Lc.exe (Compilador de Licença)](http://msdn.microsoft.com/library/2de803b8-495e-4982-b209-19a72aba0460).|  
  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.ToolTask>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a tarefa `LC` para compilar licenças.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
<!-- Item declarations, etc -->  
  
    <Target Name="CompileLicenses">  
        <LC  
            Sources="@(LicxFile)"  
            LicenseTarget="$(TargetFileName)"  
            OutputDirectory="$(IntermediateOutputPath)"  
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"  
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">  
  
            <Output  
                TaskParameter="OutputLicenses"  
                ItemName="CompiledLicenseFile"/>  
        </LC>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
