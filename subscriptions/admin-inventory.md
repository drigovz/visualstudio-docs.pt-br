---
title: Inventário de ambientes de pré-produção | Visual Studio Marketplace
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/17/2020
ms.topic: conceptual
description: Saiba mais sobre a responsabilidade dos administradores de realizar inventários de pré-produção
ms.openlocfilehash: 4dec93101cb7399da3cd493af38c0559f0ed9dee
ms.sourcegitcommit: c8b979a56c95e43cf8ae92b6c3c9570db59a8e58
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78894373"
---
# <a name="inventory-of-pre-production-environment"></a>Inventário do ambiente de pré-produção
As assinaturas do Visual Studio simplificam o gerenciamento de ativos ao contar usuários em vez de dispositivos.

Os administradores do Visual Studio devem atribuir assinaturas do Visual Studio a **pessoas específicas e determinadas**. As convenções de nomenclatura como Dev1, Dev2 ou o uso de nomes de equipe, como “FeatureTeam”, **não são permitidos**.

Aqui estão algumas maneiras para simplificar a realização do inventário do ambiente de pré-produção:
- Examine as atribuições de usuário. A Microsoft oferece um site chamado [Portal de administração do Visual Studio](https://manage.visualstudio.com/) para ajudá-lo a rastrear as atribuições de assinaturas do Visual Studio.
- Use seu Active Directory local ou baseado em nuvem para listar os usuários. Se você usa o Active Directory para gerenciar o acesso de usuários, talvez seja possível identificar usuários de desenvolvimento e teste de acordo com as respectivas associações de diretório.
- Use ferramentas automatizadas para inventariar sistemas. Talvez também seja necessário usar uma ferramenta de inventário de software para ajudá-lo a gerenciar os ativos de software e distinguir ambientes de pré-produção dos ambientes de produção. Muitos clientes com o Microsoft System Center criam convenções de nomenclatura para ajudar a automatizar essa parte do processo de inventário.
- Obter ajuda com a reconciliação manual. Inscreva a sua equipe para ajudar a reconciliar os usuários de desenvolvimento e teste com seu ambiente de desenvolvimento e teste.

## <a name="resources"></a>Recursos
- [White paper de licenciamento do Visual Studio](https://visualstudio.microsoft.com/wp-content/uploads/2019/06/Visual-Studio-Licensing-Whitepaper-May-2019.pdf)
- [Suporte à administração e às assinaturas do Visual Studio](https://visualstudio.microsoft.com/support/support-overview-vs)
- [Termos de licenciamento por volume](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="see-also"></a>Veja também
- [Documentação do Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Documentação do Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Documentação do Azure](https://docs.microsoft.com/azure/)
- [Documentação do Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Próximas etapas
Saiba mais as políticas dos administradores:
- [Responsabilidades do administrador](admin-responsibilities.md)
- [Gerenciar equipes grandes e prestadores de serviço externos](manage-teams.md)
- [Rastrear atribuição de usuário e processar pedidos](assignments-orders.md)
- Utilizar o [Uso Máximo](maximum-usage.md) para rastrear os compromissos de compra



