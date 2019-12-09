---
title: -Project (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- project Devenv switch (/project)
- Devenv, /project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f9c54691ed343493ef1e43798faf4d2ab6f60fb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662121"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Identifica um único projeto dentro da configuração da solução especificada para ser compilado, limpo, recompilado ou implantado.

## <a name="syntax"></a>Sintaxe

```
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName
[/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Arguments
 /Build compila o projeto especificado por `/project` `ProjName`.

 /Clean limpa todos os arquivos intermediários e diretórios de saída criados durante uma compilação.

 /Rebuild limpa então compila o projeto especificado por `/project` `ProjName`.

 /deploy especifica que o projeto seja implantado após uma compilação ou recompilação.

 `SolnConfigName` Necessário. O nome da configuração da solução que será aplicado à solução nomeada em `SolutionName`.

 `SolutionName` Necessário. O caminho completo e o nome do arquivo de solução.

 /project `ProjName` Opcional. O caminho e o nome de um arquivo de projeto na solução. É possível inserir um caminho relativo da pasta `SolutionName` para o arquivo de projeto ou o nome de exibição do projeto ou o caminho completo e o nome do arquivo de projeto.

 /projectconfig `ProjConfigName` Opcional. O nome de uma configuração de build do projeto a ser aplicado ao `/project` nomeado.

## <a name="remarks"></a>Comentários

- Parte de um comando `devenv /build`, /`clean`, `/rebuild` ou `/deploy` deve ser usada.

- Coloque as cadeias de caracteres que incluem espaços entre aspas duplas.

- As informações de resumo para builds, incluindo erros, podem ser exibidas na janela **Comando** ou em qualquer arquivo de log especificado com a opção `/out`.

## <a name="example"></a>Exemplo
 Este exemplo compila o projeto `CSharpConsoleApp`, usando a configuração de build do projeto `Debug` na configuração de solução `Debug` de `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Veja também
 [Opções](../../ide/reference/devenv-command-line-switches.md) [de linha de comando do devenv/ProjectConfig (devenv. exe)](../../ide/reference/projectconfig-devenv-exe.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md) [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md) [/Deploy (devenv. exe)](../../ide/reference/deploy-devenv-exe.md) [/out (devenv. exe](../../ide/reference/out-devenv-exe.md) )
