---
title: Referência de opções de contas
ms.date: 12/10/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: 3cfe09d2-1120-46e8-b882-f7056acb778b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ff457523024db49502ae982a390d9a7be6ba9dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595898"
---
# <a name="accounts-environment-options-dialog-box"></a>Caixa de diálogo Contas, Ambiente, Opções

Use essa página para definir várias opções relacionadas às contas que você usa para entrar no Visual Studio.

## <a name="personalization-account"></a>Conta de personalização

### <a name="synchronize-settings-across-devices"></a>Sincronizar configurações em todos os dispositivos

Use essa opção para especificar se deseja sincronizar as configurações em vários computadores. Para obter mais informações, confira [Configurações sincronizadas](../../ide/synchronized-settings-in-visual-studio.md).

### <a name="enable-device-code-flow"></a>Habilitar o fluxo de código do dispositivo

Quando essa opção é selecionada, o comportamento do Visual Studio é alterado quando você seleciona **Adicionar uma conta** na página **Arquivo** > **Configurações da Conta**. Em vez de ver a página **Entrar em sua conta**, você verá uma caixa de diálogo com uma URL e um código para colar em um navegador da Web para entrar. Essa opção é útil nos casos em que você não pode entrar no Visual Studio da maneira normal, por exemplo, se você usa uma versão mais antiga do Internet Explorer ou se o firewall restringe o acesso. Para obter mais informações, consulte [Trabalhar com várias contas de usuário](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow).

## <a name="registered-azure-clouds"></a>Nuvens do Azure registradas

Esta seção mostra as instâncias de nuvem do Azure às quais você tem acesso por meio de uma ou mais contas que você usa para entrar no Visual Studio. Por exemplo, talvez você tenha acesso a uma instância particular do Azure no data center de sua empresa. Ou você pode ter acesso a uma instância do soberanas ou governamental do Azure, como o Azure China 21 vianet ou o Azure U.S. governamental. A instância de nuvem global do Azure é exibida por padrão na lista e não pode ser removida.

Registre uma nuvem adicional do Azure escolhendo o botão **Adicionar**. A caixa de diálogo **Adicionar Nova Nuvem do Azure** lista várias instâncias de nuvem do Azure conhecidas às quais você pode se conectar ou você pode inserir a URL para um ponto de extremidade particular do Azure.

![Adicionar nova instância de nuvem do Azure](media/add-new-azure-cloud.png)

Depois de registrar uma nuvem adicional do Azure, você pode escolher à qual nuvem do Azure deseja se conectar quando entrar no Visual Studio.

## <a name="see-also"></a>Confira também

- [Sincronizar configurações em vários computadores](../synchronized-settings-in-visual-studio.md)
- [Entrar no Visual Studio](../signing-in-to-visual-studio.md)
- [Trabalhar com várias contas de usuário](../work-with-multiple-user-accounts.md)
- [Configurações do ambiente](../environment-settings.md)
