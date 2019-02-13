---
title: -Log (devenv.exe)
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b2e11cb36176aec94528019cdd19bb5fa86c92b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907211"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Registra toda a atividade no arquivo de log para resolução de problemas. Este arquivo aparece depois de você chamar `devenv /log` pelo menos uma vez. Por padrão, o arquivo de log está localizado aqui:

**%APPDATA%\\Microsoft\\VisualStudio\\**\<Versão\>**\\ActivityLog.xml**

em que \<Versão\> é a versão do Visual Studio. No entanto, você pode especificar um caminho e um nome de arquivo diferentes.

## <a name="syntax"></a>Sintaxe

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Arguments

- *NameOfLogFile*

  Necessário. O caminho completo e o nome do arquivo de log em que será salvo.

## <a name="remarks"></a>Comentários

Essa opção deve aparecer no fim da linha de comando, depois de todas as outras opções.

O log é gravado somente nas instâncias do Visual Studio que você chamou com a opção `/Log`.

## <a name="example"></a>Exemplo

Este exemplo direciona o registro de log para o arquivo `MyVSLog.xml` no diretório base do usuário.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)