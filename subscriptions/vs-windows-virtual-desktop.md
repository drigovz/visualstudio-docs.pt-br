---
title: Microsoft Windows Virtual Desktop beneficia em assinaturas do Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 04/20/2020
ms.topic: conceptual
description: Saiba como você pode tirar proveito do Microsoft Windows Virtual Desktop através da sua assinatura do Visual Studio
ms.openlocfilehash: 87911b1b7b6eb63eb85b64515d5d24755e4656e6
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649730"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>Acesse o Windows Virtual Desktop em assinaturas 
Os assinantes do Visual Studio agora podem usar seus créditos individuais de dev/teste do Azure para os serviços de Desktop Virtual do Microsoft Windows.  
O Windows Virtual Desktop é um serviço abrangente de virtualização de aplicativos e desktop em execução na nuvem. É a única infra-estrutura de desktop virtual (VDI) que oferece gerenciamento simplificado, windows 10 de várias sessões, otimizações para o Office 365 ProPlus e suporte para ambientes RDS (Remote Desktop Services, serviços de desktop remotos). Implante e dimensione seus desktops e aplicativos do Windows no Azure em minutos e obtenha recursos de segurança e conformidade incorporados.
Veja o que você pode fazer ao executar a Área de Trabalho Virtual do Windows no Azure:
- Configurar uma implantação do Windows 10 de várias sessões que fornece uma escalabilidade completa do Windows 10
- Virtualizar o Office 365 ProPlus e otimizá-lo para execução em cenários virtuais de vários usuários
- Fornecer áreas de trabalho virtuais do Windows 7 com Atualizações de Segurança Estendida gratuitas
- Trazer seu RDS (Serviços de Área de Trabalho Remota) existente, além de aplicativos e áreas de trabalho do Windows Server para qualquer computador
- Virtualizar aplicativos e áreas de trabalho
- Gerencie desktops e aplicativos do Windows 10, Windows Server e Windows 7 com uma experiência de gerenciamento unificada Para obter mais informações sobre o que você pode fazer com o Windows Virtual Desktop, assista ao [vídeo introdutório](https://docs.microsoft.com/azure/virtual-desktop/overview).

## <a name="use-windows-virtual-desktop-with-azure"></a>Use o Windows Virtual Desktop com o Azure 
Os assinantes do Visual Studio agora têm várias maneiras de usar as assinaturas do Azure para pagar pelos serviços de Desktop Virtual do Windows:
- [Créditos individuais do Azure DevTest](vs-azure.md).  Os assinantes que recebem créditos individuais do Azure DevTest como parte de suas assinaturas podem usar esses créditos para pagar pelos serviços de Windows Virtual Desktop.  O valor do crédito mensal depende do nível de subscrição.
- [Assinaturas do Azure DevTest Pay-as-you-Go](vs-azure-payg.md).  Você pode criar assinaturas do Azure e anexar um instrumento de pagamento para ter uma maneira perfeita de pagar pelo uso do Seu Windows Virtual Desktop. 
- [Oferta de devTest do Azure Enterprise Agreement](azure-ea-devtest.md).  Com esta oferta, os assinantes com Contratos Corporativos podem pagar pelo Windows Virtual Desktop com o Azure a preços com desconto. 

## <a name="requirements"></a>Requisitos
O Windows Virtual Desktop requer um Azure Active Directory (Azure AD) ao qual as VMs serão aderidas.  Os usuários devem ser membros deste Azure AD.  Existem duas opções para implementar o Azure AD:
- Azure AD Directory Services.  Para a maioria dos usuários, esta é a opção mais fácil de implementar.
- Uma máquina virtual executando uma promo ção do Controlador de Domínio.  Essa opção requer mais trabalho para configurar, mas oferece à maioria dos usuários um custo operacional menor.
Para ver uma lista completa de pré-requisitos para usar o Windows Virtual Desktop, visite a [página de visão geral](https://docs.microsoft.com/azure/virtual-desktop/overview#requirements)do Windows Virtual Desktop . 

## <a name="get-started"></a>Introdução 
Quando todos os seus pré-requisitos estiverem em vigor, você vai querer concluir várias ações para obter sua implementação no lugar.  Confira estes tutoriais para começar:
- [Criar um inquilino de área de trabalho virtual do Windows](https://docs.microsoft.com/azure/virtual-desktop/tenant-setup-azure-active-directory)
- [Crie um pool de host](https://docs.microsoft.com/azure/virtual-desktop/create-host-pools-azure-marketplace) usando o portal Azure
- [Gerenciar grupos de aplicativos](https://docs.microsoft.com/azure/virtual-desktop/manage-app-groups) para windows virtual desktop

## <a name="eligibility"></a>Qualificação
| Nível de Assinatura                                                 |     Canais                                            | Benefício                                                          | Renovável?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise (Standard)   | VL, Azure, Retail, | Disponível|  Sim          |
| Visual Studio Enterprise com GitHub Enterprise  | Vl | Disponível|  Sim          |
| Visual Studio Professional (Standard) | VL, Azure, Retail                                       | Disponível                                                             |  Sim             |
| Visual Studio Professional com GitHub Enterprise | Vl                                       | Disponível                                        |  Sim           |
| Visual Studio Test Professional (Padrão)                         | VL, Retail                                              | Disponível|  Sim          |
| Plataformas MSDN (Padrão)                                          | VL, Retail                                              | Disponível                                         |  Sim          |
| Visual Studio Enterprise (Standard)  | NFR<sup>1</sup> |Não disponível  | N/D |
| Visual Studio Enterprise, Visual Studio Professional (nuvem mensal) | Azure | Não disponível | N/D |

<sup>1</sup>  *Inclui: Não para revenda (NFR), FTE, Profissional Mais Valioso (MVP), Diretor Regional (RD), Microsoft Partner Network (MPN), Visual Studio Industry Partner (VSIP), Microsoft Certified Trainer, BizSpark, Imagine*

> [!NOTE]
> A Microsoft não oferece mais assinaturas anuais do Visual Studio Professional e do Visual Studio Enterprise nas Assinaturas na Nuvem. Não haverá nenhuma alteração na experiência dos clientes existentes nem na capacidade de renovar, aumentar, diminuir ou cancelar suas assinaturas. Novos clientes são incentivados a [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/) ir para explorar diferentes opções para comprar o Visual Studio.

Não tem certeza de qual assinatura você está usando?  Conecte-se [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs) para ver todas as assinaturas atribuídas ao seu endereço de e-mail. Se não vir todas as suas assinaturas, talvez você tenha uma ou mais atribuídas a outro endereço de email.  Você precisará entrar com esse endereço de email para ver as assinaturas.

## <a name="see-also"></a>Confira também
- [Documentação do Azure](https://docs.microsoft.com/azure/)
- [Documentação do Windows Virtual Desktop](https://docs.microsoft.com/azure/virtual-desktop/)

## <a name="next-steps"></a>Próximas etapas
-   Se você precisa comprar assinaturas do Visual Studio, confira:
     - [Preços para compras no varejo](https://visualstudio.microsoft.com/vs/pricing/) através da Microsoft Store
     - [Programas de licenciamento de volume](https://www.microsoft.com/licensing/default)
-   Conheça o [Windows Virtual Desktop](https://docs.microsoft.com/azure/virtual-desktop/overview) 
