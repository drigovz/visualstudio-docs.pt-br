---
title: -SafeMode (devenv.exe)
description: Saiba como usar a opção de linha de comando devenv de modo de segurança para iniciar o Visual Studio no modo seguro, carregando apenas o ambiente e os serviços padrão.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1626776ec41bdbdfe5ad2b611516e62ada4f15a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957862"
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

## <a name="see-also"></a>Confira também

- [Opções de linha de comando do Devenv](../../ide/reference/devenv-command-line-switches.md)
