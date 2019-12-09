---
title: -ProjectConfig (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a33c7cbaef473e75631bb4ac6c0d217198cbf250
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662094"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Especifica uma configuração de build do projeto a ser aplicada ao compilar, limpar, recompilar ou implantar o projeto nomeado no argumento `/project`.

## <a name="syntax"></a>Sintaxe

```
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
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

- Deve ser usado com a opção `/project` como parte de um comando `devenv /build`, /`clean`, `/rebuild` ou `/deploy`.

- Coloque as cadeias de caracteres que incluem espaços entre aspas duplas.

- As informações de resumo para builds, incluindo erros, podem ser exibidas na janela **Comando** ou em qualquer arquivo de log especificado com a opção `/out`.

## <a name="example"></a>Exemplo
 Este exemplo compila o projeto `CSharpConsoleApp`, usando a configuração de build do projeto `Debug` na configuração de solução `Debug` de `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Veja também
 [Opções](../../ide/reference/devenv-command-line-switches.md) [de linha de comando do devenv/Project (devenv. exe)](../../ide/reference/project-devenv-exe.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md) [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md) [/Deploy (devenv. exe)](../../ide/reference/deploy-devenv-exe.md) [/out (devenv. exe](../../ide/reference/out-devenv-exe.md) )
