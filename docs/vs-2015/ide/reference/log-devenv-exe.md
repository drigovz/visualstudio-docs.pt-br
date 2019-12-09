---
title: -Log (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f427edfe294605b7b2adcbb0889e48c4f37b6ba9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666839"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Registra toda a atividade no arquivo de log para resolução de problemas. Este arquivo aparece depois de você chamar `devenv /log` pelo menos uma vez. Por padrão, o arquivo de log é:

 *%APPDATA%* \Microsoft\VisualStudio\\*Version*\ActivityLog.xml

 em que *Versão* é a versão do Visual Studio. No entanto, você pode especificar um caminho e um nome de arquivo diferentes.

## <a name="syntax"></a>Sintaxe

```
Devenv /log Path\NameOfLogFile
```

## <a name="remarks"></a>Comentários
 Essa opção deve aparecer no fim da linha de comando, depois de todas as outras opções.

 O log é gravado em todas as instâncias do Visual Studio que você invocou com a opção /log. As instâncias de log do Visual Studio que você invocou sem a opção não são registradas.

## <a name="see-also"></a>Veja também
 [Opções de linha de comando devenv](../../ide/reference/devenv-command-line-switches.md)
