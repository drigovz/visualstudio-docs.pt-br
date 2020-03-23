---
title: Estender uma versão de avaliação ou atualizar uma licença
description: Aprenda a estender uma avaliação gratuita do Visual Studio, use uma assinatura online ou chave de produto para desbloquear o Visual Studio e atualize uma licença obsoleta ou expirada.
ms.date: 12/18/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 8e11d77a94c7c1d3d7b038ecea1a6c61646e371f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027575"
---
# <a name="extend-a-trial-version-or-update-a-license"></a>Estender uma versão de avaliação ou atualizar uma licença

Você pode avaliar um teste gratuito do [Visual Studio Professional ou Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/compare/) por 30 dias. E se você entrar, você pode estender o período de teste para 90 dias. (Visual Studio Community é gratuito sem um período de teste. No entanto, você deve [fazer login](signing-in-to-visual-studio.md) periodicamente para manter sua [licença atualizada](#update-a-stale-license).)

Para continuar usando o Visual Studio após o término de um período de teste, desbloqueie-o com uma [assinatura online](#use-an-online-subscription) ou uma chave [de produto](#enter-a-product-key).

## <a name="use-an-online-subscription"></a>Use uma assinatura online

1. Escolha o botão **Entrar no** canto superior direito do IDE (ou vá para**Configurações da conta de** **arquivo** > para abrir a caixa de diálogo **Configurações da conta** e, em seguida, escolha o botão Entrar **em).**

1. Insira as credenciais para uma conta da Microsoft ou uma conta corporativa ou de estudante. O Visual Studio encontrará uma Assinatura do Visual Studio ou uma organização do Azure DevOps associada à sua conta.

> [!IMPORTANT]
> O Visual Studio procura automaticamente assinaturas online associadas quando você se conecta a uma organização do Azure DevOps na janela de ferramentas do **Team Explorer**. Quando se conecta a uma organização do Azure DevOps, você pode entrar usando contas da Microsoft e corporativas ou de estudante. Se houver uma assinatura online para aquela conta de usuário, o Visual Studio automaticamente desbloqueará o IDE para você.

Para obter mais informações sobre as assinaturas do Visual Studio e como elas funcionam, consulte a página [de perguntas frequentes de suporte a assinaturas.](https://visualstudio.microsoft.com/subscriptions/support/)

## <a name="enter-a-product-key"></a>Inserir uma chave do produto

1. Selecione**Configurações da conta de** **arquivo** > para abrir a caixa de diálogo **Configurações da** conta e, em seguida, escolha a Licença com um link chave de **produto.**

1. Insira a chave do produto (Product Key) no espaço fornecido.

> [!TIP]
> As versões de pré-lançamento do Visual Studio não têm chaves de produto. Você deve entrar no IDE para usar as versões de pré-lançamento.

Para obter mais informações sobre as chaves de produtos do Visual Studio para o Visual Studio e como obtê-las, consulte as chaves de uso do produto na página [de assinaturas do Visual Studio.](/visualstudio/subscriptions/product-keys)

## <a name="update-a-stale-license"></a>Atualize uma licença obsoleta

Você pode ver uma mensagem no Visual Studio que diz: "Sua licença ficou obsoleta e deve ser atualizada."

![Mensagem de licença obsoleta do Visual Studio](../ide/media/vs2017_stale-license.png)

Esta mensagem indica que, embora sua assinatura ainda possa ser válida, o token de licença que o Visual Studio usa para manter sua assinatura atualizada não foi atualizado. Visual Studio relata que a licença está obsoleta por uma das seguintes razões:

* Você não usou o Visual Studio ou não se conectou à internet por um longo período de tempo.
* Você saiu do Visual Studio.

Antes de o token de licença ficar obsoleto, o Visual Studio mostrará primeiro uma mensagem de aviso que solicita que você insira suas credenciais novamente.

Se você não reinserir suas credenciais, o token começa a ficar obsoleto e a caixa de diálogo **Configurações da conta** informa quantos dias você ainda tem antes do seu token expirar. Depois que o token expirar, será preciso digitar novamente suas credenciais de conta para continuar usando o Visual Studio.

> [!Important]
> Se estiver usando o Visual Studio por longos períodos em ambientes com acesso limitado ou sem acesso à Internet, você deverá usar uma chave do produto (Product Key) para desbloquear o Visual Studio a fim de evitar uma interrupção.

## <a name="update-an-expired-license"></a>Atualize uma licença expirada

Se sua assinatura expirou e você não tem mais direitos de acesso ao Visual Studio, você deve renovar sua assinatura ou adicionar outra conta que tenha uma assinatura. Para ver mais informações sobre a licença que você está usando, vá para**Configurações da conta de** **arquivo** > e veja as informações da licença no lado direito da caixa de diálogo. Se você tiver outra assinatura associada a uma conta diferente, adicione essa conta à lista **Todas as Contas** no lado esquerdo da caixa de diálogo, selecionando o link Adicionar uma **conta.**

## <a name="get-support"></a>Obtenha suporte

Às vezes, as coisas dão errado. Se você tiver um problema, aqui estão algumas opções de suporte:

* Relatar problemas do produto usando a ferramenta [Relatar um problema.](how-to-report-a-problem-with-visual-studio.md)
* Encontre respostas para perguntas sobre assinaturas, contas e faturamento no [FAQ de suporte de assinaturas](https://visualstudio.microsoft.com/subscriptions/support/).

## <a name="see-also"></a>Confira também

* [Entrar no Visual Studio](../ide/signing-in-to-visual-studio.md)
* [Compare as edições do Visual Studio](https://visualstudio.microsoft.com/vs/compare/)
* [Saiba mais sobre as assinaturas do Visual Studio](/visualstudio/subscriptions/)
