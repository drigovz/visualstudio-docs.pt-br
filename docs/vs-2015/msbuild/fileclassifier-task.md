---
title: Tarefa FileClassifier | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- classifying a resource set to embed in an assembly [WPF MSBuild]
- non-localizable resources [WPF MSBuild], classifying to embed in an assembly
- FileClassifier task [WPF MSBuild]
ms.assetid: 14e03310-fcc0-4bb2-a84d-cda12be66367
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2077b1df6d6362c924527e296d36c041e7bd9929
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693792"
---
# <a name="fileclassifier-task"></a>Tarefa FileClassifier
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O <xref:Microsoft.Build.Tasks.Windows.FileClassifier> classifica um conjunto de recursos de origem uma vez que eles serão inseridos em um assembly. Se um recurso não for localizável, ele será inserido no assembly principal do aplicativo; caso contrário, ele será inserido em um assembly satélite.  
  
## <a name="task-parameters"></a>Parâmetros da tarefa  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`CLREmbeddedResource`|Não utilizado.|  
|`CLRResourceFiles`|Não utilizado.|  
|`CLRSatelliteEmbeddedResource`|Não utilizado.|  
|`Culture`|Parâmetro de **cadeia de caracteres** opcional.<br /><br /> Especifica a cultura para o build. Esse valor pode ser **nulo** se o build não for localizável. Se for **nulo**, o valor padrão será o valor em letras minúsculas que **CultureInfo.InvariantCulture** retorna.|  
|`MainEmbeddedFiles`|Parâmetro de saída opcional **ITaskItem[]**.<br /><br /> Especifica os recursos não localizáveis que são inseridos no assembly principal.|  
|`OutputType`|Parâmetro obrigatório **String**.<br /><br /> Especifica o tipo de arquivo no qual inserir os arquivos de origem especificados. Os valores válidos são **exe**, **winexe** ou **library**.|  
|`SatelliteEmbeddedFiles`|Parâmetro de saída opcional **ITaskItem[]**.<br /><br /> Especifica os arquivos localizáveis que são inseridos no assembly satélite para a cultura especificada pelo parâmetro **Culture**.|  
|`SourceFiles`|Parâmetro **ITaskItem []** necessário.<br /><br /> Especifica a lista de arquivos a classificar.|  
  
## <a name="remarks"></a>Comentários  
 Se o parâmetro **Culture** não é definido, todos os recursos especificados usando o parâmetro **SourceFiles** não são localizáveis; caso contrário, eles são localizáveis, a menos que eles estejam associados com um atributo **Localizable** definido como **false**.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir classifica um único arquivo de origem como um recurso e, em seguida, insere-o em um assembly satélite para a cultura Francês canadense (fr-CA).  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask  
    TaskName="Microsoft.Build.Tasks.Windows.FileClassifier"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <ItemGroup>  
    <Resource Include="Resource1.bmp" />  
  </ItemGroup>  
  <Target Name="FileClassifierTask">  
    <FileClassifier  
      SourceFiles="Resource1.bmp"  
      Culture="fr-CA"  
      OutputType="exe" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Referência do MSBuild do WPF](../msbuild/wpf-msbuild-reference.md)   
 [Referência de tarefa](../msbuild/wpf-msbuild-task-reference.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Referência de tarefa](../msbuild/msbuild-task-reference.md)   
 [Criando um aplicativo WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
