---
title: -Upgrade (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 24bb6160f9895f129c4d7d36c2b0aa8a56ca282a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657908"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Atualiza o arquivo de solução e todos os seus arquivos de projeto, ou o arquivo de projeto especificado, para os formatos [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] atuais para esses arquivos.

## <a name="syntax"></a>Sintaxe

```
devenv SolutionFile | ProjectFile /upgrade
```

## <a name="arguments"></a>Arguments
 `SolutionFile` Obrigatório se você estiver atualizando uma solução inteira e os projetos dela. O caminho e o nome de um arquivo de solução. Você pode inserir apenas o nome do arquivo de solução, ou um caminho completo e o nome do arquivo de solução. Se a pasta ou o arquivo nomeado ainda não existir, ele será criado.

 `ProjectFile` Obrigatório se você estiver atualizando um único projeto. O caminho e o nome de um arquivo de projeto na solução. Você pode inserir apenas o nome do arquivo de projeto, ou um caminho completo e o nome do arquivo de projeto. Se a pasta ou o arquivo nomeado ainda não existir, ele será criado.

## <a name="remarks"></a>Comentários
 Backups são criados e copiados automaticamente para um diretório chamado Backup, que é criado no diretório atual.

 É necessário fazer o check-out de projetos ou soluções controlados pelo código-fonte para que eles possam ser atualizados.

 Usar a opção `/upgrade` não inicia [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Os resultados da atualização podem ser vistos no Relatório de Atualização da linguagem de desenvolvimento da solução ou projeto. Nenhuma informação de erro ou de uso é retornada. Para obter mais informações sobre como atualizar projetos em [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], consulte [Como solucionar problemas de atualizações de projeto do Visual Studio malsucedidas](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md).

## <a name="example"></a>Exemplo
 Este exemplo atualiza um arquivo de solução chamado "MyProject.sln" na pasta padrão para soluções [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

```
devenv "MyProject.sln" /upgrade
```

## <a name="see-also"></a>Veja também
 [Como solucionar problemas de opções de linha](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md) [de Comando Devenv de atualizações de projetos do Visual Studio malsucedidas](../../ide/reference/devenv-command-line-switches.md)
