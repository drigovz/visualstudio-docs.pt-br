---
title: -Log (devenv.exe)
description: Saiba como usar a opção de linha de comando log devenv para registrar em log todas as atividades no arquivo de log para solução de problemas.
ms.custom: SEO-VS-2020
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a7a4f8f3fc7fe0e0f8b7ff6bd460ea2efd8192d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919400"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Registra toda a atividade no arquivo de log para resolução de problemas. Este arquivo aparece depois de você chamar `devenv /log` pelo menos uma vez. Por padrão, o arquivo de log está localizado aqui:

**% AppData% \\ActivityLog.xmldo Microsoft \\ VisualStudio \\** \<Version\> **\\**

em que \<Version\> é a versão do Visual Studio. No entanto, você pode especificar um caminho e um nome de arquivo diferentes.

## <a name="syntax"></a>Sintaxe

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Argumentos

- *NameOfLogFile*

  Obrigatório. O caminho completo e o nome do arquivo de log em que será salvo.

## <a name="remarks"></a>Comentários

Essa opção deve aparecer no fim da linha de comando, depois de todas as outras opções.

O log é gravado somente nas instâncias do Visual Studio que você chamou com a opção `/Log`.

## <a name="example"></a>Exemplo

Este exemplo direciona o registro de log para o arquivo `MyVSLog.xml` no diretório base do usuário.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Confira também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
