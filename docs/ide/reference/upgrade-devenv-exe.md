---
title: -Upgrade (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c106d05b81878c6d1d48f98a8c72358cfef3c6cf
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227454"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)

Atualiza o arquivo de solução e todos os seus arquivos de projeto, ou o arquivo de projeto especificado, para os formatos atuais do Visual Studio para esses arquivos.

## <a name="syntax"></a>Sintaxe

```shell
devenv {SolutionFile|ProjectFile} /Upgrade [/Out OutputFilename]
```

## <a name="arguments"></a>Arguments

- *SolutionFile*

  Necessário se você estiver atualizando toda uma solução e seus projetos. O caminho e o nome de um arquivo de solução. Você pode inserir apenas o nome do arquivo de solução, ou um caminho completo e o nome do arquivo de solução. A pasta ou o arquivo nomeado será criado, se ainda não existir.

- *ProjectFile*

  Necessário se você estiver atualizando um único projeto. O caminho e o nome de um arquivo de projeto na solução. Você pode inserir apenas o nome do arquivo de projeto, ou um caminho completo e o nome do arquivo de projeto. A pasta ou o arquivo nomeado será criado, se ainda não existir.

- `/Out` *OutputFilename*

  Opcional. O nome de um arquivo para o qual você deseja enviar a saída da ferramenta. Se o arquivo já existir, a ferramenta anexará a saída ao final do arquivo.

## <a name="remarks"></a>Comentários

Os backups são criados e copiados automaticamente para um diretório chamado Backup, que é criado no diretório atual.

É necessário fazer o check-out de projetos ou soluções controlados pelo código-fonte para que eles possam ser atualizados.

Usar a opção `/Upgrade` não inicia o Visual Studio. Os resultados da atualização podem ser vistos no Relatório de Atualização da linguagem de desenvolvimento da solução ou projeto. Nenhuma informação de erro ou de uso é retornada. Para saber mais sobre como atualizar projetos no Visual Studio, consulte [Portar, migrar e atualizar projetos do Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).

## <a name="example"></a>Exemplo

Este exemplo atualiza um arquivo de solução chamado "MyProject.sln".

```shell
devenv "%USERPROFILE%\source\repos\MyProject\MyProject.sln" /upgrade
```

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)