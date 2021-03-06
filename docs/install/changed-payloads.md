---
title: Quando os conteúdos do pacote são alterados após um lançamento
description: Ao criar um layout, saiba como determinar se os conteúdos do pacote foram alterados depois que uma liberação já foi enviada.
ms.date: 05/22/2019
ms.topic: how-to
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: bd0013df051def28c57552c0aeb733888d55e9b6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905550"
---
# <a name="package-payload-changes"></a>Alterações de conteúdo do pacote

Alguns conteúdos do pacote podem ser alterados após o lançamento de uma liberação. Quando você ou outra pessoa cria um layout, esse comportamento pode resultar em conteúdo de layout diferente, dependendo de quando um layout foi criado.

## <a name="verify-that-a-layout-includes-package-payload-changes"></a>Verifique se um layout inclui alterações de conteúdo do pacote

Confira como determinar se o layout que foi criado anteriormente adquiriu os conteúdos do pacote que foram modificados após o lançamento da versão:

1. Abra o log de instalação. O log normalmente está em `%TEMP%\dd_setup_[date].log`, em que `[date]` é quando a operação de layout é iniciada no formato `yyyyMMddHHmmss`.

2. Busque uma linha no log estruturada como o seguinte texto:

    `Falling back to signature and signer check because hash verification returned HashMismatch for path: [path]`

3. Em seguida, procure por linhas mais tarde no log que indiquem que o download foi bem-sucedido para o [caminho]. Elas podem ser semelhantes ao seguinte texto:

    `Download of [url] succeeded using engine 'WebClient'`

    `END: Downloading [url] to [path]`

## <a name="see-also"></a>Confira também

* [Criar uma instalação de rede do Visual Studio](create-a-network-installation-of-visual-studio.md)
* [Atualizar uma instalação em rede do Visual Studio](update-a-network-installation-of-visual-studio.md)
