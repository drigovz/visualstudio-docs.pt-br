---
title: Como alterar o computador de reprodução de Diagnóstico de Gráficos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a41caf3f866c4a21d0a44fc69932066b2b7d923
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735058"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Como alterar a máquina de reprodução de diagnóstico do gráfico
Você pode reproduzir informações sobre gráficos usando seu computador local ou um computador remoto ou dispositivo.

## <a name="choosing-a-playback-machine"></a>Escolhendo um computador de reprodução
 O computador de reprodução é um computador ou dispositivo usado para reproduzir eventos gráficos de um log de gráficos. Normalmente, o computador local é a opção mais conveniente, mas um problema de renderização pode não ser reproduzido em um computador que tenha versões diferentes de hardware ou driver do computador onde ele foi capturado; Quando isso acontece, você pode escolher um computador de reprodução remota que reproduza melhor o problema e ainda usar seu computador de desenvolvimento para diagnosticar.

#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Para usar o computador local para reproduzir informações de gráficos

1. Na janela documento de log de gráficos, escolha o link **máquina de reprodução** . A caixa de diálogo **conexões do depurador remoto** é exibida.

2. Em **configuração manual**, na propriedade **endereço** , digite `localhost`.

3. Defina a propriedade **modo de autenticação** como **nenhuma**.

4. Escolha o botão **Selecionar**.

#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Para usar um computador remoto para reproduzir informações gráficas

1. Na janela documento de log de gráficos, escolha o link **máquina de reprodução** . A caixa de diálogo **conexões do depurador remoto** é exibida.

2. Em **configuração manual**, na propriedade **endereço** , insira o nome de domínio do Windows ou o endereço IP do computador ou dispositivo que você deseja usar para reproduzir informações gráficas.

3. Especifique o tipo de autorização que você deseja usar para proteger a conexão com o computador de reprodução.

    - Para a autenticação do Windows, defina a propriedade **modo de autenticação** como **Windows**.

    - Para sem autenticação, defina a propriedade **modo de autenticação** como **nenhuma**.

4. Escolha o botão **Selecionar**.

> [!NOTE]
> A caixa de diálogo **conexões do depurador remoto** também pode exibir destinos de depuração remota que estão diretamente conectados ao seu computador de desenvolvimento ou que estão na mesma sub-rede. Você pode usar um desses destinos de depuração remota como o computador de reprodução de Diagnóstico de Gráficos sem configurá-lo manualmente. Na caixa de diálogo **conexões do depurador remoto** , selecione o destino desejado e, em seguida, escolha o botão **selecionar** .

## <a name="see-also"></a>Consulte também
- [Documento de log de gráficos](graphics-log-document.md)