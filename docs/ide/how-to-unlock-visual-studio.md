---
title: 'Como: Desbloquear o Visual Studio'
titleSuffix: ''
ms.date: 03/30/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: fe0aa86be242e9a7e7ed8d877944c66247718167
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926296"
---
# <a name="how-to-unlock-visual-studio"></a>Como: Desbloquear o Visual Studio

Você pode avaliar o Visual Studio gratuitamente por até 30 dias. Entrar no IDE estende o período de avaliação para 90 dias. Para continuar usando o Visual Studio, desbloqueie o IDE:

- usando uma assinatura online

- inserindo uma chave do produto (Product Key)

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>Para desbloquear o Visual Studio usando uma assinatura online

Para desbloquear o Visual Studio usando uma Assinatura do Visual Studio, uma organização do Azure DevOps associada a uma conta Microsoft ou uma conta corporativa ou de estudante:

1. Escolha o botão **Entrar** no canto superior direito do IDE (ou acesse **Arquivo** > **Configurações de Conta** para abrir a caixa de diálogo **Configurações de Conta** e escolha o botão **Entrar**).

1. Insira as credenciais para uma conta da Microsoft ou uma conta corporativa ou de estudante. O Visual Studio encontrará uma Assinatura do Visual Studio ou uma organização do Azure DevOps associada à sua conta.

> [!IMPORTANT]
> O Visual Studio procura automaticamente assinaturas online associadas quando você se conecta a uma organização do Azure DevOps na janela de ferramentas do **Team Explorer**. Quando se conecta a uma organização do Azure DevOps, você pode entrar usando contas da Microsoft e corporativas ou de estudante. Se houver uma assinatura online para aquela conta de usuário, o Visual Studio automaticamente desbloqueará o IDE para você.

## <a name="to-unlock-visual-studio-with-a-product-key"></a>Para desbloquear o Visual Studio com uma chave do produto (Product Key)

1. Selecione **Arquivo** > **Configurações de Conta** para abrir a caixa de diálogo **Configurações de Conta** e, em seguida, escolha o link **Licenciar com uma Chave de Produto**.

1. Insira a chave do produto (Product Key) no espaço fornecido.

> [!TIP]
> As versões de pré-lançamento do Visual Studio não têm chaves de produto. Você deve entrar no IDE para usar as versões de pré-lançamento.

## <a name="address-license-problem-states"></a>Tratar os estados de problema de licença

### <a name="update-stale-licenses"></a>Atualizar licenças obsoletas

Talvez você tenha visto a mensagem a seguir que informa que sua licença ficará obsoleta no Visual Studio. A mensagem diz que "Sua licença ficou obsoleta e deve ser atualizada".

![Mensagem de licença obsoleta do Visual Studio](../ide/media/vs2017_stale-license.png)

Essa mensagem indica que embora sua assinatura ainda possa ser válida, o token de licença que o Visual Studio usa para manter sua assinatura atualizada ainda não foi atualizado e se tornou obsoleto devido a um dos motivos a seguir:

- Você não usou o Visual Studio ou não teve uma conexão com a Internet por um longo período.
- Você saiu do Visual Studio.

Antes de o token de licença ficar obsoleto, o Visual Studio mostrará primeiro uma mensagem de aviso que solicita que você insira suas credenciais novamente.

Se você não digitar novamente suas credenciais, o token começará a ficar obsoleto e a caixa de diálogo **Configurações da Conta** informará quantos dias você ainda tem até seu token expirar totalmente. Depois que o token expirar, será preciso digitar novamente suas credenciais de conta para continuar usando o Visual Studio.

> [!Important]
> Se estiver usando o Visual Studio por longos períodos em ambientes com acesso limitado ou sem acesso à Internet, você deverá usar uma chave do produto (Product Key) para desbloquear o Visual Studio a fim de evitar uma interrupção.

### <a name="update-expired-licenses"></a>Atualizar licenças expiradas

Se a sua assinatura tiver expirado completamente e você não tiver mais direitos de acesso ao Visual Studio, será necessário renovar sua assinatura ou adicionar outra conta que tenha uma assinatura. Para obter mais informações sobre a licença que você está usando, acesse **Arquivo** > **Configurações de Conta** e examine as informações de licença no lado direito da caixa de diálogo. Se você tiver outra assinatura associada a uma conta diferente, adicione essa conta à lista **Todas as Contas** no lado esquerdo da caixa de diálogo selecionando o link **Adicionar uma conta**.

## <a name="see-also"></a>Consulte também

* [Entrar no Visual Studio](../ide/signing-in-to-visual-studio.md)
