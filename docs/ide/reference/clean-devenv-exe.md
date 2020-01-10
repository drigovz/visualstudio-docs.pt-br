---
title: -Clean (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- Clean Devenv switch
- /Clean Devenv switch
- Devenv, /Clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac184f25d79a47814fee52b99bce1cddce247fc5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75570460"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)

Limpa todos os arquivos intermediários e diretórios de saída.

## <a name="syntax"></a>Sintaxe

```shell
devenv SolutionName /Clean [Config [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Necessária. O caminho completo e o nome do arquivo de solução.

- *Config*

  Opcional. A configuração (por exemplo, `Debug` ou `Release`) para limpar os arquivos intermediários da solução nomeada em *SolutionName*. Se mais de uma plataforma de solução estiver disponível, também será preciso especificar a plataforma (por exemplo, `Debug|Win32`). Se esse argumento não for especificado ou for uma cadeia de caracteres vazia (`""`), a ferramenta usará a configuração ativa da solução.

- `/Project` *ProjName*

  Opcional. O caminho e o nome de um arquivo de projeto na solução. Você pode inserir o nome de exibição do projeto ou um caminho relativo da pasta *SolutionName* para o arquivo do projeto. Também é possível inserir o caminho completo e o nome do arquivo do projeto.

- `/ProjectConfig` *ProjConfigName*

  Opcional. O nome da configuração de build do projeto (por exemplo, `Debug` ou `Release`) a ser usado ao limpar o `/Project` nomeado. Se mais de uma plataforma de solução estiver disponível, também será preciso especificar a plataforma (por exemplo, `Debug|Win32`). Se essa opção for especificada, ela substituirá o argumento *Config*.

- `/Out` *NomeDoArquivoDeSaída*

  Opcional. O nome de um arquivo para o qual você deseja enviar a saída da ferramenta. Se o arquivo já existir, a ferramenta anexará a saída ao final do arquivo.

## <a name="remarks"></a>Comentários

Esta opção tem a mesma função que o comando de menu **Limpar Solução** dentro do IDE.

Coloque as cadeias de caracteres que incluem espaços entre aspas duplas.

As informações de resumo ao realizar a limpeza ou a compilação, incluindo os erros, podem ser exibidas na janela **Command** ou em qualquer arquivo de log especificado com a opção [/Out](out-devenv-exe.md).

Se a opção `/Project` não for especificada, a ação de limpeza será realizada em todos os projetos na solução, mesmo que o *FileName* tenha sido especificado como um arquivo de projeto.

## <a name="example"></a>Exemplo

O primeiro exemplo limpa a solução `MySolution`, usando a configuração padrão especificada no arquivo da solução.

O segundo exemplo limpa o projeto `CSharpWinApp`, usando a configuração de build do projeto `Debug` dentro de `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean

devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean "Debug" /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>Veja também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
