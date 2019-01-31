---
title: 'Como: Compilar destinos específicos em soluções usando o MSBuild.exe | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 26e1670d5e67581ee61ec5517bedc4e8cfce1755
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766234"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Como: Compilar destinos específicos em soluções usando o MSBuild.exe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Você pode usar MSBuild.exe para compilar destinos específicos de projetos específicos em uma solução.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>Para criar um destino específico de um projeto específico em uma solução  
  
1.  Na linha de comando, digite `MSBuild.exe <SolutionName>.sln`, em que `<SolutionName>` corresponde ao nome de arquivo da solução que contém o destino que você deseja executar.  
  
2.  Especifique o destino após o comutador **/t** no formato *ProjectName*:*TargetName*.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir executa o destino `Rebuild` do projeto `NotInSlnFolder` e, em seguida, executa o destino `Clean` do projeto `InSolutionFolder`, que está localizado na pasta da solução `NewFolder`.  
  
```  
msbuild SlnFolders.sln /t:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [ MSBuild](msbuild.md)  
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)
