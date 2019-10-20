---
title: -SafeMode (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: abaeded184db78085a9629da0e763b2f76dbd328
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655509"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Inicia o Visual Studio no modo de segurança, carregando apenas o ambiente e os serviços padrão.

## <a name="syntax"></a>Sintaxe

```shell
devenv /SafeMode
```

## <a name="remarks"></a>Comentários

Essa opção impede que todos os VSPackages de terceiros sejam carregados quando o Visual Studio é iniciado, garantindo assim uma execução estável.

## <a name="example"></a>Exemplo

O exemplo a seguir inicia o Visual Studio no modo de segurança.

```shell
devenv /safemode
```

## <a name="see-also"></a>Consulte também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)