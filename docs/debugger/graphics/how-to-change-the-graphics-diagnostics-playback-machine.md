---
title: 'Como: Alterar o computador de reprodução de diagnóstico de gráficos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33768ffd0784d6b1fc406400c2cabb94464cf0a8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945886"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Como: Alterar o computador de reprodução de Diagnóstico de Gráficos
Você pode reproduzir informações gráficas usando seu computador local ou por meio de um computador ou dispositivo remoto.  
  
## <a name="choosing-a-playback-machine"></a>Escolhendo um computador de reprodução  
 A máquina de reprodução é um computador ou dispositivo que é usado para reproduzir eventos de gráficos de um log de gráficos. Geralmente, o computador local é a opção mais conveniente, mas um problema de renderização não pode reproduzir em um computador que tenha um hardware diferente ou versões de driver da máquina onde ele foi capturado; Quando isso acontece, você pode escolher um computador de reprodução remoto que melhor reproduza o problema e ainda usar seu computador de desenvolvimento para diagnosticá-lo.  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Usar o computador local para reproduzir informações gráficas  
  
1.  Na janela do documento de Log de gráficos, escolha o **computador de reprodução** link. O **conexões remotas do depurador** caixa de diálogo é exibida.  
  
2.  Sob **Configuração Manual**, no **endereço** propriedade, digite `localhost`.  
  
3.  Defina a **modo de autenticação** propriedade **None**.  
  
4.  Escolha o botão **Selecionar**.  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Usar um computador remoto para reproduzir informações gráficas  
  
1.  Na janela do documento de Log de gráficos, escolha o **computador de reprodução** link. O **conexões remotas do depurador** caixa de diálogo é exibida.  
  
2.  Sob **Configuração Manual**, no **endereço** propriedade, insira o nome de domínio do Windows ou o endereço IP do computador ou dispositivo que você deseja usar para reproduzir informações gráficas.  
  
3.  Especifique o tipo de autorização que você deseja usar para proteger a conexão para o computador de reprodução.  
  
    -   Para autenticação do Windows, defina as **modo de autenticação** propriedade **Windows**.  
  
    -   Para nenhuma autenticação, defina as **modo de autenticação** propriedade **None**.  
  
4.  Escolha o botão **Selecionar**.  
  
> [!NOTE]
>  O **conexões remotas do depurador** caixa de diálogo também pode exibir os destinos de depuração remota que estão diretamente conectados ao computador de desenvolvimento ou que estão na mesma sub-rede. Você pode usar um desses destinos de depuração remotos como o computador de reprodução de diagnóstico de gráficos sem configurá-lo manualmente. No **conexões remotas do depurador** caixa de diálogo, selecione o destino desejado e, em seguida, escolha o **selecione** botão.  
  
## <a name="see-also"></a>Consulte também  
 [Documento de log de gráficos](graphics-log-document.md)