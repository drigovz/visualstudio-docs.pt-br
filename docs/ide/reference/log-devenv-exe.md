---
title: -Log (devenv.exe)
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 008e7ca15595db249c05485f0d9e8f8b1277993e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595456"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Registra toda a atividade no arquivo de log para resolução de problemas. Este arquivo aparece depois de você chamar `devenv /log` pelo menos uma vez. Por padrão, o arquivo de log está localizado aqui:

**%APPDATA%\\\\Microsoft\\VisualStudio**\<Versão\>**\\ActivityLog.xml**

em que \<Versão\> é a versão do Visual Studio. No entanto, você pode especificar um caminho e um nome de arquivo diferentes.

## <a name="syntax"></a>Sintaxe

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Argumentos

- *NameOfLogFile*

  Obrigatórios. O caminho completo e o nome do arquivo de log em que será salvo.

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
