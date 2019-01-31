---
title: -Build (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 58e48676cb8719cca5da1989342642669c6565cd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54778478"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Compila uma solução usando um arquivo de configuração de solução especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]  
```  
  
## <a name="arguments"></a>Arguments  
 `SolutionName`  
 Necessário. O caminho completo e o nome do arquivo de solução.  
  
 `SolnConfigName`  
 Necessário. O nome da configuração de solução que será usada para compilar a solução nomeada no `SolutionName`.  
  
 /project `ProjName`  
 Opcional. O caminho e o nome de um arquivo de projeto na solução. É possível inserir um caminho relativo da pasta `SolutionName` para o arquivo de projeto ou o nome de exibição do projeto ou o caminho completo e o nome do arquivo de projeto.  
  
 /projectconfig `ProjConfigName`  
 Opcional. O nome de uma configuração de build de projeto a ser usada ao compilar o `/project` nomeado.  
  
## <a name="remarks"></a>Comentários  
 Essa opção executa a mesma função que o comando de menu **Compilar Solução** dentro do IDE (ambiente de desenvolvimento integrado).  
  
 Coloque as cadeias de caracteres que incluem espaços entre aspas duplas.  
  
 As informações de resumo para builds, incluindo erros, podem ser exibidas na janela **Comando** ou em qualquer arquivo de log especificado com a opção `/out`.  
  
 Esse comando compila somente projetos que foram alterados desde o último build. Para criar todos os projetos em uma solução, use [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo compila o projeto `CSharpConsoleApp`, usando a configuração de build do projeto `Debug` na configuração de solução `Debug` de `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilando e limpando projetos e soluções no Visual Studio](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
