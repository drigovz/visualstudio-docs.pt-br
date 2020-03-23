---
title: Programa de Aperfeiçoamento da Experiência do Usuário
description: Descubra como gerenciar as configurações de privacidade no Visual Studio.
ms.date: 05/21/2018
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6c785b755b64f0dd7e367a01d9c05c1981ea558
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71693010"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Programa de Aperfeiçoamento da Experiência do Usuário do Visual Studio

O VSCEIP (Programa de Aperfeiçoamento da Experiência do Usuário do Visual Studio) foi projetado para ajudar a Microsoft a aperfeiçoar o Visual Studio ao longo do tempo. Esse programa [coleta informações sobre erros](../ide/diagnostic-data-collection.md), hardware do computador e como as pessoas usam o Visual Studio, sem interromper os usuários em suas tarefas no computador. As informações coletadas ajudam a Microsoft a identificar quais funcionalidades devem ser aprimoradas. Este documento aborda como aceitar ou recusar o VSCEIP.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]
> [!NOTE]
> As configurações de telemetria VSCEIP não se aplicam a 'Relatar um problema' no Visual Studio. Quando você reporta um problema, os registros são coletados e enviados para a Microsoft somente quando você fornece permissão clicando em 'Enviar'. Se você estiver interessado em gerenciar registros antes de enviar para 'Relatar um problema' consulte [Feedback Data Privacy](./developer-community-privacy.md) para obter mais detalhes.

## <a name="opt-in-or-out"></a>Aceitar ou recusar

O VSCEIP está ativado por padrão. Você pode desligá-lo ou ativá-lo novamente seguindo estas instruções:

1. No Visual Studio, escolha **Ajudar** > **enviar feedback**e, em seguida, selecione **Configurações**.

   A caixa de diálogo **Programa de Aperfeiçoamento da Experiência do Visual Studio** será aberta.

1. Para recusar, selecione **Não, prefiro não participar** e, em seguida, selecione **OK**. Para aceitar, selecione **Sim, desejo participar** e, em seguida, selecione **OK**.

   ![Caixa de diálogo Programa de Aperfeiçoamento da Experiência do Visual Studio](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Configurações do Registro

Se você instalar as [Ferramentas de Build do Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017), precisará atualizar o Registro para configurar o VSCEIP. Os clientes corporativos podem construir uma política de grupo para aceitar ou recusar sua participação no VSCEIP por meio da definição de uma política baseada em Registro.

Chave do Registro e configurações relevantes:

::: moniker range="vs-2017"

- Em um sistema operacional de 64 bits, Chave = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM**
- Em um sistema operacional de 32 bits, Chave = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM**
- Quando a diretiva de grupo está ativada, chave = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

::: moniker range=">=vs-2019"

- Em um sistema operacional de 64 bits, Chave = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\16.0\SQM**
- Em um sistema operacional de 32 bits, Chave = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\16.0\SQM**
- Quando a diretiva de grupo está ativada, chave = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

Entrada = **Optin**

Valor = (DWORD)

- **0** é optado por sair (desligue o VSCEIP)
- **1** é optado (ligar o VSCEIP)

> [!CAUTION]
> A edição incorreta do Registro poderá danificar seriamente o sistema. Antes de alterar o Registro, faça um backup dos dados importantes do computador. Você também pode usar a opção **de inicialização última configuração boa conhecida** se encontrar problemas após a aplicação de alterações manuais.

Para obter mais informações sobre as informações coletadas, processadas ou transmitidas pelo VSCEIP, confira a [Política de privacidade da Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="see-also"></a>Confira também

* [Informações de diagnóstico coletadas pelo Visual Studio](diagnostic-data-collection.md)
* [Opções de comentários do Visual Studio](../ide/feedback-options.md)
* [Como relatar um problema com o Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md)
* [Comunidade de desenvolvedores do Estúdio Visual](https://developercommunity.visualstudio.com/)
* [Política de Privacidade da Microsoft](https://privacy.microsoft.com/privacystatement)
