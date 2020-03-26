---
title: Como usar as identidades conectadas da conta Microsoft e do Azure Active Directory | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: lank
ms.assetid: 50ce0445-ef1a-4e92-b9d0-aebb2155a111
ms.date: 03/11/2020
ms.topic: conceptual
robots: noindex, nofollow
description: Saiba como trabalhar com contas Microsoft conectadas e identidades do Azure Active Directory
ms.openlocfilehash: b88c978f330520af62f51e372db93475b71caa36
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233181"
---
# <a name="how-to-use-connected-identities-in-visual-studio-subscriptions"></a>Como usar identidades conectadas em assinaturas do Visual Studio
Se você receber uma assinatura do Visual Studio através do seu trabalho ou escola e usar sua conta Microsoft (MSA) para fazer login, o administrador de assinaturas pode conectar seu MSA à sua identidade no Azure Active Directory (Azure AD) da sua organização.  Isso mudará a forma como você acessa alguns dos benefícios incluídos em sua assinatura. 

## <a name="overview-of-connected-ids"></a>Visão geral dos IDs conectados
As organizações estão cada vez mais se movendo para as identidades baseadas no Azure AD para fornecer maior segurança e suporte para gerenciamento automatizado de assinaturas.  Se sua assinatura usar um MSA, como um @outlook.com ou outro endereço de e-mail pessoal, o administrador poderá alterar seu e-mail de login para sua identidade Azure AD.  Isso mudará a forma de entrar https://my.visualstudio.com no portal do assinante, mas pode não mudar a forma como você acessa todos os seus benefícios.  

Se o administrador conectar suas identidades MSA e Azure AD, você receberá um e-mail informando que começará a acessar sua assinatura do Visual Studio com sua identidade Azure AD em vez de seu MSA. 

## <a name="how-to-access-benefits-using-azure-ad-identities"></a>Como acessar benefícios usando identidades Ad do Azure
Depois que o seu administrador tiver conectado seu MSA à sua identidade Azure AD, https://my.visualstudio.com você precisará entrar no portal do assinante com sua identidade Azure AD para acessar benefícios que dependem do Azure AD.  Eles incluem:
- IDE do Visual Studio
- Azure DevOps
- Crédito individual do Azure DevTest

## <a name="how-to-access-benefits-using-your-msa"></a>Como acessar benefícios usando seu MSA
Para muitos dos benefícios oferecidos em assinaturas do Visual Studio, como Pluralsight, LinkedIn, CloudPilot e outros, você realmente cria contas de usuário nos sites dos parceiros.  Para essas contas, você deve continuar a usar a identidade que usou quando criou a conta.  Por exemplo, se você ativou seu benefício Pluralsight usando seu MSA, você deve continuar a usar seu MSA ao fazer o treinamento Pluralsight, independentemente da identidade que você usa para entrar no portal do assinante.  

## <a name="use-an-alternate-identity-to-access-your-subscription"></a>Use uma identidade alternativa para acessar sua assinatura
Adicionar uma conta alternativa à sua Assinatura do Visual Studio permite que você acesse os benefícios da assinatura, como o Azure DevOps e o Azure, com uma identidade diferente daquela à qual a assinatura está atribuída. No passado, essa funcionalidade estava disponível somente se a sua assinatura do VS (Visual Studio) fosse atribuída a uma conta da Microsoft (MSA). Nós estendemos essa funcionalidade para contas corporativas ou de estudante no Azure AD (Azure Active Directory).  Para obter mais informações sobre o uso de contas alternativas, confira nosso artigo [sobre identidades alternativas.](vs-alternate-identity.md) 

## <a name="frequently-asked-questions"></a>Perguntas frequentes
### <a name="q-how-can-i-contact-my-admin-about-this"></a>P: Como posso entrar em contato com meu pai sobre isso?
R: Consulte nosso [artigo de administrador de assinaturas](contact-my-admin.md) para obter informações sobre como entrar em contato com o administrador.  

## <a name="see-also"></a>Confira também
- [Documentação do Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentação do Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentação do Azure](https://docs.microsoft.com/azure/)
- [Documentação do Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Próximas etapas
Depois que seu administrador conectar suas contas Ad e MSA do Azure, recomendamos verificar se você pode entrar com sucesso no [portal de assinaturas](https://my.visualstudio.com?wt.mc_id=o~msft~docs) e acessar benefícios como Azure DevOps, Visual Studio e seu crédito individual Azure DevTest. 